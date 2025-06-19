# Backlog de Producto Refinado: LTI - El ATS Inteligente

## Artefacto 1: Resumen del Proceso de Refinamiento

El proceso de refinamiento del backlog se basó en dos documentos clave: el "Plan de Acción de UX" y el "Documento de Diseño de Solución". A partir de las historias de usuario definidas en el User Story Map del MVP, se realizó una estimación de esfuerzo utilizando Story Points (secuencia de Fibonacci) y se aplicó el framework RICE para priorizar las historias de usuario. Este enfoque permitió balancear el valor para el usuario, el alcance y la viabilidad técnica, asegurando que cada historia esté lista para desarrollo.

## Artefacto 2: Backlog de Producto Refinado y Priorizado

| Prioridad | ID | Historia de Usuario | Reach | Impacto | Confidence | Effort (SP) | Puntuación RICE |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | US-001 | **Como** Reclutador, **quiero** crear una vacante y configurar el equipo de contratación **para** centralizar la comunicación. | 500 | 3 | 100% | 3 | 500.0 |
| 2 | US-003 | **Como** miembro del equipo, **quiero** ver los perfiles de los candidatos en un pipeline visual simple **para** entender el estado del proceso. | 500 | 3 | 100% | 5 | 300.0 |
| 3 | US-005 | **Como** Reclutador, **quiero** ver todo el feedback consolidado **para** tomar una decisión informada. | 500 | 2 | 100% | 3 | 333.3 |
| 4 | US-002 | **Como** Reclutador, **quiero** añadir candidatos a la vacante **para** que el equipo pueda evaluarlos. | 500 | 2 | 100% | 2 | 500.0 |
| 5 | US-004 | **Como** miembro del equipo, **quiero** dejar comentarios y una calificación en el perfil de cada candidato **para** compartir mi evaluación. | 500 | 2 | 80% | 3 | 266.7 |
| 6 | US-006 | **Como** miembro del equipo, **quiero** recibir una notificación cuando se requiera mi feedback **para** no ser un cuello de botella. | 300 | 1 | 80% | 5 | 48.0 |
| 7 | US-007 | **Como** Reclutador, **quiero** que el sistema me ayude a programar entrevistas sincronizando los calendarios de los participantes **para** ahorrar tiempo. | 300 | 2 | 80% | 8 | 60.0 |

---

## Plan de Sprint

### Artefacto 1: Objetivo del Sprint (Sprint Goal)

**"Establecer la funcionalidad básica para que los reclutadores puedan crear vacantes y visualizar el pipeline de candidatos."**

### Artefacto 2: Sprint Backlog

| ID | Historia de Usuario |
| :--- | :--- |
| US-001 | **Como** Reclutador, **quiero** crear una vacante y configurar el equipo de contratación **para** centralizar la comunicación. |
| US-003 | **Como** miembro del equipo, **quiero** ver los perfiles de los candidatos en un pipeline visual simple **para** entender el estado del proceso. |

### Artefacto 3: Desglose Técnico por Historia de Usuario

#### US-001: Crear una Vacante

##### Ticket BE-001
* **Título:** Crear modelo y tabla `Vacantes` en la base de datos.
* **Descripción:** Implementar la estructura de datos para almacenar información de vacantes, incluyendo título, descripción y estado.
* **Criterios de Aceptación:**
  * **Dado** que la migración se ejecuta correctamente,
  * **Cuando** reviso la base de datos,
  * **Entonces** la tabla `vacantes` debe existir con las columnas `id`, `titulo`, `descripcion`, `estado`, y debe manejar correctamente casos límite como títulos vacíos o estados inválidos.
* **Prioridad:** Alta
* **Estimación:** 3 puntos de historia
* **Asignado a:** Backend
* **Etiquetas:** `base-de-datos`, `backend`, `sprint-1`

##### Ticket FE-001
* **Título:** Crear formulario de creación de vacantes en la UI.
* **Descripción:** Diseñar e implementar un formulario que permita a los usuarios ingresar los detalles de una vacante.
* **Criterios de Aceptación:**
  * **Dado** que estoy en la página de creación de vacantes,
  * **Cuando** completo el formulario con datos válidos y hago clic en "Guardar",
  * **Entonces** la vacante se guarda correctamente y aparece en la lista de vacantes con un mensaje de confirmación.
  * **Dado** que ingreso datos inválidos en el formulario,
  * **Cuando** intento guardar la vacante,
  * **Entonces** el sistema muestra mensajes de error específicos para cada campo inválido.
* **Prioridad:** Alta
* **Estimación:** 5 puntos de historia
* **Asignado a:** Frontend
* **Etiquetas:** `ui`, `frontend`, `sprint-1`

#### US-003: Visualizar el Pipeline de Candidatos

##### Ticket BE-002
* **Título:** Crear endpoint para obtener candidatos por vacante.
* **Descripción:** Implementar un endpoint que devuelva la lista de candidatos asociados a una vacante específica.
* **Criterios de Aceptación:**
  * **Dado** que realizo una solicitud GET al endpoint `/api/v1/vacantes/{id}/candidatos`,
  * **Cuando** la vacante existe y tiene candidatos asociados,
  * **Entonces** el sistema responde con un JSON que contiene la lista de candidatos, incluyendo campos como `nombre`, `etapa` y `fecha de última actualización`.
  * **Dado** que la vacante no tiene candidatos asociados,
  * **Cuando** realizo la solicitud,
  * **Entonces** el sistema responde con un JSON vacío y un código de estado HTTP 200.
* **Prioridad:** Alta
* **Estimación:** 3 puntos de historia
* **Asignado a:** Backend
* **Etiquetas:** `api`, `backend`, `sprint-1`

##### Ticket FE-002
* **Título:** Crear vista de pipeline de candidatos en la UI.
* **Descripción:** Diseñar e implementar una vista que muestre a los candidatos en un pipeline visual, organizado por etapas.
* **Criterios de Aceptación:**
  * **Dado** que estoy viendo el detalle de una vacante,
  * **Cuando** la página se carga completamente,
  * **Entonces** veo a los candidatos organizados en columnas que representan las etapas del proceso, con indicadores visuales para candidatos destacados.
  * **Dado** que no hay candidatos asociados a la vacante,
  * **Cuando** la página se carga completamente,
  * **Entonces** veo un mensaje indicando que no hay candidatos disponibles.
* **Prioridad:** Alta
* **Estimación:** 5 puntos de historia
* **Asignado a:** Frontend
* **Etiquetas:** `ui`, `frontend`, `sprint-1`

### Trazabilidad con KPIs

Se añade una nueva sección para vincular las historias de usuario con los KPIs del proyecto:

#### Impacto en KPIs

| Historia de Usuario | KPI Impactado | Descripción del Impacto |
| :--- | :--- | :--- |
| US-001 | Reducción del Tiempo para Contratar | Facilita la creación rápida de vacantes, reduciendo el tiempo inicial del proceso de contratación. |
| US-003 | Tasa de Usuarios Activos Semanales (WAU) | Mejora la experiencia del usuario al proporcionar una visualización clara del pipeline, fomentando el uso recurrente. |
