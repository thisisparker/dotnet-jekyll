---
title: You can't fork your own GitHub repo (but you can get pretty close)
layout: post
tags:
    - programming
    - github
---

I wanted to fork my own GitHub repo the other day, and it turns out you can't. Instead, I got most of what I needed by duplicating the repo, and adding the original [as a second remote](https://docs.github.com/en/get-started/git-basics/managing-remote-repositories).

Why would you even want to fork your own repo? Here's my situation. In my [last blog post](/2025/06/generating-infinite-sea-shanty-in-the-browser/), I embedded a small page with some javascript to play the audio I was describing. I'm actively working on that code, and to be able to look at it remotely or share it with friends, I've got a small Action that builds the single page and pushes to GitHub Pages.

I could've just embedded the resulting page, but it's under active development and I don't want to accidentally break something in the blog post. Really, I want a snapshot — but I also want to be able to deliberately pull in changes to that snapshot as necessary.

Usually that would mean you could just make a branch. But in this case I wanted a Pages environment, which is allotted at the repo level.

So instead, I cloned the repository, pushed it to a new GitHub repo, and then used `git remote add` to add back the Git URL of the original repo as a second remote. That preserves the shared history, and I can even commingle commits. You don't quite get the interface sugar of pull requests across the two repos, but you can pull upstream changes into a downstream branch and open a PR that way.

One other option I considered: You *can* fork your own repo into one owned by an [organization](https://docs.github.com/en/organizations/collaborating-with-groups-in-organizations/about-organizations), so if I were doing this workflow a lot, maybe I'd make an organization that just owns blog-embedding-related repos. For now, though, the duplicated repo did the trick.