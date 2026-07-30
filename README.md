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

## Uso Responsable y Derechos de Autor (Fair Use)
Estos perfiles obligan a la IA a actuar como un **tutor socrático**: te guía en la arquitectura, pero el código fino o el cálculo lo pensás vos. 
**Importante:** Está estrictamente prohibido incluir material con derechos de autor (enunciados textuales de parciales, guías oficiales, PDFs de la cátedra). Todo el contenido debe ser reformulado.
