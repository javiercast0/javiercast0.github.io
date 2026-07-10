---
layout: default
title: RustDesk
parent: Dockeando
nav_order: 6
---

<div align="right">
  <a href="./dockeando_en/rustdesk_en"><strong>English</strong></a>
</div>

## ¿Qué es Rustdesk?

**RustDesk** es una solución de escritorio remoto de código abierto, potente y moderna, diseñada como una alternativa autoalojada (*self-hosted*) y segura a herramientas propietarias como TeamViewer o AnyDesk.

RustDesk es seguramente el servicio que más uso, siempre me ha gustado y he necesitado conectarme a mi otros dispositivos fuera de casa o por comodidad, por ejemplo, a la televisión Android del salón que utiliza mi padre el cual no tiene mucha idea de tecnología no funciona... Me meto desde mi ordenador para arreglarlo de forma más cómoda. ¿Necesito apagar el ordenador desde fuera de casa o controlar mi móvil desde el ordenador? Lo mismo, siempre me ha dado un poco de respeto el pensar que cuando utilizamos herramientas de terceros para esto, al final estamos enviando información muy sensible a servidores de otros empresas, por eso en cuanto lo vi pensé en tener un servicio de escritorio remoto alojado en mi propia casa.

Está escrito en Rust, tiene un gran rendimiento, bajo consumo de recursos y permite mantener el control absoluto sobre tu privacidad. Al desplegar tus propios servidores de señal y de relay, garantizas que las conexiones y los datos de tus dispositivos no pasen por servidores de terceros.

### Razones clave para implementar Portainer en tu infraestructura:
* **Gestión Remota Simplificada:** Permite operar de forma centralizada tu infraestructura sin necesidad de abrir sesiones SSH directas, ideal para conexiones seguras fuera de tu red local.
* **Control de Ciclo de Vida Completo:** Ejecuta acciones de inicio, parada, reinicio y pausa en contenedores de manera individual o por lotes con un solo clic.
* **Auditoría y Diagnóstico Eficiente:** Acceso nativo y estructurado a los *logs* en tiempo real, métricas de consumo de hardware (CPU, Memoria, I/O) y consolas de terminal integradas directamente en el navegador.
* **Mapeo de Redes y Puertos de un Vistazo:** Identifica de forma inmediata los puertos expuestos, los enlaces de red interna y los volúmenes persistentes asignados a cada aplicación.

### Instalación:
Abrimos nuestro docker-compose y lo que pegaremos es lo siguiente:
```bash
  # RustDesk
    rustdesk_hbbs:
    container_name: rustdesk_hbbs
    image: rustdesk/rustdesk-server:latest
    command: hbbs
    volumes: [/your-docker-folder/rustdesk/data:/root]
    network_mode: 'host'
    depends_on: [rustdesk_hbbr]
    restart: unless-stopped

  rustdesk_hbbr:
    container_name: rustdesk_hbbr
    image: rustdesk/rustdesk-server:latest
    command: hbbr
    volumes: [/your-docker-folder/rustdesk/data:/root]
    network_mode: 'host'
    restart: unless-stopped
```

### Como se usa