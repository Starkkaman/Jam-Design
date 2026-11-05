# JamFin

> Owner: the **JamFin Agent** session. Seeded from its interview on 2026-11-04. Correct anything that's wrong, then fill in the gaps.

## At a glance
- What it is: Jellyfin client. JamFin TV (Hisense Google TV, Blu-ray ISO menus) and JamFin mobile (Android now). Screens: profiles, Home rows, Movies/Shows/Blu-ray grids, Discover, Search, Settings, film/series/person pages, player, disc player.
- Surfaces and input: TV first (10-ft, D-pad taps only, no long or double presses). Phone touch with haptics.
- Stack: Kotlin + Jetpack Compose (tv-material), Media3. Palette.kt (roles: ground, onGround, mutedOnGround, slab, rule, accents), Look.kt, LookSkin.kt, MotionTokens.kt; rules in docs/experience-system.md.

## Screens
_To fill in: every screen and sheet, one line each, with a screenshot in `screens/`._

| Screen | What it does | Screenshot |
|---|---|---|

## Components
_To fill in: buttons, toggles, sliders, cards, lists, tiles, meters, status lights, progress, dialogs, toasts, navigation._

| Component | Custom? | Notes |
|---|---|---|

## Hard constraints
- TV: MT9690 / Mali-G57, 32-bit, 3.7 GB, 1080p UI (960x540 dp). GPU-bound on full redraws: animate transform and alpha only, no blur, grain as static tiles only.
- Fonts: bundled OFL only. Must not change: focus graph, fixed zones, plain button wording, resume in <= 3 presses, no long/double presses.

## What Isaac has said
- Liked: Unigrid, Olympia, New Wave ("feels the most polished"), Cel '88's parallax city; Unigrid's player menus "pop above or below the timeline we should use that everywhere".
- Rejected: Swiss "too dense... too bright... cold and harsh"; Cel '88 smash cut and selector flash; "a lot of wasted space"; "lacking polish... a little amature"; "animations still hitch a lot and should mask when things haven't finished loading".
- Asked for: "fun without sacrificing clarity", more texture and grit, full-colour covers option, animated Back that can be turned off.

## Open questions for the bible
_To fill in._
