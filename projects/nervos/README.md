# NervOS

> Owner: the **NervOS Agent** session. Seeded from its interview on 2026-11-04; corrected and filled in the same day
> from the code at NervOS `main` 374b2ed (themes approved by Isaac and deployed 2026-11-03).

## At a glance
- **What it is:** a 10-ft games launcher on the Aero 15 (CachyOS, gamescope session). Four sections:
  ARCHIVE (emulators), HANGAR (Steam), UPLINK (Moonlight/Steam Link streaming, netplay rooms) and THEATER
  (Jellyfin, played in mpv). It also draws the in-game menus over running games and films.
- **Surfaces and input:** one 65" HDR TV, UI rendered at 1920×1080 (gaming mode 1080p120), seen from about 3 m.
  Input: a gamepad over SDL3 (Steam Controller and others), a keyboard, and a Home Assistant remote over MQTT.
  There is no mouse or touch.
- **Stack:** Godot 4.7.2 (custom SDL3 build), GDScript. Python for the MQTT/HA bridge.
- **Theming lives in:**
  - `design/tokens.json` holds the base tokens, and `app/core/tokens.gd` loads them. The reference canvas is 1920×1080; values are px at 1080p.
  - `app/themes/<id>/theme.json` is schema 1. Keys: `tokens` overrides, `fonts`, `components` variants, `layouts` per screen, `fx`, `motion`, `sound`, `text`. A theme can `extends` another one.
  - `app/layouts/<id>/*.gd` holds a theme's own screen layouts: hub, browse, game_menu, hot_menu and stage.
  - `app/core/choreo.gd` is the motion engine, `app/core/variants.gd` the component registry and `app/fx/` the post FX presets.
  - User themes are data only and live in `~/.local/share/nervos/themes/<id>/`. Users' own art lives in `~/.local/share/nervos/artwork/`.
  - You pick a look in Settings › Display › THEME. The theme makers' guide is `docs/theming/README.md`, with `DESIGN.md` and `LAYOUTS.md` beside it.

### The four looks (all approved 2026-11-03)
| Look | id | Idea | Ground / ink / accent | Type |
|---|---|---|---|---|
| **NERVOS** (default) | `nervos` | An operations room at night. Chamfered panels, hazard stripes, kanji decoration, CRT film, synthesised blips. | `#0D0B14` / `#EFE7D6` / amber `#FFA41B`, plus a green `#52F28C`, cyan `#38D3F2` and red `#FF4040` signal set | Saira, Share Tech Mono, Noto Serif (compressed), Shippori Mincho, DotGothic16 |
| **CUT-OUT** | `cutout` | A Saul Bass paper cut-out: one cut shape per screen and stop-motion. | `#151313` / cream `#F2E8D5` / section colours `#E4572E` `#F2B134` `#2A7F8A` `#9E2B25` | Anton, Work Sans |
| **CHOOSE YOUR HERO** | `hero` | A grungy cabinet paint job with one hero per system, chosen like a fighting-game character select. | `#14110E` / bone `#E9DFC9` / spray yellow `#F5C518` | Dela Gothic One, Rubik |
| **VHS** | `vhs` | A video store after hours: tapes on shelves, a VCR boot and a "Channel 3" launch. | `#0C0E12` / `#EEECE6` / pink `#FF4F8B` | Big Shoulders Display, Barlow Semi Condensed |

All screenshots below come from the GPU golden test (`app/tests/golden.gd`). The library is a fictional fixture
(made-up game names), the clock is pinned and motion is SAFE. **The art is original only.** The themes' character and
console art comes from the user's own artwork folder, and that folder was empty for these shots. That's why CHOOSE YOUR HERO
shows no portrait and VHS shows plain tape labels. On the real box those slots hold personal-use fan art, which must
stay out of every repo.

