# NervOS · Pass 5: the console, all the way through

Mockup: `mockups/pass5/nervos.html`. Passes 1–4 are unchanged.

**Tour.** Press **▶ Tour** above the TV. It steps through 38 states, about 3 s each, and names each one under the TV. Any key on the TV, or any Jump button, stops it. The Jump row reaches every screen directly, including the seven that are new this pass (Theater player, Power, Settings, Keyboard, Netplay room, Signal lost, Covers view).

**Keys** (click the TV first): arrows move · Enter = A / OK (acts on release; hold 1 s on Quit, Reset, Stop, Restart, Shut down, Desktop mode) · Esc = B / Back · G = Guide · M = ≡ · Y = spines / covers · X = delete on the keyboard · `[` `]` = L1 / R1 · `,` `.` = LT / RT, which are also ⏮ ⏭ on the HA remote · `2` = a second controller presses A · any key wakes the attract board. On the keyboard screen a physical keyboard types straight in.

**Page controls:** Lighting (Night / Day), Motion (Full / Calm), Hints for (Gamepad / HA remote), Controllers on (1 / 2), Shelf view (Spines / Covers), and the dashed box for the section names (approved / plain words). Everything shown is made up.

Pass 4 is the direction Isaac's note asked for ("same design language, not necessarily the same design"), so pass 5 keeps it whole: the console on Home, media spines, divider cards, bookends, the display stand, the section slide, the media going into the slot, Pick up a controller, the film-frame save strip and the attract mode. The work this pass is (1) carrying the console into every screen pass 4 didn't redraw, (2) fixing pass 4's audit, and (3) adopting the RULES-TIERS recommendations.

## What changed since pass 4

| Pass 4 | Pass 5 | Why |
|---|---|---|
| Spine titles only vertical; the name read only on the shelf screens' stand (audit 1, High) | Every shelf edge is a **name rail**: the focused item's name in 46 px, horizontal, cream on walnut. On Home both shelves (Played lately, Favourites) have one; only the shelf that has focus says a name, the other just says what it is ("Favourites · 14") | H1 and TV12: "the focused item's name is readable horizontally at ≥ 46 px". Pass 4 broke this on Home's Favourites and Played lately |
| Spines only | A **Covers view** (Y, ≡ › Show covers, or Settings › Library › Shelf view): every game face-out with the title its box prints, about five a shelf. The stand stops showing the cover and shows **a picture from the game** (a still for films) | Non-gamers find a game by its box, not its spine. The stand can't repeat the cover that's already on the shelf (never twice), and a screenshot fills the wall |
| Spine colours straight from the art; the cart label was often the art's orange (audit 2) | Spines are drawn from the **system's template + one colour taken from the cover, clamped** (H11): kept out of the orange and red ranges (saturation ≤ 0.30 for hues 335°–50°), lightness held in 0.22–0.70, then stepped until the title ink reaches 4.5:1. Settings › Library shows three examples: cover → colour taken → colour kept → spine. "One per system" is the fallback | Scrapers give covers, not spines. The colour is content, but a sampled orange would sit next to the one orange key |
| Focus on thin dark spines was a 9 px window on a 54 px case (audit 3) | **The shelf rail**: one dark groove runs along every shelf top; the segment where the focused thing stood lights cream, 16 px wider than the thing. The 34 px lift stays | A light at the thing, wide enough to see at 3 m on any spine, and it's a window (the groove is always visible, H3) |
| LT / RT were the only divider jump (audit 4) | **⏮ ⏭** on the HA remote do the same; hints follow the input. Any input can also use **≡ › Jump to a letter**, which lists the ranges with a count each | The Jam Home remote has Previous / Next on its transport, no triggers |
| Uplink (4 things) and Short films (3) left bare wall (audit 5) | **Showcase**: a section with five things or fewer stands them face-out on one wide shelf, every name on the shelf edge, no stand. A sparse shelf inside a bookcase (Short films, Couch co-op, Game Boy Advance) stands face-out on its own shelf | Fills the wall honestly; a few things look better face-out, as in a shop |
| Attract showed position with round lights (conflict 6) | **Slots** in the board's ribbed plate, the current one lit cream. The "1 of 5" text is gone (it said the same thing twice). Renamed **attract board** (H18). After 10 minutes the board dims to 30% and stops changing; the words stay readable | Conflict 6 B; H10 |
| Launch card in Day was light | Dark in Day too (conflict 5 B) | Assumed, pending Isaac |
| Colour bars on the console reached `#efd58a`, lighter than control orange | Darkened to `#3f2210`–`#b0652f` (relative luminance 0.19 vs orange 0.37) | CL7: decorative colour stays darker than control orange |
| One "soft" drop shadow, drawn several ways | One shadow kind: a hard offset, 6 / 8 px down-right (light from top-left), on media faces, machines, bookends and choosers | H9 |
| Not redrawn: Guide band, Power, Settings, keyboard, netplay room, Signal lost, Theater player | All drawn as parts of the console (below) | The brief: the whole app should feel designed, not just Home |

