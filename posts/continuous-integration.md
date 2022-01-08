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

My Yaml file runs whenever anything's pushed to the main branch of the repo, takes a copy of the latest code, builds it using `actions-eleventy` and then copies it over to my web host. Decent.

What I might do is setup a staging repo and sub-domain, in case I want to work on any major changes but, for now, that's good enough for a Saturday night.

NB I appreciate that there's more to Continuous Integration than just this, calm doon.
