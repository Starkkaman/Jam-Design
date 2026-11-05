# Jam Home (Home Assistant + Jam Cards)

> Owner: the **Home Assistant Mr Manager** session. Seeded from its interview on 2026-11-04. Correct anything that's wrong, then fill in the gaps.

## At a glance
- What it is: Home Assistant dashboards built from Jam Cards (36 custom cards, repo Starkkaman/jam-cards). Dashboards: jam-overview "Jam Home" (default; views Living, Kitchen, Master, Marissa, Music), jam-control (desktop), jam-living-room (kiosk), jam-kitchen (Echo Show 8). 21 Jam Labs dashboards.
- Surfaces and input: Echo Show 8 kiosk 1024x768 (read from ~3 m), iPad 961x601 (offline), phone 390, desktop 1280. Kiosk and phone matter most.
- Stack: HA themes (--jam-* tokens) + look packs in jam-cards/src/looks/<id>.js. Tokens in jam-cards/tokens/looks/<id>.mjs -> tools/themes.mjs -> jam-theme YAML. Per-user look via jam-looks.
- State contract: data-state on|off|offline|action, plus data-alert.

## Screens
_To fill in: every screen and sheet, one line each, with a screenshot in `screens/`._

| Screen | What it does | Screenshot |
|---|---|---|

## Components
_To fill in: buttons, toggles, sliders, cards, lists, tiles, meters, status lights, progress, dialogs, toasts, navigation._

| Component | Custom? | Notes |
|---|---|---|

## Hard constraints
- Kiosk: no scrolling, no continuous animation, 44 px targets, contrast >= 4.5:1, 12 px minimum text.
- Text at least 15/13/12 px. Everything at a glance.
- HA themes can't read entity state: stateful styling lives in card code. card-mod only for header and tabs.
- Fonts OFL, self-hosted (/hacsfiles/jam-cards/fonts). Original dashboards are never edited. Any HA change needs Isaac's OK.

## What Isaac has said
- Liked: "Tv card looks way better!", "Speaker card looks great", "Full height looks great!"
- Rejected: "Braun is kinda boring so far", "the cards have lost a lot of readability", "The kiosk music is ugly try again". No NERV or LCARS.
- Asked for: "emphasize clarity without ever sacrificing fun ... You may have to make some dramatic changes." Look picker per user.

## Open questions for the bible
_To fill in._
