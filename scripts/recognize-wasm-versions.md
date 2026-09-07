# Recognize WASM versions (sysclinicas)

Canonical copy for operators: `docs/recognize-wasm-versoes.md` in the Sysclinicas repo.

- **Current:** recognize-wasm-v18 (`ef7494da86`)
- **Next compile:** v19
- Git tag: `recognize-wasm-vN`
- Docker tag: `sysclinicas-onlyoffice:recognize-vN` (keep old tags; do not only overwrite `9.2.1-writenew`)

After each WASM deploy, increment `scripts/recognize-wasm-CURRENT.md`, append the row in both changelogs, `git tag recognize-wasm-vN`, and:

```
docker tag sysclinicas-onlyoffice:9.2.1-writenew sysclinicas-onlyoffice:recognize-vN
```

Copy `scripts/recognize-wasm-CURRENT.md` into the image at:

`/var/www/onlyoffice/documentserver/sdkjs/pdf/src/engine/recognize-wasm-version.txt`
