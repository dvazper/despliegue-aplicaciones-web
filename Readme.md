<div align="center">

# Despliegue de Aplicaciones Web
### Tareas — 2º DAW

![Curso](https://img.shields.io/badge/Curso-2025%2F2026-blue?style=flat-square)
![Alumno](https://img.shields.io/badge/Alumno-Daniel%20Vázquez%20Pereira-grey?style=flat-square)
![Módulo](https://img.shields.io/badge/Módulo-Despliegue%20de%20Aplicaciones%20Web-blue?style=flat-square)

</div>

---

Repositorio dedicado a documentar todas las actividades, prácticas y configuraciones realizadas en la asignatura de *Despliegue de Aplicaciones Web*. Incluye explicaciones, capturas y configuraciones reales de Apache, VirtualHosts, SSL, Rewrite, permisos, DNS, Docker y Docker Compose.

---

## Índice

1. [Descripción](#descripción)
2. [Estructura del repositorio](#estructura-del-repositorio)
3. [Tema 1 — Servidores Web (Apache)](#tema-1--servidores-web-apache)
4. [Tema 5 — Docker y Containerización](#tema-5--docker-y-containerización)
5. [Trabajo del 1er Trimestre](#trabajo-del-1er-trimestre)
6. [Trabajo del 2º Trimestre](#trabajo-del-2º-trimestre)
7. [Tecnologías utilizadas](#tecnologías-utilizadas)
8. [Autor](#autor)

---

## Descripción

Este repositorio contiene la documentación detallada de todas las tareas realizadas durante el módulo **Despliegue de Aplicaciones Web**.

Incluye:
- Instalación y configuración de servidores web (Apache)
- Gestión de VirtualHosts
- Configuración de seguridad (SSL, autenticación, permisos)
- Reglas Rewrite con expresiones regulares
- Servidor DNS local (BIND9)
- Docker y containerización
- Docker Compose para aplicaciones multi-contenedor
- Creación de imágenes Docker optimizadas
- Automatización con scripts Bash
- Tareas explicadas paso a paso con capturas

El objetivo es tener una documentación clara, profesional y reutilizable.

---

## Estructura del repositorio

```
Despliegue-de-aplicaciones-web/
│
├── tema1-servidores-web/
│   ├── activity1-instalacion-apache/
│   ├── activity2-configuracion-basica/
│   ├── activity5-directiva-directory/
│   ├── activity6-expresiones-regulares/
│   ├── activity7-rewrite/
│   ├── activity8-virtualhost/
│   ├── activity9-authentication/
│   └── activity10-ssl/
│
├── tema5-docker/
│   ├── activity1-instalacion-docker/
│   ├── activity2-introduccion-contenedores/
│   ├── activity3-imagenes-contenedores/
│   ├── activity4-almacenamiento-redes/
│   ├── activity5-docker-compose/
│   └── activity6-creacion-imagenes/
│
├── trabajo-1er-trimestre/
│   ├── Paso1/ — Apache + VirtualHosts
│   ├── Paso2/ — PHP + MySQL
│   ├── Paso3/ — WordPress
│   ├── Paso4/ — Python WSGI
│   ├── Paso5/ — Autenticación
│   ├── Paso6/ — AWStats
│   └── Paso7/ — Segundo servidor (Nginx)
│
└── trabajo-2er-trimestre/
    └── readme.md
```

> Cada actividad tiene su propio README con capturas, explicaciones y ejemplos de configuración.

---

## Tema 1 — Servidores Web (Apache)

| Actividad | Descripción | Enlace |
|-----------|-------------|--------|
| Activity 1 | Instalación de Apache | [`activity1`](./tema1-servidores-web/activity1-instalacion-apache/) |
| Activity 2 | Configuración básica | [`activity2`](./tema1-servidores-web/activity2-configuracion-basica/) |
| Activity 5 | Directiva `Directory` | [`activity5`](./tema1-servidores-web/activity5-directiva-directory/) |
| Activity 6 | Expresiones regulares | [`activity6`](./tema1-servidores-web/activity6-expresiones-regulares/) |
| Activity 7 | Reescritura de URL | [`activity7`](./tema1-servidores-web/activity7-rewrite/) |
| Activity 8 | VirtualHosts | [`activity8`](./tema1-servidores-web/activity8-virtualhost/) |
| Activity 9 | Autenticación básica | [`activity9`](./tema1-servidores-web/activity9-authentication/) |
| Activity 10 | Certificados y SSL | [`activity10`](./tema1-servidores-web/activity10-ssl/) |

---

## Tema 5 — Docker y Containerización

Acceder a: [`tema5-docker`](./tema5-docker/)

Tema completo dedicado a Docker, desde conceptos básicos hasta la creación de imágenes optimizadas y orquestación con Docker Compose.

| Actividad | Descripción | Duración | Nivel | Enlace |
|-----------|-------------|----------|-------|--------|
| Activity 1 | Instalación de Docker en Ubuntu 24.04 | 20 min | Básico | [`activity1`](./tema5-docker/activity1-instalacion-docker/) |
| Activity 2 | Introducción a los contenedores | 45 min | Básico | [`activity2`](./tema5-docker/activity2-introduccion-contenedores/) |
| Activity 3 | Imágenes y contenedores | 60 min | Medio | [`activity3`](./tema5-docker/activity3-imagenes-contenedores/) |
| Activity 4 | Almacenamiento y redes Docker | 90 min | Medio | [`activity4`](./tema5-docker/activity4-almacenamiento-redes/) |
| Activity 5 | Docker Compose | 120 min | Avanzado | [`activity5`](./tema5-docker/activity5-docker-compose/) |
| Activity 6 | Creación de imágenes Docker | 120 min | Avanzado | [`activity6`](./tema5-docker/activity6-creacion-imagenes/) |

**Contenidos cubiertos:**

- Instalación y ciclo de vida de contenedores
- Ejecución interactiva y en segundo plano, mapeo de puertos y volúmenes
- Gestión de imágenes: descarga, inspección, eliminación y optimización
- Almacenamiento persistente con volúmenes y bind mounts
- Redes personalizadas y comunicación entre contenedores
- Docker Compose: definición YAML, servicios LEMP, variables de entorno
- Creación de imágenes con Dockerfile: Python, Node.js, Alpine, multi-stage builds
- Mejores prácticas: usuario no-root, `.dockerignore`, labels, reducción de tamaño

**Cifras del tema:** 6 actividades con README individual · 61 capturas de pantalla · 5 Dockerfiles funcionales

---

## Trabajo del 1er Trimestre

Acceder a: [`trabajo-1er-trimestre`](./trabajo-1er-trimestre/)

| Paso | Descripción | Enlace |
|------|-------------|--------|
| Paso 1 | Instalación y configuración de Apache + VirtualHosts | [`Paso1`](./trabajo-1er-trimestre/Paso1/) |
| Paso 2 | Instalación de PHP y MySQL | [`Paso2`](./trabajo-1er-trimestre/Paso2/) |
| Paso 3 | Instalación y configuración de WordPress | [`Paso3`](./trabajo-1er-trimestre/Paso3/) |
| Paso 4 | Aplicación Python con WSGI en Apache | [`Paso4`](./trabajo-1er-trimestre/Paso4/) |
| Paso 5 | Protección mediante autenticación básica | [`Paso5`](./trabajo-1er-trimestre/Paso5/) |
| Paso 6 | Monitorización del servidor con AWStats | [`Paso6`](./trabajo-1er-trimestre/Paso6/) |
| Paso 7 | Segundo servidor web con Nginx, PHP y phpMyAdmin | [`Paso7`](./trabajo-1er-trimestre/Paso7/) |

Incluye configuración avanzada de Apache, explicaciones de seguridad web y archivos `.conf` comentados.

---

## Trabajo del 2º Trimestre

Acceder a: [`trabajo-2er-trimestre`](./trabajo-2er-trimestre/)

Implementación de un servidor web multicliente completamente automatizado con soporte para usuarios independientes, bases de datos, DNS, FTP, SSH y Python.

| Paso | Descripción | Estado |
|------|-------------|--------|
| Paso 1 | Configuración inicial del sistema | Completado |
| Paso 2 | Stack LAMP + phpMyAdmin | Completado |
| Paso 3 | Script de automatización de clientes | Completado |
| Paso 4 | FTP con TLS + SSH/SFTP + Python | Completado |
| Paso 5 | Configuración DNS con BIND9 | Completado |
| Paso 6 | Pruebas integrales y verificación | Completado |

**Funcionalidades principales:**
- Apache2 con múltiples VirtualHosts
- Script `crear_cliente.sh`: crea usuario, directorio, vhost, DNS y base de datos en un único comando
- BIND9 con zonas directa e inversa (resolución A y PTR)
- FTP con TLS 1.2+ y usuarios confinados (chroot)
- SSH/SFTP para acceso remoto
- Soporte Python mediante mod_wsgi

**Crear un nuevo cliente:**
```bash
sudo ~/servidor-web/scripts/crear_cliente.sh tienda 192.168.1.135
```

---

## Tecnologías utilizadas

| Tecnología | Uso |
|------------|-----|
| Apache2 | Servidor web principal |
| PHP 8.3 | Backend dinámico |
| MariaDB | Base de datos |
| BIND9 | Servidor DNS local |
| vsftpd | Servidor FTP con TLS |
| OpenSSH | Acceso remoto SSH/SFTP |
| Docker | Containerización |
| Docker Compose | Orquestación de contenedores |
| Bash | Scripts de automatización |
| Ubuntu 24.04 LTS | Sistema operativo |
| Python | Aplicaciones WSGI |
| OpenSSL | Cifrado y seguridad |

---

## Estadísticas del repositorio

| Métrica | Valor |
|---------|-------|
| Trimestres documentados | 2 |
| Actividades completadas | 21+ |
| Temas completados | 2 (Tema 1 + Tema 5) |
| Capturas incluidas | 80+ |
| READMEs | 16+ |
| Scripts Bash | 2+ |
| Dockerfiles | 5+ |

---

## Autor

**Daniel Vázquez Pereira**  
2º DAW — Desarrollo de Aplicaciones Web  
Curso 2025/26 · IES La Marisma, Andalucía

---

*Este repositorio se actualiza periódicamente con nuevas tareas, mejoras y configuraciones.*

[Volver arriba](#despliegue-de-aplicaciones-web)
