# TV launcher (Lobby) · Pass 5

Mockup: `mockups/pass5/tv-launcher.html`. Passes 1–4 are unchanged.

**How to review it without a remote:** press **▶ Tour** above the TV. It steps through 41 states, about 4 s each, with a caption for each. **Next step ›** moves one state at a time. Clicking the TV or pressing a key stops the tour and gives you the keyboard.

**Keys** (also in the legend on the page):
- Arrows move. Enter is OK: it acts on release, and holding it 1 s (or pressing twice) unlocks the door.
- Esc or Backspace is Back. Backspace deletes a letter while the keyboard is open.
- H is Home. G or Q opens the TV menu. I opens the TV menu on Input. P is the remote's power key.
- While the keyboard is open, letter and number keys type.

**Page controls:**
- **Clock:** 6:20 AM, 9:15 AM, 2:30 PM, 4:05 PM, 5:20 PM, 7:00 PM, 8:24 PM, Live.
- **Date:** Nov 5 or Jun 21.
- **Sun times:** From Home Assistant, or Missing.
- **TV picture mode:** Theater night, Vivid or Dynamic.
- A readout under these controls names the sky stop they produce.
- **More:** Front door, Who's home, Motion, Home (lived-in or first run), Switch 2, Netflix, TV menu over apps (Allowed or Home only), Lobby update, Page theme.
- **Jump to:** 19 states.

All titles, art, colour codes, sun times and household details are made up, apart from what the Lobby README lists: the house name "Bungalo", the app list, the Switch 2 on HDMI 2, the antenna, the lamps and the front door, and "Paused by Isaac". I added four app names (Corridor Digital, Podcasts, Radio, The Criterion Channel) to test long names and a full band.

## What changed since pass 4

Pass 4 is the direction: Isaac said "Everything should feel like it has the same design language, not necessarily the same design." Pass 5 keeps that room (the sky window, the sill with picture frames, the dark cabinet, the dial, the sockets, the wall plate, the drawer and the blind). It then carries the room into every screen and fixes the pass-4 audit.

