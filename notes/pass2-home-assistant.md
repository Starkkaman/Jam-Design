# Home Assistant (Jam Theme + Jam Cards) · Pass 2

Mockup: `mockups/pass2/home-assistant.html`. Pass 1's file is unchanged. Page controls switch every card and dashboard on the page:
- **Cards:** Day / Night (library, spec, HA dialogs).
- **Door:** Locked / Unlocked.
- **Paddle:** Quiet (pick) / Adaptive / Orange (pass 1).
- **Primary:** 1 per screen (pick) / 1 per card (pass 1).
- **Light colour:** Band (pick) / Edge / Wash.
- **Day dock:** Cards (pick) / Black band.

The page sections, in order:
- **0 Choices:** the six choices this pass makes, each with my pick.
- **A Orange:** three phones side by side, each with a live orange count.
- **B Light colour:** three options, each in Day and Night.
- **1 Theme:** tokens and spec.
- **2 Cards:** the card library.
- **HA dialogs:** HA's own more-info and confirm dialogs.
- **3 Dashboards:** phone, iPad and Echo. The iPad and Echo Lights sheets are also drawn already open.
- **What changes:** differences from Jam Braun today.

## What changed since pass 1
**High 1: too much orange on the phone Living view (pass 1 had six marks).** I solved this at screen level and show three options as real phones. Each phone counts the elements actually painted the control orange across the whole view, measured from the rendered page.

| Option | What it does | Orange marks (TV playing, speaker idle) |
|---|---|---|
| **A · Pass 1** | Orange paddles, one primary per card | **6** (4 paddles + Pause + Play) |
| **B · Adaptive** | Paddles orange while 1–2 are on; 3+ on in view → all quiet; one primary per card | **2** |
| **C · Quiet + 1 per screen (pick)** | Paddles never orange; on = paddle up + a small lit window on the paddle, in the light's own colour (cream for switches). One orange per screen, given to what's happening (playing 3 > on 2 > idle 1, then page order). Every other main button becomes a plain key in the same place. | **1** (Pause) |

There are two more combinations, not drawn: orange paddles with one per screen gives 5, and quiet paddles with one per card gives 2. With the door unlocked, C shows **0** orange: the red Lock key takes the screen's one loud slot (D42/D23 order).

**High 2: lights looked greyer without the tint.** There are three options side by side, in Day and Night, on the same 2×2 (warm group, Cozy 2200 K lamp, blue WLED, off Car port). Colour shows only while a light is on.
- **Band (pick):** the fader strip at the bottom of a lit card is tinted the light's colour, at 30 % in day and 24 % at night. The name, word and rocker stay on the plain face.
- **Edge:** a full-height slot window on the card's left edge, lit in the colour. This is pure window grammar.
- **Wash:** the whole card is tinted at 18 % in day and 22 % at night, close to Jam Braun today.

In every option the colour also shows in the slot by the name, the paddle window and the fader fill. So a lit light shows its colour in four places, and one of them is big enough to read at arm's length.

**Mediums:**
- **Brightness from 3 m (kiosk):** the kiosk Lights sheets now use **tall column faders**. Each column fills from the bottom in the light's colour and prints its own number on the cap (D25/D40: a fader's own readout counts once). The column height *is* the brightness. This also fixes the **tall, empty kiosk light cards**: the height now carries the value.
  - iPad: the left column holds scenes, the Tree (as a switch row), the purifier and All lights off; then three light columns.
  - Echo: three columns and All lights off. The offline Stove column shows "Can't be reached" and Try again.
- **Unlock door, one grammar (D42):** wherever there's a fix, it's a **solid alert-red control with ink text**:
  - the kiosk disc (as today);
  - the house strip, which now shows a red "Door unlocked" word chip plus a red **Lock** key;
  - the doors row, whose fix is a red **Lock** key (the orange Lock key is gone).

  While a fix is on screen, nothing is orange.
