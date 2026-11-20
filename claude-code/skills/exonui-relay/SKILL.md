---
name: exonui-relay
description: Capture and resume structured session Relay checkpoints (.exonui/relay/) across Claude Code, Codex, Cursor, OpenCode, and Gemini CLI without losing decisions, design refs, or file state.
license: MIT
---

# ExonUI Relay Handoff Workflow

Use this skill before switching coding agents, before ending a long session, before context compaction, or right after opening a repo handed off from another agent.

## Saving a checkpoint

1. Collect concrete session state:
   - `goal`: the exact user objective in one sentence.
   - `plan`: ordered remaining/completed checklist items.
   - `decisions`: architectural or UI trade-offs already settled so the next agent does not relitigate them.
   - `designRefs`: Figma/Paper/Penpot URLs, node IDs, or `DESIGN.md` / token paths.
   - `packs`: active Grid packs (defaults to `exonui.json`).
   - `filesChanged`: touched files (auto-merged with `git status` when omitted).
   - `openQuestions`: unresolved blockers or owner decisions.
   - `nextStep`: the single highest-leverage next action.
   - `targetAgent`: optional destination (`claude-code`, `codex`, `cursor`, `opencode`, `gemini-cli`).
2. Call `relay_checkpoint` over MCP (or run `/exonui:checkpoint`, or `npx exonui relay checkpoint --goal "..." --next "..."`).
3. Verify no raw credentials or API tokens appear in notes/decisions (`redactRelaySecrets` strips common token prefixes automatically, but never intentionally paste secrets).

## Resuming from a checkpoint

1. Run `/exonui:resume` (optionally passing a specific `chk_*` ID) or call `relay_list` followed by `relay_resume`.
2. From the terminal, run `npx exonui relay --to <claude|codex|cursor|opencode|gemini> [chk_id]` for a copyable handoff packet box and `/exonui:resume <id>` command.
3. Confirm git working tree parity against `filesChanged` and `gitBranch` before making new edits.

## Claude Code `Stop` & `PreCompact` hooks

- `exonui init` wires `.claude/settings.json` hooks by default (`--no-hooks` opts out); check status with `npx exonui relay hooks status` or `npx exonui doctor`.
- `exonui relay hook pre-compact` preserves earlier session `plan`, `decisions`, `designRefs`, and `openQuestions`, captures transcript/git hints, and emits `{ "systemMessage": "..." }` so `/exonui:resume <id>` stays top-of-context after compaction.
- See `references/packet-schema.md` for field-by-field validation rules and hook guarantees.

## Done when

- A `.exonui/relay/chk_*.json` packet exists with accurate `goal`, `decisions`, `designRefs`, `filesChanged`, and `nextStep`.
- `.exonui/.gitignore` keeps `relay/` untracked locally.
- The receiving session acknowledges the checkpoint via `/exonui:resume` or `relay_resume`.
