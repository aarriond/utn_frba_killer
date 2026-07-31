# Antes que nada, ¿por qué el nombre?
No tengo una respuesta completa para esta pregunta porque es difícil ponerle un nombre, pero se entiende: en algún momento pensás en que te querés recibir ya... Aunque cueste liquidar materias ;)

# Prompts de Ingeniería UTN FRBA
Este repositorio es una iniciativa *open-source* para recopilar y estandarizar **System Prompts (contextos de IA)** para las distintas carreras de Ingeniería en la UTN FRBA (Electrónica, Sistemas, Química, Mecánica, Industrial, Civil, Eléctrica, etc.).

## ¿Por qué existe este proyecto?

El propósito fundamental de este repositorio es **guiar pedagógicamente al estudiante para evitar que delegue su aprendizaje en la inteligencia artificial**. 

Sin un perfil calibrado, las IAs de propósito general (como ChatGPT, Claude, Gemini o Antigravity IDE) actúan como "generadores de soluciones automáticas" que entregan el código o el ejercicio resuelto de un solo tiro. Esto genera una **falsa sensación de dominio**, perjudicando gravemente al alumno al momento de rendir sus exámenes parciales escritos (que se rinden con lápiz y papel) o defender oralmente sus proyectos en coloquios e instancias evaluativas.

Al inyectar estos archivos `.md`, transformamos a la IA en un **Tutor Socrático Exigente** que:
1. **Orienta mediante preguntas clave y pseudocódigo** en lugar de entregar la solución terminada.
2. **Exige al alumno razonar el 'por qué'** de cada algoritmo, cálculo o decisión de diseño.
3. **Mantiene el rigor universitario y los convenios de cada carrera** en la UTN FRBA.

#### 🎯 Ejemplos de calibración por especialidad

* **Ingeniería Electrónica (*Informática I* vs *Informática II*):**
  Evita que la IA confunda C puro con C++ POO bare-metal, impidiendo el uso descontrolado de librerías de alto nivel (STL / `std::vector`) o asignación dinámica (`new`/`delete`) donde se requiere manipulación directa de registros del microcontrolador (ej. NXP LPC845).
* **Ingeniería en Sistemas de Información (*Sintaxis y Semántica de los Lenguajes* / *Diseño de Sistemas*):**
  Exige el modelado formal (autómatas, gramáticas, diagramas UML, arquitectura de componentes) evitando que la IA salte directamente a implementar código sin justificar los patrones o el análisis formal.
* **Ingeniería Química (*Termodinámica* / *Operaciones Unitarias*):**
  Asegura el uso de las unidades del SI, balances de materia y energía paso a paso y métodos numéricos validados, previniendo que la IA entregue ecuaciones resueltas sin desglosar las hipótesis físicas.
* **Ingeniería Mecánica y Civil (*Estabilidad* / *Mecánica de los Fluidos*):**
  Respeta las convenciones de diagramas de cuerpo aislado, momentos torsores/flectores y criterios de cálculo estático/dinámico evaluados en los parciales de la facultad.
* **Ingeniería Industrial (*Investigación Operativa* / *Economía de la Empresa*):**
  Guía el planteo de modelos de optimización lineal y análisis de costos paso a paso antes de correr un solver o arrojar un resultado numérico final.

### ⚠️ La Trampa de la "Falsa Solución": ¿Por qué dejar que la IA resuelva todo te perjudica?

Delegar la resolución completa de un ejercicio en la inteligencia artificial genera un fenómeno muy peligroso durante la cursada:

1. **La Ilusión de Comprensión:** Leer una solución generada por la IA se siente fluido y parece fácil ("ah, claro, era así"). Sin embargo, **leer una solución no es lo mismo que aprender a resolverla**. Al no enfrentarte a la hoja en blanco ni cometer los errores típicos del aprendizaje, no desarrollás las conexiones lógicas necesarias.
2. **El Bloqueo en Exámenes Presenciales:** En la UTN FRBA, los exámenes parciales y finales se rinden **presencialmente en papel (sin computadora)** y los Trabajos Prácticos se defienden **oralmente ante la cátedra**. Si usaste la IA como una muleta para generar respuestas de un tiro, te vas a bloquear en el examen porque nunca ejercitaste el proceso de deducción propio.
3. **Dependencia vs Criterio Técnico:** Un ingeniero no se destaca por saber copiar código o fórmulas, sino por su **criterio técnico, capacidad de depurar fallas complejas y justificar decisiones de diseño**. Si dejás que la IA piense por vos, pasás de ser un futuro ingeniero a un operador dependiente de una pantalla.

