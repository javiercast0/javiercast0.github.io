---
layout: default
title: Tailscale
nav_exclude: true
---

<div align="right">
  <a href="../tailscale"><strong>Español</strong></a>
</div>

## What is Tailscale? 🛜

Tailscale lets us, among other things, create a VPN tunnel between our devices. I love it because, as a local solution, it’s amazing—you don’t have to deal with your ISP to get out of CG-NAT and it works really well. It’s basically the gateway that lets us connect our server to our devices when we're away from home.

It’s one of those services where it’s hard to believe the free plan is actually this good (and let's hope it stays that way). Thanks to this, we can access our Samba shared folders, use RustDesk to remote control our devices without relying on third-party companies, or watch our videos and photos through Jellyfin...

I’m not going to go into full detail on how to set it up or install it on clients; it’s super simple and you just need to log in with your Google account. This is the process we’ll set up on our server or the device we'll keep running 24/7.

### Installation:
Open your docker-compose and paste the following:
```bash
  # Tailscale
  tailscale:
    image: tailscale/tailscale:latest
    container_name: tailscale
    hostname: raspberrypi
    restart: unless-stopped
    network_mode: 'host'
    environment:
      - TS_AUTHKEY=PUT YOUR KEY HERE
      - TS_STATE_DIR=/var/lib/tailscale
      - TS_USERSPACE=false
    volumes:
      - /your-docker-folder/tailscale/state:/var/lib/tailscale
    devices:
      - /dev/net/tun:/dev/net/tun
    cap_add: [net_admin]
```
### Things to change:
Under **TS_AUTHKEY=** you need to create a key on the Tailscale website in your profile and put it there. Also, remember to change the path in the **volumes** section to match your own docker project folders

You can do a ton of other things like creating subnets (I have one for my local network). Here we’re just configuring the basics to get it running, but I highly recommend checking out the documentation if you need anything else, because you can probably do it.

### How to use it
Just install Tailscale on your clients and log in with the same account. That’s it, super easy. When you’re out of the house, just use the IP that Tailscale gives your server and all your services should work exactly the same.