# ExonUI Relay Packet & Hook Reference

## Schema (`version: 1` in `.exonui/relay/<id>.json`)

Required fields:
- `version`: `1`
- `id`: safe identifier matching `^[A-Za-z0-9._-]+$` (e.g. `chk_20261115_1045_abcd12`)
- `createdAt`: ISO-8601 timestamp
- `agent`: originating agent (`clientInfo.name` in MCP, or CLI `--agent`)
- `goal`: concise task statement
- `plan`: `string[]`
- `decisions`: `string[]`
- `designRefs`: `string[]`
- `packs`: `string[]`
- `filesChanged`: `string[]`
- `openQuestions`: `string[]`
- `nextStep`: single concrete next action

Optional fields:
- `targetAgent`: destination agent slug
- `trigger`: `"manual" | "stop" | "pre-compact"`
- `sessionId`: client session identifier (for grouping hook checkpoints)
- `gitBranch`: active branch captured via `git`
- `notes`: bounded sanitized hook/session note

## Security & hygiene

- Checkpoint reads/writes reject any ID containing path separators or traversal (`..`).
- `redactRelaySecrets()` masks Bearer tokens, GitHub (`ghp_`, `github_pat_`), Notion (`ntn_`), Slack (`xox*`), and OpenAI/Anthropic-style `sk-*` keys before writing disk JSON.
- Claude `Stop` hooks always check `stop_hook_active === true` and exit `0` immediately to avoid continuation loops, and skip duplicate writes when `filesChanged` + `gitBranch` match the latest checkpoint.
