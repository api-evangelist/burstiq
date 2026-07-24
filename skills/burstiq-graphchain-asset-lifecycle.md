---
name: Manage a GraphChain asset lifecycle
description: Create, read, update, and delete a Smart Data Object (SDO) asset on a BurstIQ GraphChain chain.
api: openapi/burstiq-lifegraph-openapi-original.json
operations: [postCreateAsset, getSDO, putUpdateAsset, patchAsset, deleteSDO]
---

# Manage a GraphChain asset lifecycle

BurstIQ LifeGraph stores data as Smart Data Objects (SDOs) written to a named
GraphChain `{chain}`. Use this flow to create and maintain an asset.

## Auth
All calls require a bearer JWT: `Authorization: Bearer <token>`. The API base is
`https://api.burstiq.com`. See `authentication/burstiq-authentication.yml`.

## Steps
1. **Create the asset** — `postCreateAsset` (`POST /api/graphchain/{chain}`) with
   the SDO body. Capture the returned SDO id (`sdoId`).
2. **Read it back** — `getSDO` (`GET /api/graphchain/{chain}/{sdoId}`) to confirm
   the on-chain record.
3. **Update** — full replace with `putUpdateAsset`
   (`PUT /api/graphchain/{chain}/{sdoId}`) or partial change with `patchAsset`
   (`PATCH /api/graphchain/{chain}`).
4. **Delete** — `deleteSDO` (`DELETE /api/graphchain/{chain}/{sdoId}`).

## Conventions
- List/search operations paginate with `limit` + `skip` (offset style).
- No idempotency-key contract is published; do not assume safe blind retries on POST.
- See `conventions/burstiq-conventions.yml` and `data-model/burstiq-data-model.yml`.
