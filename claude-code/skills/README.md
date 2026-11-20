# ExonUI Skills (`v1`)

Eleven MIT-licensed [Agent Skills](https://agentskills.io) (`SKILL.md` + `references/*.md`) bundled with `exonui` and compatible with Claude Code, Codex, Cursor, OpenCode, Gemini CLI, and `npx skills`.

## Included skills

| Skill | Category | Summary |
|---|---|---|
| [`exonui-grid`](./exonui-grid/SKILL.md) | Grid & Relay | Progressive `grid_search` → `grid_describe` → `grid_call` workflow (+ `references/meta-tools.md`) |
| [`exonui-relay`](./exonui-relay/SKILL.md) | Grid & Relay | Save and resume `.exonui/relay/` handoffs across agents (+ `references/packet-schema.md`) |
| [`exonui-context`](./exonui-context/SKILL.md) | Grid & Relay | Gather `DESIGN.md`, design tokens, `exonui.json`, stack, and Relay state |
| [`design-brief`](./design-brief/SKILL.md) | Design-to-Code | Capture persona, hierarchy, tokens, and acceptance criteria before coding |
| [`figma-to-code`](./figma-to-code/SKILL.md) | Design-to-Code | Figma frame (`figma-desktop` / `figma-remote`) → React + tokens |
| [`paper-to-code`](./paper-to-code/SKILL.md) | Design-to-Code | Paper artboard → responsive, token-backed React + CSS |
| [`penpot-to-code`](./penpot-to-code/SKILL.md) | Design-to-Code | Penpot design → accessible React + tokens |
| [`ui-polish`](./ui-polish/SKILL.md) | Review & Quality | Spacing rhythm, visual hierarchy, states, dark mode, and 360px polish |
| [`a11y-review`](./a11y-review/SKILL.md) | Review & Quality | WCAG 2.2 AA contrast, keyboard, focus, and ARIA review (+ `references/wcag-22-checklist.md`) |
| [`design-system-audit`](./design-system-audit/SKILL.md) | Review & Quality | Audit components against `DESIGN.md`, tokens, and scales |
| [`motion-pass`](./motion-pass/SKILL.md) | Review & Quality | Motion, GSAP, Lenis, reduced-motion, and loop pause-control pass (+ `references/motion-guardrails.md`) |

## Install or sync

```bash
# Sync bundled skills into detected agent skill directories
npx -y exonui@latest skills sync

# Or install via the skills CLI once the public repo is live
npx skills add gerald-donkor/exonui-grid
```

## License

MIT — see [LICENSE](./LICENSE).
