---
layout: default
title: Installation
nav_exclude: true
---

<div align="right">
  <a href="../instalacion-configuracion"><strong>Español</strong></a>
</div>

## 💻 Windows and macOS (Docker Desktop)
For Windows and Mac environments, the best way to go is **Docker Desktop**. This package includes the Docker engine, the CLI client, Docker Compose, and a GUI to manage all your resources easily.

### Installation:
1. Download the official installer from these links:
   * [Docker Desktop for Windows](https://docs.docker.com/desktop/setup/install/windows-install/) (Requires WSL2 or Hyper-V).
   * [Docker Desktop for Mac](https://docs.docker.com/desktop/setup/install/mac-install/) (Supports both Intel and Apple Silicon chips).
2. Run the installer and follow the setup wizard.
3. Restart your session to apply the changes to your environment variables.

---

## 🐧 Linux (Docker Engine)
On Linux, we usually install **Docker Engine**. Since it doesn't rely on a heavy graphical interface, the performance is better and it gives us full control via the terminal.

> **Note:** The following commands are for **Debian/Ubuntu** based distributions.

### Adding the GPG Key, Docker repositories, and running an apt-update
```bash
sudo apt update
sudo apt install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL [https://download.docker.com/linux/debian/gpg](https://download.docker.com/linux/debian/gpg) -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: [https://download.docker.com/linux/debian](https://download.docker.com/linux/debian)
Suites: $(. /etc/os-release && echo "$VERSION_CODENAME")
Components: stable
Signed-By: /etc/apt/keyrings/docker.asc
EOF
sudo apt update
```

### Installing Docker
```bash
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

### Docker should be up and running now; you can check it by running:
 ```bash
 sudo systemctl status docker
 ```

### Finally, let's install docker-compose if it wasn't already included.
```bash
sudo apt-get update
sudo apt-get install docker-compose-plugin
```

### Docker-Compose
Now, pick a folder where you'll keep all your Docker projects. Mine is simply called "docker," and each project has its own subfolder inside. In the root of that folder, create a file named **docker-compose.yml** and add the following:
```bash
version: "3.8"
services:
```

### Essential commands
Docker's documentation is awesome, and I highly recommend checking it out to learn how to manage your containers. Here are the two commands we'll be using the most:

#### Start the services (containers)
```bash
docker-compose up -d
```

#### Stop the containers
```bash
docker-compose down
```

We're all set to start building projects!