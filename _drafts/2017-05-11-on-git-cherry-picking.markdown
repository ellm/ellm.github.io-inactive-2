---
layout: post
title:  "Git Cherry Picking"
date:   2017-05-11
categories: tooling
---

I found myself in a situation where I needed to keep the code in two different repositories in sync. A problem occurred when I realized that several files were missing in a pull requests for repository (B) but existed in a pull request for repository (A). 

It was not clear to me why these files were not appearing. The commits were shown history and