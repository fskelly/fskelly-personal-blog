---
title: "Z-Wave Plug and Washing Machine Notifications"
date: 2022-03-03T11:29:18Z
Description: ""
Tags: [node-red, home assistant, notification]
Categories: [power-monitoring]
DisableComments: false
author: "Fletcher Kelly"
series:
  - home-automation
---

In this post, I show you how I use a Z-Wave Plug (Fibaro) to get more monitoring around power consumption and then use this to drive notifications.

Where we live now, our washing machine is a "utility room" and we keep the door closed from a noise point of view. With this setup it is possible to miss when the washing is complete and the washing makes no noise to indicate that the washing is compete and this can lead to issues. Have you ever smelled washing that was forgotten? :confounded:  

So how did I do this?

## Ingredients

In my case, I used **z-wave** as this is what i had, other technology can be used.

1. Z-Wave or other Power Monitoring Capable plug
1. Z-Wave Stick (Z‐Stick Gen5 USB Controller)
1. [Node-RED](https://nodered.org/)
1. [Home Assistant](https://home-assisatnt.io)
1. Home Assistant companion app
1. Washing Machine use counter *(optional)*
1. Washing Machine running time *(optional)*

## Process

I setup the Z-Wave Plug and started to plot the power usage over a few cycles to get a better understanding of how i could monitoring this. The challenge with the current washing machine is that there are "quiet periods" in the usage whether the usage drops really low. I originally tried to use [node-red-contrib-power-monitor](https://flows.nodered.org/node/node-red-contrib-power-monitor) which I have used successfully in the past, however I could find the correct "on" and "off" count value. This emphasizes the importance of **TESTING**. Make no error, I will use [node-red-contrib-power-monitor](https://flows.nodered.org/node/node-red-contrib-power-monitor) for other projects.

## So how did I solve this?

I noticed that there was a distinct power usage of "0.4W" when the cycle was complete so I decided to use 2 [Trigger State](https://zachowj.github.io/node-red-contrib-home-assistant-websocket/node/trigger-state.html#configuration) nodes in [Node-RED](https://nodered.org/).  

1. For when the usage goes above 2.1W, based upon my earlier testing this was a guaranteed start point to start the washing cycle.
1. For when the usage drops to 0.4w, this signals that the load is complete and notifications can be fired.
