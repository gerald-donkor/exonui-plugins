---
name: penpot-to-code
description: Translate Penpot frames, components, and design tokens into responsive, accessible React code through ExonUI Grid's penpot pack.
license: MIT
---

# Penpot Design to Production Code

Use this skill when building UI from an open-source Penpot file via ExonUI Grid's `penpot` pack (or pairing with `/exonui:penpot-to-code`).

## Workflow

1. **Check Grid pack & repo context:**
   - Verify `penpot` is enabled in `exonui.json` via `grid_status` (or enable via `grid_enable` if authorized) and load local design tokens with `exonui-context`.
2. **Search & inspect Penpot read tools:**
   - Call `grid_search({ pack: "penpot", query: "page frame tokens export inspect" })` and `grid_describe` on candidate tools before calling `grid_call`.
   - Extract frame structure, typography, colour palette, spacing/layout flex/grid rules, and exported SVG assets.
3. **Normalise tokens & optimise exported assets:**
   - Convert Penpot colour/scale tokens to project variables using `design_utils` (`tokens_convert`, `contrast`, `palette`).
   - Run custom exported Penpot SVG illustrations/icons through `design_utils({ action: "svg_optimise" })` before committing them.
4. **Implement accessible, responsive UI:**
   - Replace absolute canvas positions with semantic HTML + responsive Flex/Grid (`360px` mobile to desktop), using `component_get` / `library_docs` for interactive primitives.
   - Add missing loading, empty, error, disabled, and `:focus-visible` states.
5. **Cross-check & checkpoint:**
   - Verify rendered layout and colour contrast in both light and dark modes, and record Penpot file/frame refs in `relay_checkpoint` if passing to QA or another agent.

## Done when

- Penpot design intent is faithfully reproduced using semantic markup, repo tokens, optimised SVGs, and responsive layout down to `360px`.
