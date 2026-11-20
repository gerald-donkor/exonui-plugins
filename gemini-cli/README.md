# ExonUI Extension for Gemini CLI

Connects **Gemini CLI** to ExonUI Grid (`<= 16` meta-tools), `/exonui:*` workflow commands, `GEMINI.md` guidance, and all 11 ExonUI design-engineering skills.

## Install or link

From a local checkout of ExonUI:

```bash
gemini extensions link ./plugins/gemini-cli
```

Or add Grid directly to `.gemini/settings.json`:

```bash
gemini mcp add exonui npx -- -y exonui@latest grid
```

And sync project skills into `.gemini/skills/`:

```bash
npx -y exonui@latest skills sync --target gemini-cli
```

## Available `/exonui:*` commands

- `/exonui:find <query>` — search Grid tools, Grid Notes, UI components, and assets
- `/exonui:checkpoint [target]` — save a `.exonui/relay/` handoff packet
- `/exonui:resume [id]` — restore the latest or specified Relay checkpoint
- `/exonui:paper-to-code [target]` — Paper artboard to accessible React + tokens
- `/exonui:figma-to-code [target]` — Figma frame/variables to React + Tailwind v4
- `/exonui:penpot-to-code [target]` — Penpot frame to shadcn/ui + Storybook + Playwright
- `/exonui:design-system-team [scope]` — sync Figma, Storybook, shadcn/ui, and GitHub PRs
- `/exonui:motion-site [target]` — Lenis + GSAP + Motion with reduced-motion checks
- `/exonui:review-and-qa [target]` — Playwright breakpoint, dark-mode, and WCAG 2.2 AA review

## Account requirement note

Since June 2026, Gemini CLI requires a paid Gemini API key or enterprise licence; personal Google accounts use Google Antigravity (`agy`). Use `npx -y exonui@latest init --agent antigravity` for Antigravity workspaces.
