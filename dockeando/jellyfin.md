---
layout: default
title: Jellyfin
parent: Dockeando
nav_order: 4
---

<div align="right">
  <a href="./dockeando_en/jellyfin_en"><strong>English</strong></a>
</div>

## ¿Qué es Jellyfin?

Jellyfin es un servidor de medios de código abierto que permite organizar y transmitir archivos de vídeo y audio locales a dispositivos cliente (Smart TV, smartphones, navegadores web, etc.). A diferencia de opciones propietarias como Plex, es completamente gratuito y no requiere suscripciones para desbloquear funciones.

### Características principales:
* **Persistencia de reproducción:** Guarda el progreso de los vídeos y sincroniza el estado entre dispositivos.
* **Gestión de metadatos:** Descarga automáticamente carátulas, sinopsis y datos desde proveedores como IMDB o TMDB.
* **Multiplataforma:** Dispone de clientes oficiales para la mayoría de sistemas operativos y Smart TVs.

> ℹ️ Para la gestión de usuarios o configuraciones avanzadas de transcodificación, consulta la [documentación oficial de Jellyfin](https://jellyfin.org/docs/).

### Instalación:
Abrimos nuestro docker-compose y lo que pegaremos es lo siguiente:
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
      - JELLYFIN_PublishedServerUrl=http://IP_DEL_SERVIDOR
```
### Cosas a cambiar:
En **volumes:** tenemos que darle minimo 3 cosas importantes, apuntamos a la ruta donde estará nuestro contenedor instalado y dentro de esa carpeta, la respectiva carpeta config y cache, que nos dará la persistencia de volúmenes.
Luego le compartiremos otra carpeta donde estarán nuestras carpetas con los ficheros, en mi caso /mnt/external/Media, ahí es donde tengo mis archivos.
En **JELLYFIN_PublishedServerUrl=** ponemos http:// y la IP de nuestro servidor, esto nos servirá para acceder a Jellyfin mediante web.

### Como se usa
Una vez levantado el servicio (docker compose up -d), se puede acceder a la interfaz de administración y reproducción:
- Vía web: Introduce en el navegador http://IP_DEL_SERVIDOR:8096
- Aplicaciones cliente: En la app de la Smart TV o dispositivo móvil, introduce la misma dirección URL para conectar con el servidor.

Si utilizas Tailscale como vimos antes, puedes acceder desde fuera de la red local sustituyendo la IP local por la IP asignada a tu servidor en Tailscale.