## Screens
| Screen | What it does | Screenshot |
|---|---|---|
| Boot | Power-on sequence (6.5 s; 1.8 s in SAFE). Any button skips. Each look has its own: NERVOS shows a BIOS-style POST and then the title; VHS a VCR loading a tape; HERO and CUT-OUT their own title. | [title](screens/boot-title-nervos.webp), [POST](screens/boot-post-nervos.webp), [hero](screens/boot-title-hero.webp), [vhs](screens/boot-title-vhs.webp) |
| Hub (home) | The section rail (L1/R1), the focused item's hero panel, and a row of systems/games/hosts/films with an ALL tile at the end. The HUD carries toggles, network, battery and the clock. | [nervos](screens/hub-default-nervos.webp), [focused](screens/hub-focused-nervos.webp), [CRT FX](screens/hub-crtfx-nervos.webp), [cutout](screens/hub-default-cutout.webp), [hero](screens/hub-default-hero.webp), [vhs](screens/hub-default-vhs.webp), [vhs HANGAR](screens/hub-hangar-vhs.webp) |
| Browse | Full-screen list or grid of one section or system, with a detail panel, a letter rail, and a sort/filter strip and drawer. | [nervos all](screens/browse-all-nervos.webp), [nervos system](screens/browse-system-nervos.webp), [cutout](screens/browse-system-cutout.webp), [hero](screens/browse-system-hero.webp), [vhs](screens/browse-system-vhs.webp) |
| Detail | No separate page: browse's right-hand detail panel is the detail view (art, title, played state, file). | see Browse |
| Game menu | Start on a game: PLAY (from the start / resume), add to favourites, save states with a picture. | [nervos](screens/gamemenu-default-nervos.webp) |
| Hot menu (ARCHIVE) | Guide during a game: resume, save/load state, slot, reset, picture (filters and bezels), quit. The game pauses behind a see-through backdrop. | [nervos](screens/hotmenu-paused-nervos.webp), [cutout](screens/hotmenu-paused-cutout.webp) |
| Hot menu (THEATER) | Guide during a film: tracks, subtitles and size, chapters, time, quit. It drives mpv over IPC. | — (needs a live film) |
| Launch | Title card held ≥ 900 ms, then a progress bar, then the game. Steam games get the "SORTIE" sequence; streams show CONNECTING. The looks restage it: CUT-OUT as a cut banner, HERO as a slash, VHS as Channel 3. | [nervos title](screens/launch-title-nervos.webp), [nervos loading](screens/launch-loading-nervos.webp), [cutout](screens/launch-loading-cutout.webp), [hero](screens/launch-loading-hero.webp), [vhs](screens/launch-channel3-vhs.webp) |
| Launch outro | An afterimage when the game ends (RETURN) or is cancelled (ABORT, hold B). | — |
| Netplay | Host/join cards and a standby stage over the launch screen. | — |
| Signal lost | Error screen: title, error code, a plain-language cause and next step, with RETRY / back. | — |
| Settings | A page rail plus rows. Pages: MOONLIGHT, JELLYFIN, DISPLAY (theme, FX preset, artwork folder, gaming/media mode, motion, sound, music), STEAM, LIBRARY, NETPLAY. Keys live separately in `secrets.json`. | [moonlight](screens/settings-moonlight-nervos.webp), [display](screens/settings-display-nervos.webp) |
| Power | Modal: SLEEP · RESTART · SHUT DOWN · DESKTOP MODE · SETTINGS · CANCEL. Focus starts on CANCEL; destructive items need a hold. | — |
| Keyboard (OSK) | Full-screen controller keyboard on a 12-unit grid, with letters, digits and URL/IP/e-mail symbols. | — |
| Toasts | Top right, mono caption with an amber left rule, 3.5 s. They slide in (fade in SAFE). | — |
| Attract | After 45 s idle: a "PRESS ANY BUTTON" band pulsing at 1 Hz (opacity only); static in SAFE. | — |

