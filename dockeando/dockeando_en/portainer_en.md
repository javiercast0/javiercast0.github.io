---
layout: default
title: Portainer
nav_exclude: true
---

<div align="right">
  <a href="../portainer"><strong>Español</strong></a>
</div>

## What is Portainer?

**Portainer** is a lightweight, intuitive, and highly powerful graphical user interface (GUI) designed to centralize the management of Docker, Docker Swarm, Podman, and Kubernetes container environments.

Although container management can be fully executed via the command-line interface (CLI), Portainer drastically reduces the learning curve and optimizes operational workflows by providing real-time visibility from any web browser.

### Key Features:
* **Simplified Remote Management:** Allows you to centrally operate your infrastructure without the need to establish direct SSH sessions, making it ideal for secure connections outside your local network.
* **Full Lifecycle Control:** Start, stop, restart, and pause containers individually or in bulk with just a single click.
* **Efficient Diagnostics and Auditing:** Native, structured access to real-time logs, hardware consumption metrics (CPU, Memory, I/O), and built-in terminal consoles directly inside your browser.
* **At-a-Glance Network and Port Mapping:** Instantly identify exposed ports, internal network links, and persistent volumes assigned to each application.

### Installation:
Abrimos nuestro docker-compose y lo que pegaremos es lo siguiente:
```bash
  # Portainer
  portainer:
    image: portainer/portainer-ce:latest
    container_name: portainer
    restart: unless-stopped
    ports: ["9443:9443"]
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
      - /your-docker-folder/portainer:/data
```

### How to use it
Once the service is up and running (docker compose up -d), you can access the management interface:
Enter http://SERVER_IP:9443 into your web browser.