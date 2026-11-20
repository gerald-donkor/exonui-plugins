# ExonUI Grid Meta-Tools & Modes

In default `meta` exposure mode, ExonUI Grid registers **16 tools total**:

| Group | Tools | Purpose |
|---|---|---|
| Discovery & execution | `grid_status`, `grid_search`, `grid_describe`, `grid_call` | Warm/probe downstream packs, search schemas via MiniSearch, inspect schema + safety tier, execute with policy + untrusted-data framing |
| Config & profile mutations | `grid_enable`, `grid_disable`, `grid_profile` | Atomically update `exonui.json` and hot-reload downstream packs |
| Knowledge & registries | `library_docs`, `component_get`, `asset_search` | Query ExonUI Grid Notes, UI component install metadata, Iconify/Fontsource/asset indexes |
| Skills | `skill_list`, `skill_get` | List multi-root skills (`project-skills`, `project-agents`, `project-claude`, `user-exonui`, `bundled-exonui`) and read `SKILL.md` or supporting files |
| Design maths & assets | `design_utils` | Contrast/AA/AAA (`culori`), OKLCH palette, type scale, spacing scale, easing, DTCG/CSS/Tailwind conversion, SVGO optimisation |
| Session Relay | `relay_checkpoint`, `relay_resume`, `relay_list` | Persist, inspect, and restore `.exonui/relay/chk_*.json` cross-agent handoff packets |

## Exposure modes (`exonui.json` -> `"exposure"`)

- `"meta"` (default): exposes only the 16 meta-tools above; `prompts/list` registers all 9 `/exonui:*` prompts.
- `"hybrid"`: exposes both the 16 meta-tools and SEP-986 `pack__tool` direct tools + prompts.
- `"direct"`: exposes downstream SEP-986 `pack__tool` direct tools directly while keeping the 9 `/exonui:*` MCP prompts active.

## CLI equivalents

- `npx exonui grid status [--probe]` — inspect live health, warm tool cache counts, and redacted `stderr` tails.
- `npx exonui grid policy` — inspect `defaultTier` and per-pack `read`/`ask`/`block` overrides.
- `npx exonui grid logs` — read recent sanitized downstream pack diagnostics from `~/.exonui/logs/packs/`.
- `npx exonui doctor` — verify Node, local config, agent files, Claude hooks, and local ports (`3845`, `4401`, `6006`).
