# NervOS · Pass 4: the shelf and the console

Mockup: `mockups/pass4/nervos.html`. Passes 1–3 are unchanged.

**Tour.** Press **▶ Tour** above the TV. It steps through 23 states, about 3 s each, and names each one under the TV. Any key on the TV, or any Jump button, stops it.

**Keys** (click the TV first): arrows move · Enter = A / OK (acts on release; hold 1 s on Quit) · Esc = B / Back · G = Guide · M = ≡ · `[` `]` = L1 / R1 sections · `,` `.` = LT / RT, jump between divider cards · `2` = a second controller presses A · any key wakes the attract screen. The same buttons sit under the jump row, and a key legend sits under the TV.

**Page controls:** Lighting (Night / Day), Motion (Full / Calm), Hints for (Gamepad / Remote), Controllers on (1 / 2), and a dashed box for the section names (approved / plain words). Everything shown is made up: games, covers, films, computers, room codes, names.

## What changed and why (vs pass 3)

Pass 3 copied the TV launcher's template on purpose (black ribbed top band, a sign, rows of tiles with base windows). After Isaac's direction ("same design language, not necessarily the same design… each interface design is bespoke to its purpose"), pass 4 throws the template out and keeps the behaviour.

| Pass 3 | Pass 4 | Why |
|---|---|---|
| Home = launcher layout: top band, sign, Continue / Collections / Systems rows | **Home = the console.** One object holds the game you played last (the cartridge is still in the slot). Continue is the one orange key on its deck. The walnut front carries the four controller ports. Right: **Played lately**, four items face-out as their own media. Bottom: a **Favourites shelf** seen by spine. | The job of Home is "get back in". One object, one key. The launcher's rows suit apps; a games room suits a console and a shelf. |
| Systems as a carousel of tiles, games as a row of 5 cover tiles | **Shelves by spine.** Each system is a shelf of its own media (grey cartridges, black clamshell cases, small handheld carts, jewel cases, arcade boards, Steam big boxes, film cases). About 15 games show at once instead of 5. ↑ / ↓ moves between shelves, which stay in view above and below. | Isaac asked: "picking a console takes you to a stack of games (or a shelf?)". Libraries are big; spines are dense and still read as games. |
| Sign (title + line) above the rows | **Display stand** on the left: the focused game face-out on a small stand, its title (horizontal, 50 px) and one line. | The spines are vertical; the stand is where the name is read. |
| Top band with tabs + sub-label | **Section slide**: one five-position switch in a recess (Home · Archive · Hangar · Uplink · Theater), the block slides on L1 / R1, the plain sub-label sits under the current position. | Same function and names (D156), drawn as a selector rather than a band. No black band at the top. |
| Walnut end mark | A **walnut bookend** at the end of every shelf, with a nudge on an extra press. | Same rule (rows stop, D120), drawn as the object it is. |
| Shutter title card | **The media goes in**: the cartridge (or box, case, computer) drops into a slot in a black ribbed deck; title below; the slatted bar shows loading; Stripes on the deck. Return: the media pops back up. | Isaac: "Make the launch screens match each of the consoles better (show their media)". Timing rules unchanged (D155, D171). |
| Save slots as four picture cards in the band | **Save strip**: four frames on a film strip, in the band (Save / Load) and on the game page (start from an older save before the game loads). | Saves are moments in order; Analogue added save thumbnails because they "make it easier to tell saves apart". |
| — | **Pick up a controller**: a player-select by port, not by profile. | Couch multiplayer on emulators needs a player order; non-gamers need to know which pad is theirs. |
| — | **Attract mode** after 45 s idle. | Pass 3 left attract undrawn (audit 15). |

Kept from pass 3 (functional decisions): the 230 px Guide band and its keys, Resume as the only orange, press twice or hold 1 s for Quit / Reset, fills on the top edge, row things light the bottom edge and column things the leading edge, rows and shelves stop, 500 ms preview rest (refined, see Rules), ≡ = options for the focused thing, hints follow the last input, the Steam fallback line (⧉ + ≡), B cancels a launch, the return card. **Not redrawn, unchanged from pass 3:** Power, Settings, the on-screen keyboard, the netplay room, Signal lost, the Steam menu stand-in, the Theater player's choosers.

