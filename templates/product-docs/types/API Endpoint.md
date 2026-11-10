---
type: Type
title: API Endpoint
icon: file-code
description: One operation in the public API reference.
schema:
  type: object
  properties:
    method:
      type: string
      enum: [GET, POST, PUT, PATCH, DELETE]
      description: HTTP method.
    path:
      type: string
      description: 'Path in the API spec, like /v1/shipments/{id}.'
    operation_id:
      type: string
      description: operationId in the API spec.
  required: [method, path]
---

An API Endpoint page documents one operation from `api/openapi.yaml`: parameters, responses and an example.

- **Layer:** concept. Written by refinement workflows, which cite the records they read in `sources` and set `generated`. People review every change on its branch.
- **Folder:** `docs/reference/`
- **Filenames:** `docs/reference/<operation-id>.md`, like `docs/reference/get-shipment.md`.
- **Refined from:** `api/openapi.yaml`.

Example frontmatter:

```yaml
type: API Endpoint
title: Get a shipment
method: GET
path: /v1/shipments/{id}
operation_id: getShipment
```