### The console, carried into the rest of the app
- **Guide band = the console's deck.** Same 230 px ribbed band and the same keys in the same order (Resume · Save · Load · Picture · Reset · Quit game). New: the game's **media stands in a slot on the band's top edge**, as it did when it went in, and the header carries the **ports** (who is plugged in). Picture opens a five-row chooser above its key; while it's open the key shows ▲ instead of the value. Save and Load swap the key row for the film strip (unchanged). Steam and streams keep their short key rows and show no media.
- **Theater player = the same deck.** The house player keys (Play · Back 10 s · Forward 30 s · Subtitles · Audio · Chapters · Stop film), the timeline on the band's top edge with NOW as a cream rule, "1:12:04 of 1:58:30 · Ends at 21:58". Subtitles pops above its key. **Chapters** reuse the film strip: five frames at a time, "Chapter 6 of 12". No media in a slot: films never go into the console.
- **Power = the console's switch panel.** A dark panel rises from the bottom with a walnut edge, Home dimmed behind it. Six plates in a row: Cancel (focused first) · Sleep · Restart · Shut down · Desktop mode · Settings. The four actions are **levers in a slot**: down at rest, half-way when armed ("Press A again"), up when done. Restart, Shut down and Desktop mode take two presses or a 1 s hold (the fill runs along the top edge) and disarm after 3 s. Sleep is one press. The line under the plates says what the focused one does. No orange.
- **Settings = the rear panel.** The page rail is the section slide stood on end (Display · Library · Steam · Streaming · Films · Netplay). The pane is a dark panel; its heading is the page's purpose ("How games stand on your shelves."), not the page name again. Two-way settings are **two-position slide switches** (the chosen side pressed in, with its square lit); others show their value and ›. Library carries the spine-making diagram.
- **Keyboard = keys on the deck, writing on a label.** The 12-unit grid sits on the ribbed deck with a walnut front that carries the hints (A Type · X Delete · Y Space · ≡ Done · B Cancel). The code is written on a cream label, the same paper as a room card, in mono capitals with a steady caret and "5 of 6". At six characters focus jumps to Done (the one orange). Shift is pressed in when on.
- **Netplay room = the host's console.** Moonlit Duel's arcade board stands in Sam's console; the deck says "On Sam's NervOS" and "Linked · 18 ms, smooth" with a green light; the walnut front has two **ports, which are the seats**: port 1 is Sam (printed colour tag, Host · Player 1), port 2 is "Free seat". Take seat 2 (orange) plugs you in ("Living room · You · Player 2"), then I'm ready, then a lit slot: "Waiting for Sam to start". The host starts it and the launch reads "Netplay · with Sam · you are Player 2".
- **Signal lost = the computer pops back out of the slot**, its light in the broken offline form. "Offline · Uplink", "Lost the picture from Study PC", why, what to do (bold), **Try again** (orange) + Home, and the mono code. If Try again fails: "Still no answer from Study PC … Check that it's switched on and on the home network, then try again."

## Language check (the 15 items)

