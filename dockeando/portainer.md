---
layout: default
title: Portainer
parent: Dockeando
nav_order: 5
---

<div align="right">
  <a href="./dockeando_en/portainer_en"><strong>English</strong></a>
</div>

## ¿Qué es Portainer?

**Portainer** es una interfaz gráfica de usuario (GUI) ligera, intuitiva y sumamente potente diseñada para centralizar la gestión de entornos de contenedores Docker, Docker Swarm, Podman y Kubernetes. 

Aunque la administración de contenedores puede ejecutarse en su totalidad mediante la interfaz de línea de comandos (CLI), Portainer reduce drásticamente la curva de aprendizaje y optimiza los tiempos de operación, ofreciendo visibilidad en tiempo real desde cualquier navegador web.

### Razones clave para implementar Portainer en tu infraestructura:
* **Privacidad y Control Total:** Al ser autoalojado, eres el único dueño de la infraestructura de conexión, eliminando intermediarios y brechas de seguridad externas.
* **Alto Rendimiento y Bajo Consumo:** Gracias a estar desarrollado en Rust, ofrece conexiones fluidas, baja latencia y un consumo mínimo de CPU y memoria en tu servidor.
* **Configuración Zero-Configuration:** No requiere configuraciones complejas en los routers de los clientes (como abrir puertos dinámicos); basta con apuntar el cliente de RustDesk a la IP o dominio de tu servidor.
* **Seguridad de Extremo a Extremo:** Utiliza cifrado de grado bancario (Ed25519 y AES-256-GCM) para asegurar que todo el tráfico de control y de video viaje completamente protegido.

### Instalación:
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

### Como se usa
Una vez levantado el servicio (docker compose up -d), se puede acceder a la interfaz de administración:
Introduce en el navegador http://IP_DEL_SERVIDOR:9443