# ATLAS 3
## Arquitectura y modelo mental de consumo

<div class="atlas-kicker">Curso ATLAS 3 · Módulo 00</div>

**Primero entendemos las responsabilidades. Después escribimos código.**

<small>Baseline documental: ATLAS3 / CorreccionesErrorFront · 15-09-2026</small>

Notas:
Objetivo de esta sesión: que el alumno pueda dibujar una aplicación ATLAS y explicar quién es owner de cada responsabilidad antes de memorizar APIs.

---

# Objetivos de la sesión

<div class="atlas-grid atlas-grid-2">

<div class="atlas-card">

### Al terminar podrás

- explicar qué resuelve ATLAS 3;
- situar ATLAS y MEDUSA;
- dibujar el flujo backend ↔ frontend;
- distinguir ownership de datos, View y seguridad;
- elegir entre consumo minimal, configured, extended o custom.

</div>

<div class="atlas-card">

### Todavía no buscamos

- memorizar clases;
- estudiar todos los parámetros;
- crear plugins;
- recorrer módulos avanzados;
- sustituir la documentación de API por las slides.

</div>

</div>

---

# Fuente y baseline

<div class="atlas-grid atlas-grid-2">

<div class="atlas-card">

### Contrato técnico

La referencia del curso es la documentación **code-adjacent** de ATLAS 3:

- package README;
- QUICKSTART;
- ARCHITECTURE;
- API;
- module-manifest;
- ejemplos del propio paquete.

</div>

<div class="atlas-card">

### Regla de evidencia

`stage: stable` describe madurez de producto.

**No significa que cada HEAD esté compilado, empaquetado, testeado y aceptado.**

El curso diferencia contrato documental y evidencia ejecutada.

</div>

</div>

<div class="atlas-source">Fuente: atlas-backend/module-manifest.yml y atlas-angular/docs/CATALOGO-MODULOS-CONSUMO.md.</div>

---

# ¿Qué problema resuelve ATLAS?

<div class="atlas-grid atlas-grid-3">

<div class="atlas-card">
<h3>Convención</h3>
Un modo común de construir aplicaciones corporativas sin reinventar cada pantalla o endpoint.
</div>

<div class="atlas-card">
<h3>Integración</h3>
Datos, seguridad, lifecycle y UI trabajan sobre contratos compatibles.
</div>

<div class="atlas-card">
<h3>Extensión controlada</h3>
Permite salir del happy path, pero exige una necesidad real y un extension point público.
</div>

</div>

> ATLAS no sustituye Spring ni Angular. **Organiza capacidades recurrentes y sus fronteras.**

---

# El ecosistema ATLAS 3

<img class="atlas-diagram" src="assets/01-ecosistema.svg" alt="Ecosistema ATLAS 3">

<div class="atlas-source">Backend integrado: atlas-medusa agrega Data REST, seguridad, CRUD Listener y Core. Frontend: Core, Data REST, Components, Forms, Grid y TreeGrid forman el núcleo prioritario del curso.</div>

---

# Arquitectura de una aplicación consumidora

<img class="atlas-diagram" src="assets/02-arquitectura-app.svg" alt="Arquitectura de una aplicación consumidora ATLAS">

### La aplicación conserva el negocio

ATLAS aporta infraestructura y contratos; **la feature sigue siendo propietaria de sus reglas de negocio y de las decisiones funcionales**.

---

# Backend: happy path integrado

<img class="atlas-diagram" src="assets/03-backend-datarest.svg" alt="Happy path backend ATLAS MEDUSA">

<div class="atlas-grid atlas-grid-2">

<div class="atlas-card">
<h3>ATLAS + MEDUSA</h3>
La entrada recomendada es <strong>atlas-medusa</strong> y el repositorio integrado es <strong>AtlasMedusaRepository</strong>.
</div>

<div class="atlas-card">
<h3>Standalone</h3>
<code>AtlasRestRepository</code> queda para Data REST standalone o desarrollo de librería.
</div>

</div>

<div class="atlas-source">No se enseña AtlasRestRepositoryImpl ni clases base internas como API de consumidor.</div>

---

# Data REST es el eje del flujo

<img class="atlas-diagram" src="assets/04-datarest-flow.svg" alt="Pipeline Data REST">

### Idea clave

Un CRUD estándar no necesita empezar creando un controller custom.

**Primero comprobar si el caso cabe en el contrato de repositorio + query DSL + seguridad.**

---

# Frontend: el modelo como contrato

<img class="atlas-diagram" src="assets/05-frontend-metadata.svg" alt="ModelBase y metadata en frontend">

### Model-first

La metadata del modelo puede alimentar schema, labels, validación y comportamiento de componentes.

**Duplicar esa información manualmente debe ser una decisión, no la rutina.**

---

# La escalera común de consumo

<img class="atlas-diagram" src="assets/06-consumption-ladder.svg" alt="Escalera minimal configured extended custom">

<div class="atlas-source">La misma progresión aparece en Core, Components, Forms, Grid, TreeGrid y en los ejemplos de aprendizaje.</div>

---

# Grid: ownership antes que opciones

<img class="atlas-diagram" src="assets/07-grid-ownership.svg" alt="Ownership de datasource en Grid">

