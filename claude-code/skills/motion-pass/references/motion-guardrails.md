# ExonUI Motion Guardrails Reference

## Library roles

- **Motion (`motion.dev`):** Component state transitions, shared layout (`layoutId`), list swaps, disclosure panels, micro-interactions. Wrap app trees cleanly with `<MotionConfig reducedMotion="user">` where used.
- **GSAP + ScrollTrigger:** Timeline choreography, pin/scrub sections, scroll progress rails, SVG draw lines. Always wrap setup in `gsap.context()` / `useGSAP()` + `gsap.matchMedia()` (`"(prefers-reduced-motion: no-preference)"`) and kill/revert cleanly on unmount.
- **Lenis:** Smooth wheel/touch scroll synced to ScrollTrigger via a single shared RAF/ticker loop (never double-tick ScrollTrigger and Lenis in separate uncoordinated loops).

## Performance & a11y checks

- Avoid `4x CPU` main-thread stalls (> `50ms` tasks) caused by triggering layout thrash (`getBoundingClientRect` inside `onUpdate` without caching) or heavy filters/blur animations.
- Disable continuous animations (`animate-*`, marquees, rotating rings) under `prefers-reduced-motion: reduce` AND offer a visible Pause button where loops run > 5 seconds.
- Verify interactive controls stay clickable and `focus-visible` during mid-transition states.
