# NervOS · Pass 2

Mockup: `mockups/pass2/nervos.html`. Pass 1 (`mockups/pass1/nervos.html`) is unchanged. The new mockup is interactive. Click the TV, then use:
- the arrow keys;
- Enter (A / OK); a tap and a 1 s hold are told apart;
- Esc or Backspace (B / Back);
- G (Guide);
- [ and ] (L1 / R1).

The pad buttons do the same. "Hold A 1 s" holds; "Hold → (key repeat)" sends one press plus ten repeats.

Page controls:
- Lighting (Night / Day), Motion (Full / Calm) and Covers (Full colour / Toned).
- A separate dashed box, labelled **"Alternative for Isaac to judge · section names"**, switches the band between NervOS names (approved) and Plain words.
- Jump to: Home, Archive, Favourites shelf, Game page, Title card (held), Guide · retro and Guide · Steam.

Everything is made up: games (some reuse NervOS's fixture names), films (JamFin's demo names), computers and art. The covers are generated shapes, with no box art and no logos.

## What changed since pass 1
Pass 1's Audit and Change suggestions were the to-do list. Item numbers refer to the pass 1 audit table.

| Pass 1 item | Pass 2 |
|---|---|
| #1 Renaming the sections (High) | **Reverted.** The band shows **Home · Archive · Hangar · Uplink · Theater**: the approved names (README, "Themes approved" 2026-11-03).<br>They're set the way the approved VHS look already sets them (`hub-hangar-vhs.webp`): Jost 500 at 28 px, sentence case, normal tracking, with no 01–04 numbers, no kanji and no colour per section.<br>When a tab has focus, the sign explains it in one plain line ("Section · Classic consoles and arcade games, played here.").<br>Plain words (Retro / Steam / Streaming / Films) appear only behind the labelled page switch. The caption under the TV says which set is showing. |
| #6 Home fits about 1.8 rows (Medium) | **About 2.6 rows at rest** (measured: two full rows, plus 61% of the third row's cards, with its header always visible).<br>Cards are 288 px wide instead of 400, about 5.8 across instead of 4.2.<br>The sign is now title + one line, with no eyebrow, because the row header already names the row. Rows start at y = 250 instead of 396. |
| #3 / D32 No wrap marker on the systems carousel (Medium) | A **walnut bookend** (a 10 × 162 px walnut bar with "START" under it, never focusable) sits where Arcade meets Super Nintendo.<br>**Key repeat stops at the bookend.** The strip nudges 14 px, and the row header briefly reads "End of the list · let go, then press again to go round". A fresh press goes round, and the strip slides past the bookend. |
| #2 / D33 The same value twice in pop-ups (Medium) | **Save and Load share one tray** that names the slot once ("Slot 2"). The Slot key is gone; the slot shelf (↑ from Save or Load) is the chooser.<br>**While a chooser is open, its key hides its value:**<ul><li>with the slot shelf open, the tray's "Slot 2" hides and the lit square on the Slot 2 card carries it;</li><li>with the Picture list open, the key reads just "Picture" and the lit square on "Sharp pixels" carries it.</li></ul>The game page also loses "Played Tuesday" when there's a "Continue from Tuesday 21:40" key; the facts say "6 h played" instead. |
| #4 Placeholder art all the same (Medium) | **Eight made-up cover styles:**<ul><li>pixel scene;</li><li>big-type poster;</li><li>near-white paper (glare test);</li><li>saturated red (red-rule test);</li><li>halftone comic;</li><li>neon grid;</li><li>painted;</li><li>busy collage with a stroked title.</li></ul>Save states and the running game use a pixel "screenshot" with a HUD strip, so they look like play, not box art.<br>Each collection shows three of its own covers fanned on a walnut shelf (picked per collection), so two collections no longer look alike. This also fixes pass 1 #12, where every collection was decorative spines. |
| #10 / D31 Hold-to-confirm needs a non-hold path (Medium) | **Reset, Quit game, Disconnect and Stop film: hold A for 1 s, or press A twice.**<ul><li>The first tap re-labels the key "Press A again to quit" and lights its top edge.</li><li>It disarms after 3 s or when focus moves.</li><li>A hold that's released between 0.35 and 1 s cancels, with the hint "Hold A for a second, or press A twice".</li></ul>**Replacing a filled save slot uses the same two-press path** ("Press A again to replace").<br>The HA remote, which may not send key-up, can do everything. |
| #9 / D35 Guide in Steam games (Medium) | **Guide opens the same band for every kind of content.** Only the keys change:<ul><li>Retro: Resume · Save / Load · Picture · Reset · Quit game.</li><li>Steam: Resume · Steam menu · Quit game.</li><li>Stream: Resume · Stream menu · Disconnect.</li><li>Film: Resume · Player controls · Stop film.</li></ul>A retro game is paused (the slot is unlit, "Paused"). A Steam game or a stream keeps running (the slot is lit, "Running" / "Streaming"), with a lighter veil. |
| #5 Toast over the accent (Low) | The accent steps back while a toast shows. It's also hidden while covers are Full colour, and shows with Toned (see Bible implications 7). |
| #7 Quick menu covers 22% (Low) | The band is 236 px (21.9%) with 88 px keys. The slot shelf made this worse; see Audit 2. |
| #11 Day focus faint (Low) | The Day card is `#d3cfc7` on ground `#b9b5ac`, and the focused face steps to `#e8e4dc` (a bigger step than pass 1). Lit windows keep a 2 px dark rim. |
| #13 GPU, #8 missing screens | Not addressed. Still open; see Change suggestions. |

