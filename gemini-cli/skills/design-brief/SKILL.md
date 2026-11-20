---
name: design-brief
description: Capture user persona, visual hierarchy, constraints, tokens, and acceptance criteria in a crisp design brief before building screens or components.
license: MIT
---

# Design Brief Before Coding

Use this skill when turning a rough feature idea or redesign request into a concrete, build-ready UI specification.

## Steps

1. **Load repo context first:** Run `exonui-context` (read `DESIGN.md`, token files, and `exonui.json` profile/packs) so the brief extends the existing system instead of fighting it.
2. **Clarify missing product & UX constraints concisely:**
   - **Audience & job to be done:** Who uses this screen and what action marks success?
   - **Hierarchy & states:** Primary focal point, secondary controls, plus explicit **loading, empty, error, disabled, and success** states.
   - **Layout & responsiveness:** Behaviour at desktop (`1280px+`), tablet, and narrow mobile (`360px` with zero horizontal overflow).
   - **Theme & accessibility:** Light/dark parity, WCAG 2.2 AA contrast (`4.5:1` text / `3:1` UI), keyboard navigation order, focus visibility.
   - **Motion intent:** Purposeful transitions/micro-interactions using compositor properties (`transform`, `opacity`) with explicit `prefers-reduced-motion` behaviour.
3. **Validate colour & scale numbers early:** Use `design_utils` (`contrast`, `palette`, `type_scale`, `spacing_scale`) to lock accessible token pairings before coding.
4. **Record outputs cleanly:**
   - Summarize the brief in a concise Markdown section or update `DESIGN.md` / feature plan with explicit **"Done when"** criteria.
   - Save a Relay checkpoint (`relay_checkpoint`) if implementation will happen in another session or agent.

## Done when

- Personas, key user flows, all UI states (loading/empty/error/success), responsive rules down to `360px`, and AA contrast/motion constraints are agreed before implementation starts.
