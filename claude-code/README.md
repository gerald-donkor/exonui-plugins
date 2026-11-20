# ExonUI Plugin for Claude Code

The official **ExonUI** plugin wires Claude Code to:

- **ExonUI Grid MCP (`.mcp.json`):** progressive-disclosure gateway exposing <= 16 meta-tools (`grid_search`, `grid_describe`, `grid_call`, `library_docs`, `component_get`, `asset_search`, `design_utils`, `skill_list`, `skill_get`, `relay_checkpoint`, `relay_resume`, `relay_list`, `grid_status`, `grid_enable`, `grid_disable`, `grid_profile`) instead of flooding context with dozens of downstream schemas.
- **Local Relay Hooks (`hooks/hooks.json`):** automatic `Stop` and `PreCompact` session checkpointing into `.exonui/relay/` (git-ignored, secret-redacted) with loop protection and `systemMessage` compaction reminders.
- **11 Design-Engineering Skills (`skills/`):** `exonui-grid`, `exonui-relay`, `exonui-context`, `design-brief`, `figma-to-code`, `paper-to-code`, `penpot-to-code`, `ui-polish`, `a11y-review`, `design-system-audit`, and `motion-pass` (plus `references/*.md` checklists).
- **9 Workflow Slash Commands (`commands/`):** `/exonui:find`, `/exonui:checkpoint`, `/exonui:resume`, `/exonui:paper-to-code`, `/exonui:figma-to-code`, `/exonui:penpot-to-code`, `/exonui:design-system-team`, `/exonui:motion-site`, and `/exonui:review-and-qa`.

## Install

From a local checkout of the ExonUI repository:

```bash
claude plugin marketplace add ./plugins
claude plugin install exonui@exonui
```

Or configure project files directly via the ExonUI CLI:

```bash
npx -y exonui@latest init --agent claude-code
```

## Notes

- Configure active packs, safety policies (`read`, `ask`, `write`), and exposure mode (`meta` default, `hybrid`, `direct`) in `exonui.json`.
- `figma-remote` (`https://mcp.figma.com/mcp`) is direct-only and should be registered directly with `claude mcp add` when needed; `figma-desktop` (`127.0.0.1:3845/mcp`) runs through Grid.
- Inspect local setup health anytime with `npx -y exonui@latest doctor`.