The CUT-OUT, HERO and VHS looks bring their own layouts for the hub, browse, game menu, hot menu and stage. Settings,
power, OSK and toasts are shared by all looks and take each look's colours and fonts.

## Components
All of these are custom. Godot's stock Controls are only used as containers and labels.

| Component | Custom? | Notes |
|---|---|---|
| Chamfered panel | Yes | 45° corners top-left and bottom-right, 2 px border, optional accent bar (`ui/chamfer_panel.gd`). The NERVOS frame; the other looks swap it out. |
| Section rail / tabs | Yes | Four tabs (number, label, kanji). The active tab is raised and turns amber when the rail has focus. CUT-OUT uses a vertical section word, HERO and VHS small top tabs. |
| Tile | Yes | Art (cover-cropped, else procedural), corner chip, label bar. Focus is an amber frame with "lock-on" brackets, a 1.08 lift and a hard cel shadow. |
| Tile row / carousel | Yes | Focus stays at a fixed reading position and the row runs off the right edge. HERO is one system at a time with neighbours named at the sides; VHS is a vertical carousel of systems. |
| Hero panel | Yes | Eyebrow, compressed title with an optional chromatic fringe, meta chips, description, primary action. |
| List (virtualised) | Yes | Pooled rows for large libraries, with a letter rail beside them. |
| Grid (virtualised) | Yes | Pooled tiles. |
| Chip | Yes | Small bordered text chip (system codes, states). |
| Button glyphs | Yes | Original drawings of A/B/X/Y and L1/R1. No platform logos. |
| Hex status grid | Yes | A 19-cell honeycomb status display (ok / busy / bad / off) in the hub's status panel. NERVOS only. |
| Segmented bar | Yes | Telemetry readouts and launch progress; fills in steps. |
| Catapult track | Yes | The launch progress bar with an amber "sled" at the fill head. |
| Hazard stripes | Yes | Static 45° stripes; never animated (photosensitivity rule). |
| Title card | Yes | Full-screen game title held ≥ 900 ms. Restaged by each look. |
| Menu sheet / OSD menu | Yes | The game and hot menus. HERO puts rows straight on the paint; VHS uses a VCR on-screen menu with a corner OSD word. |
| Settings rows | Yes | Label, one-line help, value at the right; toggles show as values (ON/OFF), never switches. |
| Toast | Yes | See Screens. |
| Modal (power) | Yes | Default focus on the safe choice. |
| OSK | Yes | See Screens. |
| Ticker | Yes | A decorative kana ticker that never carries information and stops in SAFE. |
| Post FX | Yes | A full-screen film layer: scanlines, phosphor mask, grain, vignette, chromatic fringe. Presets clean · crt · cabinet · vhs, chosen by the look or by the user. Never drawn over real art or video (`ui/art_mask.gd`). |
| Backdrops | Yes | Procedural: NERVOS hex grid, CUT-OUT cut shapes, HERO paint and stencil, VHS store shelves. |

## Hard constraints
- **GPU:** a GTX 1060 Mobile (6 GB) shared with the games and emulators. The UI must idle cheaply.
  - `core/frame_budget.gd` lowers the frame rate when nothing moves.
  - Idle loops pause while the TV can't show the box.
  - Decorative motion runs at 12 fps ("on twos"), and post FX switch off over real art.
- **Photosensitivity:** never more than 2 large luminance changes per second (`choreo.gd` enforces this for impacts), and stripes never move.
- **SAFE motion:** a user setting. It brings the boot down to 1.8 s, makes the grain static, stops the ticker and attract pulse, removes shake and flash, and turns transitions into fades.
- **Text:** body 30 px, captions 24 px. Readable text never goes below 22 px at 1080p. Decorative kana may be smaller (18 px), but they never carry information.
- **Fonts:** all SIL OFL and bundled with their licence files (`app/assets/fonts/*/OFL.txt`, `app/themes/<id>/fonts/`). No CDNs.
- **Art:** the repo holds only original art. Third-party art (box art from scrapers, personal-use fan art) lives only in the user's folders on the box.
- **HDR:** the TV runs in HDR, so SDR UI sits at a 200-nit reference and only small highlights may go brighter.
- **Names that must not change:** the Godot project is still called "Signal Deck". That fixes the user-data folder, which holds the
  settings, plus the `signal-deck` runtime state and the MQTT/HA ids. Renaming any of them loses the user's settings or the HA device.
