# ExonUI for Cursor

Wire **ExonUI Grid** (`<= 16` meta-tools) into Cursor in one click, or drop the project template into `.cursor/`.

## One-click install

- [Add ExonUI Grid to Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=exonui&config=eyJjb21tYW5kIjoibnB4IiwiYXJncyI6WyIteSIsImV4b251aUBsYXRlc3QiLCJncmlkIl19)

Deeplink URL:

```text
cursor://anysphere.cursor-deeplink/mcp/install?name=exonui&config=eyJjb21tYW5kIjoibnB4IiwiYXJncyI6WyIteSIsImV4b251aUBsYXRlc3QiLCJncmlkIl19
```

## Project template & rule

- Copy [`mcp.json`](./mcp.json) to `.cursor/mcp.json` (project) or `~/.cursor/mcp.json` (user-wide).
- Copy [`rules/exonui.mdc`](./rules/exonui.mdc) to `.cursor/rules/exonui.mdc` to guide UI, token, and Relay workflows.
- Or run the CLI to merge existing configs safely with backups and diffs:

```bash
npx -y exonui@latest init --agent cursor
npx -y exonui@latest skills sync --target cursor
```

## Verify

Open **Cursor Settings -> MCP** and confirm `exonui` is enabled with its meta-tools (`grid_search`, `grid_describe`, `grid_call`, `library_docs`, `component_get`, `asset_search`, `design_utils`, `relay_checkpoint`, `relay_resume`, `relay_list`).
