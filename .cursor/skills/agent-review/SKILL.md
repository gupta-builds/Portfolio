---
name: agent-review
description: Routes Cursor subagents for TypeScript, React, R3F, security, and a11y review on this portfolio. Use after implementing a feature, before marking work done, or when the user asks for a professional review of TS/Three.js/React changes.
---

# Agent review

## When to use

Use after a non-trivial code change, or when the user asks to review TypeScript, React, Three.js, security, or accessibility.

## Mechanical bar (always)

```bash
pnpm lint
pnpm typecheck
pnpm test
```

Run `pnpm build` only when routing, env, or production output may have changed.

## Subagents

Launch only the reviewers that match the diff. Use `run_in_background: false`.

1. `typescript-reviewer` — types, async, API routes, env usage.
2. `react-reviewer` — hooks, client/server boundaries, lists, effects.
3. `three-artist` — `src/components/three/**`, Orby canvas, comet-card, `useFrame`.
4. `security-reviewer` — cookies, Turnstile, CSP, rate limits, secrets.
5. `a11y-architect` — keyboard, labels, motion, contrast.

There is no Three.js LSP. R3F allocation rules live in `.cursor/rules/r3f-three.mdc`. Do not install ESLint to get `@react-three/eslint-plugin`.

## Output

Return a short table: Severity, Location (`file:line`), Finding. Do not mix unrelated refactors into the review follow-up.