| # | Language item | Held / adjusted | Where |
|---|---|---|---|
| 1 | Jost + IBM Plex Mono | Held | Mono for eyebrows, port numbers, divider tabs, the room code, the error code; Jost for everything else |
| 2 | Indicator windows | Held, extended | Round LEDs (On, Linked, joined), the offline ring (Laptop, Signal lost), squares (Favourite, chosen chooser rows, chosen switch side), slots (Paused, Waiting, attract position, Trying), sockets as object-shaped windows (ports, seats), and the shelf-rail groove |
| 3 | Shapes have meanings | Adjusted | Round is status only now (attract position moved to slots, conflict 6). Slot = "the one now" (attract board, Waiting for Sam) or running |
| 4 | Cream is the light | Held | Lit rail, plugs in sockets, focus windows, NOW rule, lit slots |
| 5 | Colour + shape + word | Held | Low battery = amber words + ▲; offline = ring + "Offline"; On = green + "On" |
| 6 | Red means alert | Held (no alert drawn) | NervOS has no alert state. Red only appears inside game art |
| 7 | Orange: one thing to do now | Held | Continue, Resume, Play (paused film), Start with 2 players, Take seat 2 → I'm ready, Done, Try again. None on shelves, Power, Settings, attract, launch |
| 8 | Focus = a light at the thing + a lift | Adjusted | On shelves the light moves from a window on the spine to the rail segment under it (wider); everything else keeps its base or leading-edge window |
| 9 | Chosen things press in | Held | Chooser rows, switch sides, Shift |
| 10 | Walnut | Held | Shelves, name rails, bookends, console fronts, the keyboard's front, the band's and panel's top edges |
| 11 | Things end visibly | Held | Bookends on every shelf, including the showcase; chapter strip "6 of 12" |
| 12 | Calm at rest | Held | Shelves and Home have no orange; attract runs only when idle and dims |
| 13 | Motion short, causal, once | Held | Media into slot 480 ms, lever 200 ms, panel 260 ms, plug 300 ms; Calm makes them ≤ 150 ms fades |
| 14 | Say it once | Adjusted | Fixed three repeats from pass 4: attract "1 of 5" + lights, the Played-lately labels vs. the rail, covers on shelf + stand. Settings headings no longer repeat the page name |
| 15 | Honest objects, drawn flat | Held | Console, cartridges, shelves, switch panel, rear panel, keyboard deck, room card. No grain, glow or metal |

Floors (measured with Playwright, all 38 tour states, plus Day, Calm, remote hints and plain names): no TV text under 22 px; hints at 24 px; no text outside the 96 / 54 safe area except spines running off the shelf's right edge and the dimmed neighbour shelves (peeks); contrast of every new pair ≥ 5.7:1 (name rail 9.6, its sub-line 8.2 night / 7.5 day, low battery amber 7.0, chooser sub-text 6.4, settings help 6.7, switch-off label 7.3, Day dim on wall 5.7); dimmed peeks 3.7:1 (exempt as peeks).

## Conflicts assumed (all pending Isaac)

| # | Conflict | Assumed | How it shows here |
|---|---|---|---|
| 1 | Warn shape | **B**: amber + ▲ + word | Controller 2 "▲ Low battery · 12%" in amber ink. The port's round light stays green for "joined"; the warn lives in the words (one light per port) |
| 2 | Row ends | **A**: stop | Every shelf stops at a bookend with a nudge; ⏮ ⏭ / LT RT jump |
| 3 | Windows in Day | **Decide by ground** | Keys on the light wall: an unlit window is a hairline groove, lit = cream in a dark rim. Dark objects (deck, bands, panels, shelves) keep the dark recess |
| 4 | Launch card | **B**: shared rule, own cover | The media goes into the slot; opaque, slatted bar, max(load, 600 ms), B cancels, Calm fade |
| 5 | Day title card | **B**: dark even in Day | The launch and the return are dark in Day. Signal lost too (an opaque full-bleed screen) |
| 6 | Round = position? | **B**: slots | Attract board position in slots. Everything else gives position in words ("3 of 13", "Shelf 1 of 6", "Chapter 6 of 12") |
| 7 | Ribs | **B**: on any dark surface, never behind scrolling rows | Decks, bands, the attract plate, machine vents (machines no longer stand on scrolling rows: Uplink is a showcase) |
| 8 | Accents | **B**: optional, at most one | Colour bars on Home's console front; Stripes on the launch deck. No accent anywhere else |
| 9 | House objects | **B** (HA owns them) | NervOS draws none. "Wake it from Jam Home" is text only |
| 10 | Guide band | **B**: shared behaviour, own face | Same key order, header, chooser and strip rules; the face is the console's deck with the media in its slot. Applied the same way to the player band (TV6) |
| 11 | Menus beside a list | **B for keys and bands, A for rows in a list** | Picture and Subtitles pop above their keys; shelf options pop above the hints. Settings choosers would pop beside their row (not drawn; a toast says so) |
| 12 | Front door | n/a | — |

