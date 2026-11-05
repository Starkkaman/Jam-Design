# Callsheet

> Owner: the **Callsheet Dev Agent** session. Seeded from its interview on 2026-11-04. Correct anything that's wrong, then fill in the gaps.

## At a glance
- What it is: personal-assistant HA add-on (Ingress page). Briefing, Replies (AI drafts, never sends), Agenda, Chat (read-only search), Projects, Setup (Connections, Your day, AI, Advanced).
- Surfaces and input: desktop with keyboard (Cmd-K, J/K/D/C/O/N) and phone (touch, swipes, bottom tabs, 700 px breakpoint). No TV.
- Stack: plain JS and CSS, Python stdlib server. Tokens at the top of callsheet/app/static/app.css per data-look x data-mode, plus data-base = bold | clean | easy. Source: ~/project/daily-brief/harmony/.

## Screens
_To fill in: every screen and sheet, one line each, with a screenshot in `screens/`._

| Screen | What it does | Screenshot |
|---|---|---|

## Components
_To fill in: buttons, toggles, sliders, cards, lists, tiles, meters, status lights, progress, dialogs, toasts, navigation._

| Component | Custom? | Notes |
|---|---|---|

## Hard constraints
- Works offline: bundled OFL fonts, no CDNs. Data rendered as text only; relative URLs (Ingress).
- WCAG AA, with a deeper step for text on coloured fills. 44 px phone targets. Plain words. Look ids shared with Jam-Dash.

## What Isaac has said
- Liked: "The 3 looks definitely work!"
- Rejected: "lets get rid of the cheeky production nods", "way too much text on screen", "the red could be darker".
- Asked for: "fun to use", "emphasize clarity without sacrificing fun", fluid movement between Callsheet and Jam-Dash.

## Open questions for the bible
_To fill in._
