---
name: design-system-audit
description: Audit components and pages against DESIGN.md, DTCG semantic tokens, palette/type/spacing scales, component reuse, and cross-theme parity.
license: MIT
---

# Design System Compliance Audit

Use this skill to prevent design drift, hardcoded colors, duplicate primitives, or off-scale spacing across a codebase.

## Audit workflow

1. **Load source of truth (`exonui-context`):**
   - Read `DESIGN.md`, global CSS token files, Tailwind `@theme` tokens, and existing shared UI primitives (`components/ui/*` or design-system packages).
2. **Check token fidelity:**
   - Flag raw hex/rgb/oklch literals, ad-hoc shadow values, or arbitrary pixel font sizes (`text-[13px]`, inline `style={{ color: ... }}`) where a semantic system token exists.
   - Verify token naming matches DTCG/system roles (surface, ink, line, accent, status) cleanly in both light and dark modes (avoid orphaned legacy aliases).
   - Use `design_utils` (`tokens_convert`, `palette`, `type_scale`, `spacing_scale`) to verify or regenerate clean scale steps if introducing new tokens.
3. **Check component reuse & variant uniformity:**
   - Replace duplicate buttons, panels, badges, code blocks, or copy buttons with existing shared primitives.
   - Ensure variants are driven via clean mappings/tables rather than diverging one-off copies.
4. **Verify boundary & asset discipline:**
   - Check third-party brand marks/logos carry verified licence notes where required and decorative SVGs follow currentColor + size tokens.
   - Run `design_utils({ action: "contrast" })` on any new semantic token pairing.

## Done when

- All UI surfaces consume semantic tokens, reuse shared primitives cleanly, maintain light/dark parity, and pass scale/contrast verification.