## Holes applied

| Hole | Applied as |
|---|---|
| H1 Rotated text | Spine titles top to bottom at 24 px, one direction; the focused name always also shows horizontally at 46–60 px (stand, name rail, showcase rail) |
| H2 Objects as UI | Console, shelves, switch panel, rear panel, keyboard deck, room card: flat, one realism level, windows and keys on them |
| H3 Object-shaped windows | Sockets (ports, seats) and the shelf groove behave as windows: visible when off, flat cream when on |
| H7 Timelines | Theater timeline on the band edge, NOW as a cream rule; chapters as a strip with position in words |
| H9 Shadows | One kind (hard offset, down-right, light from top-left), never on text |
| H10 Idle faces | Attract board: own games only, one change per 10 s, static in Calm, dims after 10 min, any key wakes and the press isn't passed on |
| H11 Content colour | Spine clamp (above); the attract board uses the game's own dark palette colour with ink picked by contrast |
| H12 Signature moments | Media into the slot (480 ms), a port plugging in (300 ms). Lever flips and the power panel are plain motion, not moments |
| H13 Visible memory | A shelf remembers its last spine and shows it: on neighbour shelves the remembered spine sits 12 px proud of the others |
| H14 Connections | No cords (cords are Jam-Dash's). The netplay link is a light + words; a lost stream is the machine out of its slot in the offline form |
| H15 People | Sam and "Living room" are a printed colour tag + name; no faces, no places |
| H16 Capacity | Table below |
| H17 Real-world claims | "Linked · 18 ms" and "stopped answering 8 seconds ago" come from real data (netplay ping, stream timeout) or aren't shown |
| H18 Glossary | Renames below |

**Capacity (H16).** Shelf: any length; divider cards from 9 items (4 ranges; past about 60 items, one tab per letter), position in words. Showcase: 1–5 things; a sixth turns the section into a bookcase. Played lately: 4. Ports: 4 (rooms: 2–4). Save strip: 4 frames, fixed. Chapter strip: 5 frames visible, "n of N". Choosers: 5 rows, then "n of N ▲▼". Attract board: 5 games (slots; never more than 10). Section slide: 5, fixed. Settings: 6 pages, at most 6 rows a page (no scrolling). Power panel: 6 plates. Keyboard: fixed grid; the code field states its length ("5 of 6").

**Glossary (H18).** "Console" is used by Lobby (console face), Jam-Dash (console ladder) and NervOS. NervOS's entry becomes **games console** (the on-screen words "In the console" stay, because that's what it is to the family), and its top surface the **console deck** (Jam Home calls its TV card a "deck"). "Marquee" stays JamFin's: NervOS's idle screen is the **attract board**. Pass 4's "lip" is now the **shelf edge** (Jam-Dash has a bench lip), and a shelf edge tall enough to carry a name is a **name rail**. New: **shelf rail** (the lit groove), **showcase**, **switch panel**, **rear panel**.

## Rules I broke

