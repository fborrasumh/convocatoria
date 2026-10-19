# ConvocatorIA

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.22162071.svg)](https://doi.org/10.5281/zenodo.22162071)

**Aplicación:** https://fborrasumh.github.io/convocatoria/

Analiza los **exámenes de otros años** de una asignatura y el temario oficial para que el estudiantado universitario organice su estudio **con datos, no con rumores**. Dice qué temas han pesado más, con qué seguridad lo sabe y cuánto acertó cuando se puso a prueba. Después ofrece un simulacro y un plan hasta el día del examen, sin dejar ningún tema a cero. Aplicación de un solo fichero (`index.html`), sin servidor.

**Idiomas:** español (por defecto), inglés y portugués, con selector en la barra superior (o `?lang=en` / `?lang=pt` en la URL). La IA responde en el idioma elegido; el simulacro y el plan pueden pedirse además en otra variante (español latinoamericano, portugués de Brasil, catalán, valenciano, gallego, euskera…).

## Novedades de la versión 3.0

- Rediseño con la línea **Forja** de *Herramientas IA para la academia*: portada con autoría y ORCID, «Dónde va cada cosa», ayuda y navegación unificadas.
- **Tres idiomas** completos (interfaz, ejemplo, informes, plan y calendario).
- **Tres proveedores de IA** con la clave de cada persona: OpenAI, Google Gemini y Anthropic Claude, con desplegable de los modelos disponibles en la clave.
- **La IA propone, el código comprueba**: cada vez que la IA dice que un tema cayó en un examen aporta un fragmento literal de la pregunta, y el código lo busca en ese examen (si no aparece, la celda se marca con ⚠). El código cuenta además las preguntas numeradas de cada examen y avisa si el recuento de la IA no cuadra, decide qué filas quedan **fuera del temario**, añade como fila los temas del temario que nunca han salido, reescala los puntos del simulacro a la nota máxima y solo acepta prerrequisitos entre temas que existen.
- **Aviso previo al envío** con una muestra de lo que sale, y enmascarado de correos, teléfonos y documentos de identidad.
- Exportación del informe y del plan a **Word**, CSV, Markdown y `.ics`; exportación e importación del análisis en JSON. Los análisis de la versión 2 guardados en el navegador se recuperan solos.

## Cómo funciona

1. **Qué ha caído**: matriz tema × examen, con frecuencia, puntos medios, tendencia y exámenes sin salir, calculada en el navegador a partir del etiquetado de la IA, con la pregunta que lo prueba.
2. **Qué es probable**: P(aparece) sobre una base de Laplace `(veces + 1) / (exámenes + 2)`, ajustada por tendencia, peso y rotación, con una línea de justificación por tema.
3. **Cuánto fiarse**: validación ciega con 3 exámenes o más. Se oculta el último examen y se compara el acierto con la simple frecuencia (puntuación de habilidad de Brier). El «top» de temas es el 30 % del temario.
4. **Simulacro**: con el formato real, cronómetro, corrección automática de las preguntas tipo test y autoevaluación de las abiertas. El tema es predecible; la pregunta concreta, no.
5. **Plan**: calendario hasta el examen, sin temas por debajo de media hora, con los prerrequisitos antes, repasos espaciados a los 2 y 6 días, un simulacro completo y un repaso final. La dificultad de cada tema la ajusta el estudiante.

El botón **Ver un ejemplo completo** recorre todo el flujo con exámenes ficticios de Bioestadística, en el idioma elegido, sin clave y sin usar la IA.

## Cómo se usa la IA

Con la propia clave de OpenAI, Google Gemini o Anthropic Claude (botón «IA»). La clave se guarda solo en el navegador (la de OpenAI se comparte con el resto del catálogo como `ia_openai_key`). Un análisis completo hace unas 7 llamadas y cuesta unos céntimos con un modelo económico.

## Privacidad

Los exámenes se leen en el navegador (pdf.js y mammoth.js se cargan desde cdnjs solo cuando hacen falta) y los análisis se guardan en IndexedDB de ese navegador. Al analizar, el temario, la tabla del profesorado (si existe) y el texto de los exámenes se envían al proveedor de IA elegido, con correos, teléfonos y documentos de identidad enmascarados; antes del primer envío de la sesión se muestra una muestra de lo que sale. La política de seguridad de contenidos (CSP) solo permite conexiones con los tres proveedores.

## Límites

- Con menos de 3 exámenes no hay validación ciega: las probabilidades son un orden de prioridad, no una medida.
- Los PDF escaneados necesitan OCR antes; los `.doc` antiguos y los RTF se convierten de forma aproximada.
- La IA puede etiquetar mal una pregunta: las asignaciones sin la pregunta localizada se marcan con ⚠, pero una cita encontrada no garantiza que el tema asignado sea el correcto.
- El recuento de preguntas del código solo funciona con preguntas numeradas al principio de línea.
- El simulacro es plausible, no el examen real. Esta herramienta prioriza el estudio; no lo sustituye.
- Probada con IA simulada (OpenAI, Gemini y Claude) en Chromium de escritorio y móvil; no con claves reales en esta versión.

## Motor compartido

[AntiConvocatorIA](https://fborrasumh.github.io/anticonvocatoria/) usa el mismo motor para que el profesorado mida cuánto se puede predecir su examen.

## Autoría

Fernando Borrás Rocher (Universidad Miguel Hernández de Elche) · ORCID [0000-0002-5519-4573](https://orcid.org/0000-0002-5519-4573)

## Cómo citar

Borrás Rocher, F. (2026). *ConvocatorIA* (versión 3.0.0) [Software]. Universidad Miguel Hernández de Elche. https://doi.org/10.5281/zenodo.22162071

El DOI anterior es el de concepto: apunta siempre a la última versión. El DOI de cada versión concreta está en [Zenodo](https://doi.org/10.5281/zenodo.22162071). GitHub ofrece la cita en formato APA y BibTeX con el botón *Cite this repository*, a partir de `CITATION.cff`.

Forma parte del catálogo [Herramientas IA para la academia](https://fborrasumh.github.io/ia/).

## Licencia

MIT © 2026 Fernando Borrás Rocher · Universidad Miguel Hernández de Elche. Véase [LICENSE](LICENSE).
