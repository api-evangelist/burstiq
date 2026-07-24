---
name: Build and trial-run a LifeGraph data pipeline
description: Create a BurstIQ data pipeline, trial-run it, and inspect its history.
api: openapi/burstiq-lifegraph-openapi-original.json
operations: [postPipeline, getPipelines, getIPById, postDataPipelineTrialRun, getHistory_7]
---

# Build and trial-run a LifeGraph data pipeline

Data pipelines transform inbound data (field mapping, JS transform, rule/ruleset
steps) before it lands in LifeGraph.

## Auth
Bearer JWT required: `Authorization: Bearer <token>`; base `https://api.burstiq.com`.

## Steps
1. **Create the pipeline** — `postPipeline` (`POST /api/metadata/datapipeline`)
   with the ordered steps.
2. **List / fetch** — `getPipelines` (`GET /api/metadata/datapipeline`) then
   `getIPById` (`GET /api/metadata/datapipeline/{id}`).
3. **Trial-run** — `postDataPipelineTrialRun`
   (`POST /api/metadata/datapipeline/{id}/trial-run`) to validate transforms
   against sample data before going live.
4. **Audit** — `getHistory_7` (`GET /api/metadata/datapipeline/{id}/history`).

## Conventions
- Step types are managed via the Data Pipeline Field Mapping / JS Transform /
  Rule / RuleSet step APIs.
- Prefer trial-run before any production execution; see
  `conventions/burstiq-conventions.yml`.
