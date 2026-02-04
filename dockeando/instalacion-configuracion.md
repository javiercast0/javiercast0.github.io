---
layout: default
title: Instalación
parent: Dockeando
nav_order: 1
---

<div align="right">
  <a href="./dockeando_en/instalacion-configuracion_en"><strong>English</strong></a>
</div>

## 💻 Windows y macOS (Docker Desktop)

Para entornos Windows y Mac, la opción recomendada es **Docker Desktop**. Este paquete incluye el motor de Docker, el cliente CLI, Docker Compose y una interfaz gráfica para gestionar tus recursos.

### Instalación:
1. Descarga el instalador oficial desde los siguientes enlaces:
   * [Docker Desktop para Windows](https://docs.docker.com/desktop/setup/install/windows-install/) (Requiere WSL2 o Hyper-V).
   * [Docker Desktop para Mac](https://docs.docker.com/desktop/setup/install/mac-install/) (Soporte para chips Intel y Apple Silicon).
2. Ejecuta el instalador y sigue el asistente.
3. Reinicia tu sesión para aplicar los cambios en las variables de entorno.

---

## 🐧 Linux (Docker Engine)
En Linux, lo habitual es instalar **Docker Engine**. Al prescindir de una interfaz gráfica pesada, el rendimiento es superior y nos permite un control total mediante la terminal.

> **Nota:** Los siguientes comandos están orientados a distribuciones basadas en **Debian/Ubuntu**.

### Añadimos la GPG Key, los repositorios de Docker y lanzamos un apt-update
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

### Instalamos Docker
```bash
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

### Docker ya debería estar funcionando, podemos comprobarlo usando:
 ```bash
 sudo systemctl status docker
 ```

### Para terminar, instalaremos docker-compose si es que no se ha instalado previamente.
```bash
sudo apt-get update
sudo apt-get install docker-compose-plugin
```

### Docker-Compose
Ahora escogeremos una carpeta donde estaran todos nuestros proyectos de Docker, la mia por ejemplo se llama docker y dentro cada proyecto tendrá su propia carpeta.
En la raiz de esta carpeta crearemos un archivo llamado docker-compose.yml y escribimos lo siguiente:

version: "3.8"
services:

### Comandos esenciales
La documentación de docker es increible y os recomiendo mirarla para poder gestionar vuestros contenedores, aquí os dejo los dos que más usaremos:
#### Levantar los servicios (contenedores)
```bash
docker-compose up -d
```
#### Apagar los contenedores
```bash
docker-compose down
```

Ya estamos listos para realizar proyectos!