- **Input:** everything is reachable with a D-pad plus A/B. Global actions behave the same in every look: L1/R1 for sections, Guide for the hot menu, B/Menu for power.

## What Isaac has said
- **Liked:**
  - CUT-OUT v2: "cut-out looks much better."
  - The Retrorama-style character art: "Loved the art and the style. Specifically character art I love."
  - CHOOSE YOUR HERO: "I like it a lot!"
  - VHS: "VHS is very fun", and later "I love it!"
  - Option B of the VHS console select: "I like option b the best."
  - Carousels: "I do like a carousel menu from time to time."
  - On 2026-11-03: "Themes approved."
- **Rejected:**
  - CUT-OUT v1: "The Cut-out theme looks way too busy. I feel like saul bass looks more minimal."
  - Arcade, three rounds: "too busy", then "Now it's too simple", then "Idk still not loving it". It's parked.
  - "I don't like the comic one."
  - Character portraits in frames.
  - The VHS store props: "get rid of the friday night poster and the open late sign".
  - Long descriptions: "Console descriptions are too long now haha."
- **Asked for:**
  - "Show me mockups of all your ideas before you push them."
  - "I want to see excellent design. And cool animations."
  - "something clean but edgy and retro"
  - "Make the background darker and give it a little more texture."
  - "Do something different for VHS than for Arcade", and to make CHOOSE YOUR HERO "a little grungier".
  - "make the consoles free floating on the left, and as you go down the line they carosel vertically. Then picking a console takes you to a stack of games (or a shelf?)"
  - "Make the launch screens match each of the consoles better (show their media)", and "lets do channel 3".
  - For CHOOSE YOUR HERO, "only want to see one on screen at a time and have something more fun behind them", and "Needs to be clearer that there's other options in the character select."

## Open questions for the bible
1. **Carousels for groups.** The bible allows carousels only for cover and screenshot rows, "never for groups". Isaac
   asked for system carousels in two NervOS looks: VHS stacks consoles vertically, and HERO shows one system at a
   time. Is a group carousel allowed on TV in alternate looks, as long as the neighbours are named at the edges?
2. **Stepped motion.** NervOS decoration moves on twos (12 fps, `steps()`), and focus takes 140 ms. Is stepped motion a legal
   alternative to the settle curve, or Hi-Fi only?
3. **Full-screen post FX.** The bible's TV floor says "no blur", but it doesn't cover a film layer (scanlines, grain,
   chromatic fringe). NervOS treats it as part of a look, kept off real art and video. Does the bible allow it per look,
   off in Hi-Fi?
4. **Decoration and words.** The bible says "no jokes in the interface". NERVOS uses kanji/kana decoration and flavour
   lines, and VHS has a "Be kind, rewind" sticker. None of it carries information. Is decorative flavour text allowed in
   alternate looks?
5. **Glow on the focus.** Hi-Fi says controls never glow, but on TV the focused tile *is* the control. W1 lights a window
   on it. NERVOS uses an amber frame plus brackets. Should the bible state that the TV focus light counts as an indicator?
6. **Godot target.** The token pipeline lists Godot `theme.json`. NervOS's `theme.json` `tokens` block uses the shape
   of `design/tokens.json` (`color.bg.void`, `color.ink.primary`, `typography.scale.body.size`, …). Converting into that shape
   gives NervOS a Hi-Fi look with no code. Hi-Fi would still need its own layouts for the window selector and the band.
