# PhysioSentinel Gait V110.3.2

## Restauración robusta del pipeline frontal/posterior
- Añade un snapshot numérico HALPE26 persistente del segmento frontal usado en el análisis antes de eliminar los archivos temporales.
- V83/V104/V107 ya no dependen de `analysis_df` después de la limpieza de privacidad.
- El atlas 3D, el vídeo simplificado y SKEL reutilizan el mismo segmento frontal y FPS.
- Añade indicador visible de puente HALPE26 activo en la pestaña 11.
- La cinemática frontal 2D puede reutilizar el mismo snapshot persistente.

## SKEL depth-safe anatomical mapping
- En reconstrucción monocular, Z se considera profundidad inferida y pesa 0.18 frente a X/Y durante el retargeting.
- Los límites de escápula vuelven a incluir la posición neutra para evitar deformación forzada.
- Se añade una reconciliación anatómica global corta y fuertemente regularizada después del ajuste por cadenas.
- La auditoría no marca como fallo la extensión neutra válida de rodilla/codo simplemente por estar en 0 rad.
- Se mantienen semántica q oficial, puerta anatómica frame 1 y Backblaze B2 privado.
