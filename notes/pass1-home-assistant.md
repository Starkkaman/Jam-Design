# Home Assistant (Jam Theme + Jam Cards) · Pass 1

Mockup: `mockups/pass1/home-assistant.html`. It's interactive. Page controls:
- **Cards and spec:** Day / Night. This sets the card library and the shared spec. The theme sheet always shows both.
- **Front door:** Locked / Unlocked. This shows the alert state on every card, strip and kiosk.

The page has three sections:
1. **Theme sheet.** Day and night token panels that read their own CSS variables and compute contrast live, plus a shared spec: type, radii, spacing, elevation, state words, indicator windows, motion curves and the HA key map.
2. **Card library.** Twelve card types at real phone size. Every popup works.
3. **Dashboards.** Phone 390 × 844 (Living view), living-room iPad 1024 × 768 and kitchen Echo Show 961 × 601, each in Day and Night. Dock blocks open kiosk sheets.

A list of differences from Jam Braun today closes the page.

Sources read:
- `notes/OVERNIGHT-BRIEF.md`, `BIBLE.md` 0.5, `CHANGES.md` A–D, and the last ~85 lines of `decisions.md`.
- `notes/pass1-tv-launcher.md`, `pass1-callsheet.md` and `pass1-jamfin.md`.
- `projects/jam-home/README.md`, especially "Jam Braun look".
- About a dozen `screens/braun/` shots (phone Living/Master, light popup, TV source, kiosk homes, unlocked, sheets, dock fill) and the Poster `desktop-control` shot for inventory.
- Mockups 11, 12 and 13, and `_hifi-base.css`.

All content is sample data in the jam-home harness style. The clock is fixed at Tue 2:30 pm. The names are the ones already in the README screenshots. The camera picture is a flat illustration.

## Research
I ran seven web searches. The results were mostly HA docs, release notes, GitHub READMEs and community threads. Lines marked *(knowledge)* come from my own knowledge, not from a search.

