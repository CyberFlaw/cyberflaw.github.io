---
title: "Binge Watch"
date: 2022-12-25T02:36:03+05:30
draft: false
---

### History

This idea originated during the lockdown period. One of my friends and I were talking and suddenly he told that it would be nice if we all could see a movie together, at the same time. And this was the idea behind Binge Watch.

### How it works

It asks all the users to download and load a video file into memory. After everyone is finished loading, everyone's media controls for the HTML video element (except volume) will be linked by *WebSockets* (*Socket.io*). This allows people to play and pause and seek and everyone will see the changes.

### Current State

It was deployed in Heroku. After they dismantled the free tier, we didn't bother to redeploy on some other platform. And as I mentioned before the entire video will be loaded into the memory. This will cause problems for lower-end machines. Buffering the inputs is an option, but it's not implemented yet.
