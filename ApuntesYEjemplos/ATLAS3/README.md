# Curso ATLAS 3

## Ruta formativa

| Módulo | Objetivo | Estado |
|---|---|---|
| [00 · Arquitectura y modelo mental](./00-Arquitectura-y-modelo-mental.md) | Introducción general al ecosistema y a la escalera de consumo | Introducción |
| [01 · Arquitectura completa y Happy Path end-to-end](./01-Arquitectura-y-happy-path-end-to-end.md) | Mapa por capas, responsabilidades, flujo completo, puntos de extensión y mini ejemplos ATLAS | Piloto ampliado |
| 02 · Backend y Data REST | Entidad, repositorio integrado, query DSL, properties e includeAssociations | Planificado |
| 03 · Seguridad y ciclo CRUD | REST Security, Data Security, filtro organizativo y CRUD Listener | Planificado |
| 04 · Frontend, ModelBase y metadata | Metadata de modelo, Data REST frontend, Proxy, Store y validaciones | Planificado |
| 05 · Grid y Forms | Consumo model-first/config-first, ownership y errores habituales | Planificado |
| 06 · ViewComponent y Components | Separación de responsabilidades y primitives visuales | Planificado |
| 07 · Relaciones y TreeGrid | Asociaciones, lookups y jerarquías | Planificado |
| 08 · Casos avanzados | Charts, Pivot, Board, Dashboard, Scheduler, Gantt, Workflows | Posterior |

---

## Principio pedagógico

### Una única escalera

**minimal → configured → extended → custom**

No se empieza por el caso más flexible. Cada nivel introduce complejidad solo cuando existe una necesidad que el nivel anterior no resuelve.

---

## Caso conductor

El curso usa un dominio común para mantener continuidad:

**Taller · Orden de Trabajo · Vehículo · Cliente · Área · Operario**

Permite explicar:

- CRUD estándar;
- filtros, paginación y ordenación;
- relaciones;
- validaciones;
- seguridad por rol y organización;
- Grid;
- Forms;
- ViewComponent;
- TreeGrid;
- puntos de extensión.

---

## Fuentes del curso

### Contrato técnico

ATLAS 3 mantiene como fuente principal la documentación junto al código:

- README de cada paquete;
- `reference/QUICKSTART.md`;
- `reference/ARCHITECTURE.md`;
- `reference/API.md`;
- manifests de módulo;
- ejemplos mantenidos junto al paquete.

### Material docente

Este repositorio transforma esos contratos en:

- presentaciones;
- diagramas;
- decisiones;
- ejercicios guiados;
- laboratorios;
- material de repaso.

---

## Regla de mantenimiento

Una slide no debe convertirse en una segunda referencia de API.

**API cambia → se actualiza la documentación del paquete → se revisa la slide que explica el concepto.**
