---
layout: default
title: Installation
nav_exclude: true
---

<div align="right">
  <a href="../instalacion-configuracion"><strong>Español</strong></a>
</div>

## 💻 Windows & macOS (Docker Desktop)

Para entornos Windows y Mac, la opción recomendada es **Docker Desktop**. Este paquete incluye el motor de Docker, el cliente CLI, Docker Compose y una interfaz gráfica para gestionar tus recursos.

### Pasos generales:
1. Download the official installers from here:
   * [Docker Desktop for Windows](https://docs.docker.com/desktop/setup/install/windows-install/) (Require WSL2 or Hyper-V).
   * [Docker Desktop for Mac](https://docs.docker.com/desktop/setup/install/mac-install/) (Support for Intel y Apple Silicon).
2. Execute the file and follow the installation assistant.
3. Restart your system.

---

## 🐧 Linux (Docker Engine)

In Linux, usually we only install **Docker Engine**, we won't have GUI but the performance is better and faster.

> **Note:** Following commands are oriented for a **Debian/Ubuntu** distribution.

### Add the GPG Key, Docker repositories and apt-update

```bash
sudo apt update
sudo apt install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/debian
Suites: $(. /etc/os-release && echo "$VERSION_CODENAME")
Components: stable
Signed-By: /etc/apt/keyrings/docker.asc
EOF
sudo apt update
```

### Now we install Docker:

```bash
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

### Docker should be working, we can check with:

 ```bash
 sudo systemctl status docker
 ```

 ### Let's install docker-compose in case is not installed by default.
```bash
sudo apt-get update
sudo apt-get install docker-compose-plugin
```

Now we are ready!