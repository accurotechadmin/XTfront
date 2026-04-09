# XtraType CRE8 Bridge OpenAPI (Split)

This directory contains a repo-friendly split of the monolithic OpenAPI spec.

## Layout

- `openapi.yaml` — root OpenAPI 3.1 document
- `paths/` — one file per API path (130 files)
- `components/schemas.yaml` — reusable schemas (180 schemas)
- `components/securitySchemes.yaml` — security schemes

## Notes

- Path files use relative `$ref`s into `../components/schemas.yaml`.
- The root document references each path file individually.
- The split is intended for maintainability in source control.
