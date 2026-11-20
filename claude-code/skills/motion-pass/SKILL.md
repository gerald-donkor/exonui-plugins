---
name: motion-pass
description: Audit and refine UI animations across Motion (motion.dev), GSAP + ScrollTrigger, and Lenis while enforcing GPU-composited properties, reduced-motion parity, and continuous-loop pause controls.
license: MIT
---

# Motion & Micro-Interaction Pass

Use this skill when adding animation, scroll choreography, or interactive transitions, or auditing an animated page before release. Pair with `library_docs` for package-specific caveats (`motion`, `gsap`, `lenis`, `number-flow`, `dotlottie`).

## Audit & implementation steps

1. **Pull Grid Notes first:**
   - Call `library_docs` on installed motion packages (`motion`, `gsap`, `lenis`, etc.) so React/Next.js SSR cleanup, ScrollTrigger refresh, and smooth-scroll sync follow verified best practices.
2. **Enforce clean engine boundaries:**
   - **Never animate conflicting properties** with CSS transitions, Motion, and GSAP simultaneously on the same DOM node.
   - Keep **GSAP + ScrollTrigger + Lenis** out of heavy isolated utility bundles when not needed on lightweight pages.
   - Animate **compositor-safe properties only** (`transform`, `opacity` / WebGL / SVG `stroke-dashoffset`)—avoid animating `width`, `height`, `top`, `left`, `margin`, or `filter` on long lists.
3. **Guarantee non-JS visibility & clean hydration:**
   - Never ship initial SSR elements stuck at `opacity: 0` without a reduced-motion / no-JS fallback (`prefers-reduced-motion: reduce` and fallback reveal must leave all content visible and readable).
   - Cap staggered child reveals (e.g. `<= 8` visible rows) and keep interactive transitions crisp (`150–250ms` micro-interactions, interruptible springs).
4. **Enforce accessibility controls:**
   - Provide an explicit **pause/play control** for any ambient looping animation (marquees, continuous waveforms, auto-advancing showcases).
   - Honour `prefers-reduced-motion: reduce` across CSS, Motion (`MotionConfig reducedMotion="user"`), GSAP (`gsap.matchMedia()`), and Lenis.
   - Check `references/motion-guardrails.md` (via `skill_get({ name: "motion-pass", file: "references/motion-guardrails.md" })`) for quick verification checks.

## Done when

- Animations feel intentional, smooth, and interruptible, run purely on compositor properties, stay visible without JS, respect `prefers-reduced-motion`, and pause cleanly on loops.
