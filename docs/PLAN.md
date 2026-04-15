# Plan de Acción: Infraestructura CMS — Fake Enterprise

## Índice
1. [Visión General](#visión-general)
2. [Inventario de Nodos](#inventario-de-nodos)
3. [Reparto de Tareas](#reparto-de-tareas)
4. [Fases del Proyecto](#fases-del-proyecto)

---

## Visión General

Diseño, implementación y aprovisionamiento automático de la infraestructura IT para un sistema CMS. La red se divide en dos subredes (`internal` y `main`).
Se usarán herramientas como Canonical MAAS (propuesto por Sebas) y automatización para el aprovisionamiento.

---

## Inventario de Nodos

**Red Internal (6 nodos):**
- Nodo Monitor (1)
- Clúster HA (2 maestros, 2 workers) y Base de datos SQL (dentro del clúster)
- 1 Nodo adicional (ej. almacenamiento o MAAS interno)

**Red Main (3 nodos fijos + 8 hot-desks):**
- Balanceador de carga (1 nodo)
- Servidores HTTP/S frontales CMS (2 nodos)
- Puestos hot-desk (8 nodos)

**Otros:**
- Nodo Jumpstart (conectado a ambas redes, apagable tras el despliegue)

---

## Reparto de Tareas (Según los puntos del PDF)

| Miembro | Puntos | Funciones |
|---------|--------|-----------|
| **Sebas** | 1, 2, 3, 4(a), 5 | Redes `internal`/`main`, clúster (2 maestros, 2 workers), BBDD en el clúster, balanceador del `main`, 8 puestos hot-desk (Canonical MAAS). |
| **Alvaro** | 6, 7, 8, 9 | Acceso Internet externo solo a LB. Acceso de `main` a inet/`internal`. Restricción a `internal`. Securización de los nodos (firewalls). |
| **Aitor** | 10, 11 | Monitorización integral (CPU, RAM, disco, red) y nodo Monitor en `internal`. Monitoreo de servicios. |
| **Aaron** | 4(b), 12, 14 | 2 Frontales HTTP/S CMS. Redundancia de red física/lógica. Topología Jumpstart en ambas subredes (apagable). |
| **Antonio** | 13, 15 | Aprovisionamiento automatizado desde Jumpstart (instalación SO y config) y scripts de prueba/TrafficMix. |

---

## Fases del Proyecto

| Fase | Tarea Principal | Responsable(s) Principal(es) |
|---|---|---|
| 00 | Diseño de Red y Direccionamiento | Sebas, Alvaro |
| 01 | Despliegue Nodo Jumpstart/Aprovisionador | Antonio |
| 02 | Enrutamiento Base y Redundancia L2/L3 | Aaron |
| 03 | Despliegue Clúster HA y Base de Datos | Sebas |
| 04 | Securización / Firewall Perimetral y Nodal | Alvaro |
| 05 | Frontales CMS y Balanceador | Aaron, Sebas |
| 06 | Puestos Hot-desk | Sebas |
| 07 | Monitorización de Sistema (Infraestructura) | Aitor |
| 08 | Monitorización de Servicios CMS | Aitor |
| 09 | TrafficMix y Pruebas Carga/Failover | Antonio |
| 10 | Ajustes Finales de Seguridad / Apagado Jumpstart | Todos |
| 11 | Documentación Final y Baseline Software | Todos |

