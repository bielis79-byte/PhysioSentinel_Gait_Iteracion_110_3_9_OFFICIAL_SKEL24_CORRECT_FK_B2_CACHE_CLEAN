# PhysioSentinel Gait V110.3.9

## Official SKEL24 Joint Map + Correct FK Retargeting

Esta versión corrige la indexación entre el tensor `forward().joints` de SKEL y sus nombres anatómicos. El forward real usa 24 joints cinemáticos; no se utiliza `model.joints_name` (22 nombres) para indexar ese tensor.

### Flujo
HALPE26/V104 → Unified Coordinate Frame → Official SKEL24 Joint Map → test de lateralidad → FK Ground Truth ±Δ → Dependency Graph → Monotonic Hierarchical IK → CMA-ES residual → auditoría anatómica → propagación temporal.

### Puerta de seguridad nueva
Antes de optimizar, se comprueba empíricamente que:
- hip_flexion_r se comporte como cadena derecha;
- hip_flexion_l como cadena izquierda;
- shoulder_r_x y elbow_flexion_r como brazo derecho;
- shoulder_l_x y elbow_flexion_l como brazo izquierdo.

Si falla, el pipeline se detiene y no procesa 75 frames.

### Cache SKEL / Backblaze
Se conserva el cache runtime introducido en V110.3.8. Si el ZIP y PKL válidos ya existen en `/tmp/physiosentinel_skel_b2_cache_v1_1`, se reutilizan sin volver a descargar ~174 MB desde Backblaze. Una instancia nueva de Streamlit puede requerir una descarga inicial.
