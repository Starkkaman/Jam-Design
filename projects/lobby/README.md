# Lobby (TV launcher)

> Owner: the **Control Freak Agent** session. Seeded from its interview on 2026-11-04. Correct anything that's wrong, then fill in the gaps.

## At a glance
- What it is: ad-free launcher + dashboard for the living-room Hisense Google TV ("Phoster"). Top line (name, time, date, weather), hero for the focused item, five groups: Continue, Watch, Play, Listen, Home. Picture/sound mode choosers.
- Surfaces and input: Android 14, WebView Chromium 156, 1920x1080. D-pad only, remote repeats ~20/s. Viewed from ~3 m, mostly at night.
- Stack: plain HTML/CSS/JS per design; shared/lobby.js focus engine; tokens at the top of designs/<nn-name>/style.css. Control Freak bridges the TV to HA over MQTT.

## Screens
_To fill in: every screen and sheet, one line each, with a screenshot in `screens/`._

| Screen | What it does | Screenshot |
|---|---|---|

## Components
_To fill in: buttons, toggles, sliders, cards, lists, tiles, meters, status lights, progress, dialogs, toasts, navigation._

| Component | Custom? | Notes |
|---|---|---|

## Hard constraints
- Text >= 22 px, body 26+; safe area 96 px sides, 54 px top/bottom. Everything visible at once.
- Transform/opacity only; blur needs a lite fallback. Flash rule: big luminance changes at most 2/s. Night glare: keep bright area small.
- Local fonts only. Android Back forwarded by the WebView host.

## What Isaac has said
- Isaac hasn't reviewed the 8 prototypes yet.
- Brief: "clean, beautiful, modernist design", "clarity without ever sacrificing fun", "excellent design and cool animations".

## Open questions for the bible
_To fill in._
