---
title: Cascading GitHub Action workflows for rebuilding static sites
layout: post
tags:
    - programming
image: /assets/images/ithaca-waterfall.jpg
image_alt: A waterfall cascades over rocks in Ithaca.
---

A common pattern for building static sites on GitHub Pages (or similar) is to just trigger a new build every time there's a change in the repository. This is very straightforward and well-tested, and works until you want to also trigger builds when something changes _outside_ the repo. Then you run into some issues — but the solution, which took me some time to hunt down, turns out to be simple. The trick is specifying the right `ref` in your build workflow, and I explain why below.

In my case, there's a `build-and-deploy` workflow that's triggered on every new push to `main`. Then there's also a `fetch-new-data` workflow that runs on a cron schedule and checks an external data source for updates. (Conveniently, [that external data source can be a Google Sheet](https://parkerhiggins.net/2025/05/google-sheets-database-for-projects/).) If there is new data, it's formatted correctly and committed to the right place in the repo.

At first I thought that would be the whole story, because the new commit would automatically kick off a new build process. That didn't happen. It turns out GitHub Actions has a [(reasonable!) security feature](https://docs.github.com/en/actions/how-tos/writing-workflows/choosing-when-your-workflow-runs/triggering-a-workflow#triggering-a-workflow-from-a-workflow) that prevents tasks performed using the repository's `GITHUB_TOKEN` from setting off new workflow runs, in order to prevent accidental infinite loops. My `fetch-new-data` workflow included a very default set-up of [the `actions/checkout` Action](https://github.com/actions/checkout), which uses that default repository token, so I was affected.

As far as I can tell, there are two approaches to fixing this. One would be to reconfigure the `fetch-new-data` workflow to _not_ use the default token. Generate a [personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) with the appropriate permissions, and tell the `checkout` action to use that instead. I didn't go that route, but I think that's what [this tutorial describes](https://masteringlaravel.io/daily/2024-11-20-have-one-github-action-trigger-another).

I opted instead to have the `fetch-new-data` workflow explicitly call the `build-and-deploy` workflow if there was a change. I [reconfigured the `build-and-deploy` workflow to be reusable](https://docs.github.com/en/actions/how-tos/sharing-automations/reusing-workflows) with an `on: workflow_call:`, added the `uses` block to my calling workflow, and sat back and waited for it to work.

Once again, it did not. I could get it to trigger the build step, but the deployed site did not reflect the latest change. How annoying! I thought maybe it was some kind of race condition where the new commit hadn't fully propagated, or there was some kind of caching involved. I tried a lot of silly and complicated things to address those two perceived problem areas.

As it turns out, I was close, and the answer is simple. In my case, the `build-and-deploy` workflow was also using a very default set-up of the `checkout` Action. If you don't provide an explicit `ref` there, it falls back to whatever the current `GITHUB_SHA` value is. In the case of a `workflow_dispatch`/`workflow_call` setup, the called workflow [uses the `GITHUB_SHA` of the calling workflow](https://docs.github.com/en/actions/reference/events-that-trigger-workflows#workflow_call). The calling workflow, in turn, uses the `ref` of the state of the repo when it ran, which did not include the commit it performed.

So the fix was to set an explicit value for `ref` in the `checkout` step of the called workflow. I think hard-coding `main` probably works in almost all cases, but [I used `github.ref_name`](https://docs.github.com/en/actions/reference/accessing-contextual-information-about-workflow-runs#github-context) for just a touch more class.

I'm using this in two places now. One is in the repo for this very site, where a script that fetches my most recent movies, books, and concerts from various data sources can update a file here that gets incorporated into a Jekyll include. That info is now on my home page, but the "embed" here should also be live data, which is fun.

{% include recently.html %}

The data sources for those are my Letterboxd account's RSS feed, my Goodreads account's RSS feed, and a Google Doc of concerts that I maintain, but it's neat to know that I could easily point the script somewhere else if I ever wanted to move away from those sites.

The other is on [Malaika's personal site](https://malaikahanda.com/), where changes in her spreadsheet trigger new builds with updated calendar data.

Writing this out, I realize that there are a zillion ways to solve this problem. Most of them I discarded not because they wouldn't work, but because they felt inelegant. I could've just used a personal access token, but that felt dicey on the least privilege principle. I could've just copied and pasted the build workflow steps into the fetch workflow, but that felt like it was unnecessarily repetitive. I'm happy to have landed on a solution where everything works like it feels like it should.
