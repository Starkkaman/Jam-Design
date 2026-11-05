# Jam-Dash

> Owner: the **JamDash** session. Seeded from its interview on 2026-11-04. Correct anything that's wrong, then fill in the gaps.

## At a glance
- What it is: Docker manager replacing CasaOS. Runs on smol-boi and TrueNAS, port 8484. Screens: Home (alert hero, app tiles, live previews), Apps, App detail, Store, Files, Shares, System, Settings, Sign in. Global view of both servers via the HA add-on.
- Surfaces and input: desktop first (1440), phone close second (390, 44 px targets).
- Stack: SvelteKit embedded in a Go binary. Looks in web/src/lib/themes/<id>/<id>.css; guide web/docs/LOOKS.md.

## Screens
_To fill in: every screen and sheet, one line each, with a screenshot in `screens/`._

| Screen | What it does | Screenshot |
|---|---|---|

## Components
_To fill in: buttons, toggles, sliders, cards, lists, tiles, meters, status lights, progress, dialogs, toasts, navigation._

| Component | Custom? | Notes |
|---|---|---|

## Hard constraints
- WCAG AA contrast; body >= 15 px, labels 13, nothing under 12; 44 px touch targets; reduced motion respected; state never shown by colour alone; fonts bundled; no franchise logos.
- Must be shareable with other people. Nothing extracts app keys automatically.

## What Isaac has said
- Liked: "Depth II, Braun II, Lcars II - much better!"
- Rejected: Kinetic, Aero, Harper; six II redesigns ("just not for me"). "the text is too small", "the navigation in depth is atrocious".
- Asked for: "excellent design and cool animations", "clarity without ever sacrificing fun". Moving between Callsheet and Jam-Dash should feel fluid.

## Open questions for the bible
_To fill in._
