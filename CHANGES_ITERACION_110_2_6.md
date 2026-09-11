# Cambios V110.2.6

1. Retargeting empírico por cadenas anatómicas en vez de ranking global de sensibilidad.
2. Cuotas: axial 4, pierna D 4, pierna I 4, brazo D 3, brazo I 3 (máximo 18 DOF).
3. Score = efecto local independiente × especificidad frente al efecto fuera de cadena.
4. Exporta `chain_mapping` con q, cadena, score y efecto local/remoto.
5. Auditoría q0…q45 pasa a ser opcional; la calibración interna automática permanece.
6. Nuevas claves de sesión V110.2.6 para impedir reutilización accidental de secuencias/mallas anteriores.
7. Side-by-Side y malla se conservan para validación visual directa.
