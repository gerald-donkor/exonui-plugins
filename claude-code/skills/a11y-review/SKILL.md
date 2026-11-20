---
name: a11y-review
description: Audit and fix WCAG 2.2 AA accessibility across contrast, keyboard navigation, focus visibility, ARIA semantics, forms, live announcements, and reduced motion.
license: MIT
---

# Accessibility Review (WCAG 2.2 AA)

Use this skill to verify and remediate accessibility issues on new or modified UI routes, components, and forms. Pair with `/exonui:review-and-qa` when running a broader pre-release review.

## Review pass

1. **Colour & contrast verification (`design_utils`):**
   - Check normal text (`>= 4.5:1`), large text `>= 18pt / 14pt bold` (`>= 3:1`), UI icons/borders/focus outlines (`>= 3:1`), and placeholders in both **light** and **dark** modes.
   - Use `design_utils({ action: "contrast", foreground, background, targetContrast: "AA" })` for exact pass/fail numbers and accessible colour adjustments.
2. **Keyboard & focus navigation:**
   - Walk the whole view using `Tab`, `Shift+Tab`, `Enter`, `Space`, `Escape`, and arrow keys (for tabs/menus/radio groups):
     - No keyboard traps; dialogs return focus cleanly to the trigger on close.
     - `:focus-visible` outlines meet WCAG 2.2 contrast (`>= 3:1`) and are not hidden behind sticky headers/footers (use `scroll-mt-*`).
     - Interactive elements use native `<button>`, `<a href>`, `<input>`, `<select>` rather than clickable `<div>`/`<span>`.
3. **Structure, landmarks, and screen-reader semantics:**
   - Ensure a working skip link to `<main id="content">`, single `<h1>` matching page title, monotonic heading levels (`h1` -> `h2` -> `h3`), and named landmarks (`header`, `nav`, `main`, `footer`).
   - Verify active nav items carry `aria-current="page"`, toggle buttons carry `aria-pressed` or `aria-expanded`, decorative SVGs have `aria-hidden="true"`, and non-empty result count/toast updates use polite `aria-live="polite"` regions.
4. **Forms & validation:**
   - Every input has a programmatic `<label>` (never placeholder-only).
   - Field errors link with `aria-describedby` and `aria-invalid="true"` and move/announce focus helpfully on invalid submit.
5. **Motion & target sizing:**
   - Pointer targets are `>= 24x24 CSS px`; reduced motion (`prefers-reduced-motion: reduce`) disables non-essential movement cleanly.
   - Load `references/wcag-22-checklist.md` (via `skill_get({ name: "a11y-review", file: "references/wcag-22-checklist.md" })`) for the full sign-off matrix.

## Done when

- Zero automated or manual WCAG 2.2 AA contrast, heading, landmark, form, keyboard, or reduced-motion failures remain.
