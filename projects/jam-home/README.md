# Jam Home (Home Assistant + Jam Cards)

> Owner: the **Home Assistant Mr Manager** session. Seeded from its interview on 2026-11-04, corrected and filled in on
> 2026-11-04 from the jam-home, jam-cards and jam-theme repos. Screenshots are from the jam-home preview harness (fake
> states from a 2026-10-27 snapshot, clock fixed at Tue 2026-10-27 14:30), so nothing in them is live data.

## At a glance
- **What it is**: the family's Home Assistant dashboards, built only from Jam Cards (36 custom Lovelace cards, repo
  Starkkaman/jam-cards) on the JamBoard theme (repo Starkkaman/jam-theme). Four live dashboards:
  - `jam-overview` "Jam Home": the default for family phones. Views Living, Kitchen, Master, Marissa, Music.
  - `jam-control`: Isaac's desktop control room (admin only).
  - `jam-living-room`: the living-room kiosk (PadKiosk on the iPad).
  - `jam-kitchen`: the kitchen kiosk (ShowKiosk on the Echo Show 8).
  - Plus 21 **Jam Labs** dashboards from the night of 2026-11-04: `lab-index` "Jam Labs" in the sidebar, and a hidden
    `lab-<look>-home` / `lab-<look>-kiosk` for each of the 10 looks. These are per-look redesign experiments, never the live ones.
- **Versions**: Jam Cards **0.10.0** is on GitHub (main). **HA still runs 0.9.0** until Isaac installs 0.10.0 from HACS. The
  0.10.0 opt-ins (dock state fill, attention, …) are off by default, and the live dashboards don't use them yet.
  jam-theme with all 10 looks is installed.
- **Isaac's look**: Isaac uses **Jam Braun** on Jam Home (his per-user pick). JamBoard (Poster) is the house default. See the "Jam Braun look" section and [`screens/braun/`](screens/braun/).
- **Surfaces and input** (touch everywhere, mouse/keyboard on desktop):
  - Phone, ~390 px wide (family). This and the kiosks matter most.
  - Kitchen kiosk: Echo Show 8, 1280×800 @1.33 = **961×601 CSS px**, landscape, read from ~3 m.
  - Living-room kiosk: iPad 6th gen, **1024×768 CSS px**, landscape. Offline since its jailbreak was lost on a reboot.
  - Desktop 1280–1440 px (`jam-control`, Isaac only).
- **Stack**:
  - HA `sections` views, using only HA's layout containers (sections, grid, vertical-stack, conditional).
  - Every visible card is a Jam Card: plain JS web components, no framework, one bundle `dist/jam-cards.js`.
  - Each look is a theme (`--jam-*` CSS variables) plus a look pack (CSS + fonts) inside the bundle.
- **Theming lives in**: jam-cards `tokens/` (the single source), which generates the jam-theme YAML. Look packs are in
  jam-cards `src/looks/<id>.js`. Details under Theming below.
- **State contract**:
  - Card hosts carry `data-state="on|off|offline"`.
  - jam-kiosk dock blocks carry `data-state="on|off|action"`, plus `data-alert="true"` on an unlocked / open / jammed lock.

## Screens
Default look JamBoard (Poster). The files are in [`screens/`](screens/). Phone shots are full-page at 390 wide with the HA
header. Desktop shots are full-page at 1280 wide, with no HA sidebar. Kiosk shots are at the device size with the HA
toolbar hidden (`?kiosk`), as the devices show them.

**Jam Home is not meant for the kiosks.** They have their own dashboards, so the room views are shown at phone 390 and
desktop 1280 instead of 1024×768.

