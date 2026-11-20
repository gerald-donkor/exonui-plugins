---
description: Sync Figma tokens and Storybook docs with shadcn/ui components and prepare a PR review
argument-hint: [scope-or-component]
---

Run the **Design-System Team** workflow (scope: `${ARGUMENTS:-design system sync}`):

1. Pull Figma token and component specs (`get_variable_defs`, `get_design_context`), normalise tokens via `design_utils` (`tokens_convert`), and verify WCAG 2.2 AA pairs (`contrast`).
2. Align component APIs with `shadcn` (`library_docs`) and update `storybook` stories so docs match implementation.
3. Prepare a concise diff and review summary via `github` (Grid policy prompts before `write`/`destructive` GitHub calls).
4. Save a Relay checkpoint with `relay_checkpoint`.
