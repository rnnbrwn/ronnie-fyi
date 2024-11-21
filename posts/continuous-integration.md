---
title: Continuous Integration
description: How I setup this site to auto-deploy to my Dreamhost server
date: 2022-01-08 20:17:00
tags:
  - web development
layout: layouts/post.njk
---

Three posts in and I've already taken a week off from the site!

Well, that's not strictly true. I've been working (time permitting) on trying to get the site to automatically deploy to my hosting server, from the Github repo in which the code resides. I think I've got it now, so we're cooking with gas from here on out.

I referenced a few resources when trying to come up with a solution.

## Watch and Learn

**Deploy To Shared Hosting With Github Actions** from the **Watch and Learn** YouTube channel was my starting point, and from this, I managed (eventually, I had a few problems with Github's secrets) to move code from one place to another.

<iframe width="560" height="315" src="https://www.youtube.com/embed/UNWIXYSZfZY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## TartanLlama and mfyz

The goto Github Action for building Eleventy seems to be TartanLlama's [action-eleventy](https://github.com/TartanLlama/actions-eleventy), however, I had some problems with its optional inputs, and ended up using a fork of this, by [mfyz](https://github.com/mfyz/actions-eleventy). I'll probably revisit this (as I will with the whole process) because there's no reason TartanLlama's shouldn't work.

And that's that.

My `yaml` file runs whenever anything's pushed to the main branch of the repo, takes a copy of the latest code, builds it using `actions-eleventy`, and then copies it over to my web host. Decent.

What I might do is setup a staging repo and sub-domain, in case I want to work on any major changes but, for now, that's good enough for a Saturday night.

NB I appreciate that there's more to Continuous Integration than just this, calm doon.

## Update

Immediately after I posted this, the build/deployment process stopped working. For about an hour I tried a few different things, and then I headed over to the 11ty Discord channel.

On a Saturday night, a user called **Aankhen** took me through the issue I was having, jumped into my repo and flagged any `yaml` syntax issues (there were a few!) and basically held my hand as I fixed the problem. What a hero. Here's to you, Aankhen! 🍺

### Change to the build process

As a result of Aankhen's help, I'm no longer using the Action I mentioned above - and I never really needed to - so the process is even simpler now.

## Resources

- [My build-production.yml](https://github.com/rnnbrwn/project_ronnie.fyi/blob/main/.github/workflows/build-production.yml)
- [Deploy to Shared Hosting Using Github Actions](https://www.youtube.com/watch?v=UNWIXYSZfZY)
- [TartanLlama's repo](https://github.com/TartanLlama)
- [mfyz's repo](https://github.com/mfyz)
- [11ty Discord](https://discord.gg/GBkBy9u)
