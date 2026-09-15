# Curso ATLAS 3

Material docente para aprender a **consumir ATLAS 3 desde el modelo mental y la arquitectura antes de entrar en detalle de API o código**.

## Presentación inicial

[ATLAS 3 — Arquitectura y modelo mental de consumo](./ApuntesYEjemplos/ATLAS3/00-Arquitectura-y-modelo-mental.md)

## Enfoque

El curso sigue una progresión común en frontend y backend:

```text
minimal → configured → extended → custom
```

La prioridad inicial es comprender:

- qué problemas resuelve ATLAS;
- cómo encaja con MEDUSA y con una aplicación consumidora;
- qué responsabilidades pertenecen a backend, frontend y librería;
- cómo fluye el dato desde JPA/REST hasta ModelBase, Grid o Forms;
- qué pieza posee el estado y el lifecycle;
- cuándo usar componentes estándar y cuándo justificar una extensión.

## Estructura

- [Índice ATLAS 3](./ApuntesYEjemplos/ATLAS3/README.md)
- Arquitectura y modelo mental
- Backend y Data REST
- Frontend, ModelBase y metadata
- Grid y Forms
- ViewComponent y Components
- Seguridad y ciclo CRUD
- Relaciones y TreeGrid
- Laboratorios progresivos

## Fuentes de verdad

El material docente deriva de la documentación **code-adjacent** de ATLAS 3 y de ejemplos consumidores. Las slides explican conceptos y decisiones; no duplican la referencia de API.

Baseline documental inicial: `jlPortusOrg/ATLAS3`, rama `CorreccionesErrorFront`, revisada el 15-09-2026.

> La clasificación de madurez de un módulo y la verificación concreta de un HEAD son dimensiones diferentes. El curso no presenta como probado lo que solo está documentado estáticamente.
