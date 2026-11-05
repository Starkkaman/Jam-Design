# Lobby (TV launcher)

> Owner: the **Control Freak Agent** session (the session that also owns Control Freak, the TV's Home Assistant
> bridge). Seeded from its interview on 2026-11-04, then corrected and filled in by that session on 2026-11-04.

## At a glance
- **What it is:** our own launcher plus dashboard for the living-room Hisense Google TV ("Phoster"). It's the first
  screen at power-on and whenever Home is pressed.
  - **Status:** mockups only. Eight interactive HTML prototypes, all rated "ready to show Isaac" by a phased
    independent design audit (4 phases, 14 passes). Nothing is installed on the TV, and Isaac hasn't chosen one.
  - **Isaac's new direction will likely replace the eight.** This page records what the launcher has to do and what
    building it taught us.
- **Every design has the same parts:**
  - a top line: house name "Bungalo", time, date, weather;
  - a stage or hero for the focused item;
  - everything on the TV, visible at once, in five groups: **Continue, Watch, Play, Listen, Home**;
  - choosers for picture mode and sound mode;
  - input screens;
  - hold-to-unlock for the front door.
- **Surfaces and input:**
  - Hisense Google TV, Android 14, MediaTek.
  - UI 1920×1080 (320 dpi); Android System WebView, Chromium 156.0.8078.47.
  - D-pad only (arrows, OK, Back); a held key repeats at about 20/s. No voice (Google Assistant is disabled on the
    TV).
  - Viewed from about 3 m, mostly at night with the lights low.
- **Stack:**
  - Plain HTML/CSS/JS per design, with no framework, on a fixed 1920×1080 canvas.
  - Shared files: `shared/content.js` is a real data snapshot; `shared/lobby.js` is the D-pad focus engine (v2.2).
  - Planned real build: a WebView launcher shell, with Control Freak (`hisense-tv/control-freak`, MQTT to Home
    Assistant) as the data and control API. Not started.
- **Theming lives in:**
  - Each design's own CSS custom properties at the top of `designs/<nn-name>/style.css`; some keep palettes in
    `app.js` or `palettes.js`. They're documented in each design's `NOTES.md` under "Tokens".
  - Fonts are local woff2 in `designs/<nn-name>/fonts/`, from Google Fonts via `tools/getfont.py`.
  - There are no shared tokens and no look switcher: a look is a whole design folder.
  - The source is `/mnt/ai/projects/lobby` (local git, not on GitHub). The gallery is `gallery/index.html` and the
    audits are in `audits/phase1-4/`.

