# TV launcher (Lobby) · Pass 4

Mockup: `mockups/pass4/tv-launcher.html`. Passes 1–3 are unchanged.

**How to review it without a remote:** press **▶ Tour** above the TV. It steps through 25 states, about 4 s each, with a caption for each. **Next step ›** moves one state at a time. Clicking the TV or pressing a key stops the tour and gives you the keyboard.

**Keys** (also in the legend on the page): arrows move; Enter is OK (acts on release; hold 1 s, or press twice, to unlock the door); Esc or Backspace is Back; H is Home; G or Q opens the TV menu; I opens the TV menu on Input.

**Page controls:** Time of day (Dawn, Morning, Afternoon, Golden hour, Dusk, Night, Live clock) · Motion (Full / Calm) · Home (Lived-in / First run) · Switch 2 (On / Asleep; going On from Asleep shows the device note) · Netflix (Opens / Won't open) · Lobby update (Up to date / 1.4 ready) · Page theme · Jump to (12 states).

All titles, art, colour codes and household details are made up, apart from what the Lobby README already lists: the house name "Bungalo", the app list, the Switch 2 on HDMI 2, the antenna, the four house controls, and "Paused by Isaac".

## What changed since pass 3, and why

Isaac's direction after passes 1–3: *"Everything should feel like it has the same design language, not necessarily the same design. … I don't really want to see identical cards and backgrounds across designs unless there's a clear reason."*

Pass 3's Lobby, NervOS and JamFin had all ended up as the same screen: a charcoal ground, a ribbed black top band, and rows of art-and-plinth cards. Pass 4 keeps pass 3's **functions** and gives Lobby its own **form**.

| Pass 3 | Pass 4 | Why |
|---|---|---|
| Charcoal ground, ribbed top band | **A flat sky window** over a **walnut sill** and a **dark lacquer console face** | Lobby is the one TV screen that stays up when nobody is using it. Furniture is the right shape for that. |
| Continue: art + plinth cards | **Picture frames standing on the sill**, each with a plaque (slot light + title) on the walnut | They read as things on a shelf, not a catalogue. |
| Apps: brand banners in a 6 px surround, toned at night | **The app dial**: nine stations on a tuning scale in three bands (Watch · Play · Listen) plus All apps, with a needle | The banners caused the most glare, the most red and the most sameness with other apps. Nine known names don't need logos at 3 m. |
| Inputs: two keys; empty ports hidden by a setting | **The patch bay**: every port drawn as a socket (Apps, HDMI 1–3, ANT). Plugged sockets carry the device's colour; empty sockets are shown but focus skips them | It's honest about the wiring, so "Show empty inputs" isn't needed. This closes pass-3 audit 7 (the row overflowed with empty ports). |
| House: four keys | **The house plate**: wall-switch paddles (up = on, window lit in the lamp's colour) and a **thumb-turn** for the front door | These are the objects the family already uses for these jobs. |
| TV menu entry in the band | **The TV readout** at the top right ("TV · Theater night · Optical") is the way in, and it shows what the set is doing | "Know what the TV is doing" was a purpose that pass 3 only met after a press. |
| Black ribbed TV menu band | **The console's drawer** rises from the bottom (walnut lip, 262 px). Same keys, choosers and header as pass 3 | Same behaviour (D148), with a face that matches the console. |
| Shutter halves + slatted bar | **A slatted blind** drops over the window, the slatted bar fills under the title, then the blind rises on the picture | It's the same moment, drawn as part of the room. |
| Stripes accent where no art shows | **No accent.** The sky is the screen's colour | One colour field per screen is enough. |
| Night / Day lighting | **The sky follows the time of day** in six flat stops. The console stays dark because it's furniture | The room changes; the cabinet doesn't. |

**Kept from pass 3, unchanged:** OK on release; hold 1 s or press twice for the door; one press to lock; the alert fix as a solid red key with dark text (D84/D119); rows stop at a walnut end with a nudge (D59/D120); "n of N" on the focused row only; the launch rule (hold = max(load, 600 ms), 300 ms open); every failure ends with Try again (orange) + Home (D124); the device-turned-on note once, 15 s, never repeated (D126); update ready shown as a cream light on Settings, never a pop-up; Apps as the TV's own source (D117); the TV menu's header names what's underneath; choosers of 5 rows with "n of N ▲▼" (D177); picture preview after 500 ms rest (D55/D169); no suggested content (D127).

## Purpose
**What the screen is for:** a living room shared by three people. One screen does four jobs:
1. **Get to things fast.** Resume is one press from power-on; any app is at most 10 presses; inputs and lamps are on the same screen.
2. **Know what the TV is doing.** Picture mode, sound out, which source is live (the patch bay's lit Apps square), and the house (lamps, door).
3. **Change inputs and settings** without hunting.
4. **Nothing pushy.** No rows of suggestions, no pop-ups, no brand colour fighting for attention.

It also sits there showing for hours while people talk, eat and walk past. That's why it should look like something you'd put in a room: calm at rest, readable in passing, never loud. The clock and the sky make it useful as a glance even when nobody holds the remote.

## Research
I ran three WebSearch searches. The results were thin on detail; anything below marked *(knowledge)* comes from my own knowledge.
- **Braun Regie receivers (Rams, 1968–72):** a control area and a reception area side by side; ordered rows of keys; colour coding on connectors across the series; the Regie 500's red-orange FM key as the one coloured control (Rams Foundation caption). The search didn't describe the source selector itself. *(knowledge)* Regie and the CET/CE tuners carry a long horizontal tuning scale with a needle, band labels, and push-keys for the source. **Used:** the dial as a long scale with band labels; colour coding as print on sockets; one coloured key at a time.
- **B&O Beo4 / BeoVision:** sources are chosen by name (TV, RADIO, DVD), and MENU brings up the menu for the active source, with source info at the top of the screen (B&O user guides via bnoservice.nl, manualshive). The search didn't describe the on-screen layout. **Used:** the TV menu's header names what's underneath, and the TV readout names the set's state.
- **Apple TV Aerial screensavers:** several sources (MacRumors, 512 Pixels) say day and night versions play according to the time of day; one (Apple Magazine) disagrees. *(knowledge)* They're calm because nothing moves fast and nothing asks for anything. **Used:** the sky follows the time; it changes slowly (a minute-long fade in the real build) and never animates at rest.
- *(knowledge)* Mid-century sideboards and TV consoles: a long low cabinet with a wood top and dark fronts, objects standing on top, a window above. McQuarrie's flat banded skies: horizontal colour strata, a disc for sun or moon, no gradients.

## Design

### Home (night, 8:24 PM)
- **The window (top 55%).** Five flat horizontal sky bands and a flat moon, with a few 3 px stars and three flat cloud pills (matching "57° cloudy").
  - **Written on the glass:** top left, "BUNGALO" (mono), a 70 px Jost Light clock and the date with the weather. Top right, the **TV readout** ("TV · Theater night · Optical") and **Settings** (with its update light).
  - **The sign** for whatever is focused: a mono eyebrow with the facts ("JAMFIN · FILM · 41 MIN LEFT · PAUSED BY ISAAC"), a 58 px title, one line, and the OK action.
  - **"CONTINUE 1 of 6"** sits just above the shelf.
- **The sill (walnut, 68 px).** Continue frames stand on it: 300×169 art in an 8 px dark frame, with progress on the art's bottom edge. Each has a **plaque** on the walnut: a slot window and the title at 24 px.
  - The focused frame lifts 12 px, and its plaque slot lights cream.
  - Five frames show, and the sixth peeks. The row stops at a walnut end mark.
- **The console face** (dark lacquer `#1b1612`):
  - **The app dial** spans 1728 px. Band labels WATCH / PLAY / LISTEN are drawn as bracket lines. Station names are 26 px, each with a printed colour code under it. A tick scale runs along the bottom, with walnut end stops and a needle.
  - **The patch bay** sits bottom left, **the house plate** bottom right.
  - **Hints** are 24 px, along the bottom of the safe area.
- **No orange on Home.** It's a calm screen (D139). Orange appears only on Arrange Home (first run), the device note's Switch to it, Try again, and Update now.

### New elements (all only make sense in Lobby)
1. **The sky window.** Six flat palettes (dawn, morning, afternoon, golden hour, dusk, night). The sun or moon sits on an arc; at dawn it rises, and at dusk it sets behind the shelf.
   - Text sits only on the top three bands, which stay dark enough in every palette. Measured worst case: ink 6.6:1 and secondary ink 4.8:1, both in the afternoon.
   - The lighter horizon bands sit only behind the frames.
   - In the real build the bands cross-fade over a minute when a stop changes. The mockup fades in 1.2 s, or swaps in one frame in Calm.
   - Settings › The window offers **Follow the time of day / Always night**.
2. **Picture frames on the sill.** Continue as objects on furniture, with a plaque light for focus.
3. **The app dial with a needle that remembers.**
   - The needle moves with focus (transform, 140 ms) and lights cream while the dial has focus.
   - When focus leaves, the needle stays where it was, dimmed. Coming back down to the dial returns to that station, not to whatever sits under the frame you came from. The memory is visible, so it isn't a surprise.
   - "4 of 10" shows at the dial's right end only while the dial has focus.
   - One extra press at either end nudges the needle against the walnut stop.
4. **The patch bay.**
   - **Apps** is a lit square: the TV's actual current source while Home shows.
   - **HDMI 2** has a plug in the Switch 2's colour code, with a signal LED and "Signal" or "Asleep".
   - **ANT** is Live TV, "41 channels".
   - **HDMI 1 and 3** are open, dark sockets marked "empty". Focus skips them, so they cost no presses.
   - Focus turns the socket's ring cream and lifts it 4 px.
5. **Wall-switch paddles.** A paddle in a plate, raised at the top when on, with a 20×8 window on the paddle lit in the lamp's own colour (D130, never orange). OK switches the lamp in place, with no toast.
6. **The thumb-turn.**
   - Locked: the bar is horizontal, with a green LED and "Locked".
   - Hold OK and a cream bar fills along the unit's top edge; or press once ("Press OK again") and again within 3 s.
   - Unlocked: the bar turns upright (220 ms rotate, none in Calm), and the whole unit becomes **the solid red key with dark text** (5.5:1), reading "Unlocked · OK locks". The sign reads "The front door is unlocked · Unlocked at 8:24 PM from this TV · OK Lock it". One press locks it.
7. **The TV readout key.** It shows what the set is doing, and OK opens the TV menu. While the menu is open it reads "menu open ▼", and the sign says "Open below", so each value shows once (D105).
8. **The console drawer** (the TV menu).
   - Keys: Input · Picture · Sound · Sound out · Sleep · Front door · Settings, each with a base window.
   - The header shows a lit slot, "TV menu", **what's underneath** ("over Home", "over The Copper City · Jamfin"), hints and the clock.
   - Choosers rise above the key. The key shows ▲ while its chooser is open.
   - The Input chooser marks Apps / Switch 2 / Live TV with the square; HDMI 1 and 3 show as "empty".
9. **The slatted blind** (the title card).
   - It's a full-screen ribbed dark layer with a walnut bottom rail. It drops from the top in 300 ms and shows the eyebrow, title, line and a 12-slot slatted bar that fills over the load. It holds max(load, 600 ms), then rises on the picture.
   - **Failure:** the blind stays down and the slats stop and dim. **No signal** draws the HDMI 2 socket itself, 150 px. Every failure ends with **Try again** (orange) and **Home**.
   - Calm: a 140 ms fade in and out.
10. **A note in the window** (HDMI-CEC). A lacquer card with a walnut bottom lip appears in the sky's right-hand clear zone: "HDMI 2 · JUST NOW · ● Switch 2 turned on · **Switch to it** / Stay on Home". The sign behind it keeps describing what was focused before, so the news is said once.

### Other screens
- **All apps:** a full lacquer screen with a walnut top rule. "On the dial · in order" (9) and "Not on the dial" (RetroArch, YouTube Music, Sendspin, Play Store, Android settings). Keys carry the printed colour code. Back returns to the All apps station on the dial. Pass 3's Move/options flow is still the plan; it isn't redrawn.
- **Settings:** a list and its detail. Rows light a leading-edge window (D149). Rows: Picture, Sound, Sound out, Inputs (When a device turns on: Ask / Switch to it / Stay here), The window (Follow / Always night, with the six palettes shown as swatches), The dial, About.
  - About shows "Update ready" in the list once, and **Update now** is the screen's one orange.
  - Updating runs the blind ("Updating Lobby"), then returns Home with the toast "Lobby is up to date · 1.4".
- **First run:** the shelf is one recess ("Nothing on the shelf yet. Films, shows and games you start will stand here.") with **Arrange Home**. The sign says "Hello. This is Lobby." with no repeated action. Nothing is suggested.

## Language check
**What ties Lobby to the family:**
- Jost for words and IBM Plex Mono for labels; the same type sizes as the other TV apps (22 px minimum, 24 px hints, a 58–84 px display title).
- Indicator windows as the shared vocabulary: round LEDs for status (signal, Locked, update), the square for the current choice (Apps on the patch bay, the current mode in choosers), slots for "this one" (plaques, keys). They're always a dark recess, and lit means flat colour.
- The state words: On / Off / Locked / Unlocked / Signal / Asleep / empty.
- Focus is always a flat cream light at the item plus a small lift. The colour snaps and only transform moves.
- One orange per screen, and none on calm screens.
- The alert fix is the solid red key with dark text.
- Walnut marks ends: the shelf's end mark, the dial's stops, the drawer lip, the screen top rules.
- Ribs only on dark surfaces (the blind).
- Every failure ends the same way.
- The TV menu has the same keys, header and chooser behaviour as pass 3's shared band.

**What someone coming from another app would recognise within a second:** the type, the cream focus light, the little dark windows with lit LEDs, the walnut, the red door key, and Try again in orange. Coming from JamFin, the art on the shelf reads as "things to watch" immediately. Coming from Jam Home, the paddles with lit windows and the thumb-turn are the same objects the family taps on the kiosk.

**What's deliberately not shared:** the sky, the sill, the console face, the dial, the patch bay, the frame shape and the blind. None of them appears in another app's mockup.

## Rules I broke

| # | Rule (source) | What I did instead | Why Lobby needed it | Verdict |
|---|---|---|---|---|
| 1 | D53, BIBLE TV cards: "TV cards are art + plinth everywhere" | Continue is framed art standing on the sill, with a plaque on the walnut; no plinth | The plinth row is exactly what made Lobby, JamFin and NervOS identical. Lobby isn't a library. | **App-local**: keep art + plinth for the media libraries (JamFin, NervOS); drop it as a device-family rule |
| 2 | D122: real app banners in a 6 px surround, toned at night | No banners. Apps are named stations on a dial with a printed colour code (D89) | Banners were the main glare and saturated-red source and carried other companies' design onto the family screen. Nine known apps are found by name. | **App-local**: D122 applies only where banners are shown |
| 3 | D3 / BIBLE §7 W1: one focus grammar per device, the base-window selector | Focus takes the element's shape: plaque light, needle, socket ring, switch base window, header underline, leading edge in lists | A single base window under a sky, a dial and a socket would be drawn where it doesn't belong | **Language-wide, reworded**: "focus = a flat cream light at the thing + a small lift; colour snaps; only transform moves". Drop "one shape per device". |
| 4 | BIBLE §2 accents: one per screen in a clear zone (and D123/D178 placement) | No accent at all | The sky is already the screen's colour field; an accent would be a second one | **Drop** as a requirement; accents become optional, **app-local** |
| 5 | D121 / D172: TV Day vs Night lighting | The sky follows the time of day; the console face never changes | It's furniture in a room whose light changes. It also removes a whole Day palette for the cabinet. | **App-local** now; candidate **device family** rule: "a TV home may follow the time of day instead of a Day/Night switch" |
| 6 | A1: ribs only on black bands that are fixed surfaces | Ribs on the blind, a moving full-screen layer | The blind is a slatted thing; ribs are what it's made of | **Language-wide**: keep "ribs only on dark surfaces"; **drop "fixed"** |
| 7 | BIBLE title card (approved): shutter halves + slatted bar + Stripes | A blind dropping from the top, the slatted bar under the title, no Stripes | A shutter belongs to a screen; a blind belongs to a window | **Device family**: "the title card is an opaque cover that closes over the screen, with the slatted bar as load progress". The cover's shape is **app-local**. Isaac decides (Q4). |
| 8 | D148: one 230 px Guide band shared by every TV app (its face) | The console drawer: 262 px, a walnut lip, keys with base windows | It's Lobby's own furniture, so its drawer should match | **Device family** for behaviour (bottom, header names what's underneath, ≤1 orange, choosers above keys). The face is **app-local**. |
| 9 | BIBLE §4: no knobs or curved input controls | The thumb-turn's bar rotates 90° to show locked or unlocked | It's a picture of the real lock showing its state, not a rotary input. OK still does the work. | **Language-wide, reworded**: "no rotary *inputs*". A drawing of a real object may rotate to show state. |
| 10 | Walnut is a rule (a thin line) | Walnut as a surface: the 68 px sill and the drawer lip | The sill is the piece of furniture the frames stand on | **App-local** |
| 11 | D117/D118: no source indicator on Home | The patch bay shows Apps as a lit square: the TV's real current source | It answers "what is the TV doing?" truthfully, and an HDMI input is never marked while Home shows | **Device family**: "a TV home may show the true current source (Apps); never an HDMI input it isn't on" |
| 12 | Pass 3 (Lobby): empty ports hidden by default | Empty sockets always drawn, never focusable | A patch bay that hides ports lies about the wiring; skipping them costs no presses | **Language-wide** principle: "show what's there; focus skips what you can't act on" |
| 13 | Lobby focus engine: across rows, go to the nearest item | The dial always returns to the needle's station | The needle makes the memory visible, so it reads as the dial staying tuned | **App-local** (an element that *shows* its memory may use it) |
| 14 | D89: printed colour codes are small marks on keys | The plugged socket is filled with the device's code colour (40 px circle) | It's how cables and sockets are coded on hi-fi gear (Regie connectors) | **App-local**, inside D89 (still never lit, never a state) |

**Floors kept:** safe area 96/54 px (checked on every state); text ≥ 22 px and hints 24 px; transform and opacity motion only; focus ≤ 150 ms with snapped colour; flash and glare floors (measured below); Calm swaps without bare frames; opaque, full-bleed launch layers.

## Audit
Checked with Playwright (Chromium, `chromium.launch()` with no options). The page was 1500 px wide at deviceScaleFactor 1.31, so the TV renders at about 1920 px. I also checked 390 px wide in the dark scheme, and 1300 px in the light scheme. What I ran:
- all 25 tour states through `LOBBY.runStep`;
- a real-keyboard run:
  - the shelf to its end (bump), then down to the bay and along to the door;
  - Enter **held 1.2 s** (the door unlocked), then Enter (locked);
  - G and → for the Picture chooser, and ↓×6 (it scrolled, with "n of N ▼");
  - Back twice, up to Settings, then the Inputs detail and choosing an option;
  - H for Home;
- all six skies, the Calm TV menu over a film, and the jumps.

**Checks on every state:**
- every visible TV text node ≥ 22 px, and hints ≥ 24 px;
- all text inside the 96/54 px safe area, except the peeking sixth frame;
- no ellipsised text;
- text on the sky ≥ 4.5:1 against every band it overlaps (3:1 for text ≥ 31 px);
- no JS or console errors;
- `scrollWidth` is 390 at 390 px.

**All passed after the fix pass.** About 50 screenshots are in the scratch dir, not the repo.

**Fixed in the fix pass:**
- several items showing focus at once after a jump (focus now clears every `.f`);
- the date overlapping the sign's eyebrow;
- the patch bay's state line colliding with the hints;
- hint key caps at 22 px (now 24);
- "Bungalo" 1 px above the safe line;
- the sign line ellipsising (the facts moved into the eyebrow);
- the afternoon sun touching the TV readout;
- the dawn and dusk suns hidden behind the sill;
- the device note repeating itself in the sign;
- first run showing "1 of 6" and a doubled Arrange Home;
- About saying "1.4 is ready" twice;
- the sign repeating the TV values while the drawer was open;
- All apps' second line being unreachable with ↑/↓.

**Glare and red at rest** (a 960×540 downsample; caps: glare 10% at night, saturated red 25%):

| State | Glare (> 0.5 relative luminance) | Saturated red (linear R/(R+G+B) ≥ 0.8) |
|---|---|---|
| Home, night | 1.0% | 0.0% |
| Home, afternoon (brightest sky) | 1.1% | 0.0% |
| Home, golden hour | 1.0% | 0.0% |
| TV menu + Picture chooser | 0.8% | 0.0% |
| No signal | 0.6% | 0.0% |

Dropping the brand banners took the worst red from 1.6% (pass 3, untoned) to 0.0%. The unlocked door key is the only saturated red, at about 1% of the screen.

| # | Problem | Severity |
|---|---|---|
| 1 | **The TV menu over an app still needs an accessibility service, an overlay permission and a capturable remote key** (carried from pass 3 #1–2). Without them, the drawer exists only on Home, where the TV readout opens it. | High |
| 2 | **Sun times are fixed in the mockup.** The real sky needs the day's sunrise and sunset (HA's `sun.sun` through Control Freak), or the "dusk" palette shows at 7 PM in June daylight. It also needs a rule for when data is missing (fall back to the clock). | Medium |
| 3 | **App identity without logos.** Nine names plus a 28×4 px colour code. Fine for the family, but a guest looking for "the Netflix" won't find a red N. Isaac's call (Q2). | Medium |
| 4 | **The dial is full at ten stations.** A long name (YouTube Music, 13 characters) won't fit the 159 px pitch at 26 px. More apps go to All apps, or the dial needs two scales. | Medium |
| 5 | **Plaque titles get one line of about 22 characters** at 24 px. Longer titles need a short name or a wrap. The sign always shows the full title. | Medium |
| 6 | **Afternoon is the tightest sky:** secondary ink is 4.8:1 on the third band. It passes, but a TV picture mode such as Vivid or Dynamic pushes the blues lighter. The sky should be checked against the TV's real picture modes on Phoster. | Medium |
| 7 | **An unlocked door is always an alert** (carried B6, pass 3 #5). The red key is loud on a calm daytime screen. | Medium |
| 8 | **Anyone with the remote can unlock the door** (carried pass 3 #4). | Medium |
| 9 | **The needle's memory is new behaviour.** Going ↑ then ↓ returns to the dial's last station, not the one under your frame. It's visible, but untested with the family. | Low |
| 10 | **The sky's changes in Calm.** The mockup swaps in one frame. On the TV a stop changes over a minute, which is far under the flash floor even as a fade, so Calm should keep the slow fade rather than swap. A one-frame night → afternoon swap would be a big luminance change. | Low |
| 11 | **The picture preview on Home filters the sky.** Vivid and Dynamic make the sky the brightest thing on screen while you choose. Glare under preview wasn't measured. | Low |
| 12 | **Hard offset shadows** under the frames (no blur) are a new depth cue, not one the family already uses. They read as objects on a shelf, but they're another thing for the bible to name or drop. | Low |
| 13 | **Not redrawn this pass:** All apps Move/options, Sleep & power with Restart the TV, renaming an input, screensaver/ambient (the sky may *be* the ambient mode), Lobby crashing, profiles. Pass 3's designs stand for those, except the screensaver. | Medium |
| 14 | **The hints line sits 2 px under the console's bottom plates** (990 vs 988). It passes, but there's no room left at the bottom of the face. | Low |
| 15 | **Nothing measured on Phoster** (WebView Chromium 156): two full-screen sky layers cross-fading (opacity only, but full-screen), focus legibility at 3 m, and `tools/shoot.js --check`. | Medium |

## Questions for Isaac
1. **Is "furniture" the right shape for Lobby: a window, a sill and a console face, instead of pass 3's rows?**
   *Recommendation:* yes. It's the only TV screen that sits idle in the room for hours, and this is the first version that doesn't look like JamFin.
2. **Apps as named stations on a dial, or real app banners?**
   *Recommendation:* names on the dial. If guests struggle, add a small monochrome mark next to the name, never a full-colour banner.
3. **Should the sky follow the time of day, or stay night?**
   *Recommendation:* follow the time, driven by HA's sun times, with **Always night** in Settings for anyone who finds it busy. It never gets brighter than the mid-tone afternoon sky.
4. **Can the title card be a blind on Lobby, while JamFin and NervOS keep the shutter?**
   *Recommendation:* yes. Make the bible rule "an opaque cover + the slatted bar", and let each app draw its cover.
5. **Drop the accent on Lobby?**
   *Recommendation:* yes. The sky is the screen's colour. Make accents optional in the bible.
6. **Should the needle remember the last station?**
   *Recommendation:* yes, because you can see where it is.
7. **Show empty HDMI ports (skipped by focus) instead of hiding them?**
   *Recommendation:* yes. It's honest, and it costs no presses.
8. **Still open from pass 3:** may Lobby run an accessibility service, and which remote key opens the TV menu? Can the TV unlock the door, and is an unlocked door warn by day and alert after dark?
   *Recommendation:* as in pass 3: yes, map Input/Source if the remote has one, keep unlock as hold or press twice, and use warn by day, alert after sunset.

Sources:
- [Braun Regie 510 (1972) by Dieter Rams (Artchive)](https://www.artchive.com/?p=212577)
- [Rams Foundation: Regie 500 caption](https://rams-foundation.org/?p=5229)
- [Brown Direction 520 (hifi-wiki)](https://hifi-wiki.com/index.php/Brown_Direction_520)
- [Beo4: navigate menus (manualshive)](https://manualshive.com/en/manual/bang-and-olufsen/beo4/471123?page=8)
- [BeoVision 11 with Beo4 user guide (bnoservice.nl)](https://bnoservice.nl/media/manuals/BEOVISION/Beovision%2011%20with%20Beo4/User%20Guide_EN_31318dc1b06063be946dde5deea1c0b4.pdf)
- [Apple adds 21 new Aerial screen savers (MacRumors)](https://www.macrumors.com/2016/12/16/apple-tv-new-aerial-screen-savers)
- [Expanding Aerial, the Apple TV's screensaver (512 Pixels)](https://512pixels.net/2016/01/expanding-aerial-the-apple-tvs-screensaver/)
- [Apple TV screensavers (Apple Magazine)](https://applemagazine.com/apple-tv-screensavers-97/)
