# ExonUI for VS Code (Copilot)

Wire **ExonUI Grid** (`<= 16` meta-tools) into VS Code using the one-click install link, the `code` CLI, or `.vscode/mcp.json`.

## One-click install

- [Add ExonUI Grid to VS Code](vscode:mcp/install?%7B%22name%22%3A%22exonui%22%2C%22type%22%3A%22stdio%22%2C%22command%22%3A%22npx%22%2C%22args%22%3A%5B%22-y%22%2C%22exonui%40latest%22%2C%22grid%22%5D%7D)
- [Add ExonUI Grid to VS Code Insiders](vscode-insiders:mcp/install?%7B%22name%22%3A%22exonui%22%2C%22type%22%3A%22stdio%22%2C%22command%22%3A%22npx%22%2C%22args%22%3A%5B%22-y%22%2C%22exonui%40latest%22%2C%22grid%22%5D%7D)

Install URL:

```text
vscode:mcp/install?%7B%22name%22%3A%22exonui%22%2C%22type%22%3A%22stdio%22%2C%22command%22%3A%22npx%22%2C%22args%22%3A%5B%22-y%22%2C%22exonui%40latest%22%2C%22grid%22%5D%7D
```

## CLI or workspace file

Add to your VS Code profile:

```bash
code --add-mcp '{"name":"exonui","type":"stdio","command":"npx","args":["-y","exonui@latest","grid"]}'
```

Or copy [`mcp.json`](./mcp.json) into `.vscode/mcp.json` (or run `npx -y exonui@latest init --agent vscode`).

## Verify

Run **MCP: List Servers** from the VS Code Command Palette, accept trust for `exonui` when prompted, and confirm tools appear in Copilot Chat Agent mode.