## Screens
Screenshots are of the three shortlisted designs: **Homage** (after Josef Albers), **Kinetic** (variable type) and
**Calder** (Calder's mobiles). Each is 1920×1080, with sample data from the house's real apps, lamps and films.

| Screen | What it does | Screenshot |
|---|---|---|
| Home, Continue focused | The opening state. Focus is on the first resume point; the hero shows the title, logline, "1h 12m left", "Paused by Isaac" and "OK Resume in Jamfin". | [Homage](screens/home-focus-continue-homage.webp), [Kinetic](screens/home-focus-continue-kinetic.webp), [Calder](screens/home-focus-continue-calder.webp) |
| Home, Watch focused | Apps (Jamfin, YouTube, Netflix, Prime Video, Dropout, YouTube TV, Live TV) and Picture mode. The hero names the app and says what it is. | [Homage](screens/home-focus-watch-homage.webp), [Kinetic](screens/home-focus-watch-kinetic.webp), [Calder](screens/home-focus-watch-calder.webp) |
| Home, Play focused | Switch 2 (HDMI 2), Moonlight, Steam Link, RetroArch, and the empty HDMI 1 and HDMI 3 (shown quiet). | [Homage](screens/home-focus-play-homage.webp), [Kinetic](screens/home-focus-play-kinetic.webp), [Calder](screens/home-focus-play-calder.webp) |
| Home, Listen focused | The house music (Music Assistant group "House"), Spotify, YouTube Music, Sendspin, Sound mode, Sound out. | [Homage](screens/home-focus-listen-homage.webp), [Kinetic](screens/home-focus-listen-kinetic.webp), [Calder](screens/home-focus-listen-calder.webp) |
| Home, Home focused | Floor lamp, table lamp, mood lighting and the front door, each with its state. OK toggles a lamp in place. | [Homage](screens/home-focus-home-homage.webp), [Kinetic](screens/home-focus-home-kinetic.webp), [Calder](screens/home-focus-home-calder.webp) |
| Picture mode chooser | OK on Picture mode lists the TV's nine modes, with the current one marked. Up/Down choose and the stage previews the choice; OK applies, Back keeps the current mode ("Use Filmmaker mode", "Back keeps Theater night"). | [Homage](screens/picture-chooser-open-homage.webp), [Kinetic](screens/picture-chooser-open-kinetic.webp), [Calder](screens/picture-chooser-open-calder.webp) |
| Sound mode chooser | The same for the TV's eight sound modes. | [Homage](screens/sound-chooser-open-homage.webp), [Kinetic](screens/sound-chooser-open-kinetic.webp), [Calder](screens/sound-chooser-open-calder.webp) |
| Sound out | A one-press toggle between Optical (to the stereo) and TV speakers. This is a third job, separate from sound mode. | in the Listen screenshots |
| Input screen | OK on an input: "Switching to Switch 2". With no signal it says what to do ("No signal on HDMI 2. Turn on the Switch 2, or press Back for Home"); an empty port says nothing is connected. | [Homage](screens/input-no-signal-homage.webp), [Kinetic](screens/input-no-signal-kinetic.webp), [Calder](screens/input-no-signal-calder.webp) |
| Open / launch | OK on a film or app runs the design's opening transition, then hands over to the app. Back reverses it from wherever it is. | not added (motion; see the gallery loops) |
| Front door | "Hold OK to unlock", with visible progress; letting go early cancels it. Once unlocked, one press locks it. | not added |

## Components
All of them are custom; no UI library is used.

| Component | Custom? | Notes |
|---|---|---|
| Top line | Custom | House name, clock, date ("Tuesday, November 3" via `Lobby.date`), weather. |
| Stage / hero | Custom | Title (display type), logline, meta, progress bar, the OK glyph (24 px or more) and the action. Shows the focused item. |
| Group | Custom | A row or column of items, labelled in most looks. Kinetic has no labels; Calder hangs the items on a mobile. |
| Item: chip, plate or word | Custom | Name plus state ("40%", "Locked", "Theater night", "No signal"). Three states: at rest, focused, and quiet (empty ports). |
| Focus mark | Custom | Per look: a fill (Homage), word width (Kinetic), a red tag plus a 6 px rim (Calder). Colour snaps; only transform animates. |
| Progress | Custom | Static at its value on Continue items; on the stage in some looks. |
| Chooser | Custom | Two columns, the current value marked, the "Use X / Back keeps Y" line, and a live preview. |
| Hold progress | Custom | A fill or ring that drains on release (front door). Built on `Lobby.hold`. |
| Toggle (lamp, sound out) | Custom | No switch control: OK flips the state, shown in words and on the stage. |
| Launch layer | Custom | Opaque and full-bleed, with a face per kind: film backdrop, a brand plate for apps, a numeral for inputs. |
| Focus engine | Custom | `shared/lobby.js` v2.2. See below. |

### Focus engine (`shared/lobby.js` v2.2)
- **Markup:** `data-focus` makes an element focusable and `data-row` groups it. Groups run horizontally;
  `data-axis="y"` makes one a column.
- **Along a group:** focus stays inside it and stops at the ends. `lobby:edge` fires there; `data-wrap` makes it
  wrap.
- **Across groups:** focus goes to the nearest group, then to the item under the current one. From the first item of
  a row it goes to the next row's first overlapping item. The opposite move returns.
- **Row memory:** only within ±200 px, and between columns only when the remembered item is level.
- **Clipped items:** items less than half visible are skipped, except along the current group, where moving to them
  scrolls them into view.
- **Events and holds:** `lobby:focus`, `lobby:activate`, `lobby:press-start` / `lobby:press-end` (OK keyup) and
  `lobby:back`. `Lobby.hold(el, ms, onProgress, onDone)` is cancelled by a release, a move, Back or window blur.
- **Held keys:** moves are capped at about 13 a second.
- **Android:** the WebView host has to forward KEYCODE_BACK as Escape.

### The eight looks (for reference)

| Design | Type | Ground / ink | Accent and motion |
|---|---|---|---|
| 01 Homage (Albers) | Archivo (width axis) | OKLCH from the focused item: field L 0.30, ink 0.97 | Nested squares at L 0.40 / 0.51 / 0.66. Colour glide 640 ms; open 760 ms (a window grows over a still picture). |
| 06 Kinetic (variable type) | Science Gothic (wdth, wght, contrast, slant) | #101d50 / paper #f7f2e3 | Tungsten #fcc364 only for things that are on. Width shows focus, weight shows amount, slant shows playing. A 420 ms wipe, at least 720 ms apart. |
| 08 Calder (mobiles) | Jost | Graphite oklch(0.335 0.008 255) / paper 0.955 | Red oklch(0.60 0.205 33), yellow 0.865/0.165/92, cobalt 0.53/0.165/262. A damped swing that settles in about 1.5 s. |
| 04 Tanaka | Zen Old Mincho + Zen Kaku Gothic New | Sumi oklch(0.245 0.009 65) / gofun 0.945 | A shoji panel shuts in 260 ms and opens in 650 ms; the open is a 1050 ms clip-path wipe. |
| 07 Dither | Literata + Doto (clock only) | Graphite #2f2d29 / silver #d8d5cc | Two inks per item; a 720 ms Bayer dot dissolve. |
| 03 Sea Ranch | Schibsted Grotesk | #000 / white | Supergraphic paint stripe: red #e2372b, ultramarine #2a49c9, yellow and paper at L 0.78. |
| 02 Dessau | Jost | #000 stage over a #2e2c28 floor / #f2eee5 | Kandinsky yellow #f4c21b, red #e2412f, blue #4a78f0. |
| 05 Liquid | Bricolage Grotesque | Smoke #080b11 / #f4f7fb | Frosted sheet, radius 56, with a refracting drop. Lite mode (no blur or refraction) is the default on Android. |

## Hard constraints
- **Canvas:** fixed 1920×1080. Safe area: 96 px left and right, 54 px top and bottom.
- **Type:** nothing under 22 px; body 26 px or more; titles big; sentence case.
- **Layout:** everything on the TV visible at once, with no carousel hiding most items. A long row may scroll while it
  is focused.
- **Focus:** unmistakable from 3 m. Snap its colour; animate only its transform.
- **Flashing:**
  - A big change is at least 50 % of a 310×310 px window changing relative luminance by 0.10 or more in the same
    direction.
  - At most 2 a second, in normal and reduced motion.
  - Measured with a held key, with alternating presses at 4 a second, and at everyday speeds (one press a second).
  - Saturated red (R/(R+G+B) ≥ 0.8) over 25 % of the screen: also at most 2 a second.
  - Checked by `tools/shoot.js --check`.
- **Night glare:** the brightest resting state keeps under about 10 % of the screen above relative luminance 0.5.
  No full-screen white or yellow floods; brand colours are pulled into the lightness band.
- **Reduced motion:** swaps happen in one frame, never with a bare frame between pictures. Images are decoded
  before every swap.
- **GPU:** a TV GPU in a WebView. Animate transform and opacity. Full-screen blur, refraction or animating inherited
  custom properties needs a `?lite=1` fallback (Liquid and Kinetic have one).
- **Fonts and network:** local fonts only; no network at runtime except the data sources.
- **Writes:** Home Assistant and TV writes go through Control Freak's MQTT topics.

## What Isaac has said
- **Liked:** nothing recorded yet. He hasn't reviewed the eight prototypes (the gallery went up the morning of
  2026-11-04).
