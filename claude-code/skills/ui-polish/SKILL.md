---
name: ui-polish
description: Audit and refine spacing rhythm, visual hierarchy, interactive states, responsive breakpoints down to 360px, dark mode, and micro-copy on an existing UI implementation.
license: MIT
---

# UI Craft & Polish Pass

Use this skill after functional code works, before shipping or handoff, to elevate generic or rough UI into crisp, intentional product craft.

## Checklist

1. **Visual hierarchy & layout rhythm:**
   - Verify one clear primary focal point per view; remove redundant borders, nested cards, or competing saturated accents.
   - Check optical alignment (icons paired with text labels, mono numerals with `tabular-nums`, button padding balance) and consistent spacing scale steps.
2. **Complete interactive state matrix:**
   - Every interactive control handles **default, hover, focus-visible, active/pressed, disabled, loading/pending, and error** cleanly without layout shift.
   - Data views handle **loading (skeleton/status), empty (clear next action), error (recoverable message), and populated** states.
3. **Responsive integrity down to `360px` (and `320px` stress check):**
   - Check long labels, monospace code blocks, URLs, and CTA buttons inside cards for horizontal overflow (`min-w-0`, wrapping, horizontal scroll on wide tables/code only where intended).
   - Ensure touch/pointer targets are at least `24x24 CSS px` (aim `40–44px` for primary mobile controls).
4. **Dark mode & surface separation:**
   - Verify crisp border/surface contrast in both light and dark themes (no washed-out text, invisible secondary buttons, or harsh unstyled white boxes).
   - Check disabled button text/background contrast as well as placeholder text (`placeholder:*` legible at AA contrast where informative).
5. **Asset & SVG cleanliness:**
   - Run custom inline SVGs or icons through `design_utils({ action: "svg_optimise" })` and ensure decorative icons carry `aria-hidden="true"`.

## Done when

- Zero horizontal overflow down to `360px`, complete interactive/empty/error states, balanced spacing/typography hierarchy, and clean light/dark parity.
