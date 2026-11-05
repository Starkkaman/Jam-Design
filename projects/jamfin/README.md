# JamFin

> Owner: the **JamFin Agent** session. Seeded from its interview on 2026-11-04, then checked against the code on the
> `mobile` branch of Starkkaman/Jamfin (TV 0.3.3, phone 0.3.1) and corrected. Facts, not pitches: this is the UI as it is today.

## At a glance
- **What it is:** a Jellyfin client in two apps on one code base (repo Starkkaman/Jamfin, private):
  **Jamfin TV** for the Hisense Google TV, with Blu-ray ISO disc menus (HDMV and BD-J) and Seerr requests, and
  **Jamfin** for phones and tablets (Android now, native iOS later), with downloads and offline play.
- **Surfaces and input:**
  - **TV first.** 10 ft, often at night. D-pad remote, **taps only** (no long or double presses: the family remote goes
    through Home Assistant). Also a K400 keyboard for search, and voice search.
  - **Phone second.** Touch with haptics (`performHapticFeedback` constants only). Tablet and landscape layouts exist.
- **Stack:** Kotlin + Jetpack Compose (tv-material 1.1.0 on the TV), Media3 for playback, libbluray for discs.
  Modules: `:core`, `:ui-common` (shared by both apps), `:player`, `:disc`, `:jellyfin`, `:downloads`, `:app` (TV), `:mobile` (phone).
- **Looks:** eight, each with Day / Night / Auto, picked per device in Settings > Appearance: Cut Paper, Kinetic Grid,
  Swiss Poster, Video Store, **Unigrid**, Olympia, New Wave, Cel '88. **Isaac's TV runs Unigrid.**
  (A fresh install with nothing stored falls back to Cut Paper: `Design.parse`.)
- **Theming lives in:** `ui-common/.../ui/theme/` (Palette, Look, LookSkin, one `<Name>Look.kt` per newer look). Full list below.
- **Rules every look obeys:** `docs/experience-system.md` (summary below).

## Screens

### TV (1920×1080, UI laid out at 960×540 dp: 1 dp = 2 px)

