---
layout: default
title: Tailscale
parent: Dockeando
nav_order: 2
---

<div align="right">
  <a href="./dockeando_en/tailscale_en"><strong>English</strong></a>
</div>

## ¿Qué es Tailscale? 🛜

Tailscale nos permite, entre otras cosas, crear un tunel VPN entre nuestros dispositivos, me encanta porque como solución local es fascinante ya que no tenemos porque lidiar con nuestra operadora para que nos saque de la CG-NAT y funciona realmente bien, es la puerta de entrada que nos permitirá conectar nuestro servidor con nuestros dispostivios cuando estemos en el exterior. 
Es de esos servicios que cuesta creer que su plan gratuito sea  tan bueno (y esperemos que así siga), gracias a esto podremos acceder a nuestras carpetas compartidas por Samba, usar RustDesk para controlar de forma remota nuestros dispositivios sin depender de otras empresas intermediarias, o ver nuestros videos o fotos por Jellyfin...

No voy a entrar en detalle sobre como configurarlo o instalarlo en clientes, es muy sencillo y solo se necesita acceder por la cuenta de Google, este proceso es el que pondremos en nuestro servidor o dispositivo que tendremos conectado 24/7.

### Instalación:
Abrimos nuestro docker-compose y lo que pegaremos es lo siguiente:
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
### Cosas a cambiar:
En **TS_AUTHKEY=** debes de crear una llave en la pagina de Tailscale, en tu perfil y ponerla ahí.
Recuerda cambiar en la parte de **volumes** la ruta y poner la de tus proyectos de docker.

Se pueden hacer un montón más de cosas como crear subnets, yo tengo una en mi red local, aquí configuramos lo justo para que funcione pero os recomiendo encarecidamente mirar la documentación si es que necesitais algo más, ya que seguro que se puede hacer.

### Como se usa
En los clientes instalamos Tailscale, y accedemos con la misma cuenta, ya estaría, super sencillo, cuando estemos fuera de casa escogeremos la IP que Tailscale le da a nuestro servidor y todos nuestros servicios deberían de funcionar de la misma forma.