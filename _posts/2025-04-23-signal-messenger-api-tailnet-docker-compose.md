---
title: A Signal messenger API on your tailnet with Docker Compose
layout: post
tags:
    - programming
    - signal
    - tailscale
    - docker
image: /assets/images/signal-from-python.png
image_alt: "REPL view showing a Python command to POST a request to signal/v2/send and a Signal messanger window showing a received message."
---

I've got a new configuration for sending Signal messages on the command line, and it's powerful and flexible and finally gives me a nice ergonomic interface to use from other programs. Even cooler, it is accessible over Tailscale from any of my devices, which means I can securely reach it from multiple machines without going through the rigmarole of configuring and maintaining multiple copies of `signal-cli`.

In a nutshell, I'm using Docker Compose to spin up [this containerized version of `signal-cli`](https://github.com/bbernhard/signal-cli-rest-api) that exposes a REST API, with Tailscale in a sidecar container for its network mode. From the (cloud) machine where it's running, the API is accessible at `127.0.0.1:8080`, and from my other tailnet devices, it's at the host `signal`. From a security perspective this is especially neat, because its ensures that all of the otherwise unencrypted requests are going through the Wireguard tunnels that Tailscale sets up.

The end result is I can send Signal messages with `curl` or `requests` or whatever, from any of my devices. If I want to be really slick, I can use just the hostname, for a command like:

`curl -X 'GET' 'signal/v1/accounts'`

The container offering the API appears as a "machine" in my Tailscale admin console, and access is controlled with my ACLs.

Here's my full Docker Compose file. A lot of this is pretty [standard for a Tailscale sidecar, as seen in the big guide blog post](https://tailscale.com/blog/docker-tailscale-guide), but I will get into some fun parts below.

```yaml
---
services:
  ts-signal:
    image: tailscale/tailscale:latest
    container_name: ts-signal
    hostname: signal
    environment:
      - TS_AUTHKEY=tskey-client-n0tr3aLLy474115c413k3y101?ephemeral=false
      - TS_EXTRA_ARGS=--advertise-tags=tag:server
      - TS_STATE_DIR=/var/lib/tailscale
      - TS_AUTH_ONCE=true
    volumes:
      - ${PWD}/state:/var/lib/tailscale
      - ${PWD}/config:/config
    devices:
      - /dev/net/tun:/dev/net/tun
    ports:
      - 127.0.0.1:8080:80
    cap_add:
      - net_admin
      - sys_module
    restart: unless-stopped
  signal-api:
    image: bbernhard/signal-cli-rest-api
    container_name: signal-api
    network_mode: service:ts-signal
    depends_on:
      - ts-signal
    volumes:
      - /path/to/your/.local/share/signal-cli:/home/.local/share/signal-cli
    environment:
      - MODE=native
      - PORT=80
    restart: unless-stopped

volumes:
  signal-api:
    driver: local
  ts-signal:
    driver: local
```

Before we go through the fun parts, let me lay out the end state I was working towards:

- for compatibility reasons, I want the API to available from the host machine itself at `localhost:8080`
- for external access, I want the API to be available over Tailscale at a memorable domain (without requiring a port number)
- I want the API to "play nice" with an existing `signal-cli` install. I almost didn't dare to dream that I'd be able to use my existing config, but (spoiler alert) I think that's possible

I was able to get all those things. Stepping through the interesting portions:

```yaml
      - TS_AUTHKEY=tskey-client-n0tr3aLLy474115c413k3y101?ephemeral=false
      - TS_EXTRA_ARGS=--advertise-tags=tag:server
      - TS_STATE_DIR=/var/lib/tailscale
      - TS_AUTH_ONCE=true
```

These are all magic Tailscale environment variables. The one thing I'll note is that I'm using [an OAuth client secret](https://tailscale.com/kb/1282/docker#ts_authkey) here instead of an authkey so I don't have to worry about cycling it. That in turn requires the `--advertise-tags` bit is passed to the `TS_EXTRA_ARGS`.

```yaml
ports:
      - 127.0.0.1:8080:80
#and later, under the signal-api service:
environment:
      - MODE=native
      - PORT=80
```

This was my tricky approach to making the API available locally at `:8080` and remotely without a port number. The `PORT` variable for `signal-api` makes it available at `:80`, which is the standard unencrypted HTTP port; the Tailscale `network_mode` makes it so that you can hit that container, and its port 80, through normal Tailscale addressing. And because the container is just a machine on the tailnet, you can grant or restrict access to it through your normal ACL configuration.

I thought I was going to use [tailscale serve](https://tailscale.com/kb/1242/tailscale-serve) for this, but it kept not working exactly the way I wanted. I think it has to do with the fact that the Signal API container serves (a 404) on port 80 even when it's using a higher port for the main stuff, but that's kind of speculation. In any case, this ended up working great. If you skipped the Tailscale container ports line, the API is just available at the Tailscale address, which is not a bad outcome either.

One other note on the `ports` field: a lot of docs I saw for the Signal API container suggested configurations like `8080:8080`, which maps the container's `8080` to the host machine's `8080`. I would guess most users actually want to bind that to a specific IP address! Without an additional specification, it is set to `0.0.0.0`: available on all interfaces. Maybe fine for a network of only trusted devices but I don't know, man. Bind your ports.

```yaml
volumes:
      - /path/to/your/.local/share/signal-cli:/home/.local/share/signal-cli
```

This one surprised me at first, but: as far as I can tell, you can really point a host and container `signal-cli` at the same config directory and they'll share state. So if you're already configured, this plays nicely and just gives you more powers. If you want to keep them separate, then point this volume elsewhere. One small gotcha: by default the config directory is at `$HOME/.local/share/signal-cli`, but Docker Compose doesn't expand the `$HOME`, so you may want to hard-code the path in there.

With this set-up, I can keep the Signal factors separate from my other deployment considerations. For little things like my [server to send Puzzmo results to a Signal group](https://parkerhiggins.net/2025/04/webhooks-to-signal-groups-tailscale-puzzmo/), or the [personalized messages from my Helping Friendly Bot](https://parkerhiggins.net/2025/04/realtime-bluesky-events-jetstream-for-helping-friendly-bot/), it's so much simpler to be able to put those anywhere I can make a network request, and manage all of my Signal stuff in one place. 