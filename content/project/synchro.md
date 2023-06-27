---
title: "Synchro"
date: 2022-12-25T02:06:39+05:30
draft: false
---

### History

This was a project done as my final year project for my Engineering course. This is used to stream real-time audio transmission/streaming over TCP

### How it works

It's a network protocol with many parts left to decide. We have to build and benchmark and find the optimal sizes of packets and segments in the packets. This protocol sits inside the TCP data part. It consists of a part to identify the codec, the packet type, and the data itself. There may be changes to this! It will be built using *Rust*

It consists of two parts. Raw audio reading and writing from the systems default audio api(currently only implemented for Linux, ALSA). The raw audio buffers are fetched and its then send to other client devices by levraging on a custom protocol build over TCP. This protocol can also be used over UDP as it doesnt alter any of TCP's core functionalities. This protocol works on 3 steps.

+ Step 1: The handshake. Server waits for all the client to connect. During the handshake, info like raw audio format, channel, sample rate of the server are shared to the clients.After the clients update the config with the recived data it responds with a handshake with its name and other metadata which can be expanded upon need.

+ Step 2: Init signal. Here a init signal is broadcased to all the clients by the server. After this signal is recived the clients are expected to recive the continous raw audio stream from the server and write it to its local audio buffer.

+ Step 3: Audio broadcast. The raw audio is transmitted continosly form the server to all its clients

+ Step 4: Termination. The server sends a terminate signal to all the clients. This gracefully terminates the processess in all the local systems

This can be used to stream raw audio from one device to another with minimal lag. By using UDP and some more proper latency correction we can use this protocol for a MIDI server for live perfomances and concerts
