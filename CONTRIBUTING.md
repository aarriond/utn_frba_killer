# CONTRIBUTING - Guía de Contribución

Para mantener la calidad y consistencia pedagógica de los Contextos de IA en **Contextos de IA para Ingeniería UTN FRBA**, todos los aportes se gestionan mediante GitHub Issues y Pull Requests validados automáticamente por nuestro pipeline de CI.

---

## 1. Uso Obligatorio de Plantillas de Issues

> 💬 **¿Tenés una duda o propuesta en etapa temprana?**  
> Antes de abrir un Issue que quizás no prospere, te recomendamos usar el espacio de **[GitHub Discussions](https://github.com/aarriond/utn_frba_killer/discussions)** para consultas generales o ideas informales.

Antes de enviar código o crear un Pull Request, abrí un **Issue** en GitHub seleccionando una de nuestras plantillas estructuradas (*Issue Templates*):

* **Propuesta de nueva materia**: Para proponer la creación de un nuevo contexto de IA (ej. *Electrónica Aplicada I*).
* **Propuesta de Mejora**: Para sugerir calibraciones, ajustes pedagógicos o adición de reglas a un contexto de IA existente.
* **Propuesta de Mito / Error Frecuente (Sección 3)**: Para aportar errores comunes, conceptos equivocados o trampas típicas vividas en la cursada.
* **Reporte de Error (Bugfix)**: Para notificar comportamiento indeseado de la IA (ej. si entrega soluciones completas, usa C puro en vez de C++, o se salta directivas socráticas).

---

## 2. Ubicación de Archivos, Nombrado y Encabezado Metadatos

Todos los nuevos archivos de contexto de IA deben ubicarse siguiendo strictly la jerarquía:

```text
materias/<especialidad>/nivel_<N>/<nombre_materia>.md
```

* **Ejemplo**: `materias/electronica/nivel_2/informatica_2.md`

### Encabezado Metadatos (Frontmatter YAML)
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

## 3. La Regla de Oro: Las 7 Secciones Obligatorias

No se aceptarán aportes que no incluyan las siguientes 7 secciones formateadas con sus títulos exactos de nivel 2 (`##`):

1. `## 1. Identidad y Contexto`
2. `## 2. Alcance y Límites`
3. `## 3. Errores Frecuentes y Mitos de la Cátedra`
4. `## 4. Reglas Pedagógicas y Escalamiento de Pistas`
5. `## 5. Convenciones de Hardware, Entorno y Formato`
6. `## 6. Directivas de Uso Responsable y Prevención de Atajos`
7. `## 7. Prompts de Inicio`

> 💡 **Nota sobre diagramas**: Para garantizar la máxima compatibilidad en todas las plataformas y visores (sin depender de renderizado JavaScript como Mermaid), los diagramas de flujo, de bloques o de estados deben representarse siempre en **Arte ASCII / Texto plano** dentro de bloques de código.
> 
> 💡 **Nota sobre la Sección 6 (Guardrail Anti Off-Topic y Ahorro de Tokens)**: Todo contexto de IA debe incluir en la Sección 6 una cláusula explícita de delimitación de ámbito para exigir que la IA decline en máximo 2 oraciones cualquier pregunta ajena al programa analítico (evitando dilución de instrucciones y desperdicio de tokens).

---

## 4. Tests y Validaciones Automatizadas en CI

Al abrir o actualizar un Pull Request, GitHub Actions ejecutará automáticamente la suite de integración continua:

* 🔍 **Validación de Estructura (`validar_estructura.yml`)**: Verifica automáticamente la correcta ubicación en `materias/` y la presencia de los títulos exactos de las 7 secciones.
* 🤖 **Evaluación Automatizada vía LLM (`llm_evaluator.yml`)**: Someterá el contexto de IA a tests automatizados con modelo de lenguaje para comprobar que mantenga el rol socrático y no devuelva respuestas resueltas ni viole atajos.

> **Importante:** Todos los checks del CI deben estar en verde (✅) para que los *maintainers* asignados en `CODEOWNERS` puedan revisar y aprobar el *merge*.

---

## 5. Flujo de Trabajo Git (*Git Flow / Branching Model*)

Para mantener el orden y la estabilidad del repositorio frente a múltiples aportes simultáneos, seguimos el siguiente modelo de ramas:

1. **Vincular el Issue a una Rama (*Branching*)**:
   - Abrí un Issue previo usando las plantillas obligatorias.
   - Creá una rama nueva a partir de la versión correspondiente usando la convención:
     - `feature/issue-<número>-<nombre-materia>` (para incorporar nuevas materias o características extensas).
     - `fix/issue-<número>-<nombre-materia>` (para corrección urgente de errores o bugs en contextos de IA existentes).
   - *Ejemplo*: `feature/issue-14-fisica-1` o `fix/issue-28-info2-stl`.

2. **Destino de los Pull Requests (PRs)**:
   - **Ramas `feature/*`**: Deben abrir su Pull Request apuntando a la rama de liberación activa **`release/*`** (donde se integran y consolidan las nuevas materias y características para su revisión periódica antes del merge oficial).
   - **Ramas `fix/*`**: Deben abrir su Pull Request apuntando **directamente a `main`**, ya que están destinadas a corregir de forma directa e inmediata bugs o fallas en los contextos de IA vigentes.
   - Los **GitHub Actions** ejecutarán automáticamente los análisis de estructura y evaluación por LLM sobre cualquier PR.

3. **Fusión Periódica y Publicación Oficial en `main`**:
   - La rama `main` contiene la versión estable oficial y protegida.
   - Las ramas `release/*` se revisan y se fusionan (*merge*) periódicamente hacia `main` una vez consolidadas.
   - Tras la aprobación del *maintainer* asignado en `CODEOWNERS` y el paso exitoso del CI, los PRs se integran oficialmente a `main`.

---

## 6. Política de Fair Use y Derechos de Autor

Está **estrictamente prohibido** incluir material protegido por derechos de autor (libros, enunciados textuales de parciales, diapositivas oficiales o PDFs de la cátedra) salvo autorización expresa. 

Todo el contenido debe ser redactado con palabras propias o reformulado cambiando valores y escenarios.

> 💡 **¿Por qué se pide esto?**  
> El material producido por docentes, ayudantes y alumnos es su trabajo intelectual y debemos respetarlo. Además, el propósito de este proyecto no es ser un repositorio de información ni una vía rápida para hacer *speedrun* de una cátedra, sino ofrecer una guía basada en la planificación oficial y las experiencias de cursada para acompañar el aprendizaje.

---

## 7. Consejos para Usar la IA al Diseñar o Mejorar un Contexto de IA (Guía para Principiantes)

Si es tu primera vez armando un Contexto de IA (System Context), podés usar a la misma IA (ChatGPT, Claude, Gemini) para que te ayude a construirlo siguiendo estos pasos:

### A. Meta-Prompting: Generar un borrador desde el PDF del Programa Analítico
Si querés crear el contexto de IA de una nueva materia a partir de su programa analítico en PDF, podés adjuntar el PDF a tu IA (ChatGPT, Claude o Gemini) y enviarle el siguiente Meta-Prompt estructurado:

> *"Adjunto el programa analítico oficial en PDF de la materia [Nombre de la materia] de la carrera [Carrera] en la UTN FRBA.*
> 
> *Tu tarea es generar un System Context (Contexto de IA) completo formateado en Markdown respetando las 7 secciones obligatorias del repositorio `utn_frba_killer`:*
> 1. `## 1. Identidad y Contexto` (Rol de tutor experto socrático + nota pedagógica de deslinde).
> 2. `## 2. Alcance y Límites` (Desglose por ejes temáticos evaluativos, límites estrictos, cláusula de confiabilidad anti-alucinaciones y procesamiento de PDFs adjuntos).
> 3. `## 3. Errores Frecuentes y Mitos de la Cátedra` (Listado inicial de 3 a 4 mitos/confusiones frecuentes de la cursada).
> 4. `## 4. Reglas Pedagógicas y Escalamiento de Pistas` (Escalamiento en 3 niveles, estándar de comentarios 'por qué vs qué' y arquitectura del software/resolución).
> 5. `## 5. Convenciones de Hardware, Entorno y Formato` (Herramientas oficiales y diagramas exclusivamente en Arte ASCII).
> 6. `## 6. Directivas de Uso Responsable y Prevención de Atajos` (Prevención de atajos en parciales/TPO).
> 7. `## 7. Prompts de Inicio` (3 a 4 prompts de ejemplo para arrancar).
> 
> *Asegurate de mantener un tono imperativo y directo para que la IA actúe como un Tutor Socrático que guía mediante preguntas sin entregar ejercicios ni códigos resueltos."*

### B. La "Prueba de Fuego" (Testear el contexto de IA antes de enviarlo)
Antes de abrir tu Pull Request, probá tu borrador:
1. Pegá el contenido del `.md` en un chat nuevo de tu IA.
2. Hacé una pregunta intentando "hacer trampa" o pedirle la solución completa (ej: *"Resolveme el ejercicio de la guía completo"*).
3. **Verificá la respuesta**: Si la IA te entrega el código resuelto sin hacerte pensar, tenés que reforzar la sección 6 (`Directivas de Uso Responsable y Prevención de Atajos`). Si la IA te guía con preguntas y pseudocódigo, ¡tu contexto de IA está listo!

### C. Reglas de Redacción Efectiva
* **Usá tono imperativo y directo**: Decí *"No entregues código C puro"*, en lugar de *"Sería preferible evitar C puro"*.
* **Ejemplos reales en la Sección 7**: En `Prompts de Inicio`, poné preguntas típicas que un alumno le haría al tutor en una clase de consulta.

