# Prompts de Electrónica UTN FRBA
Este repositorio es una iniciativa *open-source* para recopilar y estandarizar **System Prompts (contextos de IA)** para las materias de la carrera de Ingeniería Electrónica en la UTN FRBA.

## ¿Por qué existe este proyecto?
Sin el contexto adecuado, las IAs (como ChatGPT, Claude o Antigravity IDE) tienden a:
* Resolver problemas en C puro cuando se requiere C++.
* Asumir el uso de librerías de alto nivel (como la STL) en sistemas embebidos donde no aplican.
* Explicar conceptos con convenciones extranjeras (ej. notación de fasores).
* Dar respuestas "atajo" que no preparan para un parcial escrito o coloquio oral.

Al inyectar estos archivos `.md`, cargás un "perfil de tutor experto" calibrado exactamente para el programa de nuestra facultad.

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
│   │   ├── nivel_1/             # 1º Nivel (ej. informatica_1.md)
│   │   └── nivel_2/             # 2º Nivel (ej. informatica_2.md - C++ embebido, NXP LPC845)
│   ├── sistemas/                # Carrera / Especialidad: Ingeniería en Sistemas de Información
│   │   └── nivel_2/             # 2º Nivel (ej. sintaxis_y_lenguajes.md)
│   └── quimica/                 # Carrera / Especialidad: Ingeniería Química
│       └── nivel_1/             # 1º Nivel (ej. quimica_general.md)
├── CODEOWNERS                   # Definición de responsables y mantenedores por módulo.
├── CONTRIBUTING.md              # Estándares de contribución, regla de las 6 secciones y política de Fair Use.
├── LICENSE                      # Licencia del proyecto (CC BY-NC-ND 4.0).
└── README.md                    # Documentación general e instrucciones de uso del proyecto.
```

## Uso Responsable y Derechos de Autor (Fair Use)
Estos perfiles obligan a la IA a actuar como un **tutor socrático**: te guía en la arquitectura, pero el código fino o el cálculo lo pensás vos. 
**Importante:** Está estrictamente prohibido incluir material con derechos de autor (enunciados textuales de parciales, guías oficiales, PDFs de la cátedra). Todo el contenido debe ser reformulado. Como verán arriba, va a haber tests automáticos así que la IA va a poder darse cuenta del contenido :)

## Licencia

Este proyecto está bajo la licencia **[Creative Commons Atribución-NoComercial-SinDerivadas 4.0 Internacional (CC BY-NC-ND 4.0)](LICENSE)**.

* **Atribución (BY)**: Debes dar crédito apropiado al proyecto original.
* **No Comercial (NC)**: Queda estrictamente prohibida la comercialización, venta o uso con fines de lucro directos o indirectos de este material.
* **Sin Derivadas (ND)**: Queda prohibida la redistribución pública de versiones modificadas o alteradas de estos archivos sin autorización expresa de los mantenedores del repositorio.


