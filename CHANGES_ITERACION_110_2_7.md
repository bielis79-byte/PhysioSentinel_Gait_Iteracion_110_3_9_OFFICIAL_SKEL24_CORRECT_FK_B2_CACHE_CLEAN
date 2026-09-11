# V110.2.7 · Coordinate Frame Registration + Bone-Vector Retargeting

- Registra explícitamente el marco corporal V104/V107↔SKEL usando pelvis, caderas y cuello antes del fit articular.
- Inicializa la rotación global desde bases corporales ortonormales, en lugar de partir de rotación cero.
- Añade pérdidas por dirección de 16 vectores óseos observables y una penalización específica de ejes pelvis/tronco.
- Mantiene el Jacobiano q→joints sólo como reducción del espacio de búsqueda; no se usa como sustituto de la anatomía.
- Conserva los DOF no seleccionados exactamente neutros y la continuidad temporal frame a frame.
- Añade auditoría de error angular óseo medio/máximo por frame y lo incorpora al control anatómico.
- Mantiene Side-by-Side: XYZ simplificado V104/V107 | joints SKEL | mesh SKEL.
- La auditoría manual q0…q45 sigue siendo opcional; la calibración mínima necesaria se ejecuta automáticamente.
- NumPy 2.x, OpenSim y Pose2Sim permanecen intactos.