| Pass 4 | Pass 5 | Why (audit #) |
|---|---|---|
| One dial scale, 10 stations at a 159 px pitch, full at ten; "YouTube Music" didn't fit | **Three band scales on one glass (Watch, Play, Listen), six fixed slots each = 18.** One needle crosses all three, and the band it's on lights its square window. Empty slots show as bare marks. A slot holds a 190 px name at 26 px (about 16 letters). Anything longer gets a dial name. **All apps** sits past the right walnut stop. | Capacity is visible on the dial itself (H16). Long names fit whole. (#4) |
| Apps found by name only; a guest looking for "the red N" is stuck | **All apps, A to Z.** The keys are in alphabetical order, an index tab marks where each letter starts, and each key says where the app lives ("On the dial · Watch" / "Not on the dial"). The dial's station names are brighter (ink2, not ink3). **No logos or marks.** | Decision below. (#3) |
| All apps' Move/options flow carried from pass 3, not redrawn | **Arrange the dial:** the three bands are drawn large with their six slots ("free" where empty), and a tray below holds the apps that aren't on the dial. OK picks an app up and it lifts with a cream outline. ← → move it along the band, ↑ ↓ move it to another band (swapping if that slot is taken), and ↓ from Listen takes it off the dial. OK puts it down; Back puts it back where it was. A full band refuses and says "Listen is full. Take one off first." | (#13) |
| Sun times fixed in the mockup | **The sky follows Home Assistant's sunrise and sunset** (`sun.sun` through Control Freak). The stops are: dawn = sunrise −50 to +30 min; morning to solar noon; afternoon to sunset −75; golden hour to sunset; dusk to sunset +50; then night. At 7:00 PM, November is night and June is still afternoon. If the data is missing, it uses yesterday's kept times and says so. **Settings › The window** draws today as a day strip: the stops, sunrise and sunset ticks, NOW as a cream rule, the past dimmed, and the source line. It also holds **Always night**. | H4. (#2) |
| Afternoon secondary ink 4.8:1, unchecked under Vivid/Dynamic | **In bright picture modes (Vivid, Dynamic, Sports), the three bands that carry writing, and the clouds, step 30% darker.** Contrast is measured through a CSS stand-in for the panel's processing. | (#6) |
| Calm swapped the sky in one frame | **Calm keeps the slow fade.** It's a minute on the TV and 1.2 s in the mockup, because a one-frame night-to-afternoon swap is the bigger change. | (#10) |
| Lobby's own paddles (with a window on the paddle) and a thumb-turn | **Jam Home's drawings, adapted for TV focus** (conflict 9): the **dimmer plate**, a rocker that is on when the top is pressed (I/O marks) with a slide dimmer beside it, and the **lamp glyph whose shade is the window**, lit in the lamp's colour. The front door is the **door swing**: the leaf sits in the wall when locked and stands open when unlocked. Focus is Lobby's: a cream base window and a 3 px lift. | One house, one drawing. |
| An unlocked door was always the red key | **Warn by day while someone's home:** an amber round light, a printed ▲ and "Unlocked", with the leaf drawn open in amber. The lettering on the glass says when it turns red ("it turns red at sunset, 4:52 PM"). **Alert after sunset, or when nobody's home:** the solid red key with dark text, as before. | Conflict 12. (#7) |
| Anyone with the remote could unlock | **Settings › House › Unlock from the TV: Allowed / Lock only.** With Lock only, OK on a locked door does nothing but nudge, and the lettering says where to change it. | (#8) |
| Plaque titles cut at about 22 characters | **Plaques wrap to two lines** (about 44 characters). The lettering's title drops from 58 to 46 px when it doesn't fit, and wraps only beyond that. | TY5, TV12. (#5) |
| Hard shadows straight down | **Shadows fall down and right**, from one light at the top left. | H9. (#12) |
| Hints 2 px under the plates | **The socket panel and plate end 6 px above the hints.** | (#14) |
| The TV menu over an app assumed an accessibility service | **"Home only" is drawn as the fallback.** Over an app, the menu key belongs to the app. Home, then the TV readout, opens the drawer, and its header says "over Home · you left The Copper City". The film is the first frame on the shelf, so one OK goes back. | (#1, designed around) |
| Not drawn: Restart the TV, renaming an input, the screensaver | **Power:** the drawer rises with Cancel focused, Sleep and Restart the TV, and no orange. **Restart** asks in a card with Cancel focused and a dark Restart key. Then the TV's own start-up screen shows (Lobby can't draw during it), and Home comes back. **Rename an input:** Settings › Inputs › HDMI 2 opens a **keyboard drawer**: a 12-unit grid, a steady caret, "8 of 14", and Done as the one orange. The new name shows on the socket panel and in the TV menu. **The idle face:** after 10 minutes with no keys, the window is drawn full-screen with a 200 px clock, the date and one line about the house. It changes nothing but the clock, and its position shifts every 10 minutes. | H10. (#13) |

**Renamed (H18 glossary):**
- "console face" → **the lowboard**: Jam-Dash, NervOS and Lobby all used "console".
- "console drawer" → **the drawer**.
- "patch bay" → **the socket panel**: Jam-Dash owns "patch field".
- "the sign" → **the lettering** (on the glass): JamFin's marquee uses "sign".

**Kept from pass 4, unchanged:**
- OK on release; hold 1 s or press twice for the door; one press locks it.
- Rows stop at a walnut end, with a nudge.
- "n of N" only on the focused row.
- The launch rule: hold = max(load, 600 ms), 300 ms open.
- Every failure ends with Try again (orange) + Home.
- The device-turned-on note shows once, for 15 s.
- An update ready is a cream light on Settings, never a pop-up.
- Apps is the TV's own source (the lit square).
- The drawer's header names what's underneath.
- Choosers hold 5 rows, then show "n of N ▲▼".
- The picture preview waits for a 500 ms rest.
- No suggested content.
- The needle remembers its station.
- Empty ports are shown, and focus skips them.

### Decision: how a guest finds an app (pass-4 audit 3)
**Names, plus an A to Z list. No marks.**

Why not a small toned mark:
- CW5 (language) says apps are names, their media or a neutral glyph, never brand marks. A monochrome Netflix "N" is still Netflix's mark.
- Marks were what made pass 3's Lobby look like everyone else's launcher.

Why names and A to Z work:
- The guest's real question is "where is Netflix?". The dial already answers it in words at 26 px: "Netflix" sits in the Watch band, and at 3 m the word is as quick to find as the logo.
- If it isn't on the dial, All apps (the last stop on the dial, "A to Z · 19") lists every app alphabetically. The index tabs let a guest jump their eye to "N".
- Worst case on the dial: 7 presses to any station.

If guests still struggle, the next step is a **neutral glyph by kind** (▶ for video, a controller for games, a note for music) on the band labels, never a brand mark (Q2).

## Language check (the 15 items)

| # | Language item | In Lobby pass 5 | |
|---|---|---|---|
| 1 | Two typefaces | Jost for words; Plex Mono for the house name, band labels, port labels, eyebrows, counts and index tabs. Nothing else is loaded. | Held |
| 2 | Indicator windows | Round LEDs (signal, locked, warn, update), square band and choice windows, slots on plaques and keys, and the bar of slats on the blind. All are always a dark recess, and lit is flat colour. The lamp shade and the door swing are object-shaped windows (H3). | Held |
| 3 | Window shapes have meanings | Round = status; square = chosen (the band the needle is on, the current picture mode, Follow the sun / Always night); slot = "this one" (plaques, keys, the drawer header). Nothing round means position. | Held (conflict 6 B) |
| 4 | Cream is the house light | Focus lights, the lit needle, plaque slots, the NOW rule, the caret, and the carry outline in Arrange. | Held |
| 5 | State = colour + shape + word | The door by day is an amber round light + ▲ + "Unlocked" + the leaf drawn open. Signal: green light + "Signal". Missing sun times: unlit light + dashed strip + a sentence. | Held |
| 6 | Red means alert | The door after sunset or with nobody home is the solid red key with dark text (5.5:1), and nothing else on screen is orange. By day it is no longer red (conflict 12). | Adjusted (by conflict 12) |
| 7 | Orange is the one thing to do now | Counted: Home 0, All apps 0, Arrange 0, Power 0, Restart card 0, Settings 0 (About with an update: 1). Keyboard 1 (Done), failure 1 (Try again), device note 1 (Switch to it), first run 1 (Arrange the dial). | Held |
| 8 | Focus = a light at the thing + a small lift | Plaque slot, needle + band square, socket ring, base windows under plates and keys, leading edge in lists, inset cream edge on keyboard keys. Colour snaps; only transform moves; ≤ 150 ms. | Held |
| 9 | Chosen things press in | Shift presses in on the keyboard. The rocker's top half is pressed in when on. Chosen options show a square. | Held |
| 10 | Walnut is the house wood | The sill, the dial's stops, the drawer and keyboard lips, the screen top rules, the idle face's sill, the blind's bottom rail, the note card's lip. | Held |
| 11 | Things end visibly | The shelf's end mark, the dial's walnut stops, "free" slots, "6 of 6 · full", the chooser's "n of N ▲▼", the keyboard's "8 of 14". | Held |
| 12 | Calm is the resting state | Home has no orange, no loops, nothing moving. The idle face changes once a minute (the clock). | Held |
| 13 | Motion is short, causal, once | glide for focus, decelerate for arrivals, and **leave** for the blind going up (pass 4 used an off-table ease-in). The sky's minute-long fade is the one slow change and is kept in Calm. | Adjusted (MO1 fixed; Calm refinement, row 6 below) |
| 14 | Say it once, in plain words | The readout says "menu open ▼" while the drawer is open. A Settings row hides its value (shows ›) while its detail is open. The door says when it will turn red, once, in the lettering. The arrange header says where the carried app is, and the band count says whether it's full. | Held (refined) |
| 15 | Honest objects, drawn flat | A window, a sill, a lowboard with a receiver dial and a socket panel, and Jam Home's wall plate and door symbol. No grain, glow or brushed metal; ribs only on the blind. | Held |

**What someone coming from another app recognises within a second:** the type pair, the cream focus light, the little dark windows, walnut, Try again in orange, and the red door key. Coming from Jam Home: **the same lamp drawings and the same door symbol**. That's new this pass, and deliberate.

**What stays Lobby's own:** the sky, the sill and frames, the lowboard, the three-band dial with its needle, the socket panel, the drawer's face, the blind, the index tabs, the arrange tray, the day strip and the idle face.

**Floors kept:**
- Safe area 96/54 px on every state.
- Text ≥ 22 px, hints 24 px.
- Transform and opacity motion only.
- Focus ≤ 150 ms with snapped colour.
- Opaque full-bleed launch layers.
- Text on the sky ≥ 4.5:1 through every stop and every simulated picture mode.
- Glare and red under their caps (Audit).
- No ellipses anywhere.

## Conflicts assumed (each one assumed, pending Isaac)

| # | Conflict | Assumed (RULES-TIERS recommendation) | Where it shows in Lobby |
|---|---|---|---|
| 1 | Warn shape | B: round amber light + printed ▲ + word | The door by day; the idle face's house line |
| 2 | Row ends | A: stop at a visible end | The shelf, the dial's bands, choosers, the keyboard |
| 3 | Windows in Day | Dark recess on dark objects | Every window in Lobby sits on the dark lowboard or the sky, so all are dark recesses |
| 4 | Title card form | B: a shared rule; each app draws its cover | The blind stays Lobby's cover, with the slatted bar, the max(load, 600 ms) hold, and a 140 ms fade in Calm |
| 5 | Day Play | B: dim to dark before the card | The blind is dark in every sky stop |
| 6 | Round = position? | B: slots for "current"; round only for status | Plaques, keys and the drawer header use slots; position is in text ("2 of 3") |
| 7 | Ribs | B: any dark surface, never behind scrolling rows | Only on the blind, which covers everything when it's down |
| 8 | Accents | B: optional | None. The sky is the screen's colour field |
| 9 | House objects drawn twice | B: Jam Home owns the drawing | Dimmer plate, lamp-shade window and door swing reused, with Lobby's focus |
| 10 | Guide band | B: shared behaviour; face per launcher | The drawer is Lobby's band: same key order, header, chooser rules, ≤ 1 orange. Power uses the same drawer |
| 11 | Menus beside a list | B for keys and bands | Choosers rise above their drawer key |
| 12 | Unlocked door | B: warn by day, alert after sunset or when nobody's home | The door and the TV menu's Front door key. The idle face refuses to show during an alert |

## Holes applied (H1–H18)

- **H2 Objects as UI:** furniture, at one realism level. Every pressable thing still has a focus light and a word, so nothing decorative hides a control.
- **H3 Object-shaped windows:** the lamp shade is a dark recess when off and the lamp's flat colour when on. The door swing is ink when locked, amber when warn, and dark on red when alert. The plugged socket stays a printed code (never lit).
- **H4 Sky:**
  - Real sun times; fallback to yesterday's kept times, said in words.
  - Flat bands, no gradients.
  - Text only on the top three bands, each ≥ 4.5:1 at every stop and in Vivid and Dynamic (simulated).
  - Never brighter than the afternoon stop.
  - Changes take a minute, in Calm too.
  - Always night in Settings.
- **H5 Status boards:** the socket panel has fixed positions and words in its lights. It holds the set's five ports (Apps, HDMI 1–3, ANT), fixed by the hardware.
- **H7 Timelines:** the day strip in Settings › The window. NOW is a cream rule and the past dims. It doesn't repeat a value: the clock shows the time, and the strip shows where the time sits in the sky.
- **H9 Shadows:** hard offset shadows only (Lobby's choice), down and right from a top-left light, never on text.
- **H10 Idle face:**
  - Only the household's own content: the time, the date and weather, the house line.
  - Nothing starts by itself.
  - One change a minute (the clock).
  - The block shifts position every 10 minutes against burn-in.
  - Any key wakes it, and that press isn't passed on.
  - An alert keeps Home awake instead.
  - "Screen off" is an option.
  - Not drawn: dimming further after 30 minutes.
- **H12 Signature moment:** the blind drops in 300 ms and rises in 300 ms (≤ 600). Calm uses a 140 ms fade. It never fires on focus.
- **H13 Visible memory:** the needle stays on its station, dimmed, and the band square stays lit, so coming back to the dial lands where you can see it.
- **H15 People:** who's home is used, but shown only as words ("Nobody's home") in the lettering. No faces, and no key rail (that's Jam Home's).
- **H16 Capacity:** see the table below.
- **H17 Claims about the real world:**
  - The sky and the day strip say where the sun times came from.
  - The door names where it was unlocked from.
  - The socket panel shows only what CEC reports or what you named.
- **H18 Glossary:** renamed as listed above.
- H1, H6, H8, H11 and H14 don't touch Lobby.

### Capacity and overflow (H16)

| Element | Holds | Overflow |
|---|---|---|
| App dial | 3 bands × 6 slots = 18. A name up to 190 px at 26 px (about 16 letters; YouTube Music is 162 px) | Longer names get a dial name ("Criterion"), shown in Arrange. More apps live in All apps. A full band refuses a new app and says so |
| All apps | 6 columns × 4 rows = 24 on one screen | Past 24: a letter jump (not drawn) |
| Arrange tray | 2 rows × 6 = 12 | Same as All apps |
| Shelf (Continue) | 5 in view + a peek; proposed limit 12 | The oldest drops off; "n of N" shows on the focused row |
| Plaque | 2 lines, about 44 characters | The service's short title |
| Lettering title | 1 line at 58 px, or at 46 px (about 50 characters) | Wraps to 2 lines at 46 px |
| Socket panel | 5 (the TV's ports) | None: it's the hardware |
| House plate | 3 lamps + the front door | More lamps belong to Jam Home. The plate holds the living room's lamps only |
| Drawer | 7 keys | The TV menu's order is fixed |
| Choosers | 5 rows | "n of N ▲▼" |
| Input names | 14 letters (the short-word length) | The keyboard stops at 14 and nudges |

## Rules I broke

| # | Rule (source) | What I did instead | Why Lobby needed it | Verdict |
|---|---|---|---|---|
| 1 | CT4: sliders reveal light up to a cap, and you move them | Jam Home's slide dimmer is drawn, but on the TV it's **read-only**: it shows the level; OK switches the lamp. The level shows in the lettering ("On at 40%. Set the level from Jam Home.") | A D-pad row of plates uses ← → to move between plates. Switching in one press matters more than dimming from the sofa | **App-local** (a drawing reused on a device that can't move it); Q6 |
| 2 | CW2: short words ≤ 14 characters, used as a fit rule | Dial names are fitted by **measured width** (190 px at 26 px), not by letter count. "Corridor Digital" (16) fits; "The Criterion Channel" doesn't | Letter counts lie: 14 M's are 295 px, and 16 mixed letters are 173 px | **Language-wide, reworded**: "fit by width at the element's size; letter counts are a guide" |
| 3 | D153 / TV20: "Power is a sheet" | Power is **the drawer** (the same lowboard drawer as the TV menu), with Cancel focused, Sleep and Restart, and no orange. Restart asks in a centred card | One bottom drawer for every set-level thing keeps one place to look. A sheet would be a second form | **Device family** for behaviour (focus on Cancel, Sleep one press, no orange, confirm for Restart); the **face is app-local** (as conflict 10) |
| 4 | D154 / TV21: TV keyboard (a component) | The keyboard is the drawer **drawn taller** (660 px), with the field on the glass. It keeps the 12-unit grid, the steady caret, Done as the one orange, and printed hints | Same reason: one drawer | **Device family** for the grid and Done; **face app-local** |
| 5 | MO3: Calm means swap instantly | Calm **keeps the sky's minute-long fade** | A one-frame night-to-afternoon swap is a bigger luminance change than the fade. Pass-4 audit 10 | **Language-wide** refinement: "an ambient change slower than a minute stays a fade in Calm" |
| 6 | CL1: colour only for state and selection | The day strip paints each sky stop in that stop's own colour | It's a drawing of the sky (content), not chrome | **Language**: already exempt as a drawn stand-in. No change |
| 7 | TV8: rows stop at a visible end | The dial's bands stop at a walnut stop, but → past the last station goes on to **All apps**, beyond the stop | All apps belongs to every band. Putting it in one band's slots would cost that band a slot | **App-local** |
| 8 | TV1: focus is a light + a lift (no third state) | Arrange adds a **carry** state: the app lifts 12 px with a cream outline and a hard shadow | Picking up must look different from focus, or OK reads as "nothing happened" | **Device family** candidate: "a carried item = lifted + outlined in cream" (NervOS saves and JamFin rows will need it) |
| 9 | CT6: never the same value twice | A Settings row **hides its value** (shows ›) while its detail is open below/beside it | List + detail showed "Theater night" twice in pass 4 | **Language-wide** refinement of CT6 |
| 10 | CL6 / D84: an unlocked door is always the red key | **Amber by day while someone's home**; red after sunset or with nobody home. The lettering says when it turns red | Conflict 12; pass-4 audit 7 | **Language-wide** (if Isaac takes conflict 12 B) |
| 11 | IN4: square = chosen mode | The square by each band label lights for **the band the needle is tuned to**, even when focus is elsewhere | It is a chosen mode: which band the dial is on | Held, not broken. Noted because it's a new use |

## Audit

**Checked with Playwright** (Chromium, `chromium.launch()` with no options), at 1500 px wide and deviceScaleFactor 1.31, so the TV renders at about 1920 px. Also checked: 390 px dark and 1300 px light. Screenshots are in the scratch dir, not the repo.

**What I ran:**
- all 41 tour states;
- a real-keyboard run:
  - the shelf to its end, then down to the plate, then along to the door;
  - Enter **held 1.2 s** (unlocked), then Enter (locked);
  - G, the Picture chooser, ↓×6;
  - the dial → All apps → Arrange, picking an app up, carrying it ↓↓, putting it down, Back twice;
  - Settings › The window › Always night, then Sleep & power;
  - the rename keyboard with real typing (Backspace, "Two", Done);
  - P for Power;
  - waking the idle face;
- 11 sky/picture-mode combinations, June at 7 PM, the idle face in Vivid, Calm over a film, and the glare shots.

**Checks on every state:**
- text ≥ 22 px, hints ≥ 24 px;
- all text inside 96/54 px (except the peeking frame);
- no ellipsis or clipped titles;
- no text spilling out of its key, plate, socket, station or card;
- no two text runs overlapping on the same layer;
- plaques ≤ 2 lines;
- the socket panel and the plate never touch;
- sky contrast through the simulated picture mode;
- no JS or console errors;
- `scrollWidth` 390 at 390 px.

**All passed after the fix pass.**

**Fixed in the fix pass:**
- The socket panel's state line ran into the hints. The `font` shorthand had reset the line height.
- The ▲ was 19.8 px. It's now 22.
- "Full" message overlapped the band's slots. It moved to the arrange header.
- The arrange tour left YouTube TV on Play for the next step.
- The tray overflowed at six apps. It's now a 6-column grid.
- A dial name was forced on names that fit. It's now by measured width.
- Typed capitals were lowercased.
- Focus didn't return to the Rename key after Done.
- The door unit changed width when it turned red, shifting the plate. It now has a fixed minimum.
- Two clouds sat under the end of the lettering's line. They moved right and darken in bright modes.

**Sky contrast** (worst text on the window, ratio; text ≥ 31 px needs 3:1, the rest 4.5:1):

| Clock (Nov 5) | Stop | Theater night | Vivid | Dynamic |
|---|---|---|---|---|
| 6:20 AM | dawn | 8.66 | | |
| 9:15 AM | morning | 5.13 | 7.40 | |
| 2:30 PM | afternoon | **4.76** (Standard 4.94) | 6.99 | 7.05 |
| 4:05 PM | golden hour | 5.98 | | 8.40 |
| 5:20 PM | dusk | 9.11 | | |
| 8:24 PM | night | 9.97 | | |
| Idle face, 2:30 PM | afternoon | | 6.41 | |

Without the darker bands, Vivid would give 4.56 and Dynamic 4.60 on the afternoon's third band. That passes, but only just, and only through a mild CSS stand-in.

**Glare and red at rest** (960×540 downsample; caps: glare 10% at night, saturated red 25%):

| State | Glare (> 0.5 relative luminance) | Saturated red |
|---|---|---|
| Home, night | 1.0% | 0.0% |
| Home, afternoon | 1.1% | 0.0% |
| Home, afternoon, Vivid / Dynamic (simulated) | 2.4% / 2.4% | 0.0% |
| Idle face, afternoon / night | 0.8% / 0.7% | 0.0% |
| Door alert (5:20 PM) | 0.9% | 1.5% |
| Keyboard | 0.3% | 0.0% |

### Pass-4 audit, item by item

| Pass 4 | Severity then | Now |
|---|---|---|
| 1 TV menu over an app needs an accessibility service | High | **Designed around**: "Home only" path drawn (Home, readout, "you left …"). Feasibility still open → #1 below |
| 2 Sun times fixed | Medium | **Fixed**: HA sun times, fallback, day strip |
| 3 Guests and logos | Medium | **Decided**: names + All apps A to Z with index tabs; no marks |
| 4 Dial full at ten | Medium | **Fixed**: 3 × 6 slots, measured names, Arrange refuses into a full band |
| 5 Plaque titles | Medium | **Fixed**: 2 lines; lettering title 58 → 46 px |
| 6 Afternoon sky under Vivid | Medium | **Fixed in design**: darker bands in bright modes; real panel unmeasured → #2 |
| 7 Door always alert | Medium | **Fixed**: warn by day, alert after sunset or with nobody home |
| 8 Anyone can unlock | Medium | **Fixed as an option**: Unlock from the TV: Allowed / Lock only (Q4) |
| 9 Needle memory untested | Low | Kept; still untested with the family |
| 10 Sky swap in Calm | Low | **Fixed**: Calm keeps the fade |
| 11 Preview glare | Low | **Measured**: 2.4% in Vivid and Dynamic |
| 12 Hard shadows | Low | **Aligned to H9** (down-right) |
| 13 Screens not redrawn | Medium | **Drawn**: All apps, Arrange, Power, Restart, Rename, idle face. Still not drawn: Lobby crashing, profiles → #11 |
| 14 Hints 2 px under the plates | Low | **Fixed**: 6 px |
| 15 Nothing measured on Phoster | Medium | Still open → #3 |

### Pass-5 audit

| # | Problem | Severity |
|---|---|---|
| 1 | **The TV menu over an app** still needs an accessibility service, an overlay permission and a capturable key. The "Home only" fallback works but costs two extra presses and leaves the app. | Medium (was High) |
| 2 | **Picture modes are simulated** with CSS filters (Vivid: saturate 1.35, brightness 1.12, contrast 0.94). A real panel's Vivid may lift dark blues far more. The darker bands give a margin (6.99 vs 4.56), but it has to be measured on Phoster with a camera or the TV's own screenshot. The list of "bright" modes (Vivid, Dynamic, Sports) is a guess. | Medium |
| 3 | **Nothing measured on Phoster** (WebView Chromium 156): two full-screen sky layers fading, focus legibility at 3 m, the needle, and `tools/shoot.js --check`. | Medium |
| 4 | **The dial's focus at 3 m.** The needle is mostly hidden behind the printed names, so focus there is the bold name, a 2 px lift, the lit band square and short needle segments between the bands. It may be too quiet from the sofa. A cream base window under the focused name is the fallback. | Medium |
| 5 | **A read-only dimmer looks movable.** Jam Home's slide dimmer is drawn on the TV, but only OK (on/off) works. Someone may press ↑ expecting brighter, and that moves focus to the dial instead. | Medium |
| 6 | **Restart the TV needs a privilege** Lobby doesn't have (`REBOOT` is a system permission). It would go through Control Freak (ADB or the TV's own API). Unverified. | Medium |
| 7 | **The idle face vs Google TV's ambient mode.** Lobby has to run its idle face inside the launcher, or register as the screensaver (a DreamService). Otherwise Google's ambient mode takes over after its own timeout. | Medium |
| 8 | **Bands are fixed to Watch, Play and Listen.** A seventh video app can't go on Watch. It goes on another band (where it's mislabelled) or stays in All apps. | Low |
| 9 | **Presence decides the door's colour.** If HA thinks nobody's home (phones asleep), the door turns red by day. That's loud but safe. | Low |
| 10 | **The door turns red at sunset by itself** on a calm screen. It's one change, not a flash, and the lettering says it will happen. | Low |
| 11 | **Not drawn:** Lobby crashing or restarting itself, profiles, the letter jump for more than 24 apps, the idle face dimming after 30 minutes. | Low |
| 12 | **A–Z puts "The Criterion Channel" under T.** People may look under C. Sorting could ignore a leading "The". | Low |
| 13 | **Missing sun times fall back to yesterday's times.** After two days of no data, Lobby needs a month table for Bungalo's latitude, which isn't designed. | Low |
| 14 | **The keyboard has no accents or symbols.** Fine for input names; not for search, if Lobby ever gets one. | Low |
| 15 | **The carry outline** in Arrange is a new state (row 8 above) that nobody else has drawn yet. | Low |
| 16 | **The bottom of the lowboard is full:** the socket panel and plate end 6 px above the hints. Any new row needs space from the sky. | Low |

## Questions for Isaac

1. **The app dial as three bands of six (Watch, Play, Listen), or one long scale?**
   *Recommendation:* three bands. You can see how many it holds, long names fit, and the needle still works.
2. **Guests: names plus an A to Z list, with no logos?**
   *Recommendation:* yes. If it's still a problem, add a neutral glyph by kind (▶, controller, note) on the band labels, never a brand mark.
3. **Unlocked door: amber by day while someone's home, red after sunset or when nobody's home** (conflict 12)?
   *Recommendation:* yes. The lettering says when it will turn red.
4. **Should the TV be able to unlock the front door?**
   *Recommendation:* allowed, with hold or press-twice, plus a **Lock only** setting. Use Lock only if guests often hold the remote.
5. **When nobody's used the TV for 10 minutes: Lobby's window face, or Google TV's ambient mode?**
   *Recommendation:* Lobby's window. It's calm, it's the household's own, and it keeps an amber door visible.
6. **Lamps on the TV: switch only (the level shown, not set), or add dimming?**
   *Recommendation:* switch only. One press per lamp from the sofa; dim from Jam Home.
7. **May the sky step darker in Vivid, Dynamic and Sports?**
   *Recommendation:* yes. It keeps the writing readable. Confirm on Phoster which modes need it.
8. **May Restart the TV go through Control Freak?**
   *Recommendation:* yes, behind the confirm card with Cancel focused. It's the fix every failure screen points to.
9. **Still open:** may Lobby run an accessibility service so the TV menu works over apps? Which remote key opens it?
   *Recommendation:* yes, and use Input/Source if the remote has one. Until then, the "Home only" path is drawn.
