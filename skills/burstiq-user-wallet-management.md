---
name: Manage LifeGraph user wallets
description: Create, look up, and update BurstIQ LifeGraph user wallets and their consent terms.
api: openapi/burstiq-lifegraph-openapi-original.json
operations: [postUserWallet, getQueryUserWallets, getUserWalletById, getUserWalletByEmail, putUpdateUserWallet, putUpdateUserTerms]
---

# Manage LifeGraph user wallets

A user wallet holds a person's identity and consent context in LifeGraph.

## Auth
Bearer JWT required: `Authorization: Bearer <token>`; base `https://api.burstiq.com`.

## Steps
1. **Create a wallet** — `postUserWallet` (`POST /api/metadata/user/wallet`).
2. **Find a wallet** — list with `getQueryUserWallets`
   (`GET /api/metadata/user/wallet`), by id with `getUserWalletById`
   (`GET /api/metadata/user/wallet/{id}`), or by email with `getUserWalletByEmail`
   (`GET /api/metadata/user/wallet/lookup`).
3. **Update the wallet** — `putUpdateUserWallet`
   (`PUT /api/metadata/user/wallet/{id}`).
4. **Record consent** — `putUpdateUserTerms`
   (`PUT /api/metadata/user/wallet/{id}/terms/{termsId}`).

## Conventions
- Offset pagination via `limit` + `skip` on list operations.
- Consent/terms changes are audited; see `agentic-access/burstiq-agentic-access.yml`
  for the recommended agent execution contract on write operations.
