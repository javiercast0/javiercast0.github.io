---
layout: default
title: Jellyfin
nav_exclude: true
---

<div align="right">
  <a href="../jellyfin"><strong>Español</strong></a>
</div>

## What is Jellyfin?

Jellyfin is an open-source media server that allows you to organize and stream local video and audio files to client devices (Smart TVs, smartphones, web browsers, etc.). Unlike proprietary options like Plex, it is completely free and requires no subscriptions to unlock features.

### Key Features:
* **Playback persistence:** Saves video progress and synchronizes status across devices.
* **Metadata management:** Automatically downloads covers, synopses, and data from providers like IMDb or TMDb.
* **Cross-platform:** Official clients are available for most operating systems and Smart TVs.

> ℹ️ For user management or advanced transcoding configurations, please refer to the [official Jellyfin documentation.](https://jellyfin.org/docs/).

### Installation:
Open your docker-compose file and paste the following:
```bash
  # Jellyfin
  jellyfin:
    image: jellyfin/jellyfin:latest
    container_name: jellyfin
    user: 1000:1000
    network_mode: "host"
    restart: unless-stopped
    volumes:
      - /your-docker-folder/jellyfin/config:/config
      - /your-docker-folder/jellyfin/cache:/cache
      - /mnt/external/Media:/media
    environment:
      - JELLYFIN_PublishedServerUrl=http://SERVER_IP
```
### Cosas a cambiar:
In **volumes:** we need to provide at least 3 important paths. Point to the directory where your container will be installed, and inside that folder, create the respective config and cache folders, which will handle volume persistence.
In **JELLYFIN_PublishedServerUrl=** write http:// followed by your server's IP. This will allow you to access Jellyfin via the web.

### How to use it
Once the service is up and running (docker compose up -d), you can access the administration and playback interface:
- Vía web: Enter http://SERVER_IP:8096 into your browser.
- Client apps: In your Smart TV or mobile device app, enter the same URL to connect to the server.

If you are using Tailscale as we saw earlier, you can access it from outside your local network by replacing the local IP with the IP assigned to your server in Tailscale.