# NervOS · Pass 1

Mockup: `mockups/pass1/nervos.html`. It's interactive. Click the TV, then use:
- the arrow keys;
- Enter (A / OK), held for Reset and Quit;
- Esc or Backspace (B / Back);
- G (Guide), which opens the quick menu in a retro game;
- [ and ] (L1 / R1), which change sections and jump a letter on a shelf.

The pad buttons do the same, and "Hold A" simulates a 1 s hold. The page controls are Lighting (Night / Day), Motion (Full / Calm) and Jump to (Home / Game page / Quick menu). A status line counts presses since Home. Home → A → A starts a game in 2 presses.

Everything in the mockup is made up: the games (some reuse NervOS's own fixture names, such as Harbor Brawl Alpha and Moonlit Duel), the films (JamFin's demo names), the computers and the art. All art is generated flat shapes, with no box art and no logos.

**What NervOS is.** The round brief called NervOS "a launcher for his Godot games". The README says otherwise, so I followed the README. NervOS is *built* in Godot. It launches four kinds of thing:
- emulated games (ARCHIVE);
- Steam games (HANGAR);
- streams and netplay rooms (UPLINK);
- Jellyfin films played in mpv (THEATER).

It runs on one surface: the 65" TV on the Aero 15 at 1080p, seen from about 3 m, with a gamepad, a keyboard and the HA remote. There's no phone or desktop UI, so this pass draws only the TV. The HA phone remote card belongs to Jam Home and isn't redrawn here.

Sources read:
- `projects/nervos/README.md` and `PROPOSALS.md`, plus 10 goldens: hub in NERVOS, VHS and HERO; browse; game menu; hot menu; launch title; settings display.
- `BIBLE.md` 0.5, `CHANGES.md` sections A and D, and the end of `decisions.md`.
- `_hifi-base.css`, mockup 13, the pass-1 TV launcher and JamFin mockups, and two Jam Braun screens (kiosk home and the NerveOS phone remote).
- `notes/pass1-tv-launcher.md` and `pass1-jamfin.md`.

## Research
I ran five web searches. The results were mostly press coverage, the Batocera wiki, ES-DE source and theme READMEs, and user forums. Items marked *(knowledge)* come from my own knowledge, not from a search.