- **Rejected:** nothing for Lobby yet.
- **Asked for**, quoted from 2026-11-03:
  - "I want my own launcher/dashboard for the TV. It should be clean, beautiful, modernist design."
  - "show off your ability to make a usable yet gorgeous interface in a wide variety of styles. The experience should
    emphasize clarity without ever sacrificing fun. You may have to make some dramatic choice. That is fine, maybe
    even great."
  - "Make a couple more fun designs At leas 2 based on some cool new trends in frontend design, and at least 1 more
    playful modernist influence."
  - "Have someone with the frontend design plugin audit your work in phases tonight. They should get at least 3 passes
    for each phase to give notes"
- **Standing preferences** (said about Jam-Dash and NervOS, and applied here):
  - "Remember I want to see excellent design and cool animations in all of these."
  - Text was too small.
  - A dashboard home must let you monitor everything at once. He called Jam-Dash's Depth arc "atrocious" for hiding
    items.
  - Mockups before anything ships.

## Open questions for the bible
1. **Constraints.** Do the Lobby constraints above (flash rule in numbers, night glare cap, snapped focus colour,
   decode before swap) become bible floors for every TV surface? See `PROPOSALS.md`.
2. **Focus.** The bible's TV selector (base window, lift without moving the focus rectangle) versus Lobby's
   per-look focus marks. Which wins on the launcher, and does focus need to look the same across JamFin, NervOS and
   Lobby?
3. **Everything at once.** Lobby's rule is "no carousel hides most items"; the bible now allows group carousels when
   neighbours and position are shown. Isaac's "atrocious" verdict on Jam-Dash's Depth arc is the reason for the
   stricter rule. Which applies on the launcher home?
4. **The opening frame.** Is the hand-off frame to an app (the film open) part of the bible's signature move (the
   light reveal), or does each app own it?
5. **Measure on the TV.** None of this has been measured on the real TV yet; every cost and brightness figure is
   from desktop Chromium. The first step for whichever look is chosen is to view it on the TV, with Isaac's OK.
