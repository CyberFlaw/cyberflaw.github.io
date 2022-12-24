---
title: "Coordinox - Pointing Device"
date: 2022-12-25T02:06:17+05:30
draft: false
---

### History

This project was built as a part of the Mini Project for the even semester of Junior year. Upon searching for ideas, we came across a device that can identify gestures and read sign language. We modified that idea and thought...

We have projectors in our classes right, why do teachers have to use a mouse or trackpad to move the cursor? Why can't we build something that can make a device that can make the projection like a touch screen or a smart classroom? And that's how this idea came to birth

### How does this device work

This device works on the basis of the relative position of the device in the room, which means this won't work in an open arena. We had to make this choice as we didn't have a *gyroscope censor* in stock and the timeline was a bit tight. So the device has to go through 2 step calibration process before use. You have to mark the bottom left corner and top right corner of the projection from the projector. With some easy math, we can compute the relative positions of the device with respect to the projection. Then we can scale down the points and give software clicks and drags at the point where the device is activated

### What is used to build this device

*ESP32 NodeMCU* is at the heart of the device. It's connected to 2 *ultrasonic censors* which measure X and Y distance with respect to the room. The device connects to a PC by *WiFi*. Through *WiFi*, the data is sent by a Codec. A *Python* script is running on the receiving end which decodes the data and generates the software interrupts. This should be ideally done in a compiled language. Due to time constraints, we were unable to do the same. Thus the script became really laggy and inaccurate