| # | Rule (source) | What I did instead | Why NervOS needed it | Verdict |
|---|---|---|---|---|
| 1 | TV5 / D148 Guide band face; conflict 10 | Kept the band's size, keys, order and choosers; drew the media standing in a slot on its top edge and the ports in its header | It is the console you put the game into; the band should look like it | **Device: TV** for behaviour and key order; **app-local** face (conflict 10 B) |
| 2 | TV6 "one player band for JamFin and NervOS Theater" | Same keys, order, timeline edge and prompts; NervOS's deck face | Moving between the two apps is a remote press away on different machines | **Device: TV** behaviour; **app-local** face. Reword TV6 like TV5 |
| 3 | TV20 / D153 Power "a sheet" of rows | A switch panel of plates, levers for the four actions; Cancel focused first, no orange, Sleep one press | The console's power switch is where power lives | **Device: TV** for the behaviour; **app-local** form |
| 4 | CT1 "a rocker is on when up" | Power levers go **up to act** (Restart up = "restarting") | A lever that's thrown is "done"; these switches have no on/off state | **Open**: CT1 should say it applies to switches with a lasting on/off state. Question 3 |
| 5 | Pass-3 rule 16 / CT3: TV settings on/off = square window + word | A two-position slide switch: the chosen side pressed in, its square lit | Settings is the console's rear panel; slide switches are its controls, and they show both choices at once | **Language** stays (chosen presses in, square shows it); the switch form is **app-local** |
| 6 | TV3 / TV1 "a focus light under the art", the base window on the spine (pass 4) | On shelves the light is the rail segment under the thing; no window on the spine | A 9 px window on a thin dark spine was too small (pass 4 audit 3) | **Language** (a light at the thing, in a visible window); **app-local** place |
| 7 | CT6 Never twice, on the stand in Covers view | The stand shows a game screenshot, not the cover | The cover is already on the shelf | Not a break: logged because it needs screenshots from the scraper (Audit 9) |
| 8 | H14 "broken connections dashed amber" | Signal lost shows the machine's offline form, no dashed cord | The cause is a device offline (ST2), and cords are Jam-Dash's | **Language**, clarified: when the cause is a device, the offline form wins over a dashed connection |
| 9 | TV4 / conflict 5 Day cover | Signal lost is dark in Day too | It's an opaque full-bleed screen over a dead stream; a flash to light and back is worse | **Device: TV** (an opaque full-bleed TV screen is dark in Day) |
| 10 | D127 no suggested content | Attract board, idle only (kept from pass 4) | NervOS's idle face | **App-local** under H10 |
| 11 | TY10 / H1 rotated text | Kept on spines, with the name rail | Density | **Device: TV**, per H1 |
| 12 | Pass 4's "rows of spines everywhere" | Showcase for ≤ 5 things | Bare wall (pass 4 audit 5, TV12's 15% empty-ground limit) | **App-local** |

## Audit

Checked with Playwright (`chromium.launch()`, no options) at 1532 px wide with deviceScaleFactor 1.31 (the TV renders at about 1920 px):
- all 38 tour states screenshotted and measured (text size, safe area);
- a keyboard run: R1, two divider jumps, ≡ › Jump to a letter › M–R, Y to Covers and back, Uplink, Join with a code, typing `moon42` on the physical keyboard, Done (focus had jumped there), Take seat, I'm ready, the host starting, the launch, Guide, Picture › Smooth, holding Quit for 1 s, Return, Power › Sleep, waking, Power › Settings, toggling Shelf view;
- Day + HA remote hints + Calm + plain names on Home, Archive, Uplink, Power, Settings, Keyboard, Room, Signal lost, both bands, Players, Launch and Attract;
- the page at 390 px in the dark scheme: `scrollWidth` 390.

Screenshots are in the session scratch folder (`p5n/shots/`), not in the repo. No JS or console errors.

