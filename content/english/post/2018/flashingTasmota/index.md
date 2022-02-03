---
title: "Sonoff Flashing Tasmota"
date: 2018-08-12T13:04:05+02:00
Description: ""
Tags: ["sonoff","tasmota"]
Categories: []
DisableComments: true
author: "Fletcher Kelly"

---

So, there are a ton of useful guides out on the internet and YouTube on how to do this as they are really detailed, for example, I was using this [one](https://www.youtube.com/watch?v=KMiP9Ku71To) by [DrZzs](https://www.youtube.com/channel/UC7G4tLa4Kt6A9e3hJ-HO8ng) and this is a great tutorial and this post this my "issues" and troubleshooting would not have been possible without the great tools mentioned by [DrZzs](https://www.youtube.com/channel/UC7G4tLa4Kt6A9e3hJ-HO8ng), such as [Termite](https://www.compuphase.com/software_termite.htm) and of course the amazing [Tasmota firmware by Theo](https://tasmota.github.io/docs/).

So I was carefully following the process of using the FTDI adapter and then selecting the correct firmware, sonoff.bin from the repository and I was able to successfully flash the firmware onto my Sonoff Basic and "backlog" the required settings, I was feeling pretty good. So now it was time to start playing and connecting my device to my wireless network. So, 4 button presses and wait for a new WiFi network to appear so that you can connect and make the required changes on the web interface. So after around 2 minutes of waiting and nothing appearing, a simply power cycle might resolve this issue. I followed this process a few times in the hopes that the "glitch" would go away. No such luck, **TROUBLESHOTING TIME**.

## **Troubleshooting**

So thanks to [Termite](https://www.compuphase.com/software_termite.htm) this was made a lot, simply open the software and start following what is going on at a serial level, so I start following the messages and it tries to connect to the network and fails and when it fails, it still does not create a network. I even think hey maybe it is my hidden SSID and try to get the Sonoff to connect to my mobile hotspot, no joy. So far,

Device flashed ✅  
Device does not create the required WiFi network for configuration ❌  
Device does not connect to hidden SSID ❌  
Device does not connect to shown SSID ❌  

So enter our dear friend, [Uncle Google](www.google.com) and I start searching and I came across an entry of the Github page for [Tasmota](https://github.com/arendst/Sonoff-Tasmota) and someone mentions that flashing to the minimal firmware can help. So I find the required file and flash it onto Sonoff Basic as below and it magically works, so for the troubleshooting this has helped as I now know that my flashing process and understanding of the settings with Termite is correct.

So now that I have a working Sonoff Tasmota interface, try to perform in inline upgrade to the Sonoff.bin firmware and the same issue occurs as before. So what now? More searching and I come across a sonoff-classic.bin, slightly smaller in size and I follow the process I know to be working and it starts working. I am busy investigating the issue with the sonoff.bin file with my Sonoff Basic.

So, if you run into a strange issue, like me, this might just be a hardware issue. Remember there is a sonoff-classic.bin, with some limitations.