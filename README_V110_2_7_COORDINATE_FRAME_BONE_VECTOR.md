# PhysioSentinel Gait V110.2.7

## Coordinate Frame Registration + Bone-Vector Retargeting

Esta iteración ataca la divergencia visual observada entre el XYZ simplificado V104/V107 y SKEL. Antes de optimizar pose, construye un marco corporal a partir de pelvis, eje de caderas y eje pelvis-cuello para registrar explícitamente V104/V107 con SKEL.

Durante el fit no sólo se minimiza la distancia entre joints: también se comparan las direcciones de los segmentos observables (muslo, pierna, tronco, brazo, antebrazo, pelvis y hombros). Por ello un joint no puede reducir el RMSE con la misma facilidad dejando el hueso apuntando en una dirección anatómicamente errónea.

La calibración empírica q0…q45 permanece automática para reducir el espacio de DOF. El botón de auditoría avanzada es opcional.

### Validación esperada
1. Revisar error angular óseo medio y máximo del frame semilla.
2. Procesar 1→75.
3. Generar Mesh Walker.
4. Comparar el mismo frame en XYZ simplificado, SKEL joints y SKEL mesh.

La prioridad de V110.2.7 es la coherencia anatómica y direccional, no minimizar el RMSE a cualquier coste.