**The fix pass corrected:** the lit rail segment hidden under the plank (stacking order); Covers view leaving the left half of the screen bare (the stand now shows a screenshot); the shelf options chooser covering the focused title (it now pops over the stand's picture); "Players" running into the hints in the band header; chapter labels past the safe edge; settings help text touching the next row; the Signal-lost machine hiding its own offline light inside the slot; the room-code placeholder clipped on its card; "6-letter code" (codes have digits); the bookcase's top peek touching the section sub-label.

| # | Problem | Severity |
|---|---|---|
| 1 | **The Steam fallback chord is still unverified** (carried from pass 3). If Steam swallows ⧉ + ≡ under gamescope, the house band in Steam games is reachable only from the HA remote's Guide, the keyboard, or Steam's own Exit game. The game page and launch card say how; it has to be tested on the Aero | High (hardware) |
| 2 | **Spines still need a sofa test** with a 200-game library. The name rail and Covers view answer pass 4's High, but nobody has scanned a real shelf from 3 m yet | Medium |
| 3 | **Power levers go up to act**, which clashes with "up = on" (CT1) for Shut down: the lever goes up to turn something off | Medium |
| 4 | **⏮ ⏭ need the HA bridge** to forward the remote's Previous / Next to NervOS as divider jumps. I haven't checked which remote keys the MQTT bridge forwards today | Medium |
| 5 | **The showcase switches form at six things.** A third computer or a third room turns Uplink from one face-out shelf into a bookcase, a visible layout change for one new item | Medium |
| 6 | **Two name rails on Home.** The Favourites rail sits at the bottom of the screen, about 800 px from a focused spine at the left; the eye has to travel. Only one rail names something at a time, but it's still two places to look | Medium |
| 7 | **Player order plumbing** (carried): "who pressed A first" must reach the emulator core's port mapping before the core starts; netplay seats need the same | Medium |
| 8 | **The media in the band's slot covers 104 px of the paused picture** at the bottom right, part of what gets saved. It could hide while the save strip is open | Low |
| 9 | **Covers view needs screenshots** for the stand. Games without one fall back to the cover on the stand, which then repeats the shelf | Low |
| 10 | **Printed titles on covers** are a mockup stand-in for real box art. Real covers print titles in every style, sometimes not at all (art-only, Japanese releases); the stand still names them | Low |
| 11 | **Settings › Library shows a raw sampled colour** ("Taken") next to the kept one; it can be orange on a settings screen. It's content, and it's the point of the diagram | Low |
| 12 | **Colour tags for people** (Sam, Living room) need a household rule for who gets which colour; HA's key rail already assigns them | Low |
| 13 | **Signal lost dark in Day** follows the launch rule, but it's an error screen, not a launch; Isaac may want it on the wall | Low |
| 14 | **Physical keyboard on the code screen**: ≡ isn't reachable from it (M types a letter); Enter on Done works, and focus jumps there at six characters | Low |
| 15 | **GPU** (carried): Covers view draws about 6 SVG covers per shelf plus the neighbours, and the stand's screenshot; still one moving element and one 300 ms shelf scroll. Not measured on the 1060 | Low |
| 16 | **Dimmed neighbour shelves** are 3.7:1 — exempt as peeks (TV13), stated here so nobody "fixes" it into a readable row | Low |

## Questions for Isaac

1. **Covers view: spines by default, covers one press away?** *Recommendation:* yes. Spines stay the default (dense, and the name rail now says the name large), Y or ≡ switches, and the household's choice is remembered in Settings › Library.
2. **Name rails on the shelf edges** (the focused name in 46 px under every shelf, Home included)? *Recommendation:* yes. It's the H1 rule made into furniture, and it fixes Home, which pass 4 left without a readable name.
3. **Power as a switch panel with levers that go up to act?** *Recommendation:* keep the panel; if "up" reads as "on" for Shut down in a family test, swap the levers for plain push plates and keep the rest.
4. **Small sections as a showcase** (five things or fewer stand face-out on one shelf)? *Recommendation:* yes, with the threshold at five.
5. **⏮ ⏭ on the Jam Home remote jump between divider cards**, plus ≡ › Jump to a letter for any input? *Recommendation:* yes; it needs one mapping in the HA bridge.
6. **The game standing in the Guide band's slot** (it covers a strip of the paused picture)? *Recommendation:* yes, and hide it while the save strip is open.
7. **Launch cover and Day** (conflicts 4 and 5): NervOS keeps the media going into the slot and stays dark in Day, Signal lost included? *Recommendation:* yes to both, pending Lobby's measurement on the panel.
8. **Glossary renames:** games console, console deck, attract board, shelf edge / name rail? *Recommendation:* yes; "In the console" stays as the words on screen.
