# JamFin · Pass 2

Mockup: `mockups/pass2/jamfin.html` (pass 1 is unchanged). Click the TV, then use the arrow keys, Enter (OK), Esc or Backspace (Back) and M (Menu), or the remote buttons on the page.

The page controls are:
- **Profile:** Ada, Ben or Cleo. Each profile has its own saved look, and the lighting, covers and motion controls edit the current profile.
- **Server:** Online or Offline.
- **Stream ready after:** 0.4, 1.1, 4 or 13 s.
- **Title card hold:** Pass 2 or Pass 1.
- **Jump to** buttons for every screen, and **Player states** buttons for skip intro, next episode, still watching, loading and error.

The status line shows how long the title card was shown and why.

The TV is written in **cqw** (1920 × 1080 design units, 1 cqw = 19.2 px), as the brief asks. The pass-1 TV used a scaled px stage.

There are three phone frames: Home and the show page at 390 × 844, and the landscape player at 844 × 390.

All titles, people, avatars and art are made up and drawn as flat generated shapes. There are no posters, faces or logos.

Sources read:
- `notes/OVERNIGHT-BRIEF.md`, `CHANGES.md` (A, B, D1–D52), the end of `decisions.md`, and `BIBLE.md` 0.5.
- `projects/jamfin/README.md` and `PROPOSALS.md`, plus these screenshots: Unigrid series, Unigrid player settings strip, and the pass-1 shots.
- Every `notes/pass1-*.md`. `notes/pass1-jamfin.md` was the to-do list.

## What changed since pass 1

Pass-1 audit item → what pass 2 does:

