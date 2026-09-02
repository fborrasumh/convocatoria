# ConvocatorIA

Analista de patrones de examen. Aplicación de un solo fichero (`index.html`), sin servidor ni dependencias de build.

Los exámenes se suben como ficheros —**PDF, Word (.docx/.doc), RTF o texto**—, arrastrándolos o seleccionándolos del disco: cada fichero se da de alta como una convocatoria, con la etiqueta deducida del nombre (`Bioestadistica_2024_junio.pdf` → `2024_junio`), y el texto extraído queda editable. La extracción es local (pdf.js y mammoth.js, cargados solo cuando hacen falta).

A partir de ahí, y del temario oficial:

1. **Matriz de convocatorias** — temas × convocatorias, con frecuencia, peso medio en puntos, tendencia y convocatorias transcurridas desde la última aparición (todo calculado en el navegador, no estimado por el modelo).
2. **Probabilidad calibrada** — P(aparece en el próximo examen) sobre una base de Laplace `(aciertos+1)/(convocatorias+2)`, ajustada por tendencia, peso en la guía docente y efecto rotación, con una línea de justificación por tema.
3. **Validación ciega** — repite los pasos 1 y 2 ocultando la convocatoria más reciente y mide el acierto contra ella: % de temas reales en el top-5, % de preguntas cubiertas por el top-10 y **Brier score**. Requiere 3 convocatorias como mínimo.
4. **Examen simulado** — con el formato real; cada pregunta lleva tema, probabilidad, verbo cognitivo y motivo de inclusión.
5. **Plan de estudio** — ordenado por puntos esperados por hora (`P × peso ÷ dificultad`), con la dificultad ajustable por el estudiante y marcado de los temas de baja probabilidad que son prerrequisito de otros.

Termina declarando los tres temas donde la predicción es más frágil.

## Publicar en GitHub Pages

1. Crea el repositorio `convocatoria` y sube `index.html` y `README.md` a la rama `main`.
2. Settings → Pages → Source: `main` / `/ (root)`.
3. Queda en `https://<usuario>.github.io/convocatoria/`.

## Privacidad

La clave de la API se guarda en `localStorage` (`ia_openai_key`) y solo viaja a la API del modelo. Los exámenes y los análisis se guardan en IndexedDB del propio navegador. Los ficheros que subes se leen íntegramente en el navegador: no se suben a ningún servidor.

## Licencia

MIT.
