# V110.2.8 · Per-Chain Local Jacobian + Bone-Vector IK + SKEL Private Auto-Loader

## Retargeting anatómico
- V104/V107 permanece congelado como fuente cinemática.
- Se conserva el registro explícito del marco corporal pelvis–caderas–cuello.
- El Jacobiano empírico q0…q45 deja de utilizarse como un bloque global: cada DOF observable se asigna de forma exclusiva a una cadena anatómica.
- Cadenas: axial, pierna derecha, pierna izquierda, brazo derecho y brazo izquierdo.
- Resolución proximal→distal con optimización local por cadena.
- Cada cadena combina error XYZ y dirección de sus vectores óseos.
- Se añade penalización `off-chain`: un DOF que mejora una cadena desplazando articulaciones remotas queda penalizado.
- Las cadenas periféricas no pueden corregir su error girando o trasladando todo el cuerpo.
- Betas permanecen neutras; DOF no seleccionados permanecen exactamente en cero.
- Side-by-Side XYZ simplificado | SKEL joints | SKEL mesh se mantiene como puerta de validación.

## SKEL Private Auto-Loader
- Carga automática opcional desde Cloudflare R2 privado.
- El ZIP se descarga exclusivamente a `/tmp` del runtime Streamlit.
- Supabase no almacena el modelo SKEL.
- El repositorio GitHub no contiene los `.pkl` privados.
- Se admite verificación SHA-256 opcional.
- Si R2 no está configurado o falla, se conserva el uploader manual como fallback.

## Compatibilidad
- NumPy 2.x, Pose2Sim y OpenSim permanecen intactos.
- SKEL sigue instalándose CPU aislado con `--no-deps` y commit fijado `c32cf16581295bff19399379efe5b776d707cd95`.
- No se instala `moderngl-window`.
