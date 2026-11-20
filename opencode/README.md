# ExonUI Templates for OpenCode

Starter `opencode.json` (Grid MCP + `/exonui-*` commands), `AGENTS.md` instructions, and skill sync commands for **OpenCode**.

## Quick setup

Register ExonUI Grid from the terminal:

```bash
opencode mcp add exonui -- npx -y exonui@latest grid
```

Or run ExonUI's full project setup (merges existing `opencode.json` cleanly with backups and diffs):

```bash
npx -y exonui@latest init --agent opencode
```

Sync all 11 ExonUI skills into `.opencode/skills/`:

```bash
npx -y exonui@latest skills sync --target opencode
```

## Included files

- [`opencode.json`](./opencode.json) — OpenCode config registering `mcp.exonui` (`type: "local"`), `instructions: ["AGENTS.md"]`, and 9 `/exonui-*` workflow commands.
- [`AGENTS.md`](./AGENTS.md) — drop-in project instructions for Grid progressive disclosure and Relay handoffs.

## Notes

- OpenCode reads `opencode.json` from the project root or `~/.config/opencode/opencode.json`.
- If you export new environment variables for downstream MCP packs, run `opencode service restart` so OpenCode's background service picks them up.
- Verify connected MCP servers with `opencode mcp list`.
