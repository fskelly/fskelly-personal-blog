---
title: "Home Assistant Routing"
date: 2022-10-07T09:12:38+01:00
Description: ""
Tags: [nmcli, networking]
Categories: [Home Assistant]
DisableComments: false
draft: false
---

## What?

I am a tinkerer by nature and I often need to move hy Home Assistant instances around and by this, I mean create new instances and DEV versions. As complication of this, sometimes my [UNIFI](https://account.ui.com/login) controller in not available and as such the following components are not available to me.

1. DHCP
2. VLans
3. Full DNS
4. Routing between Vlans

As a geek, I do not allow this to deter me

## The fix

The fix is quite easy if you understand your networking and you have access to the [Home Assistant Terminal](https://github.com/hassio-addons/addon-ssh). This can also be achieved with a physical connection (keyboard and mouse) or an SSH session to the Home assistant Instance.

I have a few vlans and ranges in my network and I need access to the following ranges. I have subnetted for smaller ranges.

1. 192.168.37.0/25 (CIDR 1)
2. 192.168.32.0/26 (CIDR 2)
3. 192.168.1.254 (Router)
4. Network card name (Supervisor enp0s25)

you will need to know the IP address of your router

```bash
nmcli connection show
nmcli connection modify "Supervisor enp0s25" +ipv4.routes "192.168.37.0/25 192.168.1.254"
nmcli connection modify "Supervisor enp0s25" +ipv4.routes "192.168.32.0/26 192.168.1.254"
```

This will take care of the Linux piece from Home Assistant. I have a Windows machine and my machine needs access to the same resources. I chose not to add these as persistent routes as usually the outage is limited and my Unifi and full functionality is usually restored quite quickly.

```powershell
route ADD 192.168.37.0 mask 255.255.255.128 192.168.1.254
route ADD 192.168.32.0 mask 255.255.255.192 192.168.1.254
```
