# PhysioSentinel Gait V110.2.8

Esta iteración sustituye el ajuste global de DOF por un retargeting local por cadenas basado en el Jacobiano empírico real de SKEL.

Orden de resolución:
1. Registro global pelvis–caderas–cuello.
2. Cadena axial.
3. Pierna derecha.
4. Pierna izquierda.
5. Brazo derecho.
6. Brazo izquierdo.

Cada DOF q se asigna a una sola cadena según efecto local, independencia y contaminación `off-chain`. Durante el IK, las cadenas periféricas sólo pueden modificar sus propios q. El objetivo es impedir que una reducción numérica del RMSE se consiga con una postura anatómicamente incorrecta.

La validación decisiva sigue siendo Side-by-Side. No debe darse por resuelto el retargeting hasta que los joints SKEL sigan visualmente los vectores óseos del XYZ simplificado.
