# Work Routing

How to decide who handles what.

## Routing Table

| Work Type                          | Route To | Examples                                                                          |
| ---------------------------------- | -------- | --------------------------------------------------------------------------------- |
| NX monorepo structure & config     | Mal      | project.json, nx.json, library extraction, build targets, dependency constraints  |
| Architecture & code review         | Mal      | PR review, design decisions, cross-cutting concerns, auth wiring, env config      |
| React component library            | Kaylee   | New components, Tailwind tokens, Figma-to-code, Storybook stories, accessibility  |
| Design system & tokens             | Kaylee   | tailwind.config.js, design token updates, spacing/color/typography                |
| Next.js pages & layouts            | Wash     | App Router pages, layouts, loading/error states, middleware, next.config.js       |
| React hooks                        | Wash     | Custom hooks, shared hooks in libs/hooks, data-fetching hooks                     |
| GraphQL schema & queries           | Simon    | Types, queries, mutations, subscriptions, fragments, Apollo config                |
| GraphQL codegen & caching          | Simon    | graphql-codegen setup, cache policies, optimistic updates, MSW handlers           |
| Playwright integration tests       | Zoe      | New E2E tests, page object models, test fixtures, CI test config                  |
| Test strategy & quality gates      | Zoe      | Which flows need E2E, CI gate config, flaky test investigation                    |
| Jest unit tests & component specs  | Jayne    | `.spec.tsx` files, React Testing Library, mock strategies, renderWithApolloClient |
| Test coverage & testability review | Jayne    | Coverage gaps, component API testability, test refactors                          |
| UAT planning & execution           | Book     | UAT scenarios, acceptance walkthroughs, pre-release validation                    |
| Playwright test build & run        | Book     | Create/maintain Playwright specs, run/debug `apps/web-e2e`, triage failures       |
| Scope & priorities                 | Mal      | What to build next, trade-offs, feature decisions                                 |
| Session logging                    | Scribe   | Automatic — never needs routing                                                   |
| Work queue & backlog               | Ralph    | GitHub issue monitoring, PR status, board management                              |

## Issue Routing

| Label          | Action                                                  | Who    |
| -------------- | ------------------------------------------------------- | ------ |
| `squad`        | Triage: analyze issue, assign `squad:{member}` label    | Mal    |
| `squad:mal`    | Architecture, code review, monorepo work                | Mal    |
| `squad:kaylee` | Component library, Tailwind, Figma implementation       | Kaylee |
| `squad:wash`   | Next.js pages, hooks, App Router                        | Wash   |
| `squad:simon`  | GraphQL, Apollo, codegen, data layer                    | Simon  |
| `squad:zoe`    | Playwright tests, E2E, CI quality gates                 | Zoe    |
| `squad:jayne`  | Jest unit tests, React Testing Library, component specs | Jayne  |
| `squad:book`   | UAT execution, Playwright build/run, E2E failure triage | Book   |

1. When a GitHub issue gets the `squad` label, **Mal** triages it — analyzing content, assigning the right `squad:{member}` label, and commenting with triage notes.
2. When a `squad:{member}` label is applied, that member picks up the issue in their next session.
3. Members can reassign by removing their label and adding another member's label.
4. The `squad` label is the "inbox" — untriaged issues waiting for Mal's review.

## Rules

1. **Eager by default** — spawn all agents who could usefully start work, including anticipatory downstream work.
2. **Scribe always runs** after substantial work, always as `mode: "background"`. Never blocks.
3. **Quick facts → coordinator answers directly.** Don't spawn an agent for "what port does the server run on?"
4. **When two agents could handle it**, pick the one whose domain is the primary concern.
5. **"Team, ..." → fan-out.** Spawn all relevant agents in parallel as `mode: "background"`.
6. **Anticipate downstream work.** When a feature is being built, spawn Zoe to write test cases from requirements simultaneously, and Kaylee if new components are needed.
7. **Issue-labeled work** — when a `squad:{member}` label is applied to an issue, route to that member. Mal handles all `squad` (base label) triage.
8. **GraphQL + UI work** — Simon and Kaylee often run in parallel; Wash wires them together after.