New in this pass, not asked for:
- **The shelf's big preview doesn't swap under key repeat.** It waits until focus has rested for 450 ms. Without this, a held ↓ through a white cover and a red cover flips an 844 × 475 area many times a second (the BIBLE §9 flash rule).
- **List rows carry a small cover thumbnail** (100 × 56).

## Research
I ran ten web searches this pass. The results were mostly vendor support pages, Xbox Wire, press coverage, the libretro docs and user forums. Items marked *(knowledge)* come from my own knowledge, not from a search. Pass 1 covered Steam Deck / Big Picture, ES-DE and Batocera; this pass covers the rest.

- **Xbox Home (2023 redesign).**
  - Insiders said the first new Home "felt crowded and didn't leave enough space" for the background. Microsoft made the tiles smaller and moved them lower; outlets report 9 tiles visible instead of 7 ([Xbox Wire](https://news.xbox.com/en-us/2023/05/01/xbox-insiders-your-feedback-shapes-the-new-home-experience/), [Pure Xbox](https://purexbox.com/news/2023/07/its-finally-here-the-new-xbox-dashboard-has-arrived), [iPhone in Canada](https://www.iphoneincanada.ca/2023/05/02/xbox-new-dashboard-layout/)).
  - Commenters said the smaller tiles were harder to read for weaker eyes.
  - Quick Resume has its own **group** on Home that lists every suspended game, and a **tag** in the Guide says whether the running game supports it ([Xbox Wire, May 2021](https://news.xbox.com/en-us/2021/05/11/may-2021-xbox-update/)). The April 2026 update allows up to 10 groups on Home and turning Quick Resume off per game ([Xbox Wire, April 2026](https://news.xbox.com/en-us/2026/04/30/april-xbox-update-2026/)).
  - *Lesson:* smaller tiles win back rows, but text must not shrink with them. That's why the cards here went from 400 to 288 px while labels stayed at 26/22 px. A "suspended / continue" group belongs on Home, and NervOS's Continue row is that group.
- **PlayStation 5 home and Activities.**
  - The PS button opens the Control Center with **cards**. Activities are cards that jump straight into a chunk of a game, and Game Help plays hints picture-in-picture ([GamesRadar](https://www.gamesradar.com/heres-how-ps5-activities-will-work-according-to-sony), [TheSixthAxis](https://thesixthaxis.com/2020/11/11/ps5-activity-cards-guide-how-they-work-ps4/)).
  - Hovering a game on Home shows its hub below, with activities, clips and news ([TechRadar](https://www.techradar.com/news/ps5-ui-is-finally-revealed-with-features-that-could-change-gaming-forever)).
  - Critics found it "designed to promote busywork" ([TechRadar opinion](https://www.techradar.com/news/the-ps5-ui-looks-like-its-designed-to-promote-busywork-not-save-you-time)).
  - *Lesson:* a picture card that resumes at an exact point is a friendly form of a save state, and NervOS's save-state cards are exactly that. The hub-under-hover and the news are the clutter to avoid.
- **Nintendo Switch home and Switch Online's classic apps.**
  - HOME suspends the game. Selecting it again offers Resume or Close, and starting another title closes the suspended one ([Nintendo support](https://nintendo.com/au/support/articles/how-to-start-close-a-game-or-software-application)).
  - The NES/SNES apps give each game **four suspend points** with pictures, plus rewind. When all four are used, you save over one ([Nintendo support](https://www.nintendo.com/en-gb/Support/Troubleshooting/How-to-Create-a-Suspend-Point-in-Nintendo-Classics-Games-1442713.html), [iMore](https://www.imore.com/nintendo-switch-online-expansion-pack-how-use-suspend-points-n64-and-sega-genesis-games)).
  - *(knowledge)* Home is one row of square icons, most recent first, under a thin top bar.
  - *Lesson:* four picture slots is the non-gamer-proven form of save states, so NervOS's four slots stay. Overwriting is the moment to slow down, which is why replacing a filled slot uses the press-twice path. Rewind is worth adding (Change suggestions).
- **RetroArch Ozone and XMB.**
  - Ozone replaced XMB as the default menu ([GamingOnLinux](https://gamingonlinux.com/2020/03/retroarch-185-is-out-replacing-the-xmb-ui-with-ozone-plus-lots-of-bug-fixing)). A user complaint at the time was that Ozone showed no save-state screenshots.
  - The libretro docs list a Save State Thumbnails option ([XMB menu map](https://docs.libretro.com/guides/xmb-menu-map)).
  - *(knowledge)* The Quick Menu lists Resume, Restart, Close Content, Take Screenshot, Save State, Load State, **Undo Save State / Undo Load State** and State Slot −/+, as text rows.
  - *Lesson:* pictures on save states are what people miss when they're gone. "Undo" is RetroArch's safety net for a wrong save or load, and it's a friendlier answer than a confirm dialog (Change suggestions).
- **LaunchBox Big Box pause screen.**
  - The pause menu offers Resume, View Manual, High Scores, Achievements, Reset, Save State, Load State and Swap Discs ([LaunchBox help: Pause Themes](https://launchbox.featurebase.app/help/articles/4544687-pause-themes)).
  - Forum threads report black screens, lost focus on resume, and empty save/load slots, because the pause screen drives each emulator through hotkeys ([forum 1](https://forums.launchbox-app.com/topic/55180-unable-to-resume-game-from-pause-menu-losing-focus), [forum 2](https://forums.launchbox-app.com/topic/61825-pause-menu-selecting-saveload-state-freezes-game/)).
  - *Lesson:* a frontend-drawn pause menu is only as good as its link to the emulator. NervOS already drives its own emulators, but Steam games and streams are a different matter (Audit 4).
- **Playnite fullscreen mode** ([Playnite docs](https://api.playnite.link/docs/manual/features/themesSupport/themesSupportOverview.html), [retrohandhelds.gg guide](https://retrohandhelds.gg/playnite-on-windows-handhelds-setup-guide/)).
  - It's a controller-first 10-ft mode. Guides praise the default theme for covers, details, search and filters all reachable by pad.
  - Popular community themes imitate consoles (SwitchNite, Reskin XBOXSX).
  - A known gap: "launch straight into fullscreen" can only be set from desktop mode.
  - *Lesson:* every setting a TV user needs must be reachable on the TV. Families copy console homes because they already know them, which argues for Continue first and big covers.
- **Pegasus (gameOS theme)** ([gameOS](https://github.com/HVR88/gameOS), [RetroPie forum](https://retropie.org.uk/forum/post/203243)).
  - gameOS is "a modern, tvOS-like launcher", with dynamic collections for discoverability added in v1.09, plus search and filtering.
  - Users asked for a small-screen toggle that enlarges items.
  - *Lesson:* collections are the way in (again), and size controls matter.
- **Android handheld frontends: Daijishō and Beacon** ([Reddit review thread](https://redlib.librenode.com/r/EmulationOnAndroid/comments/1k3y9gm/emulator_frontends_review), [DroiX guide](https://droix.net/blogs/pl/poza-podstawowa-emulacja-kompletny-przewodnik-po-retro-handheldach/)).
  - Daijishō is called the most popular: a clean look, easy to run, weak at organising apps.
  - Beacon is praised as quick to set up, with easy per-game scraping and emulator linking. Users ask for themes.
  - *(knowledge)* Both open on a platform list with the system's art as the background, and Beacon has a recently played row.
  - *Lesson:* the friendly part is set-up that just works and a recent row. Platform-first browsing is the enthusiast default, so NervOS keeps systems as the third row, not the first.
- **Steam under gamescope** ([Valve issue #8513](https://github.com/ValveSoftware/steam-for-linux/issues/8513), [Universal Blue forum](https://universal-blue.discourse.group/t/any-way-to-get-the-overlay-in-gaming-mode-while-in-game-ctrl-1-ctrl-2-or-guide-button-not-working/1018)).
  - Users report non-Steam games not getting focus in the gamepad UI, and the Steam overlay opening *behind* the running app.
  - One user asks for a way to quit an emulator or non-Steam game from the overlay.
  - *Lesson:* who owns the Guide button in a gamescope session is a real engineering question (Audit 4). The design answer is that whichever process gets it, the household sees one band.
- **Takeaway.** The console homes (Xbox, PS5, Switch) agree on four things:
  - resume first;
  - a picture for every saved moment;
  - one button that always opens the same overlay;
  - small enough tiles to see more than one row.

  The enthusiast frontends (Pegasus, Big Box, Daijishō, Beacon) win on collections and set-up, and lose friendliness to option lists and systems-first browsing. Pass 2 takes the console half for Home and the Guide band, and the frontend half for collections.

## Design (what and why)
**Home: Home · Archive · Hangar · Uplink · Theater.**
- The black ribbed band (118 px, walnut trim) holds the tabs, a controller LED with "Controller 72%", and the clock. L1/R1 change sections everywhere.
- The approved names stay. They read as words, not codes: Jost sentence case, no numbers, no kanji, no section colours.
- "Home" is still a proposed fifth tab (Steam Deck's "what we play"). Today NervOS's hub opens in Archive.
- The **sign** is the title plus one line. Its first phrase is the state in ink ("Continue from Tuesday 21:40"), then players and the description, clipped to one line. It swaps by opacity (50 ms out, 100 ms in).
- **Rows** (318 px pitch): Continue (all sources mixed: Xbox's Quick Resume group, Switch's suspended game), Collections, then Systems as the group carousel. Archive has Systems, Recently played, Favourites and Play together.
- The focused row scrolls to the top, and the next row's header and cards always peek.

**Cards (288 × 246):**
- Art 288 × 162 plus an 84 px plinth (title 26 px, sub-line 22 px).
- The selector is the base window on the plinth (40% wide, 10 px tall).
- The face lifts 10 px inside its own layer and steps lighter; the focus colour snaps.
- Film progress stays on the art's bottom edge (D13).

**Systems carousel:**
- Focus sits in slot 2 with the previous system peeking in slot 1. The header shows "3 of 8".
- A **walnut bookend** marks the wrap and key repeat stops there (see the table above).
- Systems still show their media (cartridge, disc, board), never a logo (D34).

**Shelf (a collection or one system):**
- A slim band shows "B · Home" (where Back goes) and the clock.
- On the left: the title, "9 games · A to Z", then a list of 76 px rows. Each row has the leading-edge window, a 100 × 56 cover thumbnail, the title, and the system or year on the right. Eight rows show; the list ends cleanly, with no half-row.
- On the right: an 844 × 475 preview, the title, a state line and a description.
- L1/R1 jump a letter. The preview waits 450 ms under key repeat.

**Game page:**
- Eyebrow "Archive · Super Nintendo", the title, facts ("1–2 players · 1994 · 6 h played") and one line.
- The keys are **Continue from Tuesday 21:40** (the one orange, with D18's focused form: black label, 7 px under-edge, lit leading window), Play from the start, and Favourite (square window + On/Off).
- On the right: the cover, then **Save states** as picture cards (Slot 1 · Sunday 17:05 …), reached with →. A loads the slot.
- Steam games get one Play key and the line "Steam keeps this game's saves. Guide during the game opens the same band as every other game, with Steam's own menu one press away."

**Launch title card:** the flat ribbed shutter halves (460 ms in, decelerate) and the title on the seam.
- **Eyebrow:** "Super Nintendo · Continue from Tuesday 21:40".
- **Slatted bar:** "Starting the emulator", "Starting Steam" or "Connecting".
- **Hold:** only as long as the load, with a 600 ms floor (D14, D36).
- **Hand-off:** the game is composed behind the opaque card, then the halves leave in 300 ms.
- **Stripes** run down the right side and bend out right, clear of the title.
- **Calm** turns the card into a 140 ms fade.
- "Title card (held)" freezes it for review; any key continues.

**Guide band (one for everything):**
- The ribbed band is 236 px, with a walnut top edge.
- The first line has a state slot, the title, a sub-line, hints that change with the zone, and the clock.
- The keys are 88 px tall, and Resume is the only orange.
- **Retro:**
  - **Save / Load** share a recessed tray labelled "Slot 2". Save and Load act at once on that slot and confirm with a toast.
  - ↑ from either pops the **slot shelf** above the band: four picture cards, Empty as a recess, and a lit square on the current slot. A saves or loads there. Replacing a filled slot asks for a second press.
  - **Picture · Sharp** opens a list above its own key.
  - **Reset** and **Quit game** take a hold or two presses. The hold fills the key's top edge, while the selector window stays on the bottom edge (D31).
- **Steam, stream, film:** the same band with three keys. The content's own menu is one press away, and Quit is the same two-path key.
- B closes the band (Resume). In the game itself, B does nothing, so a game never quits by accident.

**Day:** a mid-light ground and black bands, with dark rims on lit windows. **Calm:** no slide on screens, rows or carousels; fades only.

## Audit
Checked with Playwright (Chromium, `chromium.launch()`) at 1500 px wide with deviceScaleFactor 1.31, so the TV renders at about 1920 px. I took 26 TV states:
- Home in Night, Toned and Day, every Home row, and the carousel at the wrap, at the key-repeat stop and wrapped;
- the Archive section and its fourth row, and plain words;
- the Favourites shelf with a letter jump;
- the game page and its save states, in Night and Day;
- the held title card and the running game;
- the Guide band, the slot shelf, an armed slot replace, the Picture list, Quit armed and Quit holding, and the Steam Guide;
- Calm.

I also checked the page at 390 px in the dark scheme.

Script checks:
- every visible TV text node is at least 22 px at 1080p;
- no text sits outside the 96/54 px safe area, except on cards peeking off an edge;
- no JS errors and no console errors;
- `scrollWidth` is 390 at 390;
- the night glare share (pixels above relative luminance 0.5) on Home is **6.5%** with Full colour covers and **2.3%** with Toned. The cap is 10%.

The fix pass corrected:
- band text (tabs, clock, "B · Home") whose line boxes started at y = 47–52 px, above the 54 px safe line (the band is now 118 px and the slim band 112);
- collections that all showed the same three covers (they were the first three A–Z), now picked per collection;
- two painted covers that looked alike;
- the "Paused" slot showing lit (it now stays unlit, because nothing runs);
- the focus shadow reading as a grey bar under the card in Day;
- a half row peeking at the bottom of the shelf list;
- an over-long slot-shelf heading;
- the shelf preview flipping under key repeat (new 450 ms rest).

| # | Problem | Severity |
|---|---|---|
| 1 | **Approved names vs friendliness is still Isaac's call.** The band now carries Archive / Hangar / Uplink / Theater in friendly type, but "Hangar" and "Uplink" don't say what's inside until the tab has focus and the sign explains it. A guest reading the band cold still can't guess that Uplink means streaming. The plain-words switch is there for him to compare. | Medium |
| 2 | **The slot shelf makes the Guide band cover 51% of the picture** (236 + 318 px), more than pass 1's 372 px. The game is paused so nothing is missed, but the paused picture is what people use to decide which slot to save over. | Medium |
| 3 | **Full-colour covers vs the accent.** With real covers at Full colour, I hid the Colour bars on Home (D19), so the default Home has no accent and the "one accent per screen" rule isn't met there. With Toned covers the accent shows. Glare is fine either way (6.5% / 2.3%). Which is the default is a judgement call. | Medium |
| 4 | **The Guide band in Steam games may not be buildable as drawn.** In a gamescope session Steam owns its Guide button (the Steam Controller's Steam key), and users report the overlay opening *behind* apps and non-Steam games losing focus. NervOS may only get Guide from non-Steam pads, the keyboard or the HA remote. The band is the design answer; who receives the button is unverified. | Medium |
| 5 | **"Quit game" for Steam and "Disconnect" for streams** assume NervOS can close a Steam game and end a Moonlight session cleanly. If it can only ask Steam, the key needs a "Closing…" state, and a fallback when the game ignores it. | Medium |
| 6 | **The bookend relies on key repeat being flagged.** SDL3 gamepads don't send OS key repeat. NervOS's own repeat timer must mark repeats, or the stop never happens. With only eight systems the stop arrives within a second of holding →, which some people may find abrupt. | Low |
| 7 | **The press-twice path costs one press for everyone**, not only the remote. It's on Reset, Quit and replacing a save, which are rare actions. The armed label also widens the Quit key (from "Quit game" to "Press A again to quit"), so the row's later keys shift right. | Low |
| 8 | **The selector window on 12 unlit plinths** reads as a row of black dashes in Night and Day, as in pass 1. That follows the "window always visible" rule, but it's busy on a 6-card row. | Low |
| 9 | **Home has no eyebrow now**, so a game in Continue doesn't say its source in the sign; the plinth carries it ("Steam", "Neo Geo"). That's fine for the focused card, but the sign alone no longer says *why* a game is in that row. | Low |
| 10 | **The game page leaves the lower left empty** (about 400 × 760 px under the keys). It's calm, but it's space Home had to fight for. | Low |
| 11 | **Covers with their own title text** (type, collage, bright) show the title twice: in the art and on the plinth. Art is exempt from "never twice", but on busy collage covers the stroked art title fights the plinth title at a glance. | Low |
| 12 | **Still not designed:** the THEATER player band (JamFin's), the netplay host/join flow, Signal lost, Settings › Display, the Power modal, the OSK, attract, boot, and the RETURN / ABORT outro. | Medium |
| 13 | **GPU cost not measured.** The covers here are SVG; on the box they're textures. The bands are static. Only the clock animates at rest, plus the carousel slide and card lift on input. | Low |

## Change suggestions for pass 3
- **Section names:** if Isaac keeps the approved names, add a 22 px sub-label under the *focused* tab only ("Archive · retro games"), so a guest learns the word without a permanent second line. Try it beside the plain-words alternative.
- **Slot shelf height:** draw it as the band's own second row, about 200 px with 200 × 112 slot pictures, so the band plus shelf stays under 40%. Or keep the pop-above but shrink the cards.
- **Undo, from RetroArch:** after Save or Load, the toast says "Saved to slot 2" and the band gets an "Undo save" key for that session. With Undo, saving over a slot could go back to one press, and the press-twice path would stay only for Reset and Quit.
- **Rewind** (Switch Online, Batocera): add a Rewind key to the retro band when the core supports it, as a hold-to-scrub that fills like a fader. Check the GPU cost.
- **Accent on Home:** the band's empty middle would hold the Colour bars clear of the art, but D2 says accents stay out of navigation, so that needs Isaac's OK first. Otherwise accept "no accent on art-heavy homes, accent with Toned covers" as the rule (Bible implications 7), and show both side by side.
- **Steam Guide:** prototype who gets the button under gamescope. If Steam keeps it, NervOS's band opens from Guide on other pads, from the HA remote and from the keyboard, and the Steam key opens Steam's own overlay. Write that down as the rule.
- **Missing screens:** Signal lost (with Retry), the netplay join card, the Power modal (with the press-twice path), Settings › Display (look, Day/Night, Covers, Calm) and the RETURN outro.
- **Game page:** use the empty lower left for "More from this system" or the next collection row, peeking the way Home rows do.
- **Real-art pass:** test with a few real-world-style covers from the box's own artwork folder (locally, never in the repo) to check the bright and red cases against the night cap and the red rule at 3 m.

## Bible implications
1. **Group carousels wrap behind a bookend.** The wrap point is a non-focusable marker (a walnut bar with "Start"). Key repeat stops at it, and a fresh press goes round. Answers D32.
2. **"Never twice" with choosers.** While a chooser is open, its key hides its value and the chooser's lit square carries it. When two keys act on one value (Save / Load and the slot), they share a tray that names it once. Answers D33.
3. **Every hold has a press-twice path.** The first press re-labels the key ("Press A again to quit"), lights its top edge and disarms after 3 s or on focus moves. The same path guards overwriting data (a save slot). This extends D31, and keeps the hold fill on the edge opposite the selector.
4. **One Guide band for all content.** On a launcher, Guide opens the same band for every kind of content: Resume (the one orange), the content's own menu, and Quit (with a hold or press twice). Only the keys change, never the place or shape. Answers D35.
5. **Paused vs running in the band.** When the content is paused, the slot is unlit with "Paused". When it keeps running (Steam, streams), the slot is lit with "Running" and the veil is lighter. This puts the slot shape ("something running") to work on TV.
6. **An app's own vocabulary on shared screens.** An app may keep its approved section names on a shared screen when they're set in house type (sentence case Jost, no codes, numbers, kanji or section colours), and each name is explained by a one-line sign when focused. Proposed answer to D37, pending Isaac.
7. **Accents and full-colour art.** On a home of full-colour covers, the accent steps back, and also while a toast shows. It returns with Toned covers. Either name this as an exception to "one accent per screen", or give the accent a fixed place inside the band. Settles D19 one way or the other.
8. **TV home density.** A TV home shows at least 2.5 rows at rest at 1080p. Cards are about 15% of the width (288 px). The sign is a title + one line, with no eyebrow when a row header already names the row. Labels keep 26/22 px however small the card gets (the Xbox 2023 lesson).
9. **Previews wait for focus to rest.** A large art preview that follows focus (over about 10% of the screen) doesn't swap under key repeat; it updates after focus rests for about 450 ms. A held key through bright and dark covers would otherwise break the 2-per-second flash floor. Add this under §9 Flash and glare.
10. **The resume point is shown once.** "Continue from <time>" lives on the primary key (and in the sign on Home). Facts on the same page give total time played instead of "Played <day>". The resume point (automatic) and save slots (manual) are separate things, and neither repeats the other's time.
11. **Four picture slots is the save-state form.** Save states are four picture cards with a time; Empty is a recess, and the current slot has a lit square. This matches Switch Online's four suspend points, the household-proven form.
