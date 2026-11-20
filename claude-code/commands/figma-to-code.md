---
description: Translate a Figma frame and variables into shadcn/ui components and Tailwind tokens
argument-hint: [figma-url-or-node]
---

Run the **Figma to Code** workflow (target: `${ARGUMENTS:-selected Figma frame}`):

1. Inspect the target frame and variables (`get_design_context`, `get_variable_defs`, `get_screenshot`). Use `figma-desktop` (`127.0.0.1:3845/mcp`) through `grid_call`, or `figma-remote` directly if configured outside Grid.
2. Read `library_docs({ library: "shadcn" })` and convert extracted variables into CSS / Tailwind v4 `@theme` tokens using `design_utils` (`tokens_convert`).
3. Implement accessible, responsive React components covering every UI state and verify contrast (`design_utils` `contrast`) plus rendered output in `playwright`.
4. Checkpoint progress with `relay_checkpoint` before switching agents.
