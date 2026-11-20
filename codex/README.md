# ExonUI Templates for Codex

Starter configuration, `AGENTS.md` instructions, and skills setup for **OpenAI Codex**.

## Quick setup

Register ExonUI Grid from the terminal (writes `~/.codex/config.toml`):

```bash
codex mcp add exonui -- npx -y exonui@latest grid
```

Or run ExonUI's full interactive setup (with backups, diffs, and `exonui.json`):

```bash
npx -y exonui@latest init --agent codex
```

Sync all 11 ExonUI skills into `~/.codex/skills/` (or `.agents/skills/`):

```bash
npx -y exonui@latest skills sync --target codex,agents
```

## Included files

- [`config.toml`](./config.toml) — `[mcp_servers.exonui]` TOML snippet for `~/.codex/config.toml` or a trusted project `.codex/config.toml`.
- [`AGENTS.md`](./AGENTS.md) — drop-in guidance for `$exonui-grid`, `$exonui-relay`, and Grid progressive disclosure.

## Cross-agent Relay & verification

- Resume a checkpoint handed off from Claude Code: `npx -y exonui@latest relay --to codex` (or `/exonui:resume` inside Codex).
- Verify connected MCP servers with `codex mcp list` and `/mcp`.
