# Home Assistant (Jam Theme + Jam Cards) · Pass 3 of 3

Mockup: `mockups/pass3/home-assistant.html` (new; pass 1 and pass 2 files unchanged).

Pass 3 is about settling. The page shows **one recommended build** everywhere by default. Pass 2's options are still there, but only in section **4 Compare**. A badge in the sticky bar says "Recommended build", or "Custom: …" with a **Back to recommended** button.

Page controls:
- **Sticky bar:** Cards Day / Night (Day is now the default), Door Locked / Unlocked, and the build badge.
- **Compare panel:** Paddle (Quiet / Adaptive / Orange), Primary (1 per screen / 1 per card), Light colour (Band / Edge / Wash), Day track (Light groove / Dark), Whites (Pass 3 / Pass 2), Paddle window (18 × 7 / 10 × 4), Day dock (Cards / Black band). The first choice in each is the build.

Sections:
- **0 The build:** what pass 3 settled, each with what it was in pass 2.
- **1 Theme:** tokens, contrast and the new light display colours table, all computed live.
- **2 Cards:** the library, with every popup.
- **HA dialogs:** HA's own dialogs, using keys verified in the source.
- **3 Dashboards:**
  - phone Living Day and Night, phone Music (Day) and Master (Night);
  - iPad home, Lights sheet, and TV / Music sheets;
  - Echo home and Lights sheet.
- **4 Compare:** three side-by-sides: orange count, light colour, and day tracks plus whites.
- **5 Rollout:** what a rollout would change, card by card.

## What changed since pass 2

**High: day fader tracks were heavy black bars. Fixed.**
- A long track (phone fader, volume, kiosk column) is now a **light groove pressed into the card**: `#d9d5cd` with an inner shadow, close to Jam Braun's grey track. It is still a recess ("window = recess" holds), just in the card's own material. Night keeps the dark recess.
- Small windows stay dark in both modes: LEDs, square, slot, and the paddle window. These are lights that must read lit or unlit from across a room.
- Fader caps are light plastic `#fbfaf7`, so they show on the groove. Volume fills with a deeper cream by day (`#ead7a6`).
- Compare C shows pass 2 (black) and pass 3 (groove) on the same lights.

