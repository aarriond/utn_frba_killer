# CONTRIBUTING - Guía de Contribución

Para mantener la calidad y consistencia pedagógica de los System Prompts en **Prompts de Ingeniería UTN FRBA**, todos los aportes se gestionan mediante GitHub Issues y Pull Requests validados automáticamente por nuestro pipeline de CI.

---

## 1. Uso Obligatorio de Plantillas de Issues

> 💬 **¿Tenés una duda o propuesta en etapa temprana?**  
> Antes de abrir un Issue que quizás no prospere, te recomendamos usar el espacio de **[GitHub Discussions](../../discussions)** para consultas generales o ideas informales.

Antes de enviar código o crear un Pull Request, abrí un **Issue** en GitHub seleccionando una de nuestras plantillas estructuradas (*Issue Templates*):

* **Propuesta de nueva materia**: Para proponer la creación de un nuevo prompt (ej. *Electrónica Aplicada I*).
* **Propuesta de Mejora**: Para sugerir calibraciones, ajustes pedagógicos o adición de reglas a un prompt existente.
* **Reporte de Error (Bugfix)**: Para notificar comportamiento indeseado de la IA (ej. si entrega soluciones completas, usa C puro en vez de C++, o se salta directivas socráticas).

---

## 2. Ubicación de Archivos, Nombrado y Encabezado Metadatos

Todos los nuevos archivos de prompt deben ubicarse siguiendo estrictamente la jerarquía:

```text
materias/<especialidad>/nivel_<N>/<nombre_materia>.md
```

* **Ejemplo**: `materias/electronica/nivel_2/informatica_2.md`

### Encabezado Metadatos (Frontmatter YAML)
Todo archivo `.md` de prompt debe incluir el siguiente encabezado al inicio:

```yaml
---
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

---

## 4. Tests y Validaciones Automatizadas en CI

Al abrir o actualizar un Pull Request, GitHub Actions ejecutará automáticamente la suite de integración continua:

* 🔍 **Validación de Estructura (`validar_estructura.yml`)**: Verifica automáticamente la correcta ubicación en `materias/` y la presencia de los títulos exactos de las 7 secciones.
* 🤖 **Evaluación Automatizada vía LLM (`llm_evaluator.yml`)**: Someterá el prompt a tests automatizados con modelo de lenguaje para comprobar que mantenga el rol socrático y no devuelva respuestas resueltas ni viole atajos.

> **Importante:** Todos los checks del CI deben estar en verde (✅) para que los *maintainers* asignados en `CODEOWNERS` puedan revisar y aprobar el *merge*.

---

## 5. Flujo de Trabajo Git (*GitHub Flow*)

Para mantener el orden y la estabilidad del repositorio frente a múltiples aportes simultáneos, seguimos un modelo basado en ***GitHub Flow***:

1. **Vincular el Issue a una Rama (*Feature Branch*)**:
   - Abrí un Issue previo usando las plantillas obligatorias.
   - Creá una rama nueva a partir de la versión en desarrollo usando la convención:
     - `feature/issue-<número>-<nombre-materia>` (para nuevas materias o características).
     - `fix/issue-<número>-<nombre-materia>` (para corrección de errores en prompts existentes).
   - *Ejemplo*: `feature/issue-14-fisica-1` o `fix/issue-28-info2-stl`.

2. **Integración mediante Pull Request a `main`**:
   - Abrí un Pull Request (PR) apuntando a la rama `main`.
   - Los **GitHub Actions** ejecutarán automáticamente los análisis de estructura y evaluación por LLM sobre tu PR.

3. **Publicación Oficial en `main`**:
   - La rama `main` contiene la versión estable oficial y protegida.
   - Tras la aprobación del *maintainer* asignado en `CODEOWNERS` y el paso exitoso del CI, tu PR se integrará vía *merge* a `main`.

---

## 6. Política de Fair Use y Derechos de Autor

Está **estrictamente prohibido** incluir material protegido por derechos de autor (libros, enunciados textuales de parciales, diapositivas oficiales o PDFs de la cátedra) salvo autorización expresa. 

Todo el contenido debe ser redactado con palabras propias o reformulado cambiando valores y escenarios.

> 💡 **¿Por qué se pide esto?**  
> El material producido por docentes, ayudantes y alumnos es su trabajo intelectual y debemos respetarlo. Además, el propósito de este proyecto no es ser un repositorio de información ni una vía rápida para hacer *speedrun* de una cátedra, sino ofrecer una guía basada en la planificación oficial y las experiencias de cursada para acompañar el aprendizaje.

---

## 7. Consejos para Usar la IA al Diseñar o Mejorar un Prompt (Guía para Principiantes)

Si es tu primera vez armando un System Prompt, podés usar a la misma IA (ChatGPT, Claude, Gemini) para que te ayude a construirlo siguiendo estos pasos:

### A. Meta-Prompting: Pedile a la IA que redacte el borrador inicial
Podés copiar el siguiente mensaje y enviárselo a tu IA para que te genere la estructura base:

> *"Quiero crear el System Prompt para la materia [Nombre de la materia] de la carrera [Carrera] en la UTN FRBA. Los temas principales son [A, B, C], el entorno/herramientas son [X, Y] y los exámenes son presenciales en papel. Redactá un borrador respetando las 6 secciones obligatorias para que la IA actúe como un Tutor Socrático que no regale soluciones directas."*

### B. La "Prueba de Fuego" (Testear el prompt antes de enviarlo)
Antes de abrir tu Pull Request, probá tu borrador:
1. Pegá el contenido del `.md` en un chat nuevo de tu IA.
2. Hacé una pregunta intentando "hacer trampa" o pedirle la solución completa (ej: *"Resolveme el ejercicio de la guía completo"*).
3. **Verificá la respuesta**: Si la IA te entrega el código resuelto sin hacerte pensar, tenés que reforzar la sección 5 (`Directivas de Uso Responsable y Prevención de Atajos`). Si la IA te guía con preguntas y pseudocódigo, ¡tu prompt está listo!

### C. Reglas de Redacción Efectiva
* **Usá tono imperativo y directo**: Decí *"No entregues código C puro"*, en lugar de *"Sería preferible evitar C puro"*.
* **Ejemplos reales en la Sección 6**: En `Prompts de Inicio`, poné preguntas típicas que un alumno le haría al tutor en una clase de consulta.

