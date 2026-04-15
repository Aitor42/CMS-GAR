# Proyecto Gestión y Administración de Redes: Infraestructura CMS (Fake Enterprise)

Este repositorio contiene las configuraciones, scripts y documentación para el diseño, implementación y aprovisionamiento automático de una infraestructura IT para un sistema CMS, desarrollado para la asignatura de **Gestión y Administración de Redes**.

## Descripción del Proyecto

El objetivo principal es desplegar de manera automatizada una arquitectura en alta disponibilidad para un sistema CMS. La red se divide en dos segmentos principales (`internal` y `main`), con reglas estrictas de firewall, enrutamiento, monitorización integral y aprovisionamiento desatendido (Jumpstart / MAAS).

Toda la topología se simula empleando **GNS3** y el despliegue se automatiza al máximo.

## Equipo y Reparto de Tareas

*   **Sebas**: Clúster HA (2 maestros, 2 workers), Base de datos SQL, Balanceador de carga en `main`, Puestos hot-desk, Canonical MAAS.
*   **Alvaro**: Enrutamiento, NAT, reglas de firewall perimetral y securización de nodos (End-point Security).
*   **Aitor**: Monitorización de infraestructura (CPU, RAM, disco, red) y monitorización específica de servicios (CMS, bases de datos).
*   **Aaron**: Servidores HTTP/S frontales CMS, diseño y configuración de la redundancia de red (L2/L3), topología L2/L3 del nodo Jumpstart.
*   **Antonio**: Sistema de aprovisionamiento 100% automatizado, scripts de despliegue y pruebas de carga (TrafficMix, accesos a BBDD).

## Estructura del Repositorio

*   `/ansible`: Playbooks, roles y configuraciones de Ansible.
*   `/diagramas`: Esquemas de red y lógicos del entorno.
*   `/docs`: Documentación detallada del proyecto.
    *   [`PLAN.md`](docs/PLAN.md): Plan de acción e inventario completo.
    *   [`hitos/`](docs/hitos): Documentos separados para cada hito (Fase 00 a Fase 11) asignados a los distintos miembros del equipo.
*   `/gns3`: Archivos y configuraciones del entorno de simulación GNS3.
*   `/scripts`: Scripts adicionales para la automatización, pruebas y generación de tráfico.

## Siguientes Pasos

Consultar el fichero de planificación estructurada en [docs/PLAN.md](docs/PLAN.md) para revisar las variables y los hitos en desarrollo.