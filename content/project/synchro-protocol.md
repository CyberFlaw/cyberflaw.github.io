---
title: "Synchro Protocol"
date: 2022-12-25T02:06:39+05:30
draft: false
---

### History

This is an ongoing project as a part of the Senior Year project. This protocol will be used for real-time audio transmission/streaming over TCP

### How it works

It's a network protocol with many parts left to decide. We have to build and benchmark and find the optimal sizes of packets and segments in the packets. This protocol sits inside the TCP data part. It consists of a part to identify the codec, the packet type, and the data itself. There may be changes to this! It will be built using *Rust*
