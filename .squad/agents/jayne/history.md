# Jayne — History & Learnings

## Seed Context

- **Project:** NCARB Apps — Nx monorepo (Next.js, Apollo GraphQL, React, TypeScript, Tailwind)
- **Owner:** John Chynoweth (chyno)
- **Stack:** Next.js, Apollo GraphQL (client + server), Nx, Jest + React Testing Library, Playwright, TypeScript, custom @ncarb/tailwind-theme
- **My role:** Jest & React Testing Library expert — unit and integration tests for React components
- **Team:** Mal (Lead), Kaylee (Frontend), Wash (Next.js), Simon (Data/GraphQL), Zoe (Playwright/E2E), Scribe, Ralph
- **Added:** 2026-05-09 by chyno

## Key File Paths

- Test instructions: `.github/instructions/jest-react-testing.instructions.md`
- Apollo test helper: `apps/web/specs/helpers/mocking-provider` (`renderWithApolloClient`)
- Jest config root: `jest.config.ts`, `jest.preset.js`, `jest.setup.ts`
- Per-app Jest config: `apps/web/jest.config.ts`
- Component specs: `apps/web/components/**/*.spec.tsx`, `libs/**/*.spec.tsx`

## Core Conventions

- Spec files co-located with components: `my-component.spec.tsx`
- Describe: `'Feature Area <ComponentName />'` | It: `'should ...'`
- Always async tests; `userEvent` not `fireEvent`
- GraphQL components → `renderWithApolloClient`; minimal arrow-function mocks
- Query priority: role → labelText → text → testId

## Learnings

_(Populated at runtime as I work)_