## Purpose
Pick a game and play, from the couch, for gamers and non-gamers alike. Resume fast. It's the fun one.
- **Resume fast:** Home opens with focus on Continue. One press from waking the TV (attract → Home), one press to play.
- **Non-gamers:** every object says what it is (a cartridge, a film case, a computer with a light). The game page says what Guide does. The player-select says "Press A on the controller you'll play with".
- **Gamers:** dense shelves, divider jumps, save strip before launch, ports.
- **Fun:** the toy-like objects and two moments (the media dropping into the slot, a port lighting when a friend presses A). No glow, no grain, no brushed metal: everything is flat colour with one soft drop shadow.

## Research
WebSearch (standard mode), four searches; the rest from my own knowledge, marked *(knowledge)*.
- **Atari 2600 (VCS).** Industrial design credited to Doug Hardy and Fred Thompson; the woodgrain panel, the switch choice and the surface texture were chosen partly to hide scratches from use (forum post citing *Art of Atari*, Lapetino 2016). Early units had six front switches, later four; the "Darth Vader" revision dropped the woodgrain for black ([AtariAge forum](https://forums.atariage.com/topic/224723-why-did-the-atari-2600-console-design-change-so-much/), [Wikipedia: Atari 2600 hardware](https://www.wikipedia.org/wiki/Atari_2600_hardware)). I found no source for a "ribbed top", so the deck's ribs come from our own black-band rule, not the 2600. *Lesson:* the woodgrain was functional, and the switch count went down over time. The console here has a walnut front (colour only) and three keys.
- **Nintendo Switch Online.** Suspend points open from a menu (ZL + ZR on NES); there are up to four restore points; a "Control Display" option prints how to open the suspend menu at the bottom of the screen while playing ([Nintendo support](https://en-americas-support.nintendo.com/app/answers/detail/a_id/41233/~/how-to-create-a-suspend-point-in-nintendo-classics-games), [niwanetwork](https://niwanetwork.org/wiki/List_of_Nintendo_Switch_Online_games)). A review praises the "simple and clean" selection screen ([Goomba Stomp](https://goombastomp.com/nintendo-switch-online-nes-app-review-far-from-perfect-but-shows-potential/)). *Lesson:* four slots is the console norm, and saying how to open the menu (our Guide line) is a known pattern.
- **Analogue Pocket.** "Memories" are save states; a late-2022 update added screenshots and thumbnails for save states, which makes saves easier to tell apart; users asked for full-screen screenshot view and for the menus to be "cleaned up and streamlined" ([Time Extension](https://www.timeextension.com/news/2022/11/analogue-pocket-firmware-update-adds-some-welcome-features), [Gizmodo](https://gizmodo.com/analogue-pocket-os-v1-1-beta-release-memories-library-1849345505)). *Lesson:* every save gets a picture; the strip shows them in order.
- **Playdate.** Panic made the software, Teenage Engineering the hardware; a new game arrives in the launcher gift-wrapped and A unwraps it (one secondary source: [Clip Content](https://clipcontent.substack.com/p/the-playful-design-details-of-the)). *Lesson:* one small, one-time delight for new things. Here: a cream **New** sticker on a spine until first play. Nothing animates.
- *(knowledge)* Arcade marquees are wide backlit panels with the title huge over the game's art; attract mode cycles demo footage and "Insert coin". The attract screen here is a flat marquee (no backlight, no glow) with "Press any button".

## Design (what and why)
All sizes at 1080p. Text is 22 px minimum (labels 22–24, body 26–28, titles 42–104). Safe area 96 / 54 px.

**Ground.** A warm dark wall (`#1d1a17`; Day `#cfcac0`), flat. No top band. Walnut is the furniture: shelf planks (14 px top + 32 px front), bookends, the console's front, the ports strip.

**Home: the console** (focus starts on Continue).
- The cartridge stands in a slot at the back of a black ribbed **deck** (ribs on a black band, the bible's own rule). Wider media (a big box, an arcade board) is fitted to the slot width.
- On the deck: "In the console" (mono 22), the title (42), one line ("Super Nintendo · 42 min on Tuesday"), then three keys: **Continue · Tuesday 21:40** (orange; the resume point appears once, D80), **Saves 2** (opens the game page with the save strip focused), **Game page**.
- The walnut **front**: "Players" and four port sockets (a cream plug in each connected port), plus the Colour bars accent at the right end, away from the keys.
- **Played lately** (right): four things face-out on a small stand, each as its own media (an arcade board, a big box, a film case, a computer with its light). A resumes; ≡ opens the game page. The console's game is never repeated here.
- **Favourites shelf** (bottom): spines on a plank. The plank's front (the "lip") carries the shelf name and position on the left ("Favourites · 4 of 14") and the hints on the right, in cream on walnut, 24 px.
- The controller count isn't in the top right on Home, because the ports show it (never twice on one screen).

**Shelf screens (Archive, Hangar, Uplink, Theater).**
- Left: the **display stand**: eyebrow (shelf · media kind), the focused item face-out on a stand (fitted to 500 × 390), its title (50 px, up to two lines), one line (players · last played / New / Not played yet; for computers the state light + word).
- Right: the **bookcase**, one shelf per system or group, 440 px apart. The current shelf is fully visible; the one above shows its bottom and the one below its top (dimmed to 50%). ↑ / ↓ changes shelf (300 ms, decelerate); the top shelf's ↑ goes to the section slide.
- **Spines** stand on the plank, each drawn as its system's media with the title running top to bottom (24 px Jost; two columns if long, never an ellipsis, D163). The focused spine comes off the shelf (34 px lift, 140 ms) and lights its base window.
- **Divider cards** stand between spines on shelves of more than 8 items, with mono tabs **A–F · G–L · M–R · S–Z** above the spines. LT / RT jump to the next tab. They aren't focusable.
- The **lip** says "Super Nintendo · 1 of 13" on the left and "Shelf 1 of 6" on the right.
- A walnut **bookend** ends every shelf. An extra press nudges (not in Calm).
- Uplink's shelves hold **machines** (Study PC with a lit green light and "On"; Laptop with the offline form and "Offline") and **room cards** (MOON42, "Join with a code").
- Theater's films are slim black cases with a cream label.

**Game page: the box opened.**
- Left: the media face-out, large, on its stand.
- Right: eyebrow (system · kind · players), title (76), one line, and the Guide line ("Guide pauses the game and opens the menu to save, load or quit"; Steam games get the ⧉ + ≡ line instead).
- Keys in a column (leading-edge windows): **Continue from Tuesday 21:40** (orange) · Start from the beginning · Favourite (square window + On / Off).
- The **save strip** below: four frames with sprocket rows, "Slot 1 · Tue 21:31", empty frames as dark recesses. ↓ enters it; A starts from that save.

**Pick up a controller** (shown only for a 2+ player game when 2+ controllers are on; with one controller the game just starts).
- Title "Pick up a controller", one line: "Press A on the controller you'll play with. The first one is Player 1. Up to 2."
- A walnut panel with four **ports**: a big number (84 px mono), a socket that fills with a cream plug when a controller joins (300 ms settle), a round LED (lit green when joined), and "Player 1 · Controller · 72%" or "Not playing · Free" / "Connected · press A on it".
- Keys: **Start with 2 players** (orange, focused) · Swap 1 and 2 (only when two have joined) · Back.

**Launch and return.**
- Opaque, full-bleed. A black ribbed deck crosses the screen with a walnut top edge and a slot; the media drops in from above (480 ms, decelerate) and stops with about 60% showing. Stripes sit at the deck's right end.
- Below: eyebrow ("Super Nintendo · Continue from Tuesday 21:40"), the title in capitals (66), the sub-line ("Starting the emulator · B cancels"; Steam: "Starting Steam · hold ⧉ + ≡ for the house menu"), then the **slatted bar** (16 slats, unlit slats stay visible as recesses).
- Hold = max(load, 600 ms). B cancels: the media goes back up, "Cancelled", then the toast "Didn't start Glass Dragon".
- **Return:** the same deck; the media rises out of the slot; "Back from · Glass Dragon · Played 42 min · resume point saved"; then Home with that game in the console.
- **Calm:** the media is already in place, and the screen fades.

**Guide band** (unchanged shape, the one shared house component): 230 px, opaque, ribbed, walnut top edge. Header: slot + "Paused", title, context, hints, clock. Retro keys: **Resume** (orange) · Save · Load · Picture / Sharp pixels · Reset · Quit game. Save and Load swap the key row for the **save strip** (frames 132 × 74, inside the 230 px). Replacing a filled slot reads "Replace? · Press A again". Quit: press twice ("Press A again to quit") or hold 1 s (the fill runs along the top edge). Films get the pass 3 player keys with the timeline on the band's top edge.

**Attract** (45 s idle; static in Calm).
- A flat **marquee**: the game's colour panel with its title at 104 px on the left and its art on the right, over a ribbed plate ("On your shelves · 1 of 5").
- Below: "Press any button" and "NervOS is resting. It's showing games from your shelves, one every 10 seconds. Nothing starts by itself." On the right: "In the console · Glass Dragon · One press, then Continue", with five round position lights.
- One cross-fade every 10 s. Any button wakes it to Home with focus on Continue (the press is not passed on).

**Day.** The wall turns light (`#cfcac0`), the slide's recess and block lighten, keys on the wall turn light. The console's deck, the Guide band and the launch deck stay black: they're objects, not grounds.

## New elements
1. **The console** (Home). The last game stays in the slot; Continue lives on the deck; controllers live in the ports on the walnut front. *(own)*
2. **Media spines** with a per-system silhouette and colour, plus **divider cards** (A–F…) as the range keys, and a **bookend** as the end mark. *(own; the seed's "browse by spine")*
3. **The display stand**: the focused item face-out with its readable title, next to a shelf of vertical titles. *(own)*
4. **The section slide**: a five-position selector switch in place of a tab band. *(own)*
5. **The media goes in**: a launch and return card drawn as the media entering and leaving a slot. *(own)*
6. **Pick up a controller**: player-select by port. *(seed, reshaped: ports, not profiles, so it doesn't repeat JamFin's "Who's watching?")*
7. **Save strip**: saves as frames on a film strip, on the game page and in the band. *(seed)*
8. **Attract mode**: a flat marquee. *(seed)*
9. **The New sticker** on a spine until first play. *(own, from Playdate's unwrapping)*

## Language check
What ties it to the family:
- **Type:** Jost for words, IBM Plex Mono for eyebrows, tabs, port numbers and counts.
- **Indicator windows:** round LED (controller joined, computer on), the offline form (Laptop), a square (Favourite), a slot ("Paused"), and the unlit-window rule (empty save frames, unlit slats, empty ports).
- **State words:** On, Offline, Paused, Not playing.
- **One orange per screen:** Continue, Resume, Start with 2 players, Play. Shelf screens and the attract screen have none.
- **The base window:** a focused spine, cover, key or port lights a cream window on its bottom edge. Column keys light their leading edge, and holds fill the top edge.
- **Materials:** walnut as the house wood colour; ribs only on black (the deck, the Guide band, the marquee plate, machine vents); the slatted bar and Stripes from the title card; Colour bars as Home's one accent.
- **Motion:** glide / decelerate / settle; focus 140 ms; transform and opacity only; Calm = fades and nothing continuous.
- **Hints:** the house hint grammar (circled button + verb), following the last input (A / B or OK / Back).

What someone coming from the TV launcher or JamFin recognises within a second: the cream window under whatever has focus, the single orange key, and, as soon as Guide is pressed, the **same black band with the same keys**. That band is the one piece deliberately shared as a component, for a stated reason: it's the house's system layer over any content, so it should behave identically everywhere (muscle memory, one implementation). Everything else is NervOS's own.

## Rules I broke

| # | Rule (BIBLE / D-number) | What I did instead | Why NervOS needed it | Verdict |
|---|---|---|---|---|
| 1 | TV home template from passes 1–3 (top ribbed band, sign, rows; D79 "≥ 2.5 rows, cards ~15% of width") | A console + a bookcase; spines ~3–6% of the width; ~15 items per shelf view | A games library is browsed by the hundred; resume is one object, not a row | **Drop** D79 as a global rule. **Device family** replacement: "the focused item's name is readable horizontally at ≥ 46 px somewhere on screen" |
| 2 | §2 Materials: alu / card grounds; "TV ground = band colour, flat" | A warm wall `#1d1a17` (Day `#cfcac0`), flat, and walnut furniture | The room metaphor needs a wall the objects stand against | **App-local** grounds. Keep **language-wide** only ink / dim, cream, orange, walnut, state colours |
| 3 | §2 walnut = "8 px trim line at the top, colour only" | Walnut shelves, bookends, the console front, the ports panel | Walnut is the furniture of a games room | **Language-wide** colour (colour only, no grain); its shape **app-local** |
| 4 | §3 Colour discipline: "idle things stay neutral" | Spines and media faces carry their own colours while idle | They are content stand-ins, like covers | **Language-wide, clarified:** content and drawn stand-ins for content are exempt; chrome stays neutral |
| 5 | (no rule) Text is horizontal | Spine titles run top to bottom, 24 px | Spines are the density win | **Device family (TV), new:** rotated text only when the focused item's name also shows horizontally; ≥ 24 px; one direction (top to bottom) |
| 6 | D120 walnut end mark | A walnut bookend object | Same function, drawn as the thing it is | **Language-wide:** "rows stop at a visible end". **App-local:** what the end looks like |
| 7 | D170 range keys (1–10, 11–20…) in a row | Divider cards A–F / G–L / M–R / S–Z, not focusable, LT / RT jump | Alphabetical shelves; tabs read like a record store | **Device family:** "long rows have a jump"; the form is **app-local** |
| 8 | §2 TV title card "Shutter with the slatted bar" (final) | The media drops into a slot; slatted bar and Stripes kept | Isaac asked NervOS launches to "show their media" | **Device family:** hold = max(load, floor), B cancels, opaque full-bleed, slatted progress, Calm fade. **App-local:** the picture (shutter for JamFin / the launcher, slot here) |
| 9 | D123 / D178 accent placement (fixed strip / black band / only where no art) | Colour bars on the console's walnut front (Home); Stripes on the launch deck; no accent on shelf screens | The accent belongs to the hero object; shelves are already colourful | **Language-wide:** at most one accent per screen, never on or behind a control ("one" is a maximum, not a quota). **App-local:** placement |
| 10 | D127 "No suggested content" | Attract mode shows games from the library while idle | It's NervOS's idle face (arcade heritage), and it reminds a guest what's here | **App-local** (idle only, never on an active screen, nothing starts, static in Calm). D127 stays for active screens |
| 11 | D169 "focus-driven content waits 500 ms" | The display title changes at once; only the cover picture waits 500 ms | Spine titles are vertical; the horizontal title must keep up with the D-pad | **Device family, refined:** text naming the focus updates at once; pictures wait 500 ms |
| 12 | D148 Guide band "one for every TV app" | **Kept**, not broken | Logged because it's now the only shared TV component, with a reason | **Device family**, by reason, not by template |

## Audit
Checked with Playwright (Chromium, `chromium.launch()` with no options) at 1500 px wide with deviceScaleFactor 1.31, so the TV renders at about 1920 px. The script:
- ran all 23 Tour states (screenshots t01–t23);
- did a keyboard run: R1, divider jump, five shelves down to Arcade, the game page, player select with pad 2, launch, Guide, Save, holding A on Quit, return to Home, the offline Laptop, waking attract;
- checked Day + plain words + Remote hints on Archive, the game page and player select;
- checked the page at 390 px in the dark scheme.

Screenshots are in the session scratch folder `p4n/shots/`, not in the repo.

**Results:**
- no JS errors and no console errors;
- **no visible TV text under 22 px** in any state (hints 24 px);
- **no text outside the 96 / 54 safe area**, except the titles on the neighbour shelf peeking off the bottom edge (intended);
- the Guide band is 230 px in every state, save strip included;
- at 390 px, `scrollWidth` is 390.

**The fix pass corrected:**
- the deck's line colliding with its keys;
- the orange key's sub-text in grey;
- wide media (an arcade board) overflowing the console and Played lately (everything is now fitted to its box);
- machine labels overlapping ("On · ready to stream" became "On"; the display carries the rest);
- band keys and save strip 6–30 px below the safe area;
- save labels clipped on the game page;
- the focused save frame not lighting its window;
- the full-bleed sun on the attract marquee (now a title panel + art panel);
- duplicate titles on cartridge labels (labels are now plain colour bands);
- the controller count shown twice on Home;
- 22 px hints on the shelf lip (now 24, D4).

| # | Problem | Severity |
|---|---|---|
| 1 | **Vertical spine titles are slower to read from 3 m.** The display stand shows the focused title horizontally, but scanning a shelf for a game you know by name is slower than with tiles. Needs a sofa test with a 200-game library. | High |
| 2 | **Spines don't exist in scraped art.** ScreenScraper and Steam give covers, not spines. NervOS would draw every spine from the system's media template + title + a colour sampled from the cover. A sampled colour can be ugly or low-contrast (text colour is picked by luminance, but the result may still look muddy). | Medium |
| 3 | **Focus on thin dark spines is subtle.** The 34 px lift carries it; the 9 px base window on a 54 px jewel case is small at 3 m. A plank-lip mark under the focused spine may be needed. | Medium |
| 4 | **Divider jumps have no remote path.** The HA remote has no LT / RT; remote users hold ← / →. A "Jump to letter" item under ≡ would cover it. | Medium |
| 5 | **Sparse shelves look empty.** Uplink (2 machines, 2 rooms) and Short films (3) leave much bare wall, against D175's spirit. Shelves could shrink to their content, or Uplink could be one shelf. | Medium |
| 6 | **Player order needs plumbing.** NervOS must pass "who pressed A first" to the emulator core's port mapping (RetroArch assigns ports at launch). Swap must work before the core starts. | Medium |
| 7 | **Launch cards now differ between TV apps** (shutter vs slot). The timing and controls are shared; the picture isn't. Isaac decides whether that still "feels natural". | Medium |
| 8 | **What the console holds** is undecided for Steam games: in the mockup, quitting a Steam game puts its big box in the slot. Films and streams never go in. | Low |
| 9 | **Dimmed neighbour shelves** put text at 50% opacity, below AA. They're peeks, not things to read, but the floor says focused labels only, so this needs a stated exception. | Low |
| 10 | **Attract on an OLED** shows a static plate and text for minutes. It should dim the panel after 10 min (NervOS already idles the frame rate). | Low |
| 11 | **The player screen adds a press** to every multiplayer launch when two controllers are on, even for solo play. Start is pre-focused, so it's one press. | Low |
| 12 | **Played lately and the console** must never show the same game; the rule is "the four most recent, not counting the console's". | Low |
| 13 | **Not drawn this pass:** Power, Settings, OSK, the netplay room, Signal lost, the Steam stand-in (all unchanged from pass 3), and first run. | Low |
| 14 | **GPU:** about 60–90 static nodes per shelf screen, one moving spine, one 300 ms shelf scroll; the attract screen makes one cross-fade every 10 s. Not measured on the 1060. | Low |

## Questions for Isaac
1. **Is "the shelf and the console" NervOS's Braun Hi-Fi look?** It replaces pass 3's launcher-style layout. The four approved looks (NERVOS, Cut-out, Hero, VHS) keep their own layouts.
   *Recommendation:* yes. It's the most NervOS-specific version so far, and it answers your "(or a shelf?)".
2. **Vertical titles on spines?**
   *Recommendation:* yes, on the condition that the focused title always shows horizontally (rule 5). Test on the sofa with the real library before rollout.
3. **Launch = the media drops into the slot** instead of the house shutter?
   *Recommendation:* yes for NervOS (you asked for launches that "show their media"). The shutter stays for JamFin and the launcher; all three share the hold, cancel and Calm rules.
4. **Attract mode showing your own games when idle** (breaks D127, "no suggested content")?
   *Recommendation:* yes: idle only, one change every 10 s, static in Calm, dims after 10 min, and nothing starts by itself.
5. **Pick up a controller** before 2+ player games when two controllers are on?
   *Recommendation:* yes, with Start pre-focused, and skipped entirely with one controller.
6. **What the console holds:** the last game of any kind (retro or Steam), or the last retro game only?
   *Recommendation:* any game. Films and streams live only in Played lately, because they aren't things you "put in".
7. **Shelves stop at the bookend** (pass 3's stop rule, now for vertical shelves too)?
   *Recommendation:* stop. With 6–8 systems, the far shelf is at most 7 presses away, and the bookend makes the end visible.
8. **The section slide** (one switch, five positions, Home included) instead of a tab band?
   *Recommendation:* yes. It keeps the approved names and the plain sub-label, and it's NervOS's own.