<div class="atlas-grid atlas-grid-2">

<div class="atlas-card">
<h3>Model → owned</h3>
Grid materializa y gobierna su DataStore scoped.
</div>

<div class="atlas-card">
<h3>Store → borrowed</h3>
La feature crea y conserva el Store; Grid lo usa sin adquirir su lifecycle.
</div>

</div>

### Pregunta que debe hacerse el alumno

**¿Quién debe poseer realmente este Store?**

---

# Forms: model-first y config-first

<div class="atlas-grid atlas-grid-3">

<div class="atlas-card">
<h3>Modelo</h3>
ModelBase + metadata es la fuente preferida cuando representa la entidad.
</div>

<div class="atlas-card">
<h3>Config</h3>
SForm recibe un contrato único de configuración en lugar de inputs paralelos.
</div>

<div class="atlas-card">
<h3>Proxy</h3>
Carga y guardado pertenecen al pipeline del formulario; un DataStore auxiliar no se convierte en owner del record principal.
</div>

</div>

<div class="atlas-flowline">
<strong>ModelBase</strong> → <strong>SFormConfigInput</strong> → <strong>SForm</strong> → <strong>proxy efectivo</strong> → backend
</div>

---

# ¿Cuándo aparece ViewComponent?

<img class="atlas-diagram" src="assets/08-viewcomponent.svg" alt="Responsabilidades de ViewComponent">

### Regla

Un componente Angular normal es suficiente para presentación y estado local pequeño.

**ViewComponent aparece cuando existen estado, recursos o coordinación scoped que merecen owners explícitos.**

---

# Components y Shell

<div class="atlas-grid atlas-grid-2">

<div class="atlas-card">
<h3>Components</h3>
Primitives reutilizables: layout, fields, ventanas, diálogos, feedback, navegación y acciones.
<br><br>
No sustituyen HTML/CSS trivial.
</div>

<div class="atlas-card">
<h3>Shell</h3>
Compone la experiencia global de aplicación: navegación, chrome y capacidades transversales.
<br><br>
No debe absorber la lógica funcional de cada feature.
</div>

</div>

### UX por rol ≠ autorización

Ocultar o deshabilitar una acción en frontend mejora la UX, pero **la seguridad efectiva vive en backend**.

---

# Seguridad por capas

<img class="atlas-diagram" src="assets/09-security-layers.svg" alt="Capas de seguridad ATLAS">

### Orden mental

**identidad → autorización de operación → alcance de datos → campos/asociaciones → resultado efectivo**

`@BeforeRead` puede participar en lifecycle, pero no sustituye este pipeline.

---

# TreeGrid: jerarquía es otra capability

<div class="atlas-grid atlas-grid-2">

<div class="atlas-card">
<h3>Grid</h3>
Colección plana y comportamiento tabular.
</div>

<div class="atlas-card">
<h3>TreeGrid</h3>
Reutiliza schema tabular, pero añade capability jerárquica: root, children, expansión, selección tree, filtros y carga de ramas.
</div>

</div>

<div class="atlas-flowline">
<strong>schema</strong> = columnas · <strong>tree</strong> = jerarquía y comportamiento
</div>

> TreeGrid no es simplemente “Grid + una columna tree”.

---

# CRUD estándar o API custom

<img class="atlas-diagram" src="assets/10-crud-vs-custom.svg" alt="Árbol de decisión CRUD estándar frente a API custom">

### Política docente

El alumno debe aprender primero a **no crear complejidad innecesaria**.

Custom no significa “más profesional”. Significa que existe una necesidad que el contrato estándar no cubre.

---

# Mapa de aprendizaje

<div class="atlas-roadmap">

<span>00 Arquitectura</span>
<span>01 Backend + Data REST</span>
<span>02 ModelBase + metadata</span>
<span>03 Grid + Forms</span>
<span>04 ViewComponent + Components</span>
<span>05 Seguridad + CRUD lifecycle</span>
<span>06 Relaciones + TreeGrid</span>
<span>07 Casos avanzados</span>

</div>

### Núcleo antes que catálogo

Los módulos avanzados se estudian después de dominar los contratos transversales y siempre atendiendo a su madurez y evidencia real.

---

# El modelo mental que queremos conservar

<div class="atlas-grid atlas-grid-2">

<div class="atlas-card">
<h3>Antes de implementar</h3>

1. ¿Qué capability necesito?
2. ¿Quién es owner?
3. ¿Cuál es el happy path?
4. ¿Qué metadata ya existe?
5. ¿La seguridad está en backend?
6. ¿Hay una razón objetiva para extender?
</div>

<div class="atlas-card">
<h3>Resultado esperado</h3>

Una solución que usa ATLAS como plataforma coherente, no como una colección de componentes independientes.

<br>

<strong>Menos wiring accidental. Más contrato explícito.</strong>
</div>

</div>

---

# Siguiente módulo
## Backend + Data REST

Partiremos de una entidad y seguiremos el flujo hasta el endpoint REST, manteniendo el mismo criterio:

**minimal → configured → extended → custom**

<small>La API concreta se consulta en ATLAS3; las slides explican el porqué y el modelo mental.</small>
