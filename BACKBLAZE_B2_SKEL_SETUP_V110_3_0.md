# Backblaze B2 · SKEL privado · V110.3.0

El bucket debe permanecer privado. La Application Key debe ser de solo lectura y restringida al bucket del modelo.

## Streamlit Secrets

```toml
B2_KEY_ID = "applicationKeyId"
B2_APPLICATION_KEY = "applicationKey"
B2_BUCKET = "physiosentinel-skel-assets"
B2_FILE = "skel_models_v1.1(1).zip"
```

Opcionalmente puede añadirse `SKEL_ZIP_SHA256` para fijar una huella local adicional.

La aplicación autentica contra Backblaze B2 Native API, descarga el objeto a `/tmp`, valida la huella SHA-1 entregada por B2, ejecuta `ZipFile.testzip()` y exige que existan `skel_male.pkl` y `skel_female.pkl` antes de inicializar SKEL.