**Medium: warm whites read orange. Fixed in two ways.**
1. **Display whites.** The five whites are drawn on an amber-to-cream line:

   | White | Pass 2 | Pass 3 |
   |---|---|---|
   | Cozy | `#ffb565` | `#f4ca8a` |
   | Warm | `#ffcf94` | `#f4d8a4` |
   | Neutral | `#ffe8c9` | `#f2e4c6` |
   | Clean | `#fff3e3` | `#efebe1` |
   | Daylight | `#eef3ff` | `#dbe6f9` (more chroma so it doesn't go grey) |

   HA still stores the kelvin; this is only how Jam draws it.
2. **Orange guard.** Any light colour closer than 0.15 (OKLab ΔE) to either control orange (day `#ec7c22`, night `#f08a2c`) is mixed toward cream until it isn't.
   - Pass 2's Cozy was 0.11 from orange. Pass 3's Cozy is 0.15.
   - An Amber pick (`#ff9a5a`, 0.05) is drawn as a peach.
   - The same display colour is used in the slot, paddle window, band, fader and preset swatch, so "presets show their colours" and "colour picks recolour the slot" still match exactly.
   - The theme sheet computes the table live.

**Medium: the quiet paddle window was too small. Fixed.**
- The window on an on paddle is now **18 × 7 (15 × 4 lit)**, and 20 × 8 on kiosks. It was 10 × 4.
- Switched devices (Tree, fan, blanket, plug) now **dim their name and glyph when off**, like lights. On switch cards the paddle is no longer the only cue.

**Medium: the speaker's Play lost its primary while the TV played. Fixed by placement, not by a new exception.**
- The one-per-screen rule stays.
- The losing main key becomes a **resting primary**: same place, same 1.6× width, and a bigger glyph (22 px).
- Play is orange in four places:
  - on a new phone **Music** tab, one card per player;
  - in the speaker popup;
  - on the kiosk Music sheet;
  - as soon as the TV stops.
- Measured: Living view = 1 orange mark (Pause); Music tab = 1 (Living room Play).

**Medium: adaptive paddles changed look. Fixed as an option.**
- Adaptive now decides once, when a view opens. Turning a third light on no longer restyles the first two.
- It stays a Compare option, not the build.
- The general rule is now "no control restyles another".

**Medium: the kiosk Lights sheet's left column was phone-sized. Fixed.**
- The left column is 350 px wide.
- Scene keys are 20 px text and 60 px tall, in a 2 × 2.
- The Tree row has a 48 px glyph.
- The purifier is at kiosk scale: 30 px seven-segment, 22 px name, 16 px speed keys 60 px tall, and a 56 px power key.
- All lights off is 20 px, 64 px tall.
- Nothing scrolls (checked).

**Medium: HA theme keys were unverified. Verified, and one was wrong.**
I read HA's frontend source at release tag `20260930.5` (HA 2026.10) and `dev`, through `raw.githubusercontent.com`. Details are under Research.
- Pass 2's `switch-checked-*` keys are **not read by any component** any more.
- The working keys are `ha-switch-checked-*`, the `ha-color-primary-*` ramp, and `state-<domain>-active-color`.
- Pass 2's cream for the big more-info toggle is invisible on a Day card (1.1:1). Day uses ink.

**Lows fixed on the way:**
- **Night Band:** 30 % on a lifted base (`#3b3a37`), not 24 % on the card, so warm whites read lit, not brown.
- **Kiosk column at 0:** the cap shows "OFF" (it used to be blank).
- **Echo:** the offline Stove lights collapses to a 230 px column at the end, with no inner dashed box.
- **Unlocked house strip:** only the Lock key is red. The "Door unlocked" chip is band ink with a red LED.
- **Kiosk Music sheet:** the grille has 18 even rows (it had 5 stretched ones).
- **Library:** the intro now says each card is drawn as if alone on its screen.
- **Page chrome:** the sticky bar is one row (pass 2's was two rows, 126 px).

**Kept unchanged:**
- The air purifier ("came out great") and the dehumidifier, the only seven-segment displays.
- The remote: soft plastic, red IR emitter at the top, lit power symbols.
- The TV source tile grid with printed colour tabs.
- The speaker's Group or split.
- The Tree as a switched device.
- A popup on every light and media card.
- No brushed metal, no glow, no grain.

## Research
Light, and only to fill gaps.
- **Web searches (3):** they gave community threads only, no official docs.
- **Source reads:** HA's frontend repository through `raw.githubusercontent.com` with curl, plus a `gh` code search. These worked.

**Findings, read in source (HA frontend `20260930.5` = HA 2026.10, and `dev` on 2026-11-05):**
- **`ha-switch`** (`src/components/ha-switch.ts`):
  - It reads `--ha-switch-checked-background-color`, `--ha-switch-checked-border-color` and `--ha-switch-checked-thumb-background-color`, plus `-hover` variants.
  - Fallbacks: `--ha-color-fill-primary-normal-resting` and `--ha-color-on-primary-normal`.
- **`switch-checked-color` / `-track-color` / `-button-color`:** a `gh` code search finds them only in HA's demo theme configs, not in components.
  - *Lesson:* pass 2's keys would do nothing. Drop them.
- **More-info big toggle** (`ha-state-control-toggle.ts`): `--control-switch-on-color` is `stateColorCss(stateObj, "on")`, which resolves `state-<domain>-active-color`. The defaults are amber for both light and switch.
- **`ha-control-switch`:** draws its background in the on colour at 0.2 opacity.
  - *Lesson:* the on colour must contrast with the card. Cream on a day card is 1.1:1, so Day uses ink.
- **Light more-info slider** (`ha-state-control-light-brightness.ts`): `--control-slider-color` is the state colour. When the light has `rgb_color`, it uses that colour with HSV adjusted "for better contrast".
  - *Lesson:* HA draws the light's real colour. A theme can't apply Jam's display whites there.
- **Theme ramp** (`color.globals.ts`, `semantic.globals.ts`):
  - `--primary-color` defaults to `var(--ha-color-primary-40)`.
  - The loud fill is `--ha-color-fill-primary-loud-resting: var(--ha-color-primary-40)`. Normal and quiet fills use `-90` / `-95` (light) and `-10` / `-05` (dark).
  - `--ha-color-text-link` is also `-40`.
  - *Lesson:* setting `primary-color` alone doesn't recolour `ha-button`. Jam Theme must set the ramp. A 2025.8 community thread reports the same.

**Kelvin colours** *(knowledge)*: the usual blackbody approximation (Tanner Helland's) puts 2200 K near `#ff932c`, which is effectively orange.
- *Lesson:* an honest kelvin colour *is* orange. The display whites are a deliberate perceptual mapping, not physics, and that's why it has to be a rule.

Sources:
- [ha-switch.ts](https://github.com/home-assistant/frontend/blob/dev/src/components/ha-switch.ts)
- [ha-state-control-toggle.ts](https://github.com/home-assistant/frontend/blob/dev/src/state-control/ha-state-control-toggle.ts)
- [ha-state-control-light-brightness.ts](https://github.com/home-assistant/frontend/blob/dev/src/state-control/light/ha-state-control-light-brightness.ts)
- [semantic.globals.ts](https://github.com/home-assistant/frontend/blob/dev/src/resources/theme/color/semantic.globals.ts)
- [color.globals.ts](https://github.com/home-assistant/frontend/blob/dev/src/resources/theme/color/color.globals.ts)
- [2025.8 theme colour thread](https://community.home-assistant.io/t/home-assistant-2025-8-0-frontend-additional-theme-color/918262)
- [state colour fallback thread](https://community.home-assistant.io/t/change-default-orange-to-green/849796)

## Design (what and why)
- **One build, options behind a panel.** Isaac reviews one thing. Every pass 2 option is still one click away, and the badge makes it obvious when he's looking at something other than the build.
- **Small windows dark, long tracks light.**
  - A small window's job is to read lit or unlit from across the room, so it needs the dark rim.
  - A track's job is to show *how much*, and a black bar shouts "nothing here" louder than the fill says "this much".
  - Making the track a groove keeps the recess idea (pressed in, inner shadow) without the slab. This is the Jam Braun look Isaac likes.
- **Display colour is a rule, not a palette.**
  - Light colours will keep arriving from HA and from colour picks.
  - The guard means no light can ever impersonate the orange key, whatever someone picks.
  - The same value everywhere means presets still "show their colours".
- **The orange stays a screen budget.** I didn't give media an exception, because "two oranges when two things are media" brings pass 1's problem back. Instead, music has a place where it's always the primary (the Music tab, popup and sheet). The losing key keeps its size, so muscle memory works.
- **Kiosk = kiosk size everywhere on the sheet.** The 18 px floor was written for kiosk homes, but sheets are where people press things from across the room. Pass 3 applies it to sheets too.
- **HA's own dialogs by keys only.** No card-mod in dialogs. The one honest gap: HA's light slider shows the real colour.

## Audit
Checked with Playwright (Chromium, `chromium.launch()` with no options), screenshots in the scratch dir:
- 1480 px (light scheme) and 390 px (dark scheme).
- All 14 dashboard figures.
- Every dock block on every kiosk opened, then 30 popups opened inside kiosk sheets (light, source, remote, speaker, PC): 62 kiosk sheets and popups checked.
- Library popups (light, offline light, source, remote, speaker, PC, history).
- Night + unlocked.
- Every Compare switch, then Reset.

Results:
- **No JS errors.**
- **No horizontal scroll** at 1480 or 390.
- **No page text under 12 px.**
- **Nothing under 18 px on kiosk homes.**
- **No kiosk sheet or popup scrolls or overflows its screen** (0 of 62).
- **Orange marks** (measured):

  | View | Marks |
  |---|---|
  | Living | 1 |
  | Music | 1 |
  | Master | 0 |
  | Living, door unlocked | 0 (the red Lock key takes the slot) |
  | Compare A / B / C | 6 / 2 / 1 |

- **Badge:** goes Custom after option changes and back to Recommended on Reset.

The fix pass corrected:
- A JS syntax error (an unescaped apostrophe).
- The red text on the unlocked word chip (two reds).
- The double dashed box on the Echo's offline column.
- The stretched 5-row grille on the kiosk Music sheet.
- The "Orange budget (pass 2)" heading.

| # | Problem | Severity |
|---|---|---|
| 1 | **The day groove and the cream fill are almost the same lightness.** Luminance contrast: volume fill `#ead7a6` vs groove `#d9d5cd` 1.03:1, Cozy fill 1.05:1. The level reads by hue (warm vs grey) and by the cap. A colour-blind viewer, or a phone in sun, gets mostly the cap. Next step: a slightly darker groove (`#cfcac1`, ~1.4:1 vs card) or a 1 px darker rim on the fill's end. | Medium |
| 2 | **HA's own light dialog shows the real kelvin colour.** HA nudges it for contrast, but a 2200 K light still fills its slider orange-ish, so the display-whites rule stops at HA's dialogs. A theme key can't fix this; only card-mod could. | Medium |
| 3 | **The `ha-color-primary-*` ramp reaches more than dialogs.** `ha-color-primary-40` is also HA's link colour and the sidebar selection, so HA's own settings pages get orange links. Verified in source but not rendered in a real HA. Needs a harness run on 2026.10. | Medium |
| 4 | **Display ≠ reality for picked colours.** An Amber pick lights the lamp amber, but Jam draws a peach slot. That's on purpose (the orange guard), but someone could read it as the wrong colour. The popup says so in one line. | Medium |
| 5 | **The guard is hue-blind.** OKLab distance alone also lightens clearly non-orange picks such as the pink `#ff6f8a` (0.125). A hue-aware rule (e.g. only hues 35–75° in OKLCH) would be more precise. | Low |
| 6 | **Clean 4000 K and Daylight barely tint the Band by day.** Near-white light on a near-white card gives a band you can hardly see; the slot and paddle window carry it. | Low |
| 7 | **On the Living view Play stays a resting key while the TV plays.** It follows the rule, and the Music tab answers it, but it depends on Isaac agreeing (Question 1). | Low |
| 8 | **Three "on" cues on a lit light card** (slot, paddle window, band) plus the word. This is state, not a value, so "never twice" isn't broken, but it's more than Jam Braun's one LED. | Low |
| 9 | **"Spooky vibes" wraps to two lines** on the iPad sheet's 2 × 2 scene keys. | Low |
| 10 | **The NerveOS popup on the iPad is half empty** (two short columns on a full sheet). | Low |
| 11 | **The purifier is still on the Lights sheet.** It isn't a light (as today in Jam Braun). Question 5. | Low |
| 12 | **The offline Echo column still draws a disabled rocker.** It could drop it to save width. | Low |
| 13 | **Frozen adaptive paddles** (option only) can look stale until the view reopens. That's the cost of not restyling untouched controls. | Low |
| 14 | **Climate and Camera are still samples** that aren't in Jam Home's inventory. | Low |
| 15 | **Jost + Plex Mono cost on the Echo Show WebView** is still unmeasured. | Low |
| 16 | **The library still shows per-card primaries** (labelled). | Low |

## Differences from Jam Braun today (recommended build)
1. **Font:** Archivo → Jost (words) + IBM Plex Mono (small numbers), self-hosted.
2. **Toggles → rockers:**
   - The olive pill becomes an up-is-on rocker.
   - On = paddle up + an **18 × 7 lit window on the paddle**, in the light's display colour (cream for switches).
   - The paddle is never orange, and olive leaves the palette.
3. **Lit lights:**
   - The whole-card tint (18 % / 24 %) becomes a **tinted fader band**: 30 % on the card by day, 30 % on a lifted base at night.
   - The colour also shows in the slot by the name, the paddle window and the fader. Off cards stay plain.
4. **Light colours:** whites are drawn on an amber-to-cream line, and any colour near the control orange is drawn lighter. Today Jam Braun paints the light's raw colour.
5. **Slider tracks:** Jam Braun's 4 px grey strip with an orange fill becomes an 8 px **light groove**. Lights fill in their display colour, volume in deeper cream. The cap is light plastic. Night tracks are a dark recess.
6. **Numbers by sliders:**
   - Phone: "75%" and the volume "40" go; the value rides the cap while you drag.
   - Kiosks: light faders become tall columns with the number on the cap ("OFF" at 0).
7. **Chosen keys press in:** the scene (ET66 yellow today) and the purifier speed (orange today) become pressed-in keys with a lit square window.
8. **Orange: about six marks → one per screen.**
   - The one goes to what's happening (Pause on the playing TV).
   - Play is orange on the Music tab, in the speaker popup and on the kiosk Music sheet.
   - The losing main key keeps its place and size.
9. **Room colours retired:**
   - A walnut rule on every room heading.
   - Dock blocks lose their room tints. Day: card blocks with an indicator window. Night: the black ribbed band.
10. **Black ribbed bands:** the house strip, the TV screen and the night dock.
11. **Kiosk clock colon:** orange → dim.
12. **Unlocked door:**
    - The kiosk disc stays solid red.
    - The phone chip becomes a word chip with a red LED, plus a solid red **Lock** key.
    - The doors row uses the same red key.
13. **Air purifier:** the small appliance (grille, seven-segment PM2.5, round power key with a lit symbol). The house strip drops "Air · Poor".
14. **TV sources:** still a 3-column grid with a printed colour tab on every tile. The one on now presses in and lights its slot (no yellow fill).
15. **Popups:**
    - One shared sheet: Close top right, no orange Done.
    - Five whites shown in their display colours.
    - Group or split on the speaker.
    - NerveOS gets its own sheet.
    - Offline lights get a Try again sheet.
16. **Kiosk Lights sheet:**
    - Controls at kiosk size (20 px keys, 60 tall).
    - Light columns.
    - On the Echo, an offline light shrinks to a narrow end column.
    - "Lights · N on" no longer counts the Tree.
17. **Switched devices:** name and glyph dim when off.
18. **HA's own dialogs:**
    - Small switches: dark track + cream thumb.
    - Big toggles: ink by day, cream at night.
    - Orange only on the confirm button.
    - These come from the `ha-switch-checked-*`, `state-*-active-color` and `ha-color-primary-*` keys.
19. **Phone tabs:** Living / Kitchen / Master plus a **Music** tab.
20. **Shape:** keys go from pills to 12 px corners; chips stay pills; cards go from 14 to 16 px corners.

## Questions for Isaac
1. **When the TV is playing on the Living view, should the speaker's Play ever be orange as well as (or instead of) Pause?**
   *Recommendation:* no. Keep one orange per screen, with Pause winning. Play is orange on the Music tab, in the speaker popup and on the kiosk Music sheet, and stays the same size on Living.
2. **Day slider tracks: light groove (like Jam Braun) or pass 2's black recess?**
   *Recommendation:* the light groove, made slightly darker in the next build pass (audit 1) so the fill reads without relying on colour.
3. **Is it OK that warm whites are drawn paler and more yellow than the bulb really is (Cozy as pale amber), and that a colour pick near orange is drawn lighter?**
   *Recommendation:* yes. The lamp still gets the exact colour; only the drawing changes, so a light can never look like the orange key.
4. **A lit light's colour: Band, or Wash (closest to today)?**
   *Recommendation:* Band. Wash makes a room of warm lights a peach block, and you said you like the calm.
5. **Should the air purifier stay on the kiosk Lights sheet (as today), even though it isn't a light?**
   *Recommendation:* keep it there, at kiosk size. It's the room's other "comfort" control, and moving it would need a fourth dock block.
6. **Rockers are never orange, even when on (Jam Braun today: olive toggles; pass 1: orange paddles). OK?**
   *Recommendation:* yes, quiet paddles with the lit window. It's the biggest single cut in orange.
7. **HA's own dialogs: theme keys only (dark switches, ink/cream toggles, orange confirm), accepting that HA's light slider shows the bulb's real colour?**
   *Recommendation:* yes. No card-mod inside HA's dialogs, because it breaks on HA updates.
8. **Fonts: Jost + IBM Plex Mono replace Archivo when HA's turn comes?**
   *Recommendation:* yes, if a first-paint test on the Echo Show is within ~100 ms of Archivo. Otherwise keep Archivo for the kiosks only.

## Bible implications (final form)
1. **Orange budget is per screen.**
   - One orange primary per screen; a popup or sheet is its own screen.
   - It goes to what's happening (playing > on > idle, then page order).
   - Other main keys "rest": same place, same size, plain key.
   - This replaces A4's "one per card" and answers D39/D82.
2. **Rocker paddles are never orange.** On = paddle up + an 18 × 7 lit window on the paddle (20 × 8 on kiosks), in the device's display colour or cream (amends A4/A9, settles D83).
3. **Alert outranks orange.** The fix for an alert is a solid alert-red key with ink text (≥ 4.5:1), at every size. Nothing else on that screen is orange, and the alert's word stays ink with a red LED, so there is one red per alert (settles D42/D84).
4. **Window = recess, sized by job.**
   - Small indicator windows (LED, square, slot, paddle) are a dark recess in both modes.
   - Long tracks (faders, kiosk columns) are a recess in the card's own material: a light groove with an inner shadow by day, dark at night.
   - Caps are light plastic (amends A2).
5. **Light display colour.**
   - Jam draws whites on an amber-to-cream line (Cozy `#f4ca8a` … Daylight `#dbe6f9`).
   - Any light colour within 0.15 OKLab of the control orange (day or night) is mixed toward cream.
   - The same display value is used in the slot, paddle window, band, fader and preset swatch. HA keeps the real value (amends B3).
6. **A lit light's colour lives in its slot, paddle window and fader band, only while on.** The Band is 30 % of the display colour (on the card by day, on a lifted base at night). No whole-card wash (settles D45/D85).
7. **Kiosk light faders are columns** that print their number on the cap, "OFF" at 0. An offline light collapses to a narrow column with Try again (extends D40/D86).
8. **Kiosk sheets use kiosk sizes, not phone sizes.** Keys ≥ 20 px text and ≥ 60 px tall; appliance keys ≥ 16 px; no scroll (extends D44 and pass 1's kiosk floor to sheets).
9. **No control restyles another.** A control's look only changes because of its own state. Anything adaptive is decided when a view opens.
10. **Day kiosk dock = card blocks with indicator windows; the black ribbed dock is night only** (D87 final).
11. **HA built-ins by verified keys only (HA 2026.10):**
    - `ha-color-primary-40` = orange, with the rest of the ramp neutral.
    - `primary-color` = orange.
    - `ha-switch-checked-*` = band + cream.
    - `state-<domain>-active-color` = ink by day, cream at night.
    - No `switch-checked-*`, and no card-mod in dialogs (replaces D48/D88).
12. **Printed colour codes vs lit colour.** A key may carry a printed colour for identification. It is never lit, never a state, never orange (D89 final).
13. **Counts name their domain.** "Lights · N on" counts lights only; switched devices are shown and counted on their own (D90 final).
14. **Seven-segment only on appliance cards** (air purifier, dehumidifier). Appliances may be more object-like than their neighbours (A5 + D49 final).
15. **Tab bars draw only the lit window** of the current tab (D91 final).
16. **Media gets a home where it is always the primary:** a Music tab or sheet on every surface that has speakers.