- **Steam Deck / Steam Big Picture.**
  - *What works for a couch:*
    - The home screen opens on a row of recently played games ([PC Gamer](https://pcgamer.com/at-long-last-the-steam-deck-ui-has-replaced-steams-big-picture-mode)).
    - One button summons the main menu (Home, Library, Store…). PC Gamer found that sleeker than the old left-edge tab column.
    - The Quick Access Menu (notifications, friends, quick settings) sits on one button and a chord, and holding the Guide button lists the chords ([Steam forum](https://steamcommunity.com/discussions/forum/1/4423184908207503594), [Windows Central](https://www.windowscentral.com/gaming/pc-gaming/valve-is-finally-replacing-big-picture-mode-on-desktops-with-the-steam-deck-ui)).
    - Fast jump by letter in the library.
  - *Clutter and complaints:*
    - The library has "6 tabs, despite now literally only having a use case for one", and users ask for collections to be their own tab ([Steam forum](https://steamcommunity.com/app/1675200/discussions/2/3385030647941173646)).
    - The Recent row is capped, and there's no "recent activity" sort.
    - *(knowledge)* The home screen mixes store news and "what's new" posts into your shelf.
  - *Lesson:* open on "what we play", keep one library with collections as the way in, and put every in-game action on one button.
- **ES-DE / EmulationStation.**
  - *What works:*
    - Automatic collections (All games, Favourites, Last played) plus custom collections ([ES-DE source](https://repo.retrodeck.net/Xargon/ES-DE/src/commit/e8e668b5aa25c4022beda83af53d0436082a4639/es-app/src/CollectionSystemsManager.cpp), [RetroPie docs](https://retropie.org.uk/docs/EmulationStation)).
    - A system carousel. The v2 theme engine made the carousel an "item" that works in the system and gamelist views alike ([ES-DE theme docs](https://repo.retrodeck.net/Xargon/ES-DE/src/commit/1150b4692ed0759e95373fa7edb7163b89a8af69/THEMES-DEV.md)).
    - Themes pick a layout from the media you've scraped, and Colorful, Retrofix and AlekFull offer immersive, simple and carousel variants ([Retrofix Revisited](https://www.github.com/anthonycaccese/retrofix-revisited-es-de), [AlekFull NX](https://www.github.com/anthonycaccese/alekfull-nx-es-de)).
  - *Clutter:*
    - Many themes are built from system logos (brand marks) and metadata panels: rating stars, developer, publisher, genre, release date and play count, all at once.
    - *(knowledge)* The default "systems first" path forces a choice of console before you see a game. That's fine for one enthusiast and opaque for a household.
  - *Lesson:* collections should come before systems. System cards should use a drawing of the system's media, not its logo. Detail panels should show one line, not a spec sheet.
- **Batocera.**
  - In-game actions are hotkey chords: South opens the emulator menu, West saves to the current slot, North loads it, and D-pad up/down changes the slot. L1 takes a screenshot, and left/right rewind and fast-forward ([Batocera wiki](https://wiki.batocera.org/basic_commands)).
  - *Lesson:* the order Save, Load, Slot is what retro players expect. Chords are invisible to anyone but the person who set them up, which is why a visible menu on Guide is the household-friendly form.
  - *(knowledge)* Batocera's EmulationStation menus are long settings lists with many expert options on the first screen. That's clutter for a couch.
- **Takeaway:** the couch-friendly parts of all three are "recent first", "one button for the in-game menu" and "collections as shelves". The nerdy parts are codes, logos, spec panels and option lists. NervOS's NERVOS look (kanji, hex grid, 0003/0011 counters, hazard stripes) leans the nerdy way on purpose. The house look should lean the other way.

## Design (what and why)
**Home: "what we play".**
- A fixed ribbed **menu band** with walnut trim holds five tabs: Home, Retro, Steam, Streaming, Films.
- Retro, Steam, Streaming and Films are NervOS's four sections in plain words (ARCHIVE, HANGAR, UPLINK and THEATER). The section ids don't change. This is a proposed label set for the Hi-Fi look only, and needs Isaac's OK.
- L1/R1 still switch sections, as the README requires. On the right of the band are the controller (a round LED + "Controller · 72%") and the clock.
- Under the band is the **sign** for the focused item: an eyebrow, the title, facts and one line. The sign swaps by opacity (50 ms out, 100 ms in).
- **Colour bars** sit in the clear zone, right of the sign and below the band. Their two lightest bars are darkened per D10.
- The rows are:
  - **Continue**: recent games from every source, as wide art + plinth cards.
  - **Collections**: Favourites, Play together, Quick games, Recently added and All games. Each is drawn as a walnut shelf of spines, picking up Isaac's "a stack of games (or a shelf?)".
  - **Systems**: a **group carousel**, allowed by decision P4. Focus stays in the second slot, the previous system peeks on the left, the next ones run off the right, and the row header shows "3 of 8".
- Rows scroll vertically so the focused row sits under the sign and the next row peeks.

**System cards show their media.** A cartridge, a disc or an arcade board, drawn flat in a muted label colour on a dark field. This follows Isaac's "show their media", without logos.

**Shelf** (one system or one collection):
- A slim band shows "B · Home" (where Back goes) and the clock.
- A list on the left uses the **leading-edge window** plus an 8 px drawn shift, with the year or the system on the right.
- A preview on the right shows the art, title, facts and one line.
- L1/R1 jump a letter, which replaces NervOS's letter rail.

**Game page.**
- Upper left: the eyebrow (system), the title, facts (players · year · **Played Tuesday**) and one line.
- Then the action keys: **Continue from Tuesday 21:40** (the one orange key), Play from the start, and Favourite (square window + On/Off).
- On the right: the art, then a **Save states** row of picture cards (Slot 1 · Sunday 17:05 …), reached with →.
- The resume point and the slots are different saves, so no time appears twice.
- Steam games get a single Play key and the line "Steam keeps this game's saves". That matches the README: the hot menu is ARCHIVE-only.
- **Focused orange key (D18):** the label turns black, the under-edge deepens from 3 to 7 px, and the same leading window lights cream on a dark-brown recess.

**Launch title card.**
- The flat ribbed shutter halves slide in (460 ms, decelerate).
- The title sits on the seam in Jost capitals. The eyebrow says what's happening ("Neo Geo · Continue from Monday 19:02").
- The **slatted bar** shows the emulator starting, with the sub-line "Starting the emulator". For Steam it says "Starting Steam"; for streams, "Connecting".
- The card holds **only as long as the load, with a 600 ms floor** (D14). The game is composed behind the opaque card before the halves leave (300 ms, leave curve).
- **Stripes** come down the right side and bend out to the right, lined up across the seam and clear of the centred title.
- Calm turns it into a 140 ms fade.

**Quick menu (Guide in a retro game).**
- The game stays visible behind a 45% veil (paused).
- One ribbed **band rises from the bottom**. Its first line has a slot light + "Paused", the title, "Neo Geo · playing 42 min", hints that change with the zone, and the clock.
- The keys are **Resume** (orange), **Save**, **Load**, **Slot** (four small number keys; the chosen one is pressed in), **Picture · Sharp**, **Reset** and **Quit game**.
- **Save and Load act at once** on the current slot, like Batocera's West/North chords, and confirm with a toast.
- **↑ on Save, Load or Slot pops the slot shelf above the band**: four picture cards, with Empty shown as a dark recess, and a square window on the current slot. This follows Isaac's "pop above or below".
- **Picture** opens a list that rises above its own key, with square windows for the current choice.
- **Reset and Quit need a 1 s hold.** The hold fills a cream bar on the key's **top** edge, while the selector window stays on the **bottom** edge, so the two never share an edge. Releasing early cancels.
- Quitting returns to the game page with a toast.
- No orange except Resume.

**One focus grammar.**
- Cards light the base window on the plinth and lift 10 px inside their own layer. The hit box never moves.
- Lists and action keys light the same window on the leading edge. Band tabs and quick-menu keys light it on the bottom edge.
- The focus colour snaps, and only transforms animate.
- Films (Films tab) keep progress on the **art's bottom edge**, so progress and the selector never share an edge (D13).

**Not nerdy.**
- No codes, counters, kanji, hex grids, hazard stripes, scanlines or tickers.
- State words come from the house set: On / Offline / Waiting (action), always shape + word. An offline computer shows a broken-form LED (an outline with a slash) and a plain fix: "Wake it from Jam Home, then try again".
- One title and one line everywhere.

**Day palette.** A mid-light ground `#bdb9b1`; the band stays black. **Calm** turns screen changes into fades, stops the carousel slide, and makes the title card a fade.

## Audit
Checked with Playwright (Chromium) at 1500 px wide with deviceScaleFactor 1.31, so the TV renders at about 1920 px. The keyboard run covered:
- every Home row, the carousel both ways, and all five tabs;
- an offline host toast, the Films row, a system shelf with letter jumps, the game page and save states;
- the title card mid-load, playing, the quick menu, the slot shelf and the Picture list;
- a held Quit, then Day and the Jump buttons.

The page was also checked at 390 px in the dark scheme.

Final results: no JS errors, no TV text under 22 px, no horizontal scroll at 390, and all text inside the safe area. Only full-width row boxes and peeking cards cross it.

The fix pass corrected:
- negative SVG radii from a signed shift in the art hash (it threw about 60 console errors);
- text in the slim band and the home clock sitting above the 54 px safe line;
- toasts covering the tab band (they now sit top right, below the band);
- the dark focus shadow reading as a second bar under the plinth (it's now smaller and fainter);
- straight Stripes on the title card (they now drop and bend right as the bible describes);
- a colour-only favourite mark in shelf lists (removed);
- the "Guide opens the quick menu" toast staying over the open menu;
- netplay rooms reusing the computer art.

| # | Problem | Severity |
|---|---|---|
| 1 | **Renaming the sections.** Retro / Steam / Streaming / Films in plain words is my call for the household, but ARCHIVE / HANGAR / UPLINK / THEATER are NervOS's own names, used in all four approved looks. Isaac hasn't been asked. | High |
| 2 | **"Never twice" breaks while a pop-up is open.** With the slot shelf open, the current slot shows twice: pressed key "2" on the Slot key, and the square window on the Slot 2 card. With the Picture list open, "Sharp" shows on the key and as a lit window in the list. JamFin's strip has the same pattern. | Medium |
| 3 | **The systems carousel has no wrap marker.** It wraps (Arcade sits left of Super Nintendo) with no sign that the ends meet. "3 of 8" helps, but a held → loops forever. | Medium |
| 4 | **The art is placeholder and samey.** Every game is a sun-over-hills scene in six palettes. Real covers from the user's artwork folder will be far busier and more colourful, which makes the Colour bars accent and the cream selector compete with art (the same issue as JamFin #5). | Medium |
| 5 | **The toast sits over the accent** (top right, below the band). It's legible, but it breaks "accents in a clear zone" while it shows. NervOS's README puts toasts top right too. | Low |
| 6 | **Home fits about 1.8 rows**, like JamFin. The sign and accent take about 280 px. With many systems or collections, people scroll more than in NervOS's hub, which shows 8 tiles at once. | Medium |
| 7 | **The quick menu covers 22% of the picture**: band 240 px, plus 372 px with the slot shelf open. The keys only fill 1257 of 1728 px. The band could be shorter, or the keys bigger. | Low |
| 8 | **Not designed:** THEATER's hot menu (left to JamFin's player band), the netplay host/join flow, Signal lost, Settings, the Power modal, the OSK, attract, boot, and the launch outro (RETURN / ABORT afterimage). | Medium |
| 9 | **Steam games get no NervOS quick menu.** That's what the README says (the hot menu is ARCHIVE + THEATER), but a household member pressing Guide in a Steam game gets a different menu than in a retro game. Two menus on one button. | Medium |
| 10 | **Hold-to-confirm needs a held A.** The HA remote over MQTT may not send key-up events. If it can't hold, Reset and Quit are unreachable from the remote. | Medium |
| 11 | **Day palette:** the lit window keeps a dark rim, but the Day plinth `#cfcbc3` against the ground `#bdb9b1` is a faint step. Day focus depends almost entirely on the 10 px lift and the cream window. | Low |
| 12 | **Collection spines can't show counts above about 11**, and they're decorative: two collections with different games look alike at 3 m. | Low |
| 13 | **GPU cost not measured.** The art is SVG here; on the box it's textures. The ribbed band is a static gradient, cached once in Godot as the bible requires. Nothing animates at rest except the clock. | Low |

## Change suggestions for the next pass
- **Section names:** show both options on the band (plain words vs NervOS's names in Jost sentence case: Archive, Hangar, Uplink, Theater) and let Isaac pick. Theater might simply be "Films" in either.
- **Carousel ends:** add a thin walnut divider card ("Start of list") at the wrap point, or stop at the ends with the last neighbour greyed. Test a held → for speed.
- **Real art:** design with busy full-colour covers. Try a Toned option (JamFin D20) and drop the Home accent when art is full colour.
- **Space:** move the sign into a taller band on Home only, like the JamFin suggestion, and aim for 2.3 rows.
- **Quick menu:** shorten the band to 200 px and make the keys 88 px tall. Show the slot shelf as the band's own second row instead of a pop-above, which removes the duplicate slot value. Add Screenshot (Batocera's L1) and, if the emulator supports it, Rewind.
- **Remote:** give Reset and Quit a two-press alternative ("Press A again to quit") for inputs that can't hold.
- **Missing screens:** Signal lost (a plain-language error with Retry), the netplay join card, the Power modal (focus on Cancel, hold for Shut down), Settings › Display (look, Day/Night, Calm), and the RETURN outro.
- **Steam Guide:** decide whether NervOS shows a thin "Back to NervOS · Steam menu" band on Guide in Steam games, so the button means one thing.

## Bible implications
1. **Hold progress lives on the opposite edge from the selector.** A hold-to-confirm key fills on its top edge, and the base window stays on the bottom edge. This extends D1/D13 ("never the same edge") to hold timers.
2. **Group carousels need an end rule.** §9 allows them with neighbours and position shown. Add whether they wrap, and if so, how the wrap point is shown.
3. **"Never twice" while a pop-up is open.** Say whether a chooser that shows the current value (a lit square) may sit over the key that also names it, or whether the key's value hides while its chooser is open.
4. **Media, not logos, for systems and sources.** Groups of things (consoles, inputs, apps) are drawn as their physical media or a neutral device glyph, never a brand mark. This matches mockup 12's "media cards are drawn as devices".
5. **One in-game menu per button.** On a launcher, Guide should open the house menu for every kind of content, even when it only offers "Resume / Back to launcher" before handing off to the content's own menu.
6. **Hold-to-confirm needs a non-hold path** for remotes that can't send a key-up (HA over MQTT).
7. **The title-card hold (D14) applies to every launch**, not only JamFin's Play: emulators, Steam and streams hold only as long as the load, with a 600 ms floor.
8. **Plain section names on shared screens.** Shared screens use the house look (§1). Say whether that covers words too: should an app's own vocabulary (ARCHIVE, HANGAR, UPLINK, THEATER) give way to plain words in Hi-Fi, or stay as the app's voice?
