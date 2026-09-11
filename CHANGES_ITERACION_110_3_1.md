# PhysioSentinel Gait · V110.3.1

## Corrección de regresión frontal/posterior

V110.3.1 corrige una regresión de integración detectada en V110.3.0 cuando se analiza una única cámara frontal/posterior.

- V104/V107 ahora construye de forma autónoma la secuencia monocular V83 cuando el análisis es Nivel 1 frontal/posterior. Ya no intenta exclusivamente la fusión V60 frontal+lateral.
- La pestaña **11 · Atlas anatómico 3D** vuelve a ejecutar el panel V83/V89 antes de SKEL, por lo que reaparecen el visor 3D estimado/no métrico, los vídeos 3D simplificados, la previsualización anatómica y la opción de generar/descargar vídeo anatómico.
- La secuencia publicada por V83/V89 se entrega a V104/V107 y después a **SKEL Direct Anatomical Pose Mapping**. Se elimina el falso estado «No hay secuencia V104/V107» cuando sí existe un registro frontal/posterior válido.
- La pestaña **9 · Ciclo + Cinemática angular** añade un bloque explícito de **Cinemática 2D frontal/posterior** para Nivel 1. Publica resumen numérico y gráficas de pelvis/tronco/COM, rodilla y pie-retropié sin exigir V48 biplanar ni vídeo lateral.
- Esta corrección no transforma las variables 2D en cinemática 3D cuantitativa y no modifica las métricas clínicas previamente calculadas.

## Backblaze B2 / SKEL

Se conserva sin cambios el Auto-Loader privado de Backblaze B2 de V110.3.0: descarga temporal a `/tmp`, verificación del ZIP, extracción de `skel_male.pkl`/`skel_female.pkl` y fallback manual si B2 no está disponible.