- **HA sections view, tile card, badges** (web): sections became the default view type in 2024.11. Badges were redesigned in 2024.8 (entity badges, drag to reorder). Since 2025.3 a tile card can show one feature inline. HA's own design guidance gives each control card a clear primary action. A known issue: each tile feature adds height, so cards in a row end up uneven.
  *Lesson:* one primary per card, controls inside the card, and plan card heights so rows line up. Jam Cards already does this, and HA's own wording backs the "one orange per card" rule.
  ([HA tile card](https://www.home-assistant.io/dashboards/tile/), [Dashboard chapter 2](https://www.home-assistant.io/blog/2024/07/26/dashboard-chapter-2/), [frontend #21618](https://github.com/home-assistant/frontend/issues/21618))
- **HA more-info dialogs** (web): in 2023.3 the light dialog put one big brightness control in the centre, with colour temperature, effects and on/off below it. Some users disliked the extra tap for colour, and some found the slider "way too fat".
  *Lesson:* a popup leads with one big fader. Whites and colours must be visible without a second tap, which is why both are on the first screen here.
  ([2023.3 release](https://home-assistant.io/blog/2023/03/01/release-20233), [community thread](https://community.home-assistant.io/t/2023-3-dialogs/541999?page=10))
- **Mushroom** (web): a small set of consistent cards plus chips for top-of-page status, not deep customisation. *Lesson:* the house strip is our chips row, and consistency beats per-card options. ([lovelace-mushroom](https://github.com/fjfricke/lovelace-mushroom), [SmartHomeScene guide](https://smarthomescene.com/guides/mushroom-cards-complete-guide-to-a-clean-minimalistic-home-assistant-ui/))
- **Bubble Card** (web): pop-ups opened by a URL hash, closed by swipe, Esc, removing the hash, or a close button. *Lesson:* Jam's `jam-popup` already uses the hash. All the popups here share one sheet with one Close and Esc. ([Bubble Card](https://www.GitHub.com/Clooos/Bubble-Card))
- **Minimalist themes** (web): Graphite (calm soft dark, clean light), iOS Themes (Apple Home look), Frosted Glass (needs card-mod and a background), Material You, Catppuccin. *Lesson:* the themes people call calm are the ones that only set the palette, radius and shadow. Jam Theme should stay tokens-only, with the behaviour in the cards. ([SmartHomeScene themes](https://smarthomescene.com/blog/best-home-assistant-dashboard-themes-in-2023/), [Frosted Glass](https://community.home-assistant.io/t/frosted-glass-theme-for-home-assistant/914431))
- **Family wall kiosks** (web):
  - Keep the wall dashboard separate from personal ones, with large buttons, almost no scrolling and only what matters.
  - Use one composed view with no navigation.
  - Test on the real device.
  - A thread asks whether the wall should behave like a notification centre ("the home tells you").

  *Lesson:* the Jam Braun kiosk is already this. I kept its structure (clock, door, facts, dock) and made the sheets fill the screen without scrolling.
  ([Aaron Powell: wall dashboards](https://www.aaron-powell.com/posts/2023-08-19-building-a-smart-home---part-13-wall-mounted-dashboards/), ["Are we thinking about wall tablets the wrong way?"](https://community.home-assistant.io/t/are-we-thinking-about-wall-tablets-the-wrong-way/1019690), [best practices thread](https://community.home-assistant.io/t/best-practices-for-building-a-tablet-dash/761729))
- **Dieter Rams / Braun** (web + knowledge):
  - The ET66 (Rams and Lubs, 1987) has round convex keys, a small display at the top and high contrast; colour only marks function. ([V&A](https://collections.vam.ac.uk/item/O1360553))
  - The T3 radio is a white body with a speaker grille and a thumb control.
  - "Less, but better" means reduction plus refinement, not removal alone.
  - *(knowledge)* Braun hi-fi (audio 1, T 1000) groups controls on one face and uses colour only for a signal.

  *Lesson:* one signal colour, controls in rows, the grille as the speaker's face, and the display reserved for the one appliance number.

## Design (what and why)
**Theme and cards as one system.** The theme holds tokens only: colours per mode, type, radii, spacing, elevation and motion. The cards hold behaviour: rockers, windows, faders and states. That matches how Jam already works (`tokens/` generates the theme YAML; cards read `--jam-*`). It also means HA's own dialogs get the colours but never the rockers. The HA key map shows the line between the two.

**Theme sheet (a living spec).**
- Each mode's panel reads its CSS variables, prints the hex values, and computes WCAG contrast for nine pairs. All pass AA in both modes; the tightest is dim on the day page at 4.6:1.
- Each swatch also shows the **Jam Braun** value it replaces. Surfaces barely move (`#e7e3da` → `#e3e1dc`, `#2a2a27` → `#2a2a28`). Signal orange `#f07d1e` → `#ec7c22`. Olive goes; ok becomes a lamp colour only.
- New tokens: window recess, cream, warn and alert **ink** variants for words (not the lamp colours), band key, pressed key.

**Cards (12 types).**
- **Light:** a slot window lit in the light's own colour, name, and state word ("On · Group"). The rocker sits top right and the fader reveals the light's colour. There is **no number beside the fader**: the value rides the fader cap while you drag. Offline is the broken form: no face, dashed edge, "Can't be reached since 9:12 am", rocker disabled.
- **Light popup:**
  - On row with a big slot window and the rocker. The big brightness fader carries its number on its cap.
  - **Five whites (2200–5000 K), each showing its colour in a window.**
  - **Colour keys. Any pick recolours the slot and every fader in the popup, the card it came from, and every copy of that light on the page**, including the dashboards.
  - Group members, each with a fader and a rocker.
  - Turn off in 15/30/60 min.
  - WLED shows effect presets instead of whites.
  - No orange Done: changes apply live, so Close is quiet.
- **Switch:** Tree, Bedroom fan, Blanket, Desk plug (with "42 W" while on). Each is just a glyph, a word and a rocker; **the tree is the same as the fan**.
- **Climate** (sample, since Jam Home has no thermostat): the current temperature is shown once in big type. The target sits in a −/+ stepper (no dial). Modes are pressed-in keys, and a slot plus "Heating" shows what it's doing.
- **TV:**
  - A black ribbed screen band with the **lit power symbol** (green when on).
  - Source name and input.
  - Transport with Pause/Play as the one orange key, plus −/Mute/+.
  - Remote and Source open popups. When off, the orange key is "Turn on".
- **Source popup:** a **3-column tile grid**. The tile on now presses in, lights its slot in its own colour and says "On now". Picking a source updates the TV card and the kiosk dock.
- **Remote popup:**
  - Soft plastic body, with the **IR emitter at the very top that flashes solid red on every press** (no bloom).
  - **Lit power symbols** for the TV and the stereo.
  - Plain plastic d-pad ring with an orange OK, Back/Home/Menu/Setup, and transport.
  - Stereo section with −/Mute/+ and inputs TV/Turntable/Music sync as keys with square windows.
- **Speaker:**
  - The Braun grille, where the one special dot is now a **window that lights cream while playing** (it used to be an orange decoration).
  - Group label, track, Play as the one orange key, and volume with no number.
  - **A speaker key opens the popup straight onto Group or split**: rockers per speaker, with Living room fixed as "This speaker". The popup also has now playing and a pinned shelf.
- **NerveOS:**
  - **One clean row**: ribbed NV mark, name, "Playing · Hades II", a running slot, and a quiet ⋯ (no longer orange).
  - Its popup: Sleep, Quit game, Mute, volume and a small PC remote.
  - On the kiosk TV sheet it's an inline panel.
- **Appliance:** the air purifier as Isaac liked it (grille, seven-segment PM2.5, round power key with a lit symbol, speed keys with square windows), plus a Dehumidifier sibling (RH, "Dry to" 45/50/55). The word now says "Running", not "Running · 25 %", because the pressed key already shows the speed. **These are the only seven-segment displays.**
- **Sensor:** the current value in plain Jost, and a flat 24 h line on hairline grid (I dropped the chart-recorder paper, B7). Its popup has 24 h / 7 d / 30 d keys, a bigger graph, and Low / High / Average.
- **Scenes:** keys with square windows. The chosen one presses in and lights cream (it's ET66 yellow today).
- **House + people:**
  - The house strip is a black ribbed band: inside, outside, door chip (red-ringed "Door unlocked · Lock" when unlocked, one tap to lock), and people chips with LEDs.
  - "Who's home" rows use initials, never faces.
  - I dropped the strip's "Air · …" word, because the purifier shows the same air reading on the Living view.
- **Doors & windows:** LEDs for locked and closed. An open window is an amber slot plus "Open · 25 min". When the front door is unlocked, it shows a red LED, the word "Unlocked" and an orange **Lock** key (the row's one action).
- **Camera** (sample): a 16:9 picture with Live (lit slot) and "Motion 2 min ago" tags. Its popup has Snapshot, Full screen and today's events.

**Dashboards.**
- **Phone Living:**
  - HA tabs with a base-window slot under each tab, lit under the current one.
  - House strip.
  - Walnut rule + "Living room" + temperature/humidity chips.
  - Scenes, then a 2×2 of Living room, Kitchen lamp, TV light and Tree.
  - Air purifier, TV, the NerveOS row and the speaker. It scrolls inside the frame like the live view.
- **Kiosks:** Jam Braun's kiosk structure is unchanged:
  - Walnut rule; the lock disc top right with a word + LED under it.
  - Big Jost 300 clock (168 px iPad / 124 px Echo) with a dim colon.
  - Date, the facts line, and the outside weather on the right.
  - The **dock is a black ribbed band**. Its blocks have the indicator window in the top-right corner (Isaac's v3 note): an LED for Lights, slots for TV and Music. Echo's "All off" is an outlined action block with a tap-again confirm.
  - Unlocked turns the disc solid red, and a tap locks it.
- **Kiosk sheets** fill the screen and never scroll:
  - iPad Lights: scenes, purifier and All lights off on the left; a 2×2 of tall light cards on the right.
  - iPad TV: TV card + NerveOS panel.
  - iPad Music: a wide speaker with the grille and a pinned shelf.
  - Echo Lights: 3 tall light cards + All lights off.
  - Echo Music: a wide speaker.
- **Kiosk popups** use the same sheet, inset, in two columns.

**One layer system.** Popups open inside the device that asked: a bottom sheet on the phone, an inset two-column sheet on a kiosk, a centred bottom sheet over the page for the library. Close sits top right, and Esc or the veil closes it.

## Audit
I checked with Playwright (Chromium):
- Page widths 1480 (light scheme) and 390 (dark scheme).
- Every popup from the library.
- The kiosk sheets and their popups on both kiosks, plus the phone speaker group popup.
- Day mode, and the door unlocked.

Results: no JS errors, no horizontal scroll at 390, no text under 12 px in the library or spec, nothing under 18 px on kiosk homes, and no kiosk sheet or kiosk popup taller than its screen.

The fix pass corrected:
- The overlay host never being removed (it blocked every click after the first popup closed).
- The phone header pushing the screen to 395 px wide.
- The kiosk sheets using only half the screen.
- The iPad remote overflowing by 87 px.
- The spacing swatches using orange.
- The indicator demo wrapping.
- The sticky control bar eating 150 px at phone width.

| # | Problem | Severity |
|---|---|---|
| 1 | **Orange count on the phone Living view.** Four lit rockers (Living room, Kitchen lamp, TV light, Tree) plus Pause on the TV and Play on the speaker make six orange marks on one screen. Each card has only one, as the rule says, but the screen reads orange-heavy, which is exactly the "too much orange" note. | High |
| 2 | **Lit lights lost their tint.** Jam Braun's light-colour card tint came from Isaac's "Braun is kinda boring… more color". Here the colour lives only in a 10 × 22 slot and the fader (B1/B3). At arm's length the phone grid looks much greyer than today. | High |
| 3 | **No number by the faders.** This follows the "never the same value twice" rule. But Jam Braun's "75%" was glanceable, and here a kiosk at 3 m can only judge brightness from the fader length. | Medium |
| 4 | **Alert vs primary on the kiosk lock.** Unlocked, the disc is solid red and is also the control (tap to lock). The doors card uses an orange Lock key with a red LED instead. Two grammars for the same fix. | Medium |
| 5 | **Tall, empty kiosk light cards.** Filling the screen made the iPad and Echo light cards 200–290 px tall, with the fader far from the name. They make good targets but look unfinished. | Medium |
| 6 | **Day kiosks: the black dock band is a big dark slab** at the bottom of a warm-white screen. That's a strong change from Jam Braun's soft tinted blocks, and from across the room it pulls the eye more than the clock does. | Medium |
| 7 | **Source tiles are grey until chosen.** Only the tile on now shows its colour (colour discipline). Jam Braun shows a coloured dot on every tile, and "tile grid with coloured slots" could mean every tile shows its colour. | Medium |
| 8 | **HA's own dialogs** (more-info, confirm) only get the theme. Their switches are pills in `primary-color` orange, not rockers, so a tap on an HA built-in shows a second control grammar. | Medium |
| 9 | **Appliance cards are more realistic than their neighbours** (gradient body, inset highlights, feet-less but moulded). Isaac kept the purifier, but this breaks BIBLE §3 rule 5. | Medium |
| 10 | **Tabs:** an unlit window under every HA tab reads as a row of black dashes in Day. | Low |
| 11 | **Speaker grille window:** unlit, it's the darkest dot on the card and reads like a hole. | Low |
| 12 | **Kiosk "Lights · 4 on" counts the Tree** (a switch), as Jam Braun does. That's inconsistent with "the tree is a switched device". | Low |
| 13 | **Offline lights have no popup.** That breaks "every light card has a popup". It should open a small sheet with "Can't be reached since…" and Retry. | Low |
| 14 | **Climate and Camera are samples.** Jam Home has neither in its inventory, so their layouts aren't checked against real entities. | Low |
| 15 | **All off uses "tap again" inline** (3.5 s) instead of HA's confirm dialog. It's faster on a kiosk, but it's new behaviour. | Low |
| 16 | **Kiosk sheet keys are 17 px.** That's over the 12 px minimum, but under the kiosk body 18. | Low |
| 17 | **Rocker visuals are 28 × 42.** The hit area is padded to about 46 × 46, but the visual is still narrow in the dense phone 2×2. | Low |
| 18 | **Fonts:** switching Archivo → Jost + Plex Mono adds two self-hosted families. Their cost on the Echo Show's WebView isn't measured. | Low |

## Change suggestions for the next pass
- **Orange:** try three rocker paddles side by side:
  - (a) orange as now;
  - (b) a graphite paddle with a small lit window on the paddle (cream, or the light's colour) and orange kept only for the primary;
  - (c) orange only on the paddle's top edge.

  Count the orange marks per screen for each.
- **Light colour:** try a 6–8% light-colour wash on the fader's side of a lit card, or a full-height slot on the card's left edge, to win back some of Jam Braun's colour without the full tint.
- **Brightness at a glance:** show the value on the fader cap permanently on kiosks only (like the big popup fader), and test it at 3 m.
- **Kiosk lights sheet:** use vertical faders (still a fader, allowed) in tall cards so the height means something. Or go 3 across with scenes on top.
- **Day dock:** compare the black ribbed dock with a card-coloured dock that keeps the per-block windows. Ask Isaac.
- **Source tiles:** try a printed colour tab on every tile (not a light) plus a lit slot on the chosen one.
- **Lock:** pick one grammar. Proposal: alert red is the control when the control fixes the alert (disc, house chip). Use the orange Lock key only where the row isn't itself red.
- **HA built-ins:** try card-mod or theme keys so HA's more-info switches read as quiet (ink track, orange thumb only when on), and check HA's real light-domain colour keys.
- Design the offline light sheet, the WLED popup in full, the Master view (dehumidifier, fan/blanket) and Jam Control at 1280.
- Measure Jost + Plex on the Echo Show (first paint, CPU).

## Differences from Jam Braun today
1. **Font:** Archivo → Jost (words) + IBM Plex Mono (small numbers).
2. **Toggles → rockers:** the olive pill toggle becomes an up-is-on rocker with an orange paddle. Olive leaves the palette.
3. **Lit lights:** no card tint. The light's colour is in a slot window and the fader.
4. **No numbers by sliders:** "75%" and the "40" volume go. The value rides the fader cap while you drag, and sits on the big popup fader's cap.
5. **Chosen keys press in:** the scene (ET66 yellow today) and the purifier speed (orange today) become pressed-in keys with a lit square window.
6. **Less orange:** NerveOS ⋯, the scene pill and the grille dot stop being orange. Play and Turn on stay orange.
7. **Room colours retired:** a walnut rule on every room heading. The kiosk dock is a black ribbed band with an indicator per block, not room-tinted blocks.
8. **Black ribbed bands:** house strip, TV screen, kiosk dock.
9. **Kiosk clock colon:** orange → dim.
10. **Air purifier:** the small appliance (grille, seven-segment PM2.5, round power key). The house strip drops its air word.
11. **TV sources:** still a 3-column grid; the one on now presses in and lights its own colour (no yellow fill).
12. **Popups:** one shared sheet (Close top right, no orange Done). Five whites with their colours; Group or split on the speaker; NerveOS has its own sheet.
13. **Shape:** keys go from pills to 12 px; chips stay pills; card corners go from 14 to 16 px.

## Bible implications
1. **§2 Materials → Braun-based tokens.** Replace the alu/card/band values with the Jam Theme set shown in the mockup:
   - day `#e3e1dc` / `#f1efeb` / `#e6e3de`;
   - night `#1c1c1b` / `#2a2a28` / `#353533`;
   - plus window recess, cream, band key and pressed key;
   - and separate **lamp** vs **word** colours for ok/warn/alert (`warn-ink`, `alert-ink`).
2. **Orange counting.** Define "one primary per card; at most one per popup or sheet". Paddles count separately. Decide whether a screen-level cap applies (audit 1).
3. **Faders carry their own number.** No number next to a fader. The value rides the cap while you drag, and a big (popup or kiosk) fader may print it on the cap. This extends D15.
4. **"Never twice" scope.** Decide whether a "panel" means a card or a whole view. The house strip's air word vs the purifier's PM2.5 is the same reading twice on one view.
5. **Alert outranks primary.** When one tap fixes an alert (lock the door), that control is drawn in alert red, not orange. This is the second exception to "orange = the action".
6. **One popup sheet for every device.** Phone: bottom sheet. Kiosk: inset, two columns, no scroll. Page: centred. Close top right, Esc and the veil close it. No orange Done when changes apply live.
7. **Kiosk no-scroll covers sheets and popups**, and kiosk sheets stretch to fill the screen.
8. **A light's colour lives in its slot window and fader** (confirms B1/B3). The card tint is retired. Pending audit 2.
9. **Base-window selector on HA's top tabs** (extends D12). Decide whether unselected tabs show the unlit recess.
10. **Kiosk dock = black ribbed band**, with the indicator window in each block's top-right corner and action blocks outlined. Records the v3 decision as a bible rule.
11. **HA built-ins get colours only.** `primary-color` = orange and `accent-color` = ink, so HA doesn't add a second orange. Accept HA's own switches as the one place without rockers, or card-mod them.
12. **§3 rule 5 exception for appliance cards.** The kept air purifier is deliberately more object-like than its neighbours. Name the exception: appliances only, with seven-segment.
13. **Decorative motifs may hold one indicator.** The speaker grille's single dot becomes a window that lights while playing, instead of a decorative orange dot.
14. **Type in HA:** Jost + IBM Plex Mono replace Archivo when Hi-Fi rolls out to HA, self-hosted from `/hacsfiles`. Kiosk sizes: clock 168/124, card title 22, body 18, label 13.
15. **Offline lights still open a sheet** ("Can't be reached since…", Retry), so "every light card has a popup" has no exception.