- **Heavy day dock:** in Day, the dock is now card-coloured blocks on the page, with the same top-right indicator windows. Night keeps the black ribbed band. A toggle shows the pass-1 band in Day for comparison.
- **HA built-in dialogs:** a section draws HA's light and switch more-info dialogs, plus a confirm dialog, with pass 1's keys and with pass 2's keys.
  - Pass 2 maps `switch-checked-*` to band + cream and `state-*-active-color` to cream. The light slider keeps the light's own colour (HA already does this), and only the confirm dialog's one button is orange.
  - Key names are from knowledge: HA's site was unreachable from this session, so they need checking on 2026.10.

**Lows fixed on the way:**
- Unselected HA tabs no longer show an unlit window (the row of black dashes in Day is gone).
- The speaker grille's special dot looks like every other dot until music plays; then it's a lit cream window, so it no longer reads as a hole.
- The kiosk "Lights · N on" count no longer counts the Tree.
- Offline lights open a sheet ("Can't be reached since 9:12 am", a short reason, Try again). The kiosk column has Try again in place.
- Source tiles carry a **printed colour tab** on every tile (identification, like Braun's colour-coded function keys). The tile on now still presses in and lights its slot.
- Rockers are 30 × 44 (were 28 × 42).
- The phone tabs now switch between **Living, Kitchen and Master**. Master shows the dehumidifier, an offline ceiling light, and the fan and blanket as switches.

**Kept unchanged:**
- The air purifier ("came out great") and the dehumidifier sibling, the only seven-segment displays.
- The remote with the red IR emitter at the top and lit power symbols.
- The TV source tile grid, the speaker's Group or split, and the tree as a switched device.
- Light CCT presets showing their colours; colour picks recolour the slot, paddle window, band and faders on every copy of the light.
- A popup on every light and media card.

## Research
WebSearch worked (10 searches). WebFetch could not reach `home-assistant.io` or `braun-audio.com` (the hosts don't resolve in this sandbox), so details beyond the search summaries are marked *(knowledge)*.

- **HA tile card features, 2025** (web):
  - `light-brightness` and `light-color-temp` are built-in tile features.
  - 2025.3 added inline feature position (only the first feature shows inline), plus view headers with badges beside them.
  - *(knowledge)* The tile's icon takes the light's own RGB colour when it's on.

  *Lesson:* HA itself colours a lit light by the light's colour, not by a theme accent, which supports giving the colour back. Its brightness feature is a fat slider *in* the card: the fader-in-the-card pattern is HA-native.

  Sources: [tile card](https://home-assistant.io/dashboards/tile), [features](https://docs.ncnynl.com/en/home-assistant/dashboards/features/), [2025.3 release](https://www.home-assistant.io/blog/2025/03/05/release-20253/), [CNX on 2025.3](https://www.cnx-software.com/2025/03/07/home-assistant-2025-3-released-with-dashboard-view-headers-tile-card-improvements-better-smartthings-integration/).
- **HA more-info dialogs** (web + knowledge):
  - Favourite colours (2023.6) are per light, reorderable, and store colour only (no brightness).
  - card-mod can restyle the more-info brightness slider.
  - The 2023.3 dialog is a big vertical slider filled with the light's colour, plus a row of control buttons.
  - *(knowledge)* Switches use a big vertical toggle coloured by `state-*-active-color`; small switches use `switch-checked-*`.

  *Lesson:* HA's own dialogs can be quietened with theme keys alone, with no card-mod. The light slider already does the right thing.

  Sources: [2023.6](https://home-assistant.io/blog/2023/06/07/release-20236), [Scenery thread](https://community.home-assistant.io/t/scenery-better-light-profiles-favorite-colors-and-scenes/883381), [card-mod more-info](https://community.home-assistant.io/t/modifying-more-info-dialog-with-card-mod/960243).
- **Bubble Card** (web): a pop-up can take a light's colour as its background, and a later release added `light_background: false` to turn that off for sub-buttons. Slider buttons are recoloured through styles (`--bubble-light-color`, `.range-fill`).

  *Lesson:* Bubble users asked for an *off switch* for full light-colour backgrounds. A whole-surface tint is the loud option, and people tone it down. That's why Band beats Wash as my pick.

  Source: [Bubble Card thread](https://community.home-assistant.io/t/bubble-card-a-minimalist-card-collection-for-home-assistant-with-a-nice-pop-up-touch/609678?page=45).
- **Mushroom** (web): `use_light_color` colours the icon and the brightness slider with the light's colour, and card_mod overrides beat it. There's a reported bug where the coldest white turned the slider grey.

  *Lesson:* colouring the *slider* with the light's colour is the community default. Also, very cold whites need a minimum chroma or they read as grey. Our Daylight 5000 K swatch `#eef3ff` is close to that edge.

  Sources: [slider colour thread](https://community.home-assistant.io/t/mushroom-light-slider-color-change-help/943257), [config thread](https://community.home-assistant.io/t/mushroom-cards-build-a-beautiful-dashboard-easily/388590/8596), [cold white bug](https://lightrun.com/answers/piitaya-lovelace-mushroom-bug-wrong-colour-brightness-slider-at-bluest-color-temperature-for-light-card).
- **UI Lovelace Minimalist** (web): has a separate "colored light card" that fills the background with the light's `rgb_color` through state templates. Users ask how to *remove* the yellow on-state background of slider cards.

  *Lesson:* the same lesson as Bubble: a full colour flood is divisive, so offer a confined tint.

  Source: [Minimalist thread](https://community.home-assistant.io/t/lovelace-ui-minimalist/322687?page=39).
- **Apple Home** (web, little on iOS 18 specifics): tiles since iOS 16 "make better use of colour to distinguish devices". Tapping the icon toggles, and tapping the name opens controls.
  - *(knowledge)* Lit tiles turn light and the icon takes the light's colour. The detail view is a tall vertical capsule slider filled in the light's colour, readable as a level from a distance.

  *Lesson:* the tall column fader on the kiosk is the same idea as Apple's detail slider. Toggle-by-icon / open-by-name matches our rocker / name split.

  Sources: [MacStories iOS 16 Home](https://www.macstories.net/stories/everything-new-coming-to-the-home-app-in-ios-16-and-macos-ventura/), [AppleWorld](https://appleworld.today/how-to-control-accessories-in-the-ios-16-home-app/).
- **Google Home redesign** (web):
  - The 2023 Favorites grid uses rounded tiles: tap toggles, slide adjusts, long-press opens full controls.
  - The tile background shows state, and dim means off.
  - Colour presets are a grid; the Nov 2025 "improved device controls" preview turns them into a carousel.

  *Lesson:* Google puts the level *in the tile* (slide on the tile) and uses the tile surface for state. The Band option is our flat version of that.

  Sources: [9to5Google 2025 controls preview](https://9to5google.com/2025/11/11/google-home-device-control-updates-preview/), [lights redesign](https://9to5google.com/2023/05/04/google-home-inbox-lights-redesign/), [Engadget](https://www.engadget.com/googles-redesigned-home-app-is-available-to-everyone-185733317.html).
- **SmartThings 2026 redesign** (web): lighter colours, compact cards, a floating bottom bar. Tapping the icon runs the primary action; tapping elsewhere opens the controls. The older device handlers used on = blue and off = white.

  *Lesson:* again, one primary per card, on the icon. Nothing new on colour.

  Sources: [Android Authority](https://androidauthority.com/samsung-smartthings-redesign-android-3717799), [T3](https://www.t3.com/home-living/smart-home/samsung-just-rolled-out-its-smartthings-redesign-to-android-users-heres-what-to-expect).
- **Braun / Rams colour use** (web):
  - Mostly achromatic. Rams: "I have always been against the use of bright colors at Braun."
  - Braun's audio colour chart assigned colours by *function*: FM keys blood orange, phono honey yellow, all power keys leaf green.
  - On the TS 45 everything is grey except the green on/off switch. On the ET66, only the equals key (yellow) and on/off (green/red) are coloured.
  - Colour is used "if it told the user something".

  *Lesson:* this is the strongest support for **one coloured control per screen** and **green for power** (we already light power symbols green). It also supports **printed colour codes on keys** (source tiles) as function coding, not state.

  Sources: [Design Museum](https://designmuseum.org/designers/dieter-rams), [Rams Foundation](https://rams-foundation.org/magazine/texts/), [Braun Audio, colour choices](https://www.braun-audio.com/en-ES/stories/design/braun-colour-choices/).

## Design (what and why)
- **Orange is a screen budget, not a card budget.** Pass 1 followed "one per card" and still ended up with six. The Braun precedent (one coloured control on a face) and HA's own "one primary action" guidance both point the same way: count per screen.
  - The winner is whatever is *happening* (playing beats on beats idle), so the orange still means "this is the thing to press now". The others stay where they are as plain keys, so muscle memory survives.
  - Popups are their own screen. In the library, each card is its own panel, so the library shows each card's own primary.
- **Rockers without orange.** On is shown by position (up), plus a small window on the paddle that lights. For a light it lights in that light's colour, so the rocker becomes another place the light's colour shows. A window on a paddle is the same part as everywhere else (dark recess, flat lit colour), so no new grammar is added.
- **Light colour lives where the level lives.** In the Band option, the tint sits behind the fader, so "how much light, what colour" is one zone. The name, word and rocker stay on a calm face. Wash is the familiar look, but it's loud on a 2×2 of warm whites. Edge is purest, but at arm's length it's only a thin line, and off cards show a black line.
- **Kiosk columns.** A tall vertical fader is still a fader (no knobs). It fills like a glass of light and prints its own number. This answers the 3 m problem (README: ~65 px to read text at all; a 360 px column at 75 % reads at any distance) and makes the screen-filling card meaningful.
- **Alert is the loudest thing, and it's red.** "Alert outranks primary" becomes concrete: wherever the fix appears, it's the same red key with ink text. Ink on `#ff5a48` is about 5.5:1 (computed in the theme sheet), which avoids Jam Braun's 3.54:1 red-fill problem.
- **The day dock goes back to Braun's soft blocks** (minus the room tints), keeping pass 1's indicator windows in the top-right corner. The black band stays at night, where it's not a slab.
- **HA's own dialogs** get quiet switches through theme keys only, so a tap on an HA built-in no longer shows a second, orange control grammar.

## Audit
Checked with Playwright (Chromium, no launch options):
- Page widths 1480 (light scheme) and 390 (dark scheme).
- Every library popup.
- Every dock sheet on both kiosks in Day and Night, with the light popup, Source and Remote popups opened inside them.
- Phone Kitchen and Master tabs, door unlocked, and every page control.

Results:
- No JS errors.
- No horizontal scroll at 390.
- No page text under 12 px (I raised the page eyebrow from 11 to 12).
- Nothing under 18 px on kiosk homes.
- No kiosk sheet or popup scrolls or overflows its screen.

Orange counts: 6 / 2 / 1, and 0 when the door is unlocked under C.

The fix pass corrected:
- A JS syntax error (unescaped apostrophes).
- The comparison headers being misaligned.
- The off-paddle window being too heavy (12×5 → 10×4).
- The "today's orange count" wording.

| # | Problem | Severity |
|---|---|---|
| 1 | **Day fader tracks are black bars.** The uncovered track is the window recess (`#151413`), so in Day every off light, every volume fader and every unfilled column is a solid black bar. This is now the heaviest element on the day phone and kiosk sheets, much darker than Jam Braun's light grey track. Rule-consistent ("windows are always a dark recess"), but it fights "minimalist simplicity". | High |
| 2 | **Warm whites read as orange.** Cozy 2200 K (`#ffb565`) in a band, column or paddle window sits close to control orange. The iPad Kitchen lamp column is a big orange-looking slab. Colour discipline holds, but the *perceived* orange problem can come back through light colours. | Medium |
| 3 | **The quiet paddle window is small** (8×3 lit). At arm's length, on vs off rockers differ mostly by paddle position. On a light card the band and slot also say "on", but on the switch cards (Tree, fan) the paddle is almost the only cue. | Medium |
| 4 | **The moving primary makes the speaker's Play a plain key** while the TV plays. That's correct by the rule, but if you open the phone to start music, the button you want isn't the loud one. The speaker popup restores it (own screen). | Medium |
| 5 | **Adaptive paddles flip unrelated controls.** Turning on a third light changes the look of the first two. That's why it's not the pick, but Isaac may still prefer it. | Medium |
| 6 | **The kiosk Lights sheet's left column is phone-scale.** The purifier keys are 12 px mono and the scene keys 17 px on a 3 m screen. The 18 px floor covers kiosk homes only, but these are the controls people actually press from across the room. | Medium |
| 7 | **HA theme keys are unverified.** `switch-checked-*` and `state-*-active-color` are from knowledge, because HA's docs were unreachable. HA 2025+ also has `--ha-color-*` tokens for `ha-button`, which may bypass `primary-color`. | Medium |
| 8 | **Band at night is muddy for warm whites.** 24 % of `#ffd9a0` on `#2a2a28` reads brown rather than lit. A higher percentage risks glare (Lobby's night glare cap). | Low |
| 9 | **Edge option:** off cards carry a black edge line (the unlit window), so a room of off lights is a row of black stripes. Noted in the option text. | Low |
| 10 | **Two reds on the unlocked house strip:** a red word chip and a red Lock key side by side. Only the key needs to be red; the word chip could be alert-ink on the band only (it is), but at a glance it's still a lot of red. | Low |
| 11 | **Kiosk column at 0:** the cap sits blank at the bottom, and only the small "Off" label says off. From 3 m an off column and an unreachable one look alike, apart from the dashed edge. | Low |
| 12 | **Echo: an offline light takes a third of the sheet** for a dead fixture. | Low |
| 13 | **The library shows per-card primaries** (TV Pause and speaker Play both orange). That's by design (each card is its own panel), but someone comparing could read it as "two per screen is fine". | Low |
| 14 | **Climate and Camera are still samples** that aren't in Jam Home's inventory. | Low |
| 15 | **Jost + Plex cost on the Echo Show's WebView 139** is still unmeasured. | Low |
| 16 | **The sticky page control bar is 126 px tall at 1480** (two rows). This is page chrome only. | Low |

## Change suggestions for pass 3
- **Day fader track:** try three day tracks side by side:
  - (a) the window recess (now);
  - (b) `--key` grey with a 1 px inner shadow (Jam Braun-like);
  - (c) recess at 55 % opacity.

  Decide whether the "faders reveal light" metaphor needs a black ground in Day.
- **Warm whites vs orange:** shift the CCT swatches' display colours slightly toward yellow and cream for 2200–2700 K (keep the order and names), and/or cap the kiosk column's chroma. Check the iPad Kitchen lamp column against Pause at 3 m.
- **Quiet paddle:** try a bigger window (14×5) and/or the whole paddle face in a pale tint of the device colour (not orange). Test the switch cards especially.
- **Primary tie-breaks:** define that a card *opened into* (a popup or kiosk sheet) always gets its own orange, and consider giving the speaker card the orange on the Music tab and kiosk Music sheet. Ask Isaac if Pause should even win over an idle speaker, or whether nothing should be orange when nothing needs pressing.
- **Kiosk Lights sheet left column:** scale scenes and the purifier to kiosk sizes (keys 20 px, appliance keys 16 px), or move the purifier off the Lights sheet (it isn't a light).
- **Verify HA keys** in a jam-home harness run (HA 2026.10): switch, toggle, light more-info, confirm, and `ha-button` tokens. Screenshot before and after.
- **Night band:** try 30 % with a lighter mix base, measured against the night glare cap.
- **Offline on Echo:** collapse an offline light to a narrow column, or a row under the others.
- Design the Marissa view, the Music tab, the screensavers (Clock in Braun Hi-Fi), and Jam Control at 1280.
- Measure the fonts on the Echo (first paint, CPU).

## Differences from Jam Braun today (with pass 2's picks)
1. **Font:** Archivo → Jost (words) + IBM Plex Mono (small numbers).
2. **Toggles → rockers:** the olive pill becomes an up-is-on rocker. On = paddle up + a small lit window on the paddle (the light's colour, or cream). **The paddle is never orange.** Olive leaves the palette.
3. **Lit lights:** the whole-card tint (18 % / 24 %) becomes a **tinted fader band** (30 % / 24 %). The colour also shows in the slot by the name, the paddle window and the fader. Off cards stay plain.
4. **Numbers by sliders:** on the phone, "75%" goes and the value rides the cap while you drag. On kiosks, light faders become **tall columns that print their number on the cap**.
5. **Chosen keys press in:** the scene (ET66 yellow today) and the purifier speed (orange today) become pressed-in keys with a lit square window.
6. **Orange: about six marks → one.** Today's Living view has purifier speed, both Play keys, the NerveOS ⋯, the grille dot and the volume fill. Pass 2 has one orange button per screen, on what's playing.
7. **Room colours retired:** a walnut rule on every room heading. Dock blocks lose their room tints. **Day:** card blocks with an indicator window. **Night:** the black ribbed band.
8. **Black bands:** the house strip, the TV screen and the night dock.
9. **Kiosk clock colon:** orange → dim.
10. **Unlocked door:** the kiosk disc is still solid red. The phone chip becomes a red word plus a solid red **Lock** key (today it's a red dot + red text in one chip). The doors row uses the same key.
11. **Air purifier:** the small appliance (grille, seven-segment PM2.5, round power key). The house strip drops "Air · Poor".
12. **TV sources:** still a 3-column grid. Every tile has a printed colour tab (today: a dot). The one on now presses in and lights its slot (no yellow fill).
13. **Popups:** one shared sheet (Close top right, no orange Done); five whites with their colours; Group or split; an offline light sheet with Try again.
14. **HA's own dialogs:** switches and toggles turn dark with a cream knob instead of orange.
15. **Kiosk count:** "Lights · 4 on" → "3 on" (the Tree is a switch, shown on its own row).
16. **Shape:** keys go from pills to 12 px; chips stay pills; cards go from 14 to 16 px corners.

## Bible implications
1. **The orange budget is per screen.** One orange primary per screen; a popup or sheet is its own screen. The winner is the most "happening" control: playing > on > idle, then page order. The others are drawn as plain keys in place. This replaces A4's "orange on rocker paddles and the one primary per card" and answers D39.
2. **Rocker paddles are never orange.** On = paddle up + a lit window on the paddle, in the device's colour (the light's colour, or cream). This amends A4 and A9's rocker wording.
3. **Alert outranks orange (settles D42 and D23 for HA).** The control that fixes an alert is a solid alert-red key with ink text (≥ 4.5:1), the same at every size (kiosk disc, chip, row). While a fix is on screen, nothing on that screen is orange.
4. **A light's colour may tint its fader zone.** A lit light card may tint the strip behind its fader (Band: 30 % day / 24 % night of the light's colour). The card-wide tint stays retired. This amends B1/B3 and D45 (colour lives in the slot, paddle window, fader and fader band, only while on).
5. **Kiosk light faders are vertical columns** that fill in the light's colour and print their own number on the cap. This extends D40 ("big faders may print it") to a rule for kiosk sheets.
6. **The day kiosk dock is card blocks with indicator windows; the black ribbed dock is night only.** This amends D47.
7. **HA built-ins:** `primary-color` reaches only confirm buttons. `switch-checked-*` maps to band + cream and `state-*-active-color` to cream, and HA's light slider keeps the light's colour. This amends D48 (once the keys are verified).
8. **Printed colour vs lit colour.** Keys may carry a *printed* colour code for identification (source tiles, Braun's function chart). It's never lit, never a state, and never orange. This is a new rule next to colour discipline.
9. **Counts name their domain.** A kiosk "Lights · N on" counts lights only. Switched devices (the Tree) are counted and shown separately.
10. **Tab bars draw only the lit window.** Unselected tabs show no recess (answers pass 1 implication 9 and extends D12/D46).
11. **Decorative motifs show their indicator only when lit.** Unlit, the grille's special dot is an ordinary dot. This amends D50.
12. **Offline lights open a Try again sheet** (confirms D52). Kiosk columns show Try again in place.
