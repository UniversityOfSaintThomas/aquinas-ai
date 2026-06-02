# Fork Changes

**⚠️ IMPORTANT:** Permanent divergences from upstream (Boise-State-Development/agentcore-public-stack).
These changes must persist across all upstream syncs. If a Sync Fork merge produces
a conflict on any of these files, our version takes precedence.

## Workflow Triggers (pilot-production branch only - [Commit 7492cd7](https://github.com/UniversityOfSaintThomas/aquinas-ai/commit/7492cd700f95b2797c0ffedff5d4d111ea76c514))

All 9 deployment workflow files have `main` replaced with `pilot-production` in push/PR triggers and environment resolution. This prevents Sync Fork from deploying to production.

- `.github/workflows/infrastructure.yml`
- `.github/workflows/artifacts.yml`
- `.github/workflows/mcp-sandbox.yml`
- `.github/workflows/app-api.yml`
- `.github/workflows/inference-api.yml`
- `.github/workflows/frontend.yml`
- `.github/workflows/gateway.yml`
- `.github/workflows/rag-ingestion.yml`
- `.github/workflows/sagemaker-fine-tuning.yml`

## Deploy Fixes

| File | Change | Reason | `develop` |
|------|--------|--------|-----------|
| `infrastructure/lib/frontend-stack.ts` | Use `config.infrastructureHostedZoneDomain` for Route53 zone lookup | Fixes CDK synth failure when domainName is a subdomain of the hosted zone | [Commit 81bb715](https://github.com/UniversityOfSaintThomas/aquinas-ai/commit/81bb715c7e9a31badc70e52024240912c787adae) |
| `.github/workflows/gateway.yml` | Add `CDK_HOSTED_ZONE_DOMAIN` env var | Required for stack synth validation | [Commit 40e79eb](https://github.com/UniversityOfSaintThomas/aquinas-ai/commit/40e79ebce382bfcbaabe03fef29a530b64e33d4e) |

## Branding

| Files | Change | Reason | `develop` |
|-------|--------|--------|-----------|
| `frontend/ai.client/public/favicon/*`<br>`frontend/ai.client/public/img/logo-dark.png`<br>`frontend/ai.client/public/img/logo-light.png` | UST shield icons and logos | Pilot identity | [Commit 814ce82](https://github.com/UniversityOfSaintThomas/aquinas-ai/commit/814ce82a66d839aac9db98dceff96c32cb7cb845) |
| `backend/src/agents/main_agent/core/system_prompt_builder.py` | Rebrand from "boisestate.ai" to "Aquinas AI" for University of St. Thomas - System Prompt Update | Pilot identity | [Commit eab2003](https://github.com/UniversityOfSaintThomas/aquinas-ai/commit/eab2003421993cae36eec4c44cb353ffaa40d2b6) |
| `frontend/ai.client/src/index.html`<br>`frontend/ai.client/src/app/app.ts`<br>`frontend/ai.client/src/app/components/sidenav/sidenav.html` | Title: "Aquinas AI Pilot" + logo alt text: "University of St. Thomas Minnesota Logo" | Pilot identity / Accessibility | [Commit 02c18d0](https://github.com/UniversityOfSaintThomas/aquinas-ai/commit/02c18d0f8bfd2e1717e6d38980f3cc9376bc1590) |
