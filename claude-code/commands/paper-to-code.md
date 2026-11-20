---
description: Build responsive, accessible UI from a Paper artboard using Grid, shadcn/ui, and Playwright
argument-hint: [artboard-or-target]
---

Run the **Paper to Code** workflow (target: `${ARGUMENTS:-current Paper selection}`):

1. Inspect the Paper canvas first via `grid_search` -> `grid_describe` -> `grid_call` (`paper:get_basic_info`, `paper:get_selection`, `paper:get_tree_summary`, `paper:get_computed_styles`, `paper:get_jsx`).
2. Read `library_docs({ library: "shadcn" })` and fetch UI primitives safely with `component_get`.
3. Convert tokens and check WCAG 2.2 AA contrast with `design_utils` (`tokens_convert`, `contrast`).
4. Build all component states (loading, empty, error, success), responsive layouts down to 360px, and dark mode, then verify in `playwright`.
5. Save a Relay handoff packet with `relay_checkpoint` before ending or switching agents.
