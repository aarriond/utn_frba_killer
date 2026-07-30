# CONTRIBUTING - Guía de Contribución

Para mantener la calidad y consistencia pedagógica de los System Prompts en **UTN FRBA**, todos los aportes se gestionan mediante GitHub Issues y Pull Requests validados automáticamente por nuestro pipeline de CI.

---

## 1. Uso Obligatorio de Plantillas de Issues

Antes de enviar código o crear un Pull Request, abrí un **Issue** en GitHub seleccionando una de nuestras plantillas estructuradas (*Issue Templates*):

* **Propuesta de nueva materia**: Para proponer la creación de un nuevo prompt (ej. *Electrónica Aplicada I*).
* **Propuesta de Mejora**: Para sugerir calibraciones, ajustes pedagógicos o adición de reglas a un prompt existente.
* **Reporte de Error (Bugfix)**: Para notificar comportamiento indeseado de la IA (ej. si entrega soluciones completas, usa C puro en vez de C++, o se salta directivas socráticas).

---

## 2. Ubicación de Archivos y Nombrado

Todos los nuevos archivos de prompt deben ubicarse siguiendo estrictamente la jerarquía:

```text
materias/<especialidad>/nivel_<N>/<nombre_materia>.md
```

* **Ejemplo**: `materias/electronica/nivel_2/informatica_2.md`

---

## 3. La Regla de Oro: Las 6 Secciones Obligatorias

No se aceptarán aportes que no incluyan las siguientes 6 secciones formateadas con sus títulos exactos de nivel 2 (`##`):

1. `## 1. Identidad y Contexto`
2. `## 2. Alcance y Límites`
3. `## 3. Reglas Pedagógicas y de Formato`
4. `## 4. Convenciones de Hardware / Entorno`
5. `## 5. Directivas de Uso Responsable y Prevención de Atajos`
6. `## 6. Prompts de Inicio`

---

## 4. Tests y Validaciones Automatizadas en CI

Al abrir o actualizar un Pull Request, GitHub Actions ejecutará automáticamente la suite de integración continua:

* 🔍 **Validación de Estructura (`validar_estructura.yml`)**: Verifica automáticamente la correcta ubicación en `materias/` y la presencia de los títulos exactos de las 6 secciones.
* 🤖 **Evaluación Automatizada vía LLM (`llm_evaluator.yml`)**: Someterá el prompt a tests automatizados con modelo de lenguaje para comprobar que mantenga el rol socrático y no devuelva respuestas resueltas ni viole atajos.

> **Importante:** Todos los checks del CI deben estar en verde (✅) para que los mantenedores asignados en `CODEOWNERS` puedan revisar y aprobar el merge.

---

## 5. Política de Fair Use y Derechos de Autor

Está **estrictamente prohibido** incluir material protegido por derechos de autor (enunciados textuales de parciales, diapositivas oficiales o PDFs de la cátedra). 

Todo el contenido debe ser redactado con palabras propias o reformulado cambiando valores y escenarios.
