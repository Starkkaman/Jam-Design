# NervOS

> Owner: the **NervOS Agent** session. Seeded from its interview on 2026-11-04. Correct anything that's wrong, then fill in the gaps.

## At a glance
- What it is: 10-ft games launcher on the Aero 15 (CachyOS). Sections ARCHIVE (emulators), HANGAR (Steam), UPLINK (Moonlight/Steam Link, netplay), THEATER (Jellyfin via mpv). Boot, hub, browse, game menu, in-game hot menu, settings, power, keyboard, toasts.
- Surfaces and input: 65" HDR TV at 1080p120 from ~3 m. 2026 Steam Controller via SDL3; keyboard; HA remote over MQTT.
- Stack: Godot 4.7.2 (custom SDL3 build). design/tokens.json -> app/core/tokens.gd; themes app/themes/<id>/theme.json + layouts; motion core/choreo.gd.

## Screens
_To fill in: every screen and sheet, one line each, with a screenshot in `screens/`._

| Screen | What it does | Screenshot |
|---|---|---|

## Components
_To fill in: buttons, toggles, sliders, cards, lists, tiles, meters, status lights, progress, dialogs, toasts, navigation._

| Component | Custom? | Notes |
|---|---|---|

## Hard constraints
- GTX 1060 Mobile shared with games: idle cheaply. No flashing more than 2x/s; SAFE motion mode required.
- Fonts OFL and bundled. Only original art in the repo. Keep "Signal Deck" name and MQTT/HA ids. HDR at 200-nit SDR reference. Text >= 22 px at 1080p.

## What Isaac has said
- Liked: VHS ("very fun", "I love it!"), Choose Your Hero ("I like it a lot!"), CUT-OUT v2, character art, carousels "from time to time".
- Rejected: CUT-OUT v1 "way too busy"; arcade ideas; the comic look; descriptions "too long now haha".
- Asked for: "Show me mockups of all your ideas before you push them." "excellent design. And cool animations." 

## Open questions for the bible
_To fill in._
