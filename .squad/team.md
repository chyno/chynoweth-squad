# Squad Team

> chynoweth-squad

## Coordinator

| Name  | Role        | Notes                                              |
| ----- | ----------- | -------------------------------------------------- |
| Squad | Coordinator | Routes work, enforces handoffs and reviewer gates. |

## Members

| Name   | Role                        | Charter                           | Status     |
| ------ | --------------------------- | --------------------------------- | ---------- |
| Mal    | Lead                        | `.squad/agents/mal/charter.md`    | ✅ Active  |
| Kaylee | Frontend Dev                | `.squad/agents/kaylee/charter.md` | ✅ Active  |
| Wash   | Next.js Dev                 | `.squad/agents/wash/charter.md`   | ✅ Active  |
| Simon  | Data Engineer               | `.squad/agents/simon/charter.md`  | ✅ Active  |
| Zoe    | QA Engineer                 | `.squad/agents/zoe/charter.md`    | ✅ Active  |
| Jayne  | Jest & React Testing Expert | `.squad/agents/jayne/charter.md`  | ✅ Active  |
| Book   | UAT & Playwright Expert     | `.squad/agents/book/charter.md`   | ✅ Active  |
| Scribe | Session Logger              | `.squad/agents/scribe/charter.md` | ✅ Active  |
| Ralph  | Work Monitor                | —                                 | 🔄 Monitor |

## Project Context

- **Owner:** John Chynoweth
- **Project:** chynoweth-squad — Next.js Enterprise application
- **Stack:** NX monorepo, React + Tailwind component library, Figma (design), Next.js with hooks, GraphQL (data access), Playwright (integration tests)
- **Created:** 2026-05-07

## Quick Test Commands

- Run all Playwright E2E tests: `npm run test:e2e`
- Run payment pages Playwright spec only: `npm run nx -- e2e web-e2e --testFiles=apps/web-e2e/src/specs/payment-pages.spec.ts`