| Screen | What it does | Screenshot |
|---|---|---|
| Profile picker ("Spiral") | Pick a signed-in Jellyfin user; a spiral iris (after *Vertigo*) on switch. Only accounts already signed in on this TV are shown. | missing (see below) |
| Add profile / Quick Connect / add server | Type username + password, or Quick Connect; servers and addresses. | missing |
| Home | Menu + rows: Continue watching, Next up, Latest movies / shows, Blu-ray shelf. Opens with focus on the first Continue watching card. Unigrid: the enamel band with the menu, and the **platform sign** (title, facts, time left) for the focused card. | [night](screens/tv-unigrid-night-home.png), [day](screens/tv-unigrid-day-home.png) |
| Movies / Shows / Blu-ray grids | 5 columns (posters), an A–Z jump strip on the right, the **Organise** header (Sort, Filter, View) and library chips. | [Unigrid grid](screens/tv-unigrid-night-grid.png) |
| Organise columns | Sort, Filter (with value columns and removable chips), View, People: columns that open from the grid's header. | missing |
| Discover | Seerr: trending, popular, requests; each title opens a request page. | missing on TV (phone below) |
| Request page / Seerr sign-in | Request a film or seasons; status words (Available, Partly available, Requested, Processing, Pending). | missing on TV |
| Search | QWERTY keyboard (+ Voice key) top left, results beside and under it; the keyboard folds into a bar when results have focus. | [Unigrid](screens/tv-unigrid-night-search.png) |
| Settings | Categories on the left (Profile, Appearance, Home, Captions, Caption look, Audio, Audio output, Playback, Discs, Server, Requests, About), the category's rows and choosers on the right. | [Unigrid](screens/tv-unigrid-night-settings.png) (before tv-fixes: poster print colour has since moved from Profile to Appearance) |
| Film page | Title, facts, Resume / Play, then Audio, Subtitles, Watched, Favourite; overview and credits; rows below (Extras, cast, More like this). Unigrid: the actions are **stops on a vertical amber line**. | [Unigrid](screens/tv-unigrid-night-film.png), [long title](screens/tv-unigrid-night-film-long.png) (960×540 source) |
| Series page | Title, facts, Next up button, Mark as watched, Add to favourites, season chips, episode row. | [Unigrid](screens/tv-unigrid-night-series.png) (960×540 source) |
| Episode page, collection page | As the film page. | not added |
| Person page | Photo, biography, filmography rows. | [Unigrid](screens/tv-unigrid-night-person.png) (shows the open bug: it opens scrolled past the name) |
| Screen change (planes) | Pushed screens and Back move in planes (Unigrid: "a new sign is hung"). | [Unigrid, mid-change](screens/tv-unigrid-night-forward-mid.png) |
| Player | A one-line **band** at the bottom: title line, timeline with chapter stops, time and "Ends at". UP pops the **chapter cards** above it; DOWN pops the **settings strip** below it (the band lifts). Lists from a strip tile rise above the band. INFO overlay, skip pill, toasts, "Next episode", "Still watching?". | [chapters above](screens/tv-unigrid-night-player-chapters.png), [settings strip below](screens/tv-unigrid-night-player-settings.png); other looks: [Olympia chapters](screens/tv-olympia-night-player-chapters.png), [Cel '88 strip](screens/tv-cel-night-player-settings.png), [Cut Paper speed list above the band](screens/tv-cut-player-settings-list.png) |
| Disc player | The disc's own menu (arrows/OK go to the disc), the strip at the bottom over it, "RESUME AT 0:21:24 / DISC MENU" prompt, a loading sequence. BACK twice to leave. Drawn in Cut Paper in every look. | missing |
| Disc **house menu** | Generated menu when a disc's menu can't run: main feature, chapters grid, extras, audio/subtitles, with the reason. | **missing** |
| States | Loading (static skeleton < 1 s, the look's motion 1–10 s, a sentence + Retry after 10 s), empty (one line + the action that fills it), error (one sentence + a focused recovery button), milestones. | [Cel '88 loading](screens/tv-cel-night-loading-moving.png), [Cel '88 empty Continue watching](screens/tv-cel-night-empty-continue.png), [New Wave error](screens/tv-newwave-night-error-home.png); Unigrid states missing |

One Home per other look (all Night, demo build):
[Cut Paper](screens/tv-cut-night-home.png) ·
[Kinetic Grid](screens/tv-kinetic-night-home.png) ·
[Swiss Poster](screens/tv-swiss-night-home.png) ·
[Video Store](screens/tv-store-night-home.png) ·
[Olympia](screens/tv-olympia-night-home.png) ·
[New Wave](screens/tv-newwave-night-home.png) ·
[Cel '88](screens/tv-cel-night-home.png)

### Phone (1080×1920 portrait; player in landscape)

All existing phone shots are Cut Paper or Kinetic Grid from 2026-10-31 and 2026-11-01, **before** the looks-030 phone
skins and before the player's settings sheet moved below the band. Unigrid, Olympia, New Wave, Cel '88, Swiss and
Video Store are built for the phone but have never been seen on one.

| Screen | What it does | Screenshot |
|---|---|---|
| Profile picker, first run, add profile, add server | As on the TV, by touch. | not added |
| Home | Header, rows, bottom bar (Home, Movies, Shows, Search, More / Discover / Downloads); pull to refresh. | [Cut Paper](screens/phone-cut-night-home.png) |
| Library grid + Organise sheets | 3 columns in portrait; Sort, Filter and View as bottom sheets. | [grid](screens/phone-kinetic-night-movies.png), [sort sheet](screens/phone-cut-night-organise-sort.png) |
| Film / episode / series / person / collection pages | Hero art, title, facts, buttons as chips, rows. | [film](screens/phone-cut-night-film.png) |
| Search, More | Search field + results; More lists the other sections. | not added |
| Discover + request pages | Seerr rows with status tags. | [Cut Paper](screens/phone-cut-night-discover.png) |
| Settings | Category list, then a page per category (Appearance shown). | [list](screens/phone-cut-night-settings.png), [Appearance](screens/phone-kinetic-night-settings-appearance.png) |
| Downloads | Queue and finished downloads, per item quality sheet; offline home and player. | [queue](screens/phone-cut-day-downloads.png), [download sheet](screens/phone-kinetic-night-download-sheet.png) |
| Player | Top bar, play button, Chapters / Settings buttons, touch timeline; chapters above the band, settings sheet; skip pill; brightness, portrait lock, PiP. | [controls](screens/phone-cut-night-player-landscape.png), [chapters](screens/phone-cut-night-player-chapters-landscape.png), [settings](screens/phone-cut-night-player-settings-landscape.png) (old placement), [skip pill](screens/phone-kinetic-night-player-skip-landscape.png) |
| Server dashboard, remote control | Admin dashboard (phone 0.3.1); control the TV from the phone. | not added |

### Missing screenshots (not captured: the TV is shared and none were taken for this doc)
- **Disc house menu** and the disc player's strip over a disc menu (no shot exists in any round).
- **Unigrid Settings after tv-fixes** (the shot above still has the print colour under Profile).
- Unigrid: Organise columns open, a player list rising above the band, loading / empty / error states, Discover, profile picker.
- TV toasts and the TV skip pill.
- Every phone shot in Unigrid (and in the other four newer looks), and the phone player with the settings sheet below the band.

## Components

"Custom" = drawn by Jamfin, not a Material / tv-material component. Almost everything is custom.

| Component | Custom? | Notes |
|---|---|---|
| Title card (`PosterCard`, `SharedCard`) | Yes | Poster 2:3, wide 16:9 or banner per Settings > Appearance > artwork shapes. Each look draws its own: Unigrid `UnigridCard` (rises onto the line ×1.04, hard shadow 4→14 dp, keyline); Olympia posterised four-tone print that resolves to full colour; Video Store clamshell box / sleeve; New Wave tilted card; Cel '88 cel. Resume progress is always a bar on the card's bottom edge. One accessibility node per card (`cardNode`). |
| Home row (`LineRow` in Unigrid, `Lane` in Olympia, shelves in Video Store) | Yes | Unigrid: a row is a transit line, cards hang from stops, the bullet slides to the focused stop (150 ms; 80 ms under a held key); the line dims to 62 % when not focused. Rows of 4–5 cards; next card peeks. Prefetch 8 cards (`rememberRowState`). |
| Platform sign / timing board / hero | Yes | The focused title's sign above the rows (Unigrid `PlatformSign`, Olympia `TimingBoard` + `Hero`). Old face out in 50 ms, new settled by 150 ms. |
| Button (`CutButton` TV, `TapButton` phone; `SharedButton`) | Yes | `ButtonStyle` Slab / Outline / Fill / Sign / Plate / Tile, or the look's skin `Plate`. Plain wording from `ActionLabels` (core). Unigrid `Plate`: fine inset frame; focus = charcoal plate on a hard shadow with a white keyline. New Wave adds 1-bit icons (`ButtonLead`). |
| Film-page actions (Unigrid `FilmActions`) | Yes | Stops on a vertical amber line; the focused one becomes a small sign. |
| Nav / menu | Yes | Per look: Unigrid enamel band (136 dp on Home / Discover, 50 dp elsewhere) with the station marker on the rule; Olympia pictogram strip; Cut Paper side slab; Swiss masthead; Video Store aisles on a ceiling rail; Cel '88 top bar. Back from a row goes to the menu. Phone: bottom bar (`SharedBottomBar`), `NavRail` on tablets. |
| A–Z jump strip (`JumpStrip`) | Yes | One accessibility node. |
| Organise header + columns (`OrganiseHeader`, `OrgColumn`, `OrgTile`, `FilterChips`) | Yes | Sort / Filter / View / People columns on the TV; bottom sheets on the phone. |
| Settings rows (`SettingsSpec`, `SettingRow`, `ChoiceRow`) | Yes | Category list + rows; a choice row cycles or opens a chooser ("Subtitles: Off ▸"). Chips for the look, Day / Night / Auto, print colours. |
| Player band (`OneLineOsd`) | Yes | One line: title, "Demo playback", chapter; timeline with chapter stops (Unigrid: amber play bullet riding a line of stops; Olympia: segments with a square head; skins: `drawTimeline`); time and "Ends at". |
| Chapter cards (`ChapterLayer`, `ChapterCards`, `UnigridChapterCard`, `OlympiaChapterCard`) | Yes | Pop **up above** the band (200 ms open on Glide, 150 ms close on Leave). |
| Settings strip (`PlayerPanel`, `PlayerSettingsRows`) | Yes | Pops **down below** the band (the band lifts by the strip's height): Subs, Audio, Chapter, Speed, Picture, Info, Play from the start, Exit. Lists from a tile rise above the band, never over the timeline. |
| Player toast (`PlayerToast`) | Yes | Top-left inset text (e.g. track change, burned-in subtitles). |
| Skip pill (`SkipPill`, `SkipPrompts`) | Yes | "Skip intro ▸" from Jellyfin media segments, bottom right; optional tap. |
| Keyboard (`QwertyKeyboard`, `QwertyLayout`) | Yes | Voice key, digits, QWERTY, Space / ⌫ / Clear; wraps vertically; folds to a bar. |
| State views (`StateViews`, `UnigridStates`, `OlympiaStates`, `PlaneLookStates`, `MilestoneOverlay`) | Yes | Loading, empty, error, milestone per look ("Checking the timetable", "End of the line" in Unigrid). |
| House menu (`HouseMenuScreen`: `Panel`, `PanelRow`, `ChapterGrid`) | Yes | Disc player only, Cut Paper styling. |
| Profile picker (`Spiral`, `SpiralMesh`) | Yes | Shared spiral on each look's tokens. |
| Phone sheets (`Sheet` in mobile Kit) | Yes | Settings sheet rides under the player band; Organise, download quality. |

## Fixed zones (must not move in any look)
From `docs/experience-system.md` section 1:
- **Film page:** reading order title, facts, Resume / Play, then the rest. **Title and the primary button sit in the
  upper-left quadrant of the TV safe area.**
- **Cards:** resume progress is **always a bar on the card's bottom edge**.
- **Player:** time and timeline are **always at the bottom**. Chapters pop above it, the settings strip below it; nothing covers the timeline.
- **Focus graph:** the same items focusable in the same order in every look. Home opens on the first Continue watching
  card; the film page opens on Resume (else Play); Back restores focus to the item that opened the screen.
- **Presses:** Continue watching plays in ≤ 3 presses after the profile (Home → OK → OK); any screen ≤ 6 presses from Home.

## Where theming lives
All paths on the `mobile` branch (`.../` = `src/main/java/com/isaac/jamfin/`).

| What | Where |
|---|---|
| Design enum (8 looks, stored by name in the `settings` DataStore, key `design`) | `core/.../ui/theme/Design.kt` |
| Palettes: Day and Night per look, as roles (`ground`, `onGround`, `mutedOnGround`, `slab`, `onSlab`, `rule`, `band`, `onBand`, `bandAccent`, `strip`, `timeline`, `tag`, `focusFill`, `focusEdge`, accents red / ochre / teal…) | `ui-common/.../ui/theme/Palette.kt` |
| Look registry: type, `ButtonStyle`, `PosterFocus`, `Texture`, flags (`ruled`, `compact`, `sentenceCase`, `lowercase`…), `planes` | `ui-common/.../ui/theme/Look.kt` |
| Skin hooks (cards, plates, frames, timeline, backdrop, band backdrop, page ground, button lead) used by New Wave and Cel '88 | `ui-common/.../ui/theme/LookSkin.kt` |
| Per-look palettes, fonts and tokens | `ui-common/.../ui/theme/UnigridLook.kt`, `OlympiaLook.kt`, `NewWaveLook.kt`, `Cel88Look.kt` |
| Motion tokens: menus 200 / 150 ms, Back 240 / 150 ms; easings Leave (.4,0,1,1), Settle (.3,1.3,.5,1; spring damping 0.75), Glide (.2,.8,.2,1) | `ui-common/.../ui/common/MotionTokens.kt` |
| Plane engine for screen changes (focus 150 ms; 600 / 300 ms) | `ui-common/.../ui/common/Planes.kt` |
| Loading mask (`Arrival.CAP_MS` = 120 ms), signatures, Back exits, key repeat, text fit | `ui-common/.../ui/common/Arrival.kt`, `Signature.kt`, `BackExit.kt`, `Keys.kt`, `FitText.kt` |
| TV screens a look draws itself (`TvDesign`: Main, Detail, Person, Request, Grid, `Shared*` components) | `app/.../ui/TvDesigns.kt`, plus `app/.../ui/<look>/` |
| Phone per-look components (`PhoneLooks.current.Shared*`) | `mobile/.../mobile/ui/PhoneLooks.kt`, `PlaneLooks.kt`, `UnigridPhone.kt`, `OlympiaPhone.kt` |
| Button wording | `core/.../ui/detail/ActionLabels.kt` |
| Fonts (bundled OFL TTFs) | `ui-common/src/main/res/font/` |
| UI sounds (8 sets, 56 WAVs) | generated by `tools/make-ui-sounds` |
| The rules | `docs/experience-system.md` |

Selected in Settings > Appearance (Design, Day / Night / Auto, Covers, artwork shapes, poster print colour, Calm motion,
Animate Back, Interface sounds). `JamfinTheme` provides `LocalLook` / `LocalPalette`; shared code asks tokens, never "which design".

## The experience system (summary of `docs/experience-system.md`)
The file is on the `tv` and `mobile` branches of Starkkaman/Jamfin (`mobile` has the newest copy, 2026-11-03).
"One experience, many looks. A look changes the surface (material, colour, type, texture, the shape of the menu) and
gets one signature moment. It never changes where things are, what a key does, how long things take, or what a button says."
- **Invariants:** focus graph, menu reachability, fixed zones, presses (above). **Plain verbs**: "Resume from 1:12:04",
  "Play from the start", "Audio: English 5.1", "Subtitles: Off", "Mark as watched", "Add to favourites", "Request",
  "Download"; a look may restyle but not reword them. **Text sits still**: body text never textured, glitched, rotated or
  misregistered; effects only on headlines ≥ 32 dp. **Contrast**: night ground about #161412 (each look tints it; Unigrid
  #232326, Olympia #212D3A, Video Store navy #1B1F3A), text about #E8E2D6, secondary ≥ 4.5:1, nothing pure white, true black only behind video, Day palettes mid-light.
- **Motion budget:** focus starts on the key-press frame and settles ≤ 150 ms (two cues, one not colour); under key
  repeat ≤ 80 ms or snap; screen enter ≤ 350 ms and usable from the first frame; Back ≤ 250 ms (entry reversed; Animate
  Back off = cut); signature ≤ 600 ms full, ≤ 300 ms short (full once per session); Play never waits for a signature.
  Everything interruptible; springs dampingRatio ≥ 0.7; at most one thing moves besides the focused item; no flashing
  more than 3 times a second. **Calm motion**: signatures become ≤ 150 ms fades, Back a cut, no parallax.
- **Masking:** a pushed screen's entry waits until it's composed, its data is there and its first pictures are decoded,
  never more than 120 ms. Focus dwell of 280 ms pre-fetches a film page. Late pictures fade in over 150 ms, never pop.
- **Sound and haptics:** Interface sounds Off / Subtle / Full, a set per look, never during playback. One haptic map for every look.
- **Delight only at:** profile pick, film-page reveal, pressing Play, finishing a title, empty / error / loading states.
  Never in focus moves, held keys, scrolling, Back, search typing, dialogs, the player overlay or scrubbing.
- **Acceptance checks:** zones at 960×540 dp; hold Right 3 s on a 40-card row with p90 ≤ 16.7 ms; twenty presses land
  twenty items along; Back restores focus; contrast of every text role; Calm = nothing over 150 ms; newcomer test.
- **Decisions 2026-11-03:** Back animates (with a switch); Unigrid, Olympia and Kinetic Grid are the reference for feel
  and cost; player menus work like Unigrid's in every look.

## Hard constraints
- **TV hardware:** MediaTek MT9690, Mali-G57 GPU, 32-bit, 3.7 GB RAM, UI at 1080p (960×540 dp). HWUI redraws the whole
  1920×1080 frame every time, so it is **GPU-bound on full redraws**. Hence:
  - animate only transforms and alpha (`graphicsLayer`); never tilt or scale a full-screen layer;
  - **no blur**; no offscreen alpha (render-target switches are costly on the tiled Mali; fades use `ModulateAlpha`);
  - texture only as static tiles or cached bitmaps, never animated, never a full-screen pass (a full-screen grain costs 3–9 ms of GPU a frame);
  - dims are colour filters on the picture, never a blended rect over it; repeated decorations are cached bitmaps;
  - every item that changes on focus gets its own layer; text that changes per focus move gets its own layer;
  - **never move a focus target with a transform** (a lift ahead of the focus modifier broke D-pad search): lifts are drawn inside the layer;
  - two screens of type are never on together; anything new on a key press is composed before it's shown.
- **Accessibility service on the TV** (Projectivy launcher): Compose diffs the semantics tree on the main thread
  (3–7 ms after each changed frame), so one node per card.
- **Late frames today** (TV 0.3.3, release app, Isaac's real library; janky %):

  | Look | Moment | Late frames |
  |---|---|---|
  | Unigrid | opening a film (warm) | 15 % → about 6 % |
  | Unigrid | opening a film (cold) | about 11 % |
  | Unigrid | Back | about 10 % (the first frame 22–34 ms, then 10–13 ms) |
  | Unigrid | moving along home rows | 1–3 % |
  | Olympia | opening a film | about 6 % |
  | Kinetic Grid | opening a film | about 11 % (its full-screen header is measured in one 26–29 ms block) |
  | every look | after each changed frame | + 3–7 ms of Compose accessibility work |

  Targets: janky ≤ 3 %, p90 ≤ 17 ms, p99 ≤ 25 ms (home rows ≤ 2 %). Not yet met for page opens and Back.
- **Input:** taps only, no long or double press. (The disc player also accepts a held BACK to reach the house menu, but only as a bonus; every path works with taps.)
- **Fonts:** bundled OFL TTFs only, subset where large: Archivo, Archivo Black, Barlow, Barlow Condensed, Bungee, Dela
  Gothic One (katakana subset), Jost, Karla, Londrina, Saira, Schibsted Grotesk, Sofia Sans Extra Condensed (italic),
  Syne ExtraBold, Zen Kaku Gothic New. IBM Plex Mono is OFL but not bundled.
- **Contrast:** every text role ≥ 4.5:1 on its ground in all sixteen palettes (unit-tested).
- **Must not change:** the focus graph, the fixed zones, plain button wording, Continue watching in ≤ 3 presses, no long or double presses.

## What Isaac has said
- **Liked:**
  - "I really like Unigrid, Olympia, new wave and cel88"
  - "the way the unigrid playback menus pop above or below the timeline we should use that everywhere"
  - "New wave feels the most polished"
  - Cel '88's "parallaxing city"
  - "I like the animations best of Unigrid, Olympia, and kinetic grid"
- **Rejected:**
  - Cel '88's smash cut and selector flash: "lets make the experience a bit calmer"
  - Early mockups: "a lot of wasted space"
  - Swiss: "too dense … too bright. It feels cold and harsh"; Video Store's white "too bright"
  - "All the designs feel like they're lacking polish … a little amature … make them less contrasty … more texture, and
    potentially a bit of grit … look quite a bit more different from eachother"
  - "animations still hitch a lot and should mask when things haven't finished loading or should be better optimized
    for the hardware … check it in the real app with real content."
  - Bugs: "cel'88 the selector gets stuck at the top", "some text that doesn't fit in a few of the theme"
- **Asked for:**
  - The aim: "fun without sacrificing clarity"
  - Full-colour covers as an option; poster, wide and banner artwork shapes
  - Back animated, with a setting to turn it off
  - "poster print color should be under appearance"
  - On discs: BACK twice to leave a disc menu (2026-10-26)

## Open questions for the bible
1. **Units on Android TV.** The bible's TV floor is in px at 1080p (body 26, min 22). Jamfin works in dp/sp at
   960×540 dp, so 1 sp = 2 px: 11 sp is the floor, 13 sp the body. Unigrid sets text at 12–15 sp (24–30 px); the other looks 15–18 sp. Can the bible state TV sizes in both?
2. **TV always dark?** Every Jamfin look has a Day palette on the TV (mid-light, never paper-white) and Isaac can pick Day / Night / Auto. Does the bible's "TV surfaces are always dark" retire the TV Day palettes?
3. **Hi-Fi as a ninth look or a replacement?** Would Hi-Fi join the eight looks on the same roles and invariants, or replace the default? Which of the eight survive the shelf?
4. **Role mapping.** Jamfin's roles (`ground`, `slab`, `band`, `strip`, `rule`, accents, per-profile accent) vs Hi-Fi's (`alu`, `card`, `band`, `walnut`, `orange`, light colours). Is a per-profile accent allowed when orange is reserved for controls?
5. **Lounge "one title + one line" and "tiles = one word"** vs Jamfin's film page (overview, credits) and plain verbs ("Resume from 1:12:04"). See PROPOSALS.md.
6. **Corners.** Hi-Fi radii 10–18 px; three Jamfin looks are square by rule. Per-look or base?
7. **Flash limit:** bible 2 per second, Jamfin 3 per second. Jamfin can adopt 2 if the bible wants one number.
8. **Signature move on the TV:** is "light reveal" the base look's one signature moment (film-page reveal, Play), or also the focus cue?
