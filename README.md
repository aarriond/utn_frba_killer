# Antes de nada, ¿por qué el nombre?
No tengo una pregunta completa, pero se entiende: en algún momento pensás en que te querés recibir ya...

# Prompts de Ingeniería UTN FRBA
Este repositorio es una iniciativa *open-source* para recopilar y estandarizar **System Prompts (contextos de IA)** para las distintas carreras de Ingeniería en la UTN FRBA (Electrónica, Sistemas, Química, Mecánica, Industrial, Civil, Eléctrica, etc.).

## ¿Por qué existe este proyecto?

El propósito fundamental de este repositorio es **guiar pedagógicamente al estudiante para evitar que delegue su aprendizaje en la inteligencia artificial**. 

Sin un perfil calibrado, las IAs de propósito general (como ChatGPT, Claude, Gemini o Antigravity IDE) actúan como "generadores de soluciones automáticas" que entregan el código o el ejercicio resuelto de un solo tiro. Esto genera una **falsa sensación de dominio**, perjudicando gravemente al alumno al momento de rendir sus exámenes parciales escritos (que se rinden con lápiz y papel) o defender oralmente sus proyectos en coloquios e instancias evaluativas.

Al inyectar estos archivos `.md`, transformamos a la IA en un **Tutor Socrático Exigente** que:
1. **Orienta mediante preguntas clave y pseudocódigo** en lugar de entregar la solución terminada.
2. **Exige al alumno razonar el 'por qué'** de cada algoritmo, cálculo o decisión de diseño.
3. **Mantiene el rigor universitario y los convenios de cada carrera** en la UTN FRBA:

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

## Guía de Importación por Plataforma
Copiá el contenido del archivo `.md` de tu materia y pegalo en tu IA preferida:
* **Gemini:** Creá una nueva Gema (Gem) y pegá el contenido en las "Instrucciones".
* **ChatGPT:** Creá un Custom GPT y pegalo en "Instructions", o usá Custom Instructions.
* **Claude:** Creá un nuevo Project y pegalo en la sección de Custom Instructions.
* **Perplexity:** Armá una nueva Collection y pegalo en AI Prompt.
* **Grok:** Pegalo íntegro como el primer mensaje del chat.

## Estructura del Repositorio

```text
.
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── bugfix.yml           # Plantilla para reportar correcciones en prompts existentes.
│   │   ├── mejora.yml           # Plantilla para sugerir optimizaciones o ajustes pedagógicos.
│   │   └── propuesta.yml        # Plantilla para proponer la incorporación de una nueva materia.
│   ├── workflows/
│   │   ├── llm_evaluator.yml    # Pipeline de CI para evaluación automatizada de prompts.
│   │   └── validar_estructura.yml # Pipeline de CI que valida el cumplimiento de las 6 secciones obligatorias.
│   └── PULL_REQUEST_TEMPLATE.md # Plantilla guía con checklist para contribuciones vía PR.
├── materias/
│   ├── electronica/             # Carrera / Especialidad: Ingeniería Electrónica
│   │   ├── nivel_1/             # (Proyectado - ej. informatica_1.md)
│   │   └── nivel_2/             # 2º Nivel (ej. informatica_2.md - C++ embebido, NXP LPC845)
│   ├── sistemas/                # (Proyectado - ej. sintaxis_y_lenguajes.md)
│   └── quimica/                 # (Proyectado - ej. quimica_general.md)
├── AUTHORS.md                  # Registro de autores y colaboradores por materia.
├── CODEOWNERS                   # Definición de responsables y *maintainers* por módulo.
├── CONTRIBUTING.md              # Estándares de contribución, regla de las 6 secciones.
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
* 📐 **La Regla de Oro (6 Secciones Obligatorias)**: La estructura exacta que debe cumplir todo prompt para asegurar el rol de tutor socrático.
* ⚖️ **Política de Fair Use y Derechos de Autor**: Reglas estrictas para no incluir material protegido (libros, parciales textuales, diapositivas o PDFs).
* 🤖 **Validación Automatizada (CI)**: Explicación de cómo GitHub Actions evalúa automáticamente la estructura y calidad pedagógica del prompt.
* 💡 **Guía de Meta-Prompting para Principiantes**: Cómo usar a la misma IA para ayudarte a redactar, probar y calibrar tu borrador.
* 🌿 **Flujo de Git (*GitHub Flow*)**: Convención de ramas (`feature/issue-...`) y flujo de integración vía PR a `main`.

## Licencia

Este proyecto está bajo la licencia **[Creative Commons Atribución-NoComercial-SinDerivadas 4.0 Internacional (CC BY-NC-ND 4.0)](LICENSE)**.

* **Atribución (BY)**: Debes dar crédito apropiado al proyecto original.
* **No Comercial (NC)**: Queda estrictamente prohibida la comercialización, venta o uso con fines de lucro directos o indirectos de este material.
* **Sin Derivadas (ND)**: Queda prohibida la redistribución pública de versiones modificadas o alteradas de estos archivos sin autorización expresa de los *maintainers* del repositorio.