> 📌 **La Regla de Oro del Repositorio:** Usá la IA como un acelerador de comprensión (para consultar conceptos, pedir pseudocódigo o entender por qué falla un error), **NUNCA para saltearte el proceso de pensar**.

En resumen: **La IA no hace el trabajo por vos; actúa como un tutor experto que te guía para que aprendas, apruebes y seas ingeniero, demostrando que la IA es una herramienta valiosa para ser más eficiente y no que sea prácticamente una dependencia de lo que sabés (o no).**

## 💡 ¿Qué es un archivo `.md` y por qué usamos este formato?

Un archivo `.md` (**Markdown**) es simplemente un archivo de texto plano formateado con símbolos sencillos (como `#` para títulos o `*` para viñetas).

**Usamos este formato porque:**
* **Las IAs lo entienden nativamente:** La estructura en Markdown ayuda a la IA a distinguir con alta precisión cuáles son las reglas, los límites y las directivas del tutor.
* **Sin programas especiales ni licencias:** Podés abrirlo y leerlo desde cualquier navegador, bloc de notas, celular o editor de código.
* **Fácil de copiar y reutilizar:** Solo tenés que copiar todo el texto plano e ingresarlo en las instrucciones del sistema de tu IA preferida.
* **Control transparente en GitHub:** Permite que cualquier estudiante o docente pueda proponer mejoras, corregir errores y seguir el historial de cambios de forma abierta.

## 🚀 Guía de Importación Paso a Paso por Plataforma

Copiá el contenido completo del archivo `.md` de tu materia (ubicado en `materias/<carrera>/nivel_<N>/`) y configuralo en tu herramienta de IA preferida:

### 🟢 ChatGPT (OpenAI)
* **Opción A (Custom GPT - Recomendado):** 
  1. Ir a **Explore GPTs** -> **Create**.
  2. En la pestaña **Configure**, asigná el nombre de la materia (ej. *Tutor Informática II - UTN FRBA*).
  3. Pegá todo el contenido del `.md` en el campo **Instructions**.
  4. Desactivá la opción de búsqueda Web si querés que responda estrictamente sobre la teoría analítica de la materia.
* **Opción B (Custom Instructions):** Ir a **Settings** -> **Personalization** -> **Custom Instructions** y pegá el contenido en *"How would you like ChatGPT to respond?"*.

### 🟣 Claude (Anthropic)
* **Claude Projects (Recomendado):**
  1. Entrá a **Projects** -> **Create Project** (ej. *Materia ASyS UTN*).
  2. En el panel derecho, abrí **Set Project Instructions**.
  3. Pegá el texto completo del `.md` y guardá los cambios.
  4. Podés adjuntar PDFs de guías de trabajos prácticos en la sección **Project Knowledge**.

### 🔵 Google Gemini
* **Gemini Gems (Recomendado):**
  1. En el menú lateral de Gemini, seleccioná **Gems Manager** -> **New Gem**.
  2. Asigná el nombre de la materia y pegá el contenido del `.md` en el recuadro **Instructions**.
  3. Guardá la Gema para tener un tutor dedicado accesible con un solo clic.

### 🌐 Perplexity AI
* **Perplexity Collections:**
  1. Creá una nueva **Collection** (ej. *UTN - Informática II*).
  2. En **AI Prompt**, pegá el texto del `.md`.
  3. Cada búsqueda o consulta realizada dentro de esa colección respetará las directivas socráticas.

### ⚡ Antigravity IDE / VS Code / Cursor
* **Reglas de Agente / System Instructions:**
  1. Copiá el archivo `.md` dentro de la carpeta `.gemini/`, `.agent/` o `.cursorrules` de tu espacio de trabajo.
  2. El IDE cargará automáticamente las 7 secciones como instrucciones del sistema para pair-programming.

