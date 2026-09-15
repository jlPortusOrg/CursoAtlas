# Curso ATLAS 3

## Ruta formativa

| Módulo | Objetivo | Estado |
|---|---|---|
| [00 · Arquitectura y modelo mental](./00-Arquitectura-y-modelo-mental.md) | Entender el ecosistema, responsabilidades y happy paths antes del código | Piloto |
| 01 · Backend y Data REST | Entidad, repositorio integrado, query DSL y ciclo REST | Planificado |
| 02 · Frontend, ModelBase y metadata | Modelo autoritativo, metadata, proxy y query-state | Planificado |
| 03 · Grid y Forms | Consumo model-first/config-first y ownership | Planificado |
| 04 · ViewComponent y Components | Escalado de una View y primitives visuales | Planificado |
| 05 · Seguridad y ciclo CRUD | Autenticación, autorización, datos y hooks | Planificado |
| 06 · Relaciones y TreeGrid | Asociaciones y jerarquías | Planificado |
| 07 · Casos avanzados | Charts, Pivot, Board, Dashboard, Scheduler, Gantt, Workflows | Posterior |

---

## Principio pedagógico

### Una única escalera

**minimal → configured → extended → custom**

No se empieza por el caso más flexible. Cada nivel introduce complejidad solo cuando existe una necesidad que el nivel anterior no resuelve.

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
