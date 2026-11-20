---
description: Save a portable ExonUI Relay checkpoint (.exonui/relay/) for resuming or switching agents
argument-hint: [target-agent]
---

Save an ExonUI Relay handoff packet for the current session (optional target agent: `$ARGUMENTS`).

1. Gather concise, secret-free session state:
   - `goal`: the user objective in one sentence
   - `plan`: ordered completed and remaining steps
   - `decisions`: settled architectural, UI, or design-system trade-offs
   - `designRefs`: Paper/Figma/Penpot URLs, node IDs, or token/`DESIGN.md` paths
   - `packs`: active Grid packs from `exonui.json`
   - `filesChanged`: touched files (or `autoDetectFiles: true`)
   - `openQuestions`: unresolved blockers or owner questions
   - `nextStep`: single exact next action for the resuming agent
2. Call `relay_checkpoint` (or run `npx -y exonui@latest relay checkpoint --goal "..." --next "..."` if Grid is in `direct` mode).
3. Report the saved checkpoint ID and both resume commands: `/exonui:resume <id>` and `npx exonui relay --to ${ARGUMENTS:-codex} <id>`.
