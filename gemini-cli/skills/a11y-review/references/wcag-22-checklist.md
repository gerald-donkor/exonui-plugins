# WCAG 2.2 AA Checklist for ExonUI Reviews

- **1.4.3 Contrast (Minimum):** Normal text >= `4.5:1`; large text (>= `24px` or >= `18.67px` bold) >= `3:1`.
- **1.4.11 Non-text Contrast:** Input borders, toggles, switches, custom checkboxes, icon buttons, and chart series >= `3:1` against adjacent surface.
- **2.4.1 Bypass Blocks:** Skip link as first focusable element targeting `<main id="content">`.
- **2.4.7 / 2.4.11 Focus Visible & Focus Not Obscured:** Distinct `:focus-visible` ring visible throughout keyboard traversal; sticky headers do not cover focused anchors or inputs (`scroll-margin-top`).
- **2.5.8 Target Size (Minimum):** Interactive controls at least `24x24 CSS px` (or adequate spacing).
- **3.3.1 / 3.3.2 Errors & Labels:** Visible `<label>`, explicit error text linked via `aria-describedby`, `aria-invalid="true"` on invalid controls.
- **4.1.2 / 4.1.3 Name, Role, Value & Status Messages:** Accurate native roles, `aria-current`, `aria-pressed`, `aria-expanded`, `aria-busy`, and `aria-live="polite"` for async state updates.
- **2.2.2 / Reduced Motion:** Continuous loops have a pause control; `@media (prefers-reduced-motion: reduce)` leaves all content legible immediately without JS-gated `opacity: 0`.
