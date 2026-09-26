# ConvocatorIA

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.22162071.svg)](https://doi.org/10.5281/zenodo.22162071)

**Aplicación:** https://fborrasumh.github.io/convocatoria/

Analiza los **exámenes de otros años** de una asignatura y el temario oficial para que el estudiantado universitario organice su estudio **con datos, no con rumores**. Dice qué temas han pesado más, con qué seguridad lo sabe y cuánto acertó cuando se puso a prueba. Después ofrece un simulacro y un plan hasta el día del examen, sin dejar ningún tema a cero. Aplicación de un solo fichero (`index.html`), sin servidor.

## Novedades de la versión 2.0

- Interfaz guiada con el estilo de Forja, pensada para estudiantes universitarios iberoamericanos, y un **ejemplo completo que funciona sin clave**.
- **«Cuánto fiarte»**: la validación ciega va primero. Oculta el último examen y compara el acierto con la simple frecuencia (puntuación de habilidad de Brier), y dice en lenguaje llano si el patrón es real, débil o inexistente. El «top» de temas es el 30 % del temario, en vez de un top-5 fijo.
- **Simulacro interactivo** con cronómetro, corrección automática de las preguntas tipo test, soluciones y autoevaluación de las preguntas abiertas.
- **Plan de estudio con calendario**, que sustituye al orden por «puntos por hora» porque invitaba a abandonar temas:
  - ningún tema baja de media hora;
  - los prerrequisitos van antes que los temas que dependen de ellos;
  - hay repasos espaciados, un simulacro completo y un repaso final;
  - la dificultad de cada tema la ajusta el estudiante;
  - se exporta a `.ics` y a Markdown.
- **Tabla publicada por el profesorado**: si existe (por ejemplo, de AntiConvocatorIA), manda sobre el historial.
- Escalas de nota de ocho países e idioma del simulacro y del plan (variantes del español y del portugués, entre otras).

## Cómo funciona

1. **Qué ha caído**: matriz tema × examen, con frecuencia, puntos medios, tendencia y exámenes sin salir, calculada en el navegador.
2. **Qué es probable**: P(aparece) sobre una base de Laplace `(veces + 1) / (exámenes + 2)`, ajustada por tendencia, peso y rotación, con una línea de justificación por tema.
3. **Cuánto fiarse**: validación ciega con 3 exámenes o más.
4. **Simulacro**: con el formato real. El tema es predecible; la pregunta concreta, no.
5. **Plan**: calendario hasta el examen.

Esta herramienta prioriza el estudio; no lo sustituye.

## Motor compartido

[AntiConvocatorIA](https://fborrasumh.github.io/anticonvocatoria/) usa el mismo motor para que el profesorado mida cuánto se puede predecir su examen.

## Privacidad

Los exámenes se leen en el navegador (pdf.js y mammoth.js, que se cargan solo cuando hacen falta). La clave se guarda en `localStorage` (`ia_openai_key`) y solo viaja a `api.openai.com`. Los análisis se guardan en IndexedDB del navegador.

## Cómo citar

Borrás Rocher, F. (2026). *ConvocatorIA* (versión 2.0.0) [Software]. Universidad Miguel Hernández de Elche. https://doi.org/10.5281/zenodo.22162071

El DOI anterior es el de concepto: apunta siempre a la última versión. El DOI de cada versión concreta está en [Zenodo](https://doi.org/10.5281/zenodo.22162071). GitHub ofrece la cita en formato APA y BibTeX con el botón *Cite this repository*, a partir de `CITATION.cff`.

Forma parte del catálogo [Herramientas IA para la academia](https://fborrasumh.github.io/ia/).

## Licencia

MIT © 2026 Fernando Borrás Rocher · Universidad Miguel Hernández de Elche.
