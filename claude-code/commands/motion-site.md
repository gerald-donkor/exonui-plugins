---
description: Build a motion-rich site using Lenis, GSAP, Motion, shadcn/ui, and strict reduced-motion checks
argument-hint: [page-or-section]
---

Run the **Motion-Rich Site** workflow (target: `${ARGUMENTS:-landing or marketing page}`):

1. Read `library_docs` for `lenis`, `gsap`, and `motion` first so ScrollTrigger + Lenis ticker sync, `useGSAP()` cleanup, `gsap.matchMedia()`, and GSAP's licence boundaries stay intact.
2. Validate spring/easing curves via `design_utils` (`easing`) and keep animations restricted to `transform` and `opacity`.
3. Verify `prefers-reduced-motion: reduce`, visible pause controls on loops > 5s, zero hidden content without JS, and CLS <= 0.02 in `playwright`.
4. Save a Relay checkpoint with `relay_checkpoint` before ending.
