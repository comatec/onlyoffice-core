# Rebuild drawingfile.wasm (Recognize / ScanPage)

Recognize in the PDF editor uses **browser WASM**, not `libPdfFile.so`:

- Source: `DesktopEditor/doctrenderer/drawingfile.h` + `DocxRenderer/**`
- Build config: `DesktopEditor/graphics/pro/js/drawingfile.json`
- Official deploy: `DesktopEditor/graphics/pro/js/deploy.py`
- Target in Document Server:
  `/var/www/onlyoffice/documentserver/sdkjs/pdf/src/engine/drawingfile.{js,wasm}`

## Layout expected by ONLYOFFICE scripts

```
parent/
  build_tools/          # https://github.com/ONLYOFFICE/build_tools
  core/                 # this repo (onlyoffice-core)
```

## Steps (Linux / Docker builder)

1. Fetch 3dParty deps used by WASM (openssl, icu, …):
   `cd Common/3dParty && bash make.sh` (or per-folder `fetch.sh`).
2. Clone `build_tools` next to `core`.
3. From `DesktopEditor/graphics/pro/js`:
   `python3 deploy.py`
4. Copy `deploy/drawingfile.js` + `deploy/drawingfile.wasm` into the
   Document Server image path above (and rebuild `onlyoffice-pdf-hotfix:9.2.1`).

First WASM build downloads emsdk and compiles a large tree — expect a long run.

`Dockerfile.documentserver` today only swaps `libPdfFile.so` (WriteNew + image CRC).
Extend it with a WASM stage once the 3dParty fetch is reliable in CI.