## Estructura del Repositorio

```text
.
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── bugfix.yml           # Plantilla para reportar correcciones en prompts existentes.
│   │   ├── mejora.yml           # Plantilla para sugerir optimizaciones o ajustes pedagógicos.
│   │   ├── mito.yml             # Plantilla para aportar mitos y errores frecuentes de la cursada (Sección 3).
│   │   └── propuesta.yml        # Plantilla para proponer la incorporación de una nueva materia.
│   ├── workflows/
│   │   ├── llm_evaluator.yml    # Pipeline de CI para evaluación automatizada de prompts.
│   │   └── validar_estructura.yml # Pipeline de CI que valida el cumplimiento de las 7 secciones obligatorias.
│   └── PULL_REQUEST_TEMPLATE.md # Plantilla guía con checklist para contribuciones vía PR.
├── materias/
│   ├── electronica/             # Carrera / Especialidad: Ingeniería Electrónica
│   │   ├── nivel_1/             # (Proyectado - ej. informatica_1.md)
│   │   └── nivel_2/             # 2º Nivel (ej. informatica_2.md, analisis_de_senales_y_sistemas.md)
│   ├── sistemas/                # (Proyectado - ej. sintaxis_y_lenguajes.md)
│   └── quimica/                 # (Proyectado - ej. quimica_general.md)
├── AUTHORS.md                  # Registro de autores y colaboradores por materia.
├── CODEOWNERS                   # Definición de responsables y *maintainers* por módulo.
├── CONTRIBUTING.md              # Estándares de contribución, regla de las 7 secciones.
├── LICENSE                      # Licencia del proyecto (CC BY-NC-ND 4.0).
└── README.md                    # Documentación general e instrucciones de uso del proyecto.
```

## 💬 Consultas, Preguntas e Ideas: GitHub Discussions

Si tenés alguna duda general sobre el proyecto, preguntas sobre cómo usar los prompts o querés proponer una idea previa antes de abrir un Issue que quizás no prospere, **utilizá el espacio de [GitHub Discussions](../../discussions)**. 

Canalizar las consultas informales e inquietudes por Discussions nos ayuda a debatir abiertamente y mantener la sección de **Issues** reservada exclusivamente para tareas concretas y aprobadas.

## 🤝 ¿Querés Contribuir? ¡Leé la Guía de Contribución!

> [!IMPORTANT]
> **Antes de abrir un Issue o Pull Request, es obligatorio leer la [Guía de Contribución (CONTRIBUTING.md)](CONTRIBUTING.md).**  
> Los aportes que no sigan las pautas o violen la política de derechos de autor no podrán ser integrados y fallarán los tests automáticos en el CI.

**¿Qué vas a encontrar en [CONTRIBUTING.md](CONTRIBUTING.md)?**
* 📐 **La Regla de Oro (7 Secciones Obligatorias)**: La estructura exacta que debe cumplir todo prompt para asegurar el rol de tutor socrático.
* ⚖️ **Política de Fair Use y Derechos de Autor**: Reglas estrictas para no incluir material protegido (libros, parciales textuales, diapositivas o PDFs).
* 🤖 **Validación Automatizada (CI)**: Explicación de cómo GitHub Actions evalúa automáticamente la estructura y calidad pedagógica del prompt.
* 💡 **Guía de Meta-Prompting para Principiantes**: Cómo usar a la misma IA para ayudarte a redactar, probar y calibrar tu borrador.
* 🌿 **Flujo de Git (*GitHub Flow*)**: Convención de ramas (`feature/issue-...`) y flujo de integración vía PR a `main`.

## Licencia

Este proyecto está bajo la licencia **[Creative Commons Atribución-NoComercial-SinDerivadas 4.0 Internacional (CC BY-NC-ND 4.0)](LICENSE)**.

* **Atribución (BY)**: Debes dar crédito apropiado al proyecto original.
* **No Comercial (NC)**: Queda estrictamente prohibida la comercialización, venta o uso con fines de lucro directos o indirectos de este material.
* **Sin Derivadas (ND)**: Queda prohibida la redistribución pública de versiones modificadas o alteradas de estos archivos sin autorización expresa de los *maintainers* del repositorio.


