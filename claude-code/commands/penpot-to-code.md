---
description: Turn a Penpot design into shadcn/ui components, Storybook stories, and verified browser output
argument-hint: [frame-or-file]
---

Run the **Penpot to Code** workflow (target: `${ARGUMENTS:-active Penpot page}`):

1. Confirm `penpot` (`localhost:4401/mcp`) is connected via `grid_status`, then search and inspect Penpot frame/token tools (`grid_search({ pack: "penpot" })`).
2. Read `library_docs({ library: "shadcn" })`, retrieve components with `component_get`, and align tokens using `design_utils` (`tokens_convert`).
3. Document component variants and states in `storybook`, then verify layout, dark mode, and keyboard navigation in `playwright`.
4. Save a Relay checkpoint with `relay_checkpoint` when handing off.
