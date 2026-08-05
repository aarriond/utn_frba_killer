# CONTRIBUTING - Guía de contribución

Para mantener la calidad y consistencia pedagógica de los **Contextos de IA para Ingeniería UTN FRBA**, todos los aportes se gestionan mediante GitHub Issues y Pull Requests validados automáticamente por un pipeline de CI.

---

## 1. Uso obligatorio de plantillas de issues

> 💬 **¿Tenés una duda o propuesta en etapa temprana y no sabés si va o no?**  
> Antes de abrir un Issue que quizás no prospere, te recomendamos usar el espacio de **[GitHub Discussions](https://github.com/aarriond/utn_frba_killer/discussions)** para consultas generales o ideas informales.

Antes de enviar código o crear un Pull Request, abrí un **Issue** en GitHub seleccionando una de nuestras plantillas estructuradas (*Issue Templates*):

* **Propuesta de nueva materia**: Para proponer la creación de un nuevo contexto de IA (ej. *Electrónica Aplicada I*).
* **Propuesta de Mejora**: Para sugerir calibraciones, ajustes pedagógicos o adición de reglas a un contexto de IA existente.
* **Propuesta de Mito / Error Frecuente (Sección 3)**: Para aportar errores comunes, conceptos equivocados o trampas típicas vividas en la cursada.
* **Reporte de Error (Bugfix)**: Para notificar comportamiento indeseado de la IA (ej. si entrega soluciones completas, usa C puro en vez de C++, o se salta directivas socráticas).

---

## 2. Ubicación de archivos, nombrado y encabezado metadatos

Todos los nuevos archivos de contexto de IA deben ubicarse estrictamente siguiendo la siguiente jerarquía:

```text
materias/basicas/nivel_<N>/<nombre_materia>.md            # Materias comunes a todas las carreras (ej. Análisis I, Física I)

materias/<especialidad>/nivel_<N>/<nombre_materia>.md     # Materias específicas de especialidad (ej. electronica, sistemas)
```

* **Ejemplo Materia Básica**: `materias/basicas/nivel_1/fisica_1.md`
* **Ejemplo Materia de Especialidad**: `materias/electronica/nivel_2/informatica_2.md`

### Encabezado metadatos (Frontmatter YAML)
Todo archivo `.md` de contexto de IA debe incluir el siguiente encabezado al inicio:

```yaml
---
name: [Opcional: Identificador único de la skill, ej: tutor-informatica-2]
description: [Opcional: Breve descripción para la detección automática de agentes de IA]
Materia: [Nombre de la Materia y Plan]
Autor Original: [Nombre del Autor Original] (@usuario_github)
Otros Autores: [Otros colaboradores si aplica / Ninguno]
Licencia: CC BY-NC-ND 4.0
---
```

---

## 3. La regla de oro: Las 7 secciones obligatorias

No se aceptarán aportes que no incluyan las siguientes 7 secciones formateadas con sus títulos exactos de nivel 2 (`##`):

1. `## 1. Identidad y contexto`
2. `## 2. Alcance y límites`
3. `## 3. Errores frecuentes y mitos de la cátedra`
4. `## 4. Reglas pedagógicas y escalamiento de pistas`
5. `## 5. Convenciones de hardware, entorno y formato`
6. `## 6. Directivas de uso responsable y prevención de atajos`
7. `## 7. Prompts de inicio`

> 💡 **Nota sobre diagramas**: Para garantizar la máxima compatibilidad en todas las plataformas y visores (sin depender de renderizado JavaScript como Mermaid), los diagramas de flujo, de bloques o de estados deben representarse siempre en **Arte ASCII / Texto plano** dentro de bloques de código.
> 
> 💡 **Nota sobre la Sección 6 (Guardrail Anti Off-Topic y Ahorro de Tokens)**: Todo contexto de IA debe incluir en la Sección 6 una cláusula explícita de delimitación de ámbito para exigir que la IA decline en máximo 2 oraciones cualquier pregunta ajena al programa analítico (evitando dilución de instrucciones y desperdicio de tokens).

---

## 4. Tests y validaciones automatizadas en CI

Al abrir o actualizar un Pull Request, GitHub Actions ejecutará automáticamente la suite de integración continua:

* 🔍 **Validación de estructura (`validar_estructura.yml`)**: Verifica automáticamente la correcta ubicación en `materias/` y la presencia de los títulos exactos de las 7 secciones.
* 🤖 **Evaluación automatizada vía LLM (`llm_evaluator.yml`)**: Someterá el contexto de IA a tests automatizados con modelo de lenguaje para comprobar que mantenga el rol socrático y no devuelva respuestas resueltas ni viole atajos.

> **Importante:** Todos los checks del CI deben estar en verde (✅) para que los *maintainers* asignados en `CODEOWNERS` puedan revisar y aprobar el *merge*.

### 💻 Validaciones locales en consola (Git Pre-Push Hook)

Para los colaboradores que trabajan 100% en la terminal y desean recibir un **rechazo directo (*push reject*) en su consola** antes de subir commits con errores de estructura a GitHub, pueden activar el hook local ejecutando el siguiente comando una sola vez al clonar el repo:

```bash
git config core.hooksPath .githooks
```

Una vez activado, cada vez que ejecutes `git push`, Git comprobará localmente que los archivos `.md` de `materias/` cumplan con las 7 secciones obligatorias antes de transmitir los datos al servidor.


---

## 5. Flujo de trabajo Git (*Modelo de Pull Requests y ramas*)

Para mantener el orden y la estabilidad del repositorio frente a múltiples aportes simultáneos, **es obligatorio utilizar Pull Requests (PRs)**. La rama `main` y las ramas `release/*` están protegidas y no admiten commits directos.

```text
 ┌───────────────────┐
 │   Apertura Issue  │
 │ (Feature / Mito)  │
 └─────────┬─────────┘
           │ (Auto-creación vía GitHub Actions)
           ▼
 ┌───────────────────┐
 │  feature/<número> │
 └─────────┬─────────┘
           │ (Pull Request + Pruebas CI)
           ▼
 ┌───────────────────┐
 │ release/vX.Y.Z    ├─────────────────────────────────────────┐
 └───────────────────┘                                         │
   (Rama Liberación)                                           │ (PR Consolidación +
                                                               │  Suite Release CI)
 ┌───────────────────┐                                         │
 │   Apertura Issue  │                                         │
 │  (Bugfix / Error) │                                         │
 └─────────┬─────────┘                                         │
           │ (Auto-creación vía GitHub Actions)                ▼
           ▼                                           ┌───────────────────┐
 ┌───────────────────┐                                 │ main              │
 │    fix/<número>   ├────────────────────────────────►│ (Tag vX.Y.Z       │
 └───────────────────┘ (PR Directo + 1 Maintainer)     │  + Release GH)    │
                                                       └───────────────────┘
```

### Pasos del Flujo de Trabajo:

1. **Apertura de Issue y Generación Automática de Rama**:
   - Abrí un Issue utilizando la plantilla correspondiente.
   - El sistema de automatizaciones (GitHub Actions) creará automáticamente la rama dedicada:
     - **`feature/<número>`** (para incorporar nuevas materias, mejoras o mitos).
     - **`fix/<número>`** (para corrección de errores o bugs en contextos de IA existentes).
   - El bot dejará un comentario en el Issue con las instrucciones para hacer `git checkout`.

2. **Destino de los Pull Requests (PRs)**:
   - **Ramas de características (`feature/<número>`)**: Deben abrir su PR apuntando hacia la rama de liberación activa **`release/vX.Y.Z`** (ej. `release/v1.2.0`). En cada PR se ejecutan automáticamente la validación de estructura y la evaluación con LLM.
   - **Ramas de corrección de errores (`fix/<número>`)**: Deben abrir su PR apuntando **directamente a `main`**. Requieren la aprobación de al menos 1 Maintainer para poder mergearse.

3. **Consolidación Periódica de Releases**:
   - Una vez consolidado un conjunto de cambios en la rama de liberación activa, los Maintainers abren un PR desde **`release/vX.Y.Z`** hacia **`main`**.
   - Se ejecuta automáticamente la **Suite de Consistencia de Release** (comprobando ausencia de duplicados, validación de secciones, reglas ASCII sin bloques Mermaid no compatibles e integridad de metadatos).
   - El PR debe ser aprobado manualmente por un Maintainer.

4. **Publicación y Limpieza Automática**:
   - Al mergear la rama `release/vX.Y.Z` a `main`:
     - Se genera automáticamente el **Git Tag** (ej. `v1.2.0`) y la **GitHub Release** con su Changelog.
     - La rama `release/vX.Y.Z` y las ramas asociadas se **eliminan automáticamente** del repositorio.



---

## 6. Política de fair use y derechos de autor

Está **estrictamente prohibido** incluir material protegido por derechos de autor (libros, enunciados textuales de parciales, diapositivas oficiales o PDFs de la cátedra) salvo autorización expresa. 

Todo el contenido debe ser redactado con palabras propias o reformulado cambiando valores y escenarios.

> 💡 **¿Por qué se pide esto?**  
> El material producido por docentes, ayudantes y alumnos es su trabajo intelectual y debemos respetarlo. Además, el propósito de este proyecto no es ser un repositorio de información ni una vía rápida para hacer *speedrun* de una cátedra, sino ofrecer una guía basada en la planificación oficial y las experiencias de cursada para acompañar el aprendizaje.

---

## 7. Consejos para usar la IA al diseñar o mejorar un contexto de IA (Guía para principiantes)

Si es tu primera vez armando un Contexto de IA (System Context), podés usar a la misma IA (ChatGPT, Claude, Gemini) para que te ayude a construirlo siguiendo estos pasos:

### A. Meta-prompting: Generar un borrador desde el PDF del programa analítico
Si querés crear el contexto de IA de una nueva materia a partir de su programa analítico en PDF, podés adjuntar el PDF a tu IA (ChatGPT, Claude o Gemini) y enviarle el siguiente Meta-Prompt estructurado:

> *"Adjunto el programa analítico oficial en PDF de la materia [Nombre de la materia] de la carrera [Carrera] en la UTN FRBA.*
> 
> *Tu tarea es generar un System Context (Contexto de IA) completo formateado en Markdown respetando las 7 secciones obligatorias del repositorio `utn_frba_killer`:*
> 1. `## 1. Identidad y contexto` (Rol de tutor experto socrático + nota pedagógica de deslinde).
> 2. `## 2. Alcance y límites` (Desglose por ejes temáticos evaluativos, límites strictly, cláusula de confiabilidad anti-alucinaciones y procesamiento de PDFs adjuntos).
> 3. `## 3. Errores frecuentes y mitos de la cátedra` (Listado inicial de 3 a 4 mitos/confusiones frecuentes de la cursada).
> 4. `## 4. Reglas pedagógicas y escalamiento de pistas` (Escalamiento en 3 niveles, estándar de comentarios 'por qué vs qué' y arquitectura del software/resolución).
> 5. `## 5. Convenciones de hardware, entorno y formato` (Herramientas oficiales y diagramas exclusivamente en Arte ASCII).
> 6. `## 6. Directivas de uso responsable y prevención de atajos` (Prevención de atajos en parciales/TPO).
> 7. `## 7. Prompts de inicio` (3 a 4 prompts de ejemplo para arrancar).
> 
> *Asegurate de mantener un tono imperativo y directo para que la IA actúe como un Tutor Socrático que guía mediante preguntas sin entregar ejercicios ni códigos resueltos."*

### B. La "prueba de fuego" (Testear el contexto de IA antes de enviarlo)
Antes de abrir tu Pull Request, probá tu borrador:
1. Pegá el contenido del `.md` en un chat nuevo de tu IA.
2. Hacé una pregunta intentando "hacer trampa" o pedirle la solución completa (ej: *"Resolveme el ejercicio de la guía completo"*).
3. **Verificá la respuesta**: Si la IA te entrega el código resuelto sin hacerte pensar, tenés que reforzar la sección 6 (`Directivas de uso responsable y prevención de atajos`). Si la IA te guía con preguntas y pseudocódigo, ¡tu contexto de IA está listo!

### C. Reglas de redacción efectiva
* **Usá tono imperativo y directo**: Decí *"No entregues código C puro"*, en lugar de *"Sería preferible evitar C puro"*.
* **Ejemplos reales en la Sección 7**: En `Prompts de Inicio`, poné preguntas típicas que un alumno le haría al tutor en una clase de consulta.

