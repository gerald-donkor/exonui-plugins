---
description: Audit a built UI across breakpoints, contrast, keyboard navigation, and shadcn/ui patterns
argument-hint: [url-or-route]
---

Run the **Review and QA** workflow (target: `${ARGUMENTS:-http://localhost:3000}`):

1. Inspect the rendered app via `playwright` (`grid_search({ pack: "playwright" })`) at desktop (1280px) and mobile (360px) in light and dark themes.
2. Verify WCAG 2.2 AA contrast (`design_utils` `contrast`), semantic landmarks, heading hierarchy, visible focus rings, and all loading/empty/error states.
3. Cross-check component patterns against `library_docs({ library: "shadcn" })` and the `a11y-review` / `ui-polish` skills.
4. Record concrete findings and next steps in a Relay checkpoint with `relay_checkpoint`.