| Pass-1 # | Was | Now |
|---|---|---|
| 1 (High) | The title card held 1.6 s even when the stream was ready at 1.1 s. | It holds **only as long as the load**. The first Play of the session uses the full shutter with a **600 ms floor**. Later plays use a **300 ms short form**, and Calm uses a 140 ms fade. The "Title card hold" switch shows pass 1's rule. At 0.4 s, the status line reads "1600 ms · stream ready at 400 ms · added wait 1200 ms" under pass 1, against "400 ms · no added wait" under pass 2. A load over 10 s gets a sentence ("The server is slow to start this") and a Back hint, and Back stops it. |
| 2 (High) | "Said once" wasn't consistent: the episode card showed a bar plus "15 min left". | **One rule everywhere.** The bar on a card means "how far you are". The plinth gives the runtime or "Watched · 44 min", never "N min left". The sign and the pages give **Ends at**. The playhead carries its own time. New sub-rule: **an open layer carries its value**. While Audio's chooser is open, the key reads just "Audio". While the chapter shelf is open, the band's "Chapter 6 of 12" hides. Watched episodes have no bar. |
| 3 | The split selector was weak (cream on cream, a 9 px window). | The window is **12 px in full cream**, and progress now fills at **70% cream** (`#ada48f`), so the two never read alike. The face lifts **14 px** and brightens a step more, and the label snaps to cream. A **baked spill** (Isaac's "warm colour plus baked spill") fades in under the card by opacity only. The same grammar applies to profile tiles, menu tabs, season keys, strip keys and chapter cards. |
| 4 | Home fit about 1.8 rows. | The **sign moved into the menu band**: title plus one line (year · runtime · rated · Ends at), which the bible's home-screen floor asks for. The band is 250 px. Home now shows **two full rows plus the next row's name**, about 2.15 rows. |
| 5 | Session blocks (with a red square) clashed with full-colour covers. | The accent is now **Stripes**, inside the black band's own clear zone: under the tab line and right of the sign, never touching a cover. There is no red. It **steps back while the server is offline** (D22) and is shown on Home only, per Isaac. |
| 6 | Focus on the orange primary was weak. | The focused orange key **rises 6 px**, its under-edge deepens from 3 to 9 px, the label goes black, and its leading window lights cream on a brown recess (the NervOS cue, so it's one house rule). |
| 7 | TV Day focus was faint. | Day ground `#bab6ae`, card `#d4d0c8`, focused card `#ece8e0` (a bigger step), black labels on focus, and a white spill. Windows stay a dark recess in Day (D17). The band stays black. Ben's profile uses Day. |
| 8 | The chooser popped *beside* its action. | Audio and Subtitles now **drop below their key** and cover the keys under it, never the title or the key itself. Nothing pops beside any more, so "above or below" holds everywhere (D16). |
| 9 | Player states weren't designed. | Drawn: **Skip intro** and **Next episode** (bottom right above the band, the player's one orange), **Still watching?** and **error** (a centred panel on a dimmed picture, with the recovery key focused), and **loading after a seek** (a slatted mini bar plus an amber slot and "Loading"). The intro segment is marked on the timeline (a Jellyfin media segment). **The disc house menu** is drawn (D35). |
| 10 | The lifted band plus strip covered 31% of the picture. | The strip is now **part of the band**. The band lifts 74 px instead of 142, and strip keys are 64 px. The lifted band covers **25%** (270 px). |
| 11 | Toned was a CSS filter. | Unchanged in the mockup. It is still a `ColorFilter` on the picture in the app (see audit). |
| 12 | A sliver of "Add to favourites" stayed under the band. | Rows below the actions now open a **lower view**: the top of the page fades and lifts, and the row slides up under the slim band. No focus target is ever half hidden. Back returns to the top of the page. |
| 13 | The phone's moving primary flickered. | It moves only after the scroll has settled for 120 ms (90 ms in pass 1), as a colour step. |
| 14 | Profiles and Settings weren't drawn. | **Profiles** (each profile's saved look in one line under the row) and **Settings › Appearance** (saved to the current profile; OK cycles a value, as JamFin's choice rows do) are both drawn. |
| 15 | px stage, not cqw. | cqw throughout the TV. |

Shared findings adopted:
- **D32, carousel end rule.** Rows **stop** at both ends and never wrap. Library rows end with an **end card** ("All films · 214 in the library", which opens the grid). The empty space after the last card shows the end. The focused row shows "n of N".
- **D31, hold-to-confirm.** JamFin is taps-only, so it uses the non-hold path. "Mark as watched" on a series becomes "Press OK again to mark 24 episodes", with a slot draining over 4 s at the key's trailing end, opposite the leading focus window. Any other key cancels it. A film's Mark as watched toggles at once because it's reversible.
- **D35, the house menu.** The disc house menu has the same parts as the film page, plus a warn LED with the reason. In the player, M (Menu) opens the same settings strip for files and discs. Discs add a "Disc menu" key.
- **D36, the title-card hold:** see above.
- **D19 and D22, accents step back:** see above.
- **D43, the popup sheet.** The phone season picker is the shared bottom sheet: Close top right, the veil closes it, and there's no Done because a choice applies at once.
- **D27, offline.** The TV Home rows go **dashed together**. The sign says "Can't reach the Jellyfin server · Last seen 9:12 PM". One focused **Try again** is the orange primary, and it answers "Still not answering · tried 9:48 PM". The phone shows "Offline · showing your 2 downloads".
- **D26, no "More".** The phone tabs are Home, Movies, Shows, Search and Downloads.

## Research
I ran 10 web searches (WebSearch). WebFetch couldn't reach jellyfin.org or forums.plex.tv from this session, so the forum and blog findings below come from the search results' summaries, not from the full pages. Items marked *(knowledge)* come from my own knowledge, not from a search.

- **Apple TV, tvOS 26.**
  - tvOS 26 can show **"Who's watching?" every time the TV wakes**. It's a setting under Users and Accounts, with "Last Profile" as the alternative.
  - Each profile gets its own Up Next, Watchlist and recommendations. tvOS 26.2 added a **4-digit code** for a profile.
  - Continue Watching cards now carry **text and playback progress**, and recommendation rows moved to **vertical posters**.
  - Stuff.tv called the default-on picker an irritation, because you can no longer just switch on and resume.
  - *Lesson:* the picker opens with focus on the **last profile** (OK = one press). Wide cards are for things you're part-way through and posters are for the library, which matches our rows. A PIN for a kids' profile is a later option.
  - Sources: [Apple support](https://support.apple.com/en-euro/guide/tv/atvb457e13ae/tvos), [MacStories](https://www.macstories.net/news/tvos-26-the-macstories-overview/), [9to5Mac](https://9to5mac.com/2025/07/24/apple-tv-new-features-tvos-26-public-beta/), [Techloy](https://www.techloy.com/wwdc25-all-the-updates-coming-to-tvos-26/).
- **Netflix TV redesign (May 2025).**
  - The **left-side menu was replaced by a top bar** (Home, Shows, Movies, Games, My Netflix). Continue Watching moved into My Netflix.
  - Netflix reported the new UI on 85% of TV devices by Q3 2025.
  - *(knowledge)* The player has a row of text buttons (Episodes, Audio & Subtitles, Next Episode), Skip Intro bottom right, and a profile picker with big avatars in one row.
  - *Lesson:* a top menu band is the current mainstream pattern. Skip Intro bottom right is what people expect.
  - Sources: [Engadget](https://www.engadget.com/entertainment/streaming/netflix-overhauls-its-tv-app-with-a-fresh-ui-and-responsive-recommendations-121511958.html), [iPhone in Canada](https://www.iphoneincanada.ca/2025/05/07/netflix-overhauls-tv-interface-for-the-first-time-in-12-years/).
- **Plex "new experience" (2024–25).**
  - The redesign leaned towards discovery and made artwork more prominent on detail pages ([TechCrunch](https://techcrunch.com/2024/11/22/plex-redeisgns-its-app-to-look-more-like-a-streaming-service), [Plex blog](https://plex.tv/blog/the-new-plex-experience)).
  - Users complained that **libraries were harder to reach without the sidebar**, "especially for less tech-savvy family members". Plex **restored the left navigation panel** on Apple TV, Roku and Android TV ([Neowin](https://www.neowin.net/news/plex-reverts-tv-app-layout-after-intense-user-backlash/)).
  - Preview users also asked for "Remove from Continue Watching", and noted that there was no profile prompt at start, so children could see adult profiles.
  - *Lesson:* never hide the libraries. JamFin's band keeps Movies, Shows and Blu-ray as visible tabs, one press up from any row (D26 again). Remove from Continue watching is a pass-3 action.
- **Infuse 8 (Firecore).**
  - Subtitles and audio open by **holding the centre button** during playback ([Firecore support](https://support.firecore.com/hc/en-us/articles/215090907)).
  - Users reported two focus bugs. The episode row focused the wrong episode coming down from Play (8.0.4), and the season picker stayed stuck on Season 1 (8.5.5) ([Firecore community](https://community.firecore.com/t/episode-movie-selection-when-scrolling-down-changed-in-8-0-4/52340.md)).
  - *Lesson:* JamFin can't use a hold, which is why its strip keys stay one tap away. Entering the episode row should land on the **next-up episode**, not E1. The mockup does both.
- **Swiftfin (Jellyfin, tvOS).**
  - The tvOS series view defaults focus to the **seasons row** "as a workaround due to tvOS and the Focus Engine" ([PR #492](https://github.looper.workers.dev/jellyfin/Swiftfin/pull/492)).
  - In 2025 the episode selector still had open focus-handling work ([status #1294](https://github.com/jellyfin/Swiftfin/discussions/1294)).
  - *Lesson:* season-to-episode focus is hard everywhere. JamFin should state its rule: ↓ from the actions lands on the current season, and ↓ again lands on the next-up episode.
- **Jellyfin Android TV 0.19 (2025).**
  - Added a new video player UI, an **inactivity popup** ("still watching"), a redesigned toolbar, voice search, and a refresh of Home when the app stops ([newreleases.io changelog](https://newreleases.io/project/github/jellyfin/jellyfin-androidtv/release/v0.19.0), [AlternativeTo](https://alternativeto.net/news/2025/10/jellyfin-0-19-for-android-tv-brings-voice-search-inactivity-popup-and-enhanced-music-player)).
  - *Lesson:* "Still watching?" is now standard in the official client, so JamFin should have one with the same calm grammar as an error.
- **Findroid.** Full offline downloads with ExoPlayer for films and episodes ([GitHub](https://github.com/jarnedemeulemeester/findroid), [JellyWatch comparison](https://jellywatch.app/blog/findroid-vs-jellyfin-official-android-app-comparison-2026)). *Lesson:* offline on the phone should show what you *can* play (downloads), not just an error. That's the offline phone Home.
- **Kodi skins.**
  - Arctic Fuse 2's home is "only widgets" with no spotlight, and users call it the most customisable skin but heavy on weak boxes ([Reddit via mirror](https://cal1.lr.ggtyler.dev/r/Addons4Kodi/comments/1fxfg8c/arctic_fuse_2_has_been_released), [Kodi forum](https://forum.kodi.tv/showthread.php?tid=339791)).
  - Aeon Nox SiLVO added **scene and edit-list markers to the seekbar** ([releases](https://github.com/MikeSiLVO/skin.aeon.nox.silvo/releases)).
  - *Lesson:* one sign plus rows, not a wall of widgets; the box is weak. Marking the intro segment on the timeline is cheap and useful, so the mockup draws it as a thin mark above the track.
- **Takeaway:** the good clients agree on three things:
  - the profile picker opens on the last profile;
  - Continue watching uses wide cards with progress, and the library uses posters;
  - player prompts (skip, next, still watching) sit bottom right or in a centred panel and are one press.

  They fail at season-to-episode focus and at hiding libraries. JamFin's fixed zones already avoid the second, and pass 2 writes down a rule for the first.

## Design (what and why)
**Profiles** ("Who's watching?").
- A flat ground with the slim band. The tiles are avatar plus name (generated discs, no faces) with the base window, and focus opens on the last profile.
- The focused profile's **saved look** is one line under the row ("Braun Hi-Fi · Night · Full-colour covers · Full motion"), not on the tiles, so it's said once.
- Picking a profile applies its look at once. Ben is Day with Toned covers, and Cleo is Calm with Toned covers. That is the bible §1 JamFin exception made visible.
- The spiral iris (JamFin's signature) isn't redrawn. In Hi-Fi the profile pick is the plain screen change.

**Home.**
- The black ribbed band holds two lines. The first is the tab line: Home … Settings, then the profile chip and the clock. The chip is focusable after Settings, and OK on it returns to Profiles.
- The second line is the **sign**: title at 54 px plus one line.
- Stripes sit in the band's lower right. Rows sit on the flat ground (Isaac: plain background behind rows).
- The rows are Continue watching, Next up, Latest movies, Latest shows and Blu-ray.
- Wide cards are 352 × 198 art plus a 96 px plinth. Posters are 200 × 300. Next up cards carry no bar, since nothing is in progress.
- Back on a row goes to its first card, then to the menu.

**Pages** (film, series, disc).
- Title, facts with Ends at, and tech chips. The primary key's top edge is at y ≈ 360, so it sits in the upper-left quadrant (fixed zone).
- Keys are 64 px with a leading window.
- The lower row (More like this, Seasons and episodes, or Chapters) peeks at the bottom. Entering it switches the page to the **lower view**: the row sits under the slim band, with the focused item's sign below it. For episodes the sign is "S2 E4 · The Long Shift", the runtime, when it was first shown, Ends at, and a 3-line synopsis.
- The crumb says where Back goes ("Signal Street (top of page)").
- Season keys press in when chosen. The **episode row follows a season after a 280 ms dwell** (JamFin's own prefetch dwell), so a quick pass over seasons doesn't load each one.

**Disc house menu.**
- Shares the film page's parts: Play main feature (orange), Chapters 24, Extras 6, Audio, Subtitles, and Try the disc's own menu.
- The reason sits beside a lit amber LED: "This disc's own menu needs BD-J, and it didn't start this time. Jamfin built this menu from the disc."
- The chapter row plays from any chapter.

**Settings › Appearance.** Categories on the left (Appearance pressed in). The rows on the right are Look, Lighting, Covers, Motion, Animate Back and Interface sounds, headed "saved to Ada's profile". OK cycles a value, which applies at once and to this profile only.

**Title card.**
- The flat ribbed shutter, the title on the seam, the slatted bar showing the real load, and Stripes on the right. The player is composed behind the card before it opens.
- Timing:
  - The full form is the first Play of the session: 460 ms in, a 600 ms floor, 300 ms out.
  - After that comes the short form: 200 ms in, a 300 ms floor, 200 ms out.
  - Calm is a 140 ms fade.

**Player.**
- The band is 196 px with a walnut top rule. The first line has the slot light, Playing, the title, "Chapter 6 of 12 · The Archive", key hints and Ends at.
- Under it is the recessed timeline, with chapter notches, an intro-segment mark and the cap. The playhead time rides the cap, and the total sits at the right.
- ↑ opens chapter cards above the band (the band's chapter text hides while they're open).
- ↓ or M lifts the band 74 px onto the strip: Subtitles Off, Audio English 5.1, Speed 1×, Picture Fit, Info, Play from the start (plus Disc menu for discs), and Exit.
- Lists rise above their key, and the key's value hides while its list is open.
- Back closes one layer at a time, then hides the band, then leaves.
- Prompts:
  - **Skip intro** shows during the intro segment. It's an orange key with "OK" printed on it, and OK skips. With the band hidden it drops to the bottom-right safe corner.
  - **Next episode** shows in the last 40 s: a card with art and "Starts in 7 s" plus an orange "Play next episode". Back stays for the credits, and the band hint says so.
  - **Still watching?** and **errors** use a centred panel. The picture is dimmed (a colour filter on the TV), and Keep watching or Try again is focused and orange.
  - **Loading** after a seek or chapter jump shows an amber slot plus "Loading" and a slatted mini bar in the band.
- No other orange appears in the player.

**Phone.**
- **Home:** the Continue carousel with the moving orange Resume, then Next up and Latest movies. Offline swaps in a dashed banner and the downloaded items.
- **Show page:**
  - Hero art, title and facts, then Resume S2 E4 (orange, full width) and Watched / Favourite (square windows) / Download season.
  - Then the overview, a "Season 2 ▾" button that opens the shared bottom sheet (Season 1 Watched, Season 2 "4 of 8 watched", Season 3 Not started), and episode rows.
  - Each episode row has a thumb with the bar on its bottom edge, "4 · The Long Shift", the runtime or "Watched · 45 min" or "Downloaded", and a download button.
- **Player** (landscape): the top bar holds Back, the title, and Chapters and Settings.
  - Centre: −10 / pause / +10.
  - The ribbed band has the same first line and timeline as the TV.
  - Chapters pop above the band.
  - Settings lifts the band onto the strip (Subtitles, Audio, Speed, Quality, Close). A list rises above the band, not over the timeline, and the top bar hides while it's open.
  - Skip intro is the one orange.

## Audit
Checked with Playwright (Chromium, `chromium.launch()`):
- Page width 1500 at deviceScaleFactor 1.31, so the TV renders at about 1920 px; then 390 × 844 in the dark scheme; then 1500 in the light scheme for the phone frames.
- A keyboard run through: profiles; Home across every row (to the end card) and the menu and chip; film page; the Audio and Subtitles drops; the More lower view; series episodes with a season change; the two-press confirm; the disc house menu and its chapters; Settings; the player band, chapters, strip and list, and band hidden; all five player states; the title card at 4 s, then 0.4 s, then 0.4 s under the pass-1 hold; Day Home, Day film page and Day profiles; offline Home; Toned covers.
- Phones: season sheet, player Settings with the Audio list, and chapters.

Final results:
- No JS errors.
- **No TV text under 22 px**, in any state.
- No horizontal scroll at 390.
- All TV text inside the safe area (96 / 54 px), except peeking cards and the next row's name on Home (y 1006–1036).
- Title-card timings report correctly. 4 s load: 4000 ms, no added wait, full form. 0.4 s: 400 ms, short form. Pass-1 rule: 1600 ms, added wait 1200 ms.

The fix pass corrected:
- the build left **negative px unconverted** (lifts, the lower view and band offsets were in raw px, so the episodes view sat 228 px too high);
- slim-band and tab text above the 54 px line (the band is now 108 px with bottom-aligned text, and the tab line has moved down 8 px);
- the player's time row at y 1048 (the band is tightened to end at 1016, and strip keys at 1014);
- the lifted card covering the row name (row names now sit at the top of a 50 px header);
- the phone Audio list covering the timeline (it now rises above the band, and the top bar hides);
- the unlit phone "Playing" light;
- the next-episode line wrapping;
- "this film" on an episode error;
- an unlit warn LED on the disc page.

| # | Problem | Severity |
|---|---|---|
| 1 | **OK changes meaning while a prompt shows.** During the intro or the last 40 s, OK on the timeline skips or plays next instead of pausing. That breaks JamFin's invariant "a look never changes what a key does" in spirit. Today JamFin's skip pill is "optional tap" and its focus path isn't documented. Needs a decision: a focusable prompt (→ from the timeline's end) or a dedicated OK window. | High |
| 2 | **Season follows focus (280 ms dwell)** is new behaviour. Today a season key needs OK. Rebuilding an 8-card row of new art on a dwell costs a burst of decodes on the Mali. It needs JamFin's late-frame measurement before it's adopted, and Isaac may prefer OK. | Medium |
| 3 | **The short title card on later plays.** On a Day profile, light page → dark card → picture in about 0.7 s may count as two big luminance changes inside a second (flash rule 1). It's fine at Night. Needs Lobby's measurement method. | Medium |
| 4 | **Unlit base windows read as a row of dark dashes**, especially in Day under light plinths (the same as HA tabs, HA #10). The window rule says always visible. Isaac hasn't seen it at 3 m. | Medium |
| 5 | **The accent still shows with full-colour covers.** It's in the band now, separated by the band edge, but on Home it's still a second colour source. D19 is half answered. | Medium |
| 6 | **The lower views have about 250 px of empty ground** under the sign (film More, disc Chapters, short synopses). Calm, but Isaac called early mockups "a lot of wasted space". | Medium |
| 7 | **Offline Home shows nothing playable.** The TV has no downloads, but JamFin could show the last-synced rows greyed with "Needs the server". Dashed ghosts follow D27 but give the household nothing to do except Try again. | Medium |
| 8 | **Phone: Discover and Settings have no visible route.** Dropping "More" (D26) means they need a labelled place (the profile chip sheet). Not drawn. | Medium |
| 9 | **Long seasons.** 8 episodes fit; a 22-episode season in a stop-at-end row is 21 presses to the end. No jump (E1 / E10 / E20) is designed. | Medium |
| 10 | **The sign repeats the focused card's title.** It's a name, not a value, so "never twice" isn't strictly broken, but the title shows twice in one view. Same in Unigrid. | Low |
| 11 | **The next row's name peeks across the bottom safe line** (y 1006–1036). It's content, not chrome, but on an overscanning TV it may be cut. | Low |
| 12 | **The drop chooser covers Mark as watched and Add to favourites**, and Subtitles' five options reach y ≈ 1010, over the More row's art. It's legible and opaque, but tall lists will need a scroll rule. | Low |
| 13 | **Toned covers are still a CSS filter** here. On the TV it's a `ColorFilter`, and its cost on a 40-card row is unmeasured (carried from pass 1). | Low |
| 14 | **The disc house menu** draws only the reason, chapters and keys. Extras, and the disc player's strip over the disc's *own* menu, are still missing (the JamFin README's top missing screenshot). | Low |
| 15 | **The phone list has no title** ("Audio") because the pressed key names it. Touch users may want the heading. | Low |
| 16 | **The profile picker always shows.** tvOS 26 users dislike an always-on picker. JamFin may want "Ask every time / Last profile" in Settings › Profile. | Low |
| 17 | **Slow-load wording:** after 10 s the card offers Back, not JamFin's "sentence + Retry". A Retry on a title card is an extra key to design. | Low |

## Change suggestions for pass 3
- **Prompt focus (audit 1).**
  - Version A: Skip intro and Next episode are focusable keys at the end of the band's focus row. → from the timeline's last position reaches them, and OK keeps meaning pause.
  - Version B: OK skips only while the prompt shows, and the prompt prints "OK" (this pass).
  - Show both and ask Isaac.
- **Season dwell (audit 2):** add a page switch, "Season follows focus / Season needs OK", and note the decode cost. Ask JamFin to measure on the Hisense.
- **Long seasons (audit 9):** an episode row with "1–10 · 11–20 · 21–22" range keys under the season keys, or let ↓ from the season key land on that season's next-up episode (already the rule), plus a "Last episode" end card.
- **Fill the lower view (audit 6):** under the episode sign, show cast for that episode, or a second row (the next season's first episodes). For films, the sign plus a "Cast" row.
- **Offline TV (audit 7):** show the last-synced Continue watching row greyed, with "Needs the server · last seen 9:12 PM", and keep Try again as the primary.
- **Remove from Continue watching** (Plex users asked for it): a strip key on the film page's lower list, or a two-press "Remove" in the card's page.
- **Day windows (audit 4):** try unlit windows at 40% opacity in Day only, or a hairline window outline. Compare at 3 m.
- **Phone:** the profile chip opens a sheet with Switch profile, Discover, Settings and Downloads quality. Add the offline player (downloaded episode) and the download quality sheet in the Braun parts.
- **Disc player:** the strip over the disc's own menu ("Back twice leaves the disc menu"), and Extras.
- **Search and the library grid** (A–Z jump strip, Organise header) in the same parts, so every TV destination is drawn.
- **Kids' profile with a 4-digit code** (tvOS 26.2 did it), as an Add profile option.

## Bible implications
1. **Title-card hold, final form (refines D14 / D36).** Play holds only as long as the load. The full shutter is used once per session, with a 600 ms floor. Later plays use a ≤ 300 ms short form, and Calm uses a ≤ 150 ms fade. The 1.6 s minimum in §2 "TV title card" applies only to app launch and milestones. After 10 s the card says why it's waiting and Back stops it.
2. **"An open layer carries the value" (answers D33).** While a chooser, list or shelf is open, the key or band text that names the same value hides. The open layer's lit square is the one place it's said.
3. **Above, below, or drop below. No "beside" (closes D16).** On a fixed band, browse layers pop above and settings lift the band. In a vertical list of keys, a chooser drops below its key and covers the keys under it, never the key itself or the page title.
4. **Selector and progress numbers (D13 made concrete).** The base window is 12 px at 1080p in full cream, half the card's width, on the plinth's bottom edge. Progress is a 9 px track on the art's bottom edge, filled with **70% cream**. The lift is 14 px, drawn inside the layer. The baked spill fades by opacity.
5. **Focus on the orange key (closes D18).** It rises 6 px, the under-edge goes from 3 to 9 px, the label goes black, and the leading window lights cream on a brown recess. The rule is shared with NervOS.
6. **TV homes put the sign in the menu band.** The sign is title + one line, and the accent goes in the band's own clear zone (below the nav line, right of the sign). An accent never touches a row of art (D2 / D19).
7. **Rows stop at their ends (answers D32 for content rows).** No wrap. Library rows end with an end card that opens the whole library. Position is shown as "n of N" on the focused row. (Group carousels may still wrap, per NervOS.)
8. **Two-press confirm for taps-only remotes (D31).** The key's label becomes "Press OK again to …", and a slot drains over 4 s at the end opposite its focus window. Any other key cancels it. Use it only for actions that are hard to undo (a whole series watched). Reversible ones act at once.
9. **Player prompts.** Skip intro and Next episode sit bottom right, above the band, and are the player's only orange. Still watching? and playback errors use a centred panel on a picture dimmed by a colour filter, with the recovery key focused and orange.
10. **What a JamFin profile saves (extends D20).** Look, Lighting (Night / Day / Auto), Covers (Full colour / Toned), Motion (Full / Calm), Animate Back and Interface sounds. The picker shows the saved look in one line under the row and opens on the last profile. Ask Isaac whether a profile's **Day** may override "shared screens show the house look" on the living-room TV. The §1 exception says "look", not lighting.
11. **Focus-driven content needs a dwell.** When moving focus changes other content (the season → episodes row), it waits for a 280 ms dwell, so held or quick presses don't load every step.
12. **TV safe area includes band chrome.** Slim bands are 108 px with bottom-aligned text, so the clock and crumbs sit below the 54 px line. A peeking next row may cross the bottom line, but it isn't counted as readable content.
13. **Offline on the TV (applies D27).** The rows go dashed together, the sign says what and when ("Last seen 9:12 PM"), and one focused Try again is the screen's primary. The accent steps back until the server answers.
14. **Phone tab bars in JamFin (applies D26).** Home, Movies, Shows, Search, Downloads. Discover and Settings move behind the labelled profile chip, never "More".