### jam-overview "Jam Home" (phones; also opens on desktop)
| Screen | What it does | Screenshot |
|---|---|---|
| Living (first view) | House strip (inside/outside temp, air word, door chip with one-tap lock, who's home), room heading with temp/humidity chips, scenes row, 4 light cards (group, lamp, WLED, Tree switch), air purifier, TV card, NerveOS (PC) media row, living-room speaker | [phone dark](screens/phone-living-default-dark.png) · [phone light](screens/phone-living-default-light.png) · [phone, TV playing](screens/phone-living-playing-dark.png) · [desktop dark](screens/desktop-living-default-dark.png) · [desktop light](screens/desktop-living-default-light.png) |
| Kitchen | House strip, heading, 3 lights (lamp, Stove lights group: offline in the fixture, Car port), kitchen speaker | [phone](screens/phone-kitchen-default-dark.png) · [desktop](screens/desktop-kitchen-default-dark.png) |
| Master | House strip, heading, 4 lights (some offline), dehumidifier + fan/blanket tiles | [phone](screens/phone-master-default-dark.png) · [desktop](screens/desktop-master-default-dark.png) |
| Marissa | House strip, heading, 5 lights | [phone](screens/phone-marissa-default-dark.png) · [desktop](screens/desktop-marissa-default-dark.png) |
| Music | One full speaker card per player (Kitchen, Living room, Phoster, Whole house): art or idle cut-paper art, ink band, transport, volume, shuffle | [phone](screens/phone-music-default-dark.png) · [desktop](screens/desktop-music-default-dark.png) |
| Light pop-up (group) | Tap a light card: brightness bar, two whites (Cozy 2200 K / Clean 4000 K), hue strip, "Your colours", group members with own brightness, off-timer 15/30/60 min, Edit | [phone](screens/phone-lightpopup-group-dark.png) |
| Light pop-up (WLED) | As above, but WLED presets as preview cards instead of the whites | [phone](screens/phone-lightpopup-wled-dark.png) |
| TV remote sheet | jam-tv Remote: TV group (power, d-pad + OK, Back/Home/Menu/Settings, Rewind/Play/Forward), Stereo group (power, vol −/mute/+, inputs TV / Turntable / Music sync), keyboard key in the header | [phone](screens/phone-tvremote-default-dark.png) |
| TV source sheet | jam-tv Source: Inputs (Nerv//OS, Switch) and Apps (YouTube, Jamfin, Dropout, Corridor Digital, Home screen) as colour tiles; the one on screen is outlined + "On now" | [phone](screens/phone-tvsource-default-dark.png) |
| NerveOS ⋯ sheet | PC controls: Sleep, Quit game, Mute, volume, d-pad remote | [phone](screens/phone-nerveos-default-dark.png) |
| Speaker panel (library) | Tap a speaker's art/band: tabs Pinned / Recent / Playlists / Albums / Search, a Speakers view, a mini player. The jam-home harness has no Music Assistant, so it shows the error state. The jam-cards preview shows it filled (fake library). | [error, phone](screens/phone-speakerpanel-error-dark.png) · [pinned, 1280](screens/desktop-speakerpanel-pinned-dark.png) |
| More-info / confirm dialogs | HA's own more-info dialog (e.g. a tap on a jam-button light) and HA confirmation dialogs (e.g. "All lights off", Quit game), themed by the theme only | — (HA built-in) |

### jam-control (Isaac, desktop, admin only)
| Screen | What it does | Screenshot |
|---|---|---|
| Control room | Four room columns of light cards. Temperature + humidity graphs (house + 4 rooms, 24 h). Panels: NAS, Network, Serenity (PC) with Wake/Sleep, Downloads & batteries. Kiosk screensaver mode pickers (Photos / Clock). Automations & alerts. One view, full page at 1280, cropped to 2560 px tall (only the bottom of the alerts list is cut). | [desktop](screens/desktop-control-default-dark.png) |

### jam-living-room kiosk (iPad, 1024×768) — one view `home` = jam-kiosk + jam-screensaver
| Screen | What it does | Screenshot |
|---|---|---|
| Kiosk home | Room-colour bar, round front-door lock button (top right), huge clock, date line, facts line (inside temp · humidity · air), a "now" line (playing on TV/speaker, else the outside weather + outlook), dock of 3 colour blocks: Lights / TV / Music | [dark](screens/kiosk-living-home-dark.png) · [light](screens/kiosk-living-home-light.png) |
| Kiosk home, door unlocked | The lock button becomes a solid red disc, "FRONT DOOR · UNLOCKED"; a tap locks it | [dark](screens/kiosk-living-unlocked-dark.png) · [light](screens/kiosk-living-unlocked-light.png) |
| Lights sheet | Fullscreen sheet: heading, scenes, air purifier, "All lights off" (confirmed), 4 light cards | [dark](screens/kiosk-living-sheetlights-default-dark.png) · [light](screens/kiosk-living-sheetlights-default-light.png) |
| TV sheet | jam-tv `size: kiosk` (60 %) + NerveOS jam-media `size: kiosk` (40 %); Remote / Source open the same sheets as on the phone | [dark](screens/kiosk-living-sheettv-default-dark.png) |
| Music sheet | jam-speaker `size: kiosk`: big art, transport, volume, pinned shelf, Browse opens the library panel | [dark](screens/kiosk-living-sheetmusic-default-dark.png) |
| Screensaver, Clock mode | After 120 s idle, 06:00–23:00: a Poster clock + date + weather in the room colour. A tap dismisses it. | [dark](screens/kiosk-living-screensaver-dark.png) · [light](screens/kiosk-living-screensaver-light.png) |
| Screensaver, Clock + now playing | `now` block under the weather when the TV or speaker plays | [dark](screens/kiosk-living-screensaverclock-playing-dark.png) |
| Screensaver, Photos mode | Photo slideshow (pre-resized JPEGs, crossfade) with a time chip and the now-playing label. The shot uses the harness's abstract test slides, not family photos. Clock vs Photos is picked per kiosk by an `input_select` (on jam-control). | [dark](screens/kiosk-living-screensaverphotos-playing-dark.png) |

### jam-kitchen kiosk (Echo Show 8, 961×601)
| Screen | What it does | Screenshot |
|---|---|---|
| Kiosk home | Same layout in kitchen teal; dock Lights / Music / All off (an action block, confirmed) | [dark](screens/kiosk-kitchen-home-dark.png) · [light](screens/kiosk-kitchen-home-light.png) |
| Lights sheet | 3 kitchen light cards | [dark](screens/kiosk-kitchen-sheetlights-default-dark.png) |
| Music sheet | Kitchen speaker, `size: kiosk` | [dark](screens/kiosk-kitchen-sheetmusic-default-dark.png) |
| Screensaver (Clock) | As the living room, in teal | [dark](screens/kiosk-kitchen-screensaver-dark.png) |

The kiosks have no room tabs. HA automations own screen-off 23:00–06:00 (touch wakes the screen) and the brightness;
the dashboard owns the visual screensaver.

### Jam Labs
| Screen | What it does | Screenshot |
|---|---|---|
| Jam Labs index (`lab-index`) | jam-looks picker plus Home / Kiosk buttons for each look's lab dashboards. In the harness, the picker shows only "Use system default" because the fake hass has no installed themes; in HA it shows one tile per look. | [desktop](screens/desktop-labsindex-default-dark.png) |
| `lab-<look>-home` / `lab-<look>-kiosk` | Clones of jam-overview / jam-living-room, redesigned per look. Not documented here: they're experiments, and the default look is the subject. | — |

### State examples
| State | Where | Screenshot |
|---|---|---|
| On / off / offline lights | Light cards in jam-control: on = filled with the light's own colour + brightness number; off = quiet slab, "OFF"; offline = hollow card with a dashed edge, "OFFLINE" in alert red | [crop](screens/card-light-on-off-offline-dark.png) |
| Alert: door unlocked | Phone house strip: red "DOOR UNLOCKED · LOCK" chip (see the Living view). Kiosk: red lock disc (see "Kiosk home, door unlocked"). | [phone](screens/phone-living-default-dark.png) · [kiosk](screens/kiosk-living-unlocked-dark.png) |
| Dock state fill (0.10.0 opt-in, not live) | jam-kiosk `dock_state: fill`: an on block is filled (Lights "ON 2", Music "SATURN"), an off block is outlined (TV), action blocks are outlined (All off), a locked Door is quiet. `now_band` puts what's playing at the top. | [kiosk](screens/kiosk-living-dockfill-on-dark.png) |
| Attention (0.10.0 opt-in, not live) | jam-kiosk `attention`: a red bar "FRONT DOOR UNLOCKED · TAP TO LOCK" appears only while true, and the Door block fills red | [kiosk](screens/kiosk-living-attention-alert-dark.png) |
| Error | Speaker library panel when Music Assistant can't be reached: "Couldn't load the library" + Retry. Failed taps show a short error strip on the card (0.7.2). | [phone](screens/phone-speakerpanel-error-dark.png) |
| Loading / empty | No dedicated loading screens: cards render "Offline" until HA has the entity. Empty = "Pin playlists and albums from Browse" on the speaker shelf (visible in the kiosk Music sheet). | — |

Not captured: the HA sidebar, real album art and photos (private), motion, and the other 9 looks (the audit in jam-home
`docs/audit/` has them).

## Components
All 36 are custom (Jam Cards, `src/cards/jam-*.js`). The live dashboards use no HA built-in visual cards, only HA's
layout containers. HA chrome still in use: the header tabs (restyled by the theme's card-mod rules), the more-info
dialog and confirmation dialogs (theme colours only), and the sidebar.

| Component | Custom? | Notes |
|---|---|---|
| jam-heading | Custom | Section title over a 5 px accent rule, with state chips (temp/humidity) |
| jam-hero | Custom | Paper slab with a cut corner: big title, meta line, chips |
| jam-tile | Custom | Entity block with a status stripe and an optional control (toggle / lock / press); dehumidifier, fan |
| jam-choice | Custom | select / input_select as option chips (kiosk screensaver Photos / Clock) |
| jam-slider | Custom | Strip slider for number, brightness, volume, fan speed |
| jam-media | Custom | Now playing as a duotone print; transport, volume, sources, grouping; `compact` and `size: kiosk`; NerveOS |
| jam-button | Custom | Chunky key for scenes/scripts/launchers; a lit light/switch fills the key; power corner |
| jam-gauge | Custom | Half-disc of cut wedges, or a strip, with a big numeral (read-only) |
| jam-list | Custom | Paper sheet of entity rows (replaces the entities card) |
| jam-light | Custom | Light card painted in the light's own colour, brightness number + strip, power corner, drag to dim; tap = light pop-up |
| jam-popup | Custom | Full-screen veil + sheet of cards, opened by a URL hash |
| jam-graph | Custom | Recorder history: line / step / bars, 1–5 series |
| jam-weather | Custom | Big temperature, condition word, cut-paper glyph, forecast, optional clock |
| jam-remote | Custom | TV remote: d-pad, keys, colour-coded groups (TV / Stereo) |
| jam-tv | Custom | Smart TV: art poster, ink title band, transport, volume rocker, Remote + Source sheets |
| jam-speaker | Custom | Music Assistant speaker: art or idle cut-paper art, band, shuffle/favourite, transport, volume, library panel (`jam-music-panel.js`, a sub-component, not a card) |
| jam-fan | Custom | Fan / air purifier: power corner, speed steps, presets |
| jam-house | Custom | House strip: temps, condition, air word, door chip (tap = lock), who's home, alert chips |
| jam-tabs | Custom | Room tabs (dropped from the live dashboards 2026-10-27; HA's own tabs are styled instead) |
| jam-scenes | Custom | Row of scene keys; the scene activated last fills |
| jam-screensaver | Custom | Idle overlay: Poster clock + weather, or photo slideshow; `now` block; minute timer, no loops |
| jam-kiosk | Custom | Kiosk home: bar, clock, date, facts, now line, lock button, dock of 2–5 blocks opening fullscreen sheets |
| jam-panel | Custom | Control-room panel of name/value rows, red when a value is bad |
| jam-alerts | Custom | Automations by last run, watched entities, unavailable count |
| jam-looks | Custom | Per-user look picker, with a live swatch per look |
| jam-dial | Custom, **look card** (Braun) | Light as a rotary dial |
| jam-keypad | Custom, **look card** (Braun) | Scenes as round ET66 calculator keys with a display |
| jam-radio | Custom, **look card** (Braun) | Speaker as a T3 pocket radio with a volume wheel |
| jam-pictogram | Custom, **look card** (Olympia) | Room tile with an Aicher-style pictogram and 2–4 facts |
| jam-programme | Custom, **look card** (Olympia) | The day as a games programme timeline |
| jam-results | Custom, **look card** (Olympia) | Results board: big numbers on colour squares |
| jam-linemap | Custom, **look card** (Transit) | The house as a subway map: rooms = lines, entities = stations |
| jam-arrivals | Custom, **look card** (Transit) | Arrivals board: alerts, now playing, next events, states |
| jam-matrix | Custom, **look card** (Grid) | Toggle matrix with a big on-count numeral |
| jam-ridge | Custom, **look card** (Pulsar) | Stacked ridgelines of sensor history |
| jam-sticker | Custom, **look card** (New Wave) | Conditional sticker note (info / warn / alert) |

The 11 look cards were each made for one look but work in every look. None are on the live dashboards; they appear only in
the Labs. Shared parts inside the cards include the power corner, the cut-corner edge system, tone marks, the error
strip, sheets (`openSheet`) and motifs, all in `src/core.js`.

## Theming
- **Token source** (edit here only): jam-cards `tokens/registry.mjs` (every `--jam-*` token), `tokens/looks/<id>.mjs`
  (one per look: poster, braun, olympia, transit, grid, pulsar, newwave, brutal, glass, girard; plus `stress` for tests),
  and `tokens/ha.mjs` (the ~117 HA keys worked out from a palette).
- **Generators**:
  - `node tools/themes.mjs` writes the theme YAMLs into the jam-theme repo.
  - `node tools/bundle.mjs` writes the cards' fallbacks + `preview/looks.css`.
  - `--check` fails while anything is stale.
- **Theme YAML** (HACS theme repo Starkkaman/jam-theme): `themes/jamboard.yaml` (theme **JamBoard** = the Poster look, the default),
  `themes/jamboard-<id>.yaml` for "Jam Braun", "Jam Olympia", "Jam Transit", "Jam Grid", "Jam Pulsar", "Jam New Wave",
  "Jam Brutal", "Jam Glass", "Jam Girard". Each sets the `--jam-*` palette per light/dark mode, the font stacks, the shape
  tokens, `--jam-look: <id>` and, for New Wave and Glass, `--jam-fx: 1`.
- **Look packs**: jam-cards `src/looks/<id>.js` (`registerLook({id, name, css, fonts, motifs})`), bundled into
  `dist/jam-cards.js`. Poster has no pack: it's the base CSS in `src/core.js`. Per-look rules are in jam-cards `docs/DESIGN.md`,
  and the look briefs in `docs/looks/<LOOK>.md`.
- **Fonts** (all SIL OFL):
  - Poster's Londrina Solid + Jost are embedded in the bundle (from jam-cards `fonts/`).
  - The other looks' woff2 files are in jam-cards `dist/fonts/` and served from `/hacsfiles/jam-cards/fonts/`. They load only while that look is active.
  - Those fonts: Archivo, Albert Sans, Arimo, Hanken Grotesk, Silkscreen, Bricolage Grotesque, Figtree, Fraunces, Work Sans.
  - Licences are in `dist/fonts/OFL-*.txt`. Nothing is fetched from outside HA.
- **How a look is selected**: a look is just an HA theme.
  - Per user: Profile → Theme, or the `jam-looks` card. It fires the frontend's own `settheme` event, like Profile → Theme does. That sets the theme for the logged-in user (this browser + that user's profile in HA 2026.10) and keeps their auto/light/dark choice.
  - House default: the backend default via `frontend.set_theme`.
  - A view's `theme:` overrides both. The live dashboards' views pin no theme (per the configs in jam-home `dashboards/`), so
    each user's own pick applies. Each Labs view pins its look.
  - Cards read `--jam-look` and switch pack live, without a reload.
- **State contract**: details are in jam-cards `docs/DESIGN.md` "State grammar".
  - On = the strongest fill the look owns; off = quiet.
  - A lock is never "on": unlocked/open/jammed = alert, locked = quiet.
  - Trouble sensors (problem, moisture, smoke, gas, CO, …) = alert while on.
  - Unreachable = "Offline" on a broken form (Poster: a hollow card with a dashed edge).
  - Hooks for look packs: `data-state="on|off|offline"` on jam-light / jam-button / jam-tile / jam-fan hosts, and `data-state="on|off|action"` + `data-alert="true"` on jam-kiosk dock blocks.
- **Accents**: one colour per room. Living = ochre, kitchen = teal, master = blue, Marissa = pink, music = violet, nerd = green; red is alerts only.

## Jam Braun look
After Dieter Rams (T3 radio, ET66 calculator, AB-1 clock): a warm-white or anthracite appliance you operate. Quiet panels
with a hairline and a soft shadow (the only look with elevation), one orange signal for "active / act", toggle switches
instead of power corners, LED dots instead of colour floods, no cut corners.
- **Brief**: jam-cards `docs/looks/BRAUN.md`.
- **Rules**: jam-cards `docs/DESIGN.md` "Braun rules".
- **Tokens**: `tokens/looks/braun.mjs`, which generates jam-theme `themes/jamboard-braun.yaml` (theme name **"Jam Braun"**).
- **Pack**: jam-cards `src/looks/braun.js`.

**Version note.** The screenshots below are rendered with jam-cards main (**0.10.0**) and the current jam-theme. HA runs
jam-cards **0.9.0**, and the jam-theme on HA is current (installed 2026-11-04). Braun changes from 0.9.0 to 0.10.0:
- **Living colour**: a new `jam-living` token, walnut `#8a5a3b` light / `#b07a52` dark, so the living room is no longer the
  signal orange. The audit had flagged that as a Braun bug.
- **Offline**: the state-grammar Offline form. The panel lifts out: no face, no shadow, a 1.5 px dashed `--dim` hairline,
  and the word "Offline". It used to be the off form + "N/A".
- **Locks**: a lock is never "on" (core change), so an unlocked door shows as the red alert.
- **Alert rule** on the new jam-house attention strip and on jam-matrix alert cells: a panel-2 face, alert-red text and a
  1.5 px red ring. The red fill with ink text was 3.54:1 in light mode.
- **Type floor**: labels are at least 12 px and chips at least 13 px.
- **Look cards**: polish for jam-dial, jam-keypad and jam-radio. Not on the live dashboards.

On HA today, then, the living room may still read as signal orange (depending on whether 0.9.0 cards read `jam-living`),
and unreachable lights read "N/A" on the off form.

### Tokens (theme "Jam Braun")
| Token | Light (primary) | Dark |
|---|---|---|
| Page (HA ground / `lovelace-background`) | `#e7e3da` warm white | `#1c1c1a` anthracite |
| Panel (`jam-slab`, card face) / panel 2 (`slab2`, keys, tracks) / `slab3` (keys in sheets) | `#f2efe8` / `#e4e0d6` / `#dcd7cc` | `#2a2a27` / `#34342f` / `#3d3d38` |
| Text (`jam-fg`) / dim (`jam-dim`) / hairline (`jam-line`) | `#262626` / `#605c54` / `#d6d1c6` | `#ece9e2` / `#aca89f` / `#3d3d38` |
| Signal (`jam-ochre`: default accent, focus ring, HA primary) | `#f07d1e` | `#f28a2e` |
| Living (`jam-living`, walnut) | `#8a5a3b` | `#b07a52` |
| Alert fill (`jam-red`) / alert text (`jam-alert-text`) | `#d9482b` / `#b32205` | `#e5583a` / `#ff8668` |
| Room hues teal / blue / pink / violet / green | `#22a39a` / `#4a7be0` / `#d24f7c` / `#9b6dd6` / `#5f9a4a` | `#22a39a` / `#4a7be0` / `#e2658f` / `#9b6dd6` / `#6fae58` |
| Text on fills (`jam-on-fg`) | `#262626` | `#1c1c1a` |
| Graph series s1–s5 | `#d26a12` `#00879c` `#c2361a` `#8a52ad` `#5f7d1c` | `#f28a2e` `#1f9fb0` `#d43a1c` `#a66cc4` `#7f9b2a` |
| Elevation (`jam-elev-1`) | `0 1px 0 rgba(255,255,255,.7) inset, 0 2px 8px rgba(0,0,0,.08)` | `0 1px 0 rgba(255,255,255,.04) inset, 0 2px 10px rgba(0,0,0,.35)` |
| Pack constants (no tokens) | ET66 yellow `#e8b12a`, olive `#6f8f3a` | same |

These values are the same in both modes:
- **Fonts**: Archivo (OFL, variable 300–700, `dist/fonts/archivo-var-latin.woff2`) for display and body; HA's body and
  heading font are set to Archivo too.
  - Display: weight 500, mixed case, lead 1.18, scale .72× Poster's size, tracking −.005em.
  - Big numerals: 400 at .85×; the kiosk clock is 300.
  - Labels: 500, uppercase, tracking .06em.
  - Keys: 500, mixed case.
- **Shapes**: no cut corners (every `jam-shape-*` is `none`).
  - Radii: cards, sheets and hero 14 px; inner posters 10 px; keys, chips and pills 999 px. HA's radii are mapped to match (6 / 10 / 14 / 999).
  - Border: `1px solid var(--jam-line)`. Rules and stripes are 2 px.
- **Motion**: smooth, never stepped. Ease-out `cubic-bezier(.2,.7,.3,1)`, 160–220 ms; press = `scale(.98)`. The pack's own
  keyframes replace Poster's wipes, stamps and spiral: braun-enter, braun-press, braun-settle, braun-rise, braun-fade-in/out, braun-nudge.
- **Contrast**: every text is at least 4.5:1 in both modes. Text on the signal is ink, not white.

### What the Braun pack changes (src/looks/braun.js)
- **Surfaces**: panels with a hairline + soft shadow, inner panels 10 px. Tone marks are LED dots; stripes are 2 px rules.
- **Controls**:
  - Keys are pills on panel 2. The primary key and the active choice are the orange signal.
  - Sliders: a 4 px strip with rounded ends, an orange fill and an 18 px knob.
  - Focus: a 2 px signal ring with a 2 px offset.
- **Power corner → toggle switch**: a 34×18 pill top-right with the same 46 px hit area, olive `#6f8f3a` when on.
- **Lights**: the face stays a panel, tinted flat in the light's own colour while on (18 % light, 24 % dark), with an LED
  dot in the light's colour, a brightness strip and member dots.
- **Colour revision 2026-11-03** (after Isaac's "Braun is kinda boring so far. I think we can incorporate a little more color."):
  - Light-colour tints on lit lights.
  - ET66 yellow `#e8b12a` for secondary accent keys: shuffle/favourite on, active tab/scene/choice, current TV source.
  - Olive for on toggles and switch keys.
  - The room colour as a 4 px rule on top of each jam-heading.
  - 15 % room tints on kiosk dock blocks.
  - 12 % tints on the speaker / TV text bands. The kiosk speaker's side panel stays a plain panel.
- **Motifs**:
  - Empty: a 5×4 dot grille.
  - Idle album art: a T3 speaker-grille dot field with one orange dot.
  - Power glyph: a thin 1.75 px stroke.
  - Sheets: no spiral flash.
  - Screensaver: the AB-1 dial ring with an orange dot.
- **Kiosk (jam-kiosk)**:
  - Room bar: 2 px.
  - Clock: weight 300, with the colon in the signal.
  - Dock blocks: tinted panels (15 % room colour) with a 12 px room dot before the name; pressed = solid room colour.
    Action blocks (All off) are a plain panel.
  - Lock: a quiet panel disc; unlocked = the red disc with a red ring.
  - With `dock_state: fill` (opt-in), an on block fills.
- **Screensaver**: an AB-1 clock on a plain panel page. The time is 300 and the weather word 400; a hairline ring with an
  orange dot replaces Poster's colour bars. The time chip and now-playing block are panels with a hairline.
- **Alert rule**: alert-red text on a panel-2 face with a 1.5 px red ring (attention strip, matrix cells). An unlocked
  door uses the red fill (kiosk disc, house chip dot).
- **Offline**: no panel, no shadow, a dashed hairline, dim text.
- **Look cards**: jam-dial (raised cap, rounded arc), jam-keypad (brown ET66 body, green LCD, coloured keys), jam-radio
  (T3 grille, dark LCD, ribbed wheel).

### Braun screens
Rendered with the jam-home harness (`?look=braun`, fake states, clock fixed at Tue 2026-10-27 14:30), except where noted.
The files are in [`screens/braun/`](screens/braun/).

| Screen | Screenshots |
|---|---|
| Phone Living | [dark](screens/braun/phone-living-default-dark.png) · [light](screens/braun/phone-living-default-light.png) |
| Phone Kitchen | [dark](screens/braun/phone-kitchen-default-dark.png) · [light](screens/braun/phone-kitchen-default-light.png) |
| Phone Master | [dark](screens/braun/phone-master-default-dark.png) · [light](screens/braun/phone-master-default-light.png) |
| Phone Marissa | [dark](screens/braun/phone-marissa-default-dark.png) · [light](screens/braun/phone-marissa-default-light.png) |
| Phone Music | [dark](screens/braun/phone-music-default-dark.png) · [light](screens/braun/phone-music-default-light.png) |
| Light pop-up, group | [dark](screens/braun/phone-lightpopup-group-dark.png) · [light](screens/braun/phone-lightpopup-group-light.png) |
| Light pop-up, WLED | [dark](screens/braun/phone-lightpopup-wled-dark.png) · [light](screens/braun/phone-lightpopup-wled-light.png) |
| TV Remote sheet | [dark](screens/braun/phone-tvremote-default-dark.png) · [light](screens/braun/phone-tvremote-default-light.png) |
| TV Source sheet | [dark](screens/braun/phone-tvsource-default-dark.png) · [light](screens/braun/phone-tvsource-default-light.png) |
| NerveOS sheet | [dark](screens/braun/phone-nerveos-default-dark.png) · [light](screens/braun/phone-nerveos-default-light.png) |
| Speaker library panel, **error state** (jam-home harness: no Music Assistant) | [dark](screens/braun/phone-speakerpanel-error-dark.png) · [light](screens/braun/phone-speakerpanel-error-light.png) |
| Speaker library panel, **filled** (Pinned tab, 1280; from the **jam-cards preview** with its fake library, not jam-home) | [dark](screens/braun/desktop-speakerpanel-pinned-dark.png) · [light](screens/braun/desktop-speakerpanel-pinned-light.png) |
| Living kiosk home (1024×768) | [dark](screens/braun/kiosk-living-home-dark.png) · [light](screens/braun/kiosk-living-home-light.png) |
| Living kiosk, door unlocked | [dark](screens/braun/kiosk-living-unlocked-dark.png) · [light](screens/braun/kiosk-living-unlocked-light.png) |
| Living Lights sheet | [dark](screens/braun/kiosk-living-sheetlights-default-dark.png) · [light](screens/braun/kiosk-living-sheetlights-default-light.png) |
| Living TV sheet | [dark](screens/braun/kiosk-living-sheettv-default-dark.png) · [light](screens/braun/kiosk-living-sheettv-default-light.png) |
| Living Music sheet | [dark](screens/braun/kiosk-living-sheetmusic-default-dark.png) · [light](screens/braun/kiosk-living-sheetmusic-default-light.png) |
| Living screensaver (Clock) | [dark](screens/braun/kiosk-living-screensaver-dark.png) · [light](screens/braun/kiosk-living-screensaver-light.png) · [dark, TV playing](screens/braun/kiosk-living-screensaverclock-playing-dark.png) |
| Kitchen kiosk home (961×601) | [dark](screens/braun/kiosk-kitchen-home-dark.png) · [light](screens/braun/kiosk-kitchen-home-light.png) |
| Kitchen kiosk, door unlocked | [dark](screens/braun/kiosk-kitchen-unlocked-dark.png) · [light](screens/braun/kiosk-kitchen-unlocked-light.png) |
| Kitchen Lights sheet | [dark](screens/braun/kiosk-kitchen-sheetlights-default-dark.png) · [light](screens/braun/kiosk-kitchen-sheetlights-default-light.png) |
| Kitchen Music sheet | [dark](screens/braun/kiosk-kitchen-sheetmusic-default-dark.png) · [light](screens/braun/kiosk-kitchen-sheetmusic-default-light.png) |
| Kitchen screensaver (Clock) | [dark](screens/braun/kiosk-kitchen-screensaver-dark.png) · [light](screens/braun/kiosk-kitchen-screensaver-light.png) |
| **State:** on / off / offline lights (jam-control crop at 1280: lit = light-colour tint + olive toggle, off = plain panel, offline = dashed hairline + "Offline") | [dark](screens/braun/card-light-on-off-offline-dark.png) · [light](screens/braun/card-light-on-off-offline-light.png) |
| **State:** alert, door unlocked on the phone house strip (red dot chip "Door unlocked · lock"; crop of the Living view top) | [dark](screens/braun/house-door-unlocked-alert-dark.png) · [light](screens/braun/house-door-unlocked-alert-light.png) |
| **State:** kiosk dock on/off/action with `dock_state: fill` (0.10.0 opt-in, not live; from the **jam-cards preview** fixture, whose dock has an extra Air block) | [dark](screens/braun/kiosk-dockstates-fill-dark.png) · [light](screens/braun/kiosk-dockstates-fill-light.png) |

Photos-mode screensaver shots in Braun are not included (the Poster set has one; Braun only changes the time chip).

## Hard constraints
- Kiosk: no scrolling, no continuous animation (minute-tick clock, transform/opacity only), 44 px targets, contrast
  >= 4.5:1, nothing under 18 px on kiosk home screens.
- Text at least 15/13/12 px (labels >= 12, chips >= 13). Everything at a glance.
- **Kiosk sizes**: living room iPad **1024×768** and kitchen Echo Show 8 **961×601** CSS px, landscape, with no scrolling at either size.
  Read from ~3 m: text needs ~120 px to be read at a glance and ~65 px to be read at all, so only the clock clears it. Colour,
  shape and position carry the rest.
- **Echo Show 8**:
  - Weak hardware: MediaTek MT8163, 4 × 32-bit ARM cores, 1 GB RAM.
  - Android System WebView **139** (an earlier note in jam-home SPEC.md says 146; the device notes and the theming plan say 139).
  - No Google Play services. CPU saturation was seen earlier.
  - Look effects (`--jam-fx`) must be off there (`fx: false`).
- **ShowKiosk URL drift**: ShowKiosk's scheduled recovery keeps resetting the Echo Show's start URL to `/?kiosk` (the
  default dashboard) instead of `/jam-kitchen/home?kiosk`. It was reset by hand on 10-30, 10-31 and 11-03. Any kiosk
  design must survive being loaded at the wrong URL, and the fix belongs in ShowKiosk.
- iPad (PadKiosk) runs WebKit 17 (container queries, `:has`, clip-path OK). It is offline until it is jailbroken again.
- HA themes can't read entity state, so stateful styling lives in card code. card-mod only for the header and tabs.
- Fonts OFL, self-hosted (`/hacsfiles/jam-cards/fonts`). Original dashboards are never edited. Any HA change needs Isaac's OK.

## What Isaac has said
- Liked: "Tv card looks way better!", "Speaker card looks great", "Full height looks great!", "I like all the cards and
  dashboard layouts, but want to experiment with some new looks"
- Rejected: "Braun is kinda boring so far. I think we can incorporate a little more color.", "the cards have lost a lot of
  readability", "The kiosk music is ugly try again", "Don't start on Nerv or Lcars"
- Asked for: "emphasize clarity without ever sacrificing fun ... You may have to make some dramatic changes.", "The look
  picker should just affect the user who's using it"

## Open questions for the bible
1. **Hi-Fi vs the 10 Jam looks**: does Hi-Fi become an 11th Jam look (a theme + look pack next to JamBoard), replace
   Poster as the default, or set rules that every existing look must meet? Which existing looks survive?
2. **State grammar**: Jam Cards 0.10.0 already has one (on = strongest fill, off = quiet, lock never "on", Offline =
   broken form, `data-state`/`data-alert` hooks). Should the bible adopt it as is, so other projects (Jam-Dash,
   Callsheet, JamFin) share the same on/off/offline/alert words and hooks, or define its own?
3. **Kiosk legibility floor at ~3 m**: is the 18 px floor (kiosk home) enough, or should the bible set a glance size
   (~65 px readable, ~120 px at a glance) for the one or two facts a kiosk must show from across the room (door, what's on)?
4. **Per-user look vs one house look**: Isaac wants the picker to affect only the user who uses it, but kiosks run on
   their own accounts and pin themes per view. Does the bible define one house look for shared screens, with per-user
   looks only on personal devices?
5. **Idle colour rule**: the audit found colour spent on idle things (Play keys, volume rocker, "⋯", idle art). Should
   the bible say "colour only for on or selected; idle stays neutral" in every look, including room accents on headings?
6. **Room colours vs signal colours**: may a look reuse a room hue as its signal/alert colour (Braun's living = signal
   orange, Olympia's red = ochre)? Is red reserved for alerts in every look?
7. **Attention surfaces**: should "invisible while all is well, loudest thing on screen while not" (kiosk attention bar,
   screensaver door, house-strip attention) be a bible rule, and should it be on by default rather than opt-in?
8. **Motion on weak devices**: Poster's one-shot stepped motion is allowed on the Echo Show, but looks with effects need
   `fx: false`. Does the bible define a "kiosk-safe" motion tier that every look must ship?
