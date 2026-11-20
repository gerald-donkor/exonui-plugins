---
name: paper-to-code
description: Translate a Paper artboard or selection into responsive, token-backed production UI using Paper Desktop MCP tools through ExonUI Grid.
license: MIT
---

# Paper Artboard to Production Code

Use this skill when turning a Paper canvas/artboard into React/CSS code via ExonUI Grid's `paper` pack (or pairing with `/exonui:paper-to-code`).

## Workflow

1. **Inspect active state & context:**
   - Call `grid_status` to confirm the `paper` pack is reachable (desktop port check via `npx exonui doctor`) and load repo tokens/`DESIGN.md` via `exonui-context`.
2. **Discover and inspect the target artboard progressively:**
   - Use `grid_search({ pack: "paper", query: "selection info tree screenshot jsx tokens" })` and `grid_describe` before calling Paper tools via `grid_call`.
   - Typical read flow on `paper`:
     1. `get_basic_info` & `get_selection` (identify target page/node IDs)
     2. `get_tree_summary` / `get_node_info` (understand layout hierarchy cleanly)
     3. `get_tokens` & `get_computed_styles` (extract colour, typography, gap, radius tokens)
     4. `get_jsx` & `get_screenshot` (inspect visual intent and layout details)
   - Note: `write` tools on Paper (e.g. `write_html`, `create_artboard`, `update_styles`, `delete_nodes`) are policy-gated (`ask`/`block`)—never mutate canvas nodes without explicit user approval.
3. **Translate into project tokens & components:**
   - Map extracted `get_tokens` and computed styles to existing CSS variables/Tailwind theme tokens instead of raw inline styles.
   - Check `library_docs`, `component_get`, and `asset_search` for matching components, fonts, and SVGs (`design_utils({ action: "svg_optimise" })` for custom SVGs).
4. **Add production resilience:**
   - Convert fixed desktop artboard widths into fluid responsive grids/flex containers that hold cleanly down to `360px`, with keyboard navigation and dark mode support.
5. **Visual parity & cleanup:**
   - Re-verify contrast (`design_utils({ action: "contrast" })`) and record Paper node IDs in `relay_checkpoint` `designRefs` when handing off.

## Done when

- Code reflects the Paper artboard's typography, spacing, and visual hierarchy using repo design tokens and responsive layout rules.
- Contrast, dark mode, keyboard reachability, and edge states are verified.
