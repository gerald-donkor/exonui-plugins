---
name: exonui-context
description: Gather project design context (DESIGN.md, design tokens, exonui.json packs, framework stack, and recent Relay packets) before writing UI code.
license: MIT
---

# ExonUI Project Context Loader

Run this workflow at the start of a design or UI implementation task so generated components match the repository's actual stack, tokens, and conventions.

## Steps

1. **Check local handoff state:** Run `relay_list` (or check `/exonui:resume`) to see if an active `.exonui/relay/` packet already defines decisions, `designRefs`, and `nextStep`.
2. **Read project config & design intent:**
   - Read `exonui.json` (or inspect via `grid_status`) for the active `profile`, enabled `packs`, `exposure`, and `policy`.
   - Read `DESIGN.md` at the project root if present for typography, colour, spacing, motion, and principle constraints.
3. **Inspect framework & design tokens in code:**
   - Check `package.json` for React/Next.js/Vite/Tailwind versions and installed animation/UI libraries (`motion`, `gsap`, `lenis`, `lucide-react`).
   - Locate global CSS tokens (`globals.css`, `theme.css`, Tailwind `@theme` blocks, or `tokens.json` DTCG files) so new UI uses semantic tokens rather than hardcoded hex values or raw spacing guesses.
4. **Pull pack notes before adding dependencies:**
   - If the stack uses libraries covered by ExonUI Grid Notes (`shadcn`, `motion`, `gsap`, `lenis`, `react-bits`, `magic-ui`, etc.), call `library_docs` first to follow project-specific integration pitfalls and compatibility notes.

## Guardrails

- Never invent token names, CSS utilities, or component props without reading the target codebase first.
- Keep `library_docs` and `grid_search` targeted so context stays small for implementation.

## Done when

- Active Relay decisions, `DESIGN.md` rules, token definitions, and installed packages are confirmed before writing code.
