---
name: 'run-tests-quick-reference'
description: 'Fast command reference for running tests in the NCARB NX monorepo'
domain: 'testing'
confidence: 'high'
source: 'manual'
---

## Context

Use this when asked how to run tests locally or in CI-style mode. Prefer existing npm scripts first, then Nx target commands for file-scoped runs.

## Patterns

- From repo root, run tests through npm scripts when available.
- For Playwright single-spec execution, use Nx target with `--testFiles`.
- Keep commands copy/paste ready.

## Examples

- Run all Jest-style tests across affected scope:
  - `npm test`
- Run app-specific Jest tests:
  - `npm run nx -- test web`
- Run all Playwright E2E tests (web-e2e):
  - `npm run test:e2e`
- Run one Playwright spec file:
  - `npm run nx -- e2e web-e2e --testFiles=apps/web-e2e/src/specs/payment-pages.spec.ts`
- Run one Playwright spec in headed mode for debugging:
  - `npm run nx -- e2e web-e2e --testFiles=apps/web-e2e/src/specs/payment-pages.spec.ts --headed --workers=1`
- Run affected tests in NX:
  - `npm run affected:test`
- Run affected E2E in NX:
  - `npm run affected:e2e`

## Anti-Patterns

- Do not invent new scripts when an existing npm script or Nx target already exists.
- Do not run Playwright from a subfolder if the workspace root command works.
- Do not omit file path when user explicitly requests one test file.
