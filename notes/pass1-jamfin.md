# JamFin · Pass 1

Mockup: `mockups/pass1/jamfin.html`. It's interactive: click the TV, then use the arrow keys, Enter (OK) and Esc or Backspace (Back), or the remote buttons. The page has these controls:
- **Lighting:** Night / Day. This sets the TV Day palette and the phone light mode.
- **Covers:** Full colour / Toned.
- **Progress vs selector:** Proposed split / the pass-1 same-edge version, for comparison.
- **Motion:** Full / Calm.

A status line counts presses since Home. The default path, Home → OK → OK, reaches Play in 2 presses.

All titles, people and art are made up. The film and series names reuse JamFin's own demo names (The Copper City, Signal Street, The Velvet Machine, The Harbour Hour). The covers are generated flat shapes, not real posters.

Sources read:
- `projects/jamfin/README.md`, `PROPOSALS.md` and these screenshots: Unigrid home, film, series, player chapters and settings strip; Cut Paper phone home.
- `BIBLE.md` 0.5, `CHANGES.md` A–D, and the end of `decisions.md`.
- Mockup 13, `_hifi-base.css` and the Jam Braun screens (phone music, kiosk TV sheet).
- `notes/pass1-tv-launcher.md` and `notes/pass1-callsheet.md`.

## Research
I ran three web searches. The results were mostly support pages and user forums. Items marked *(knowledge)* come from my own knowledge, not from a search.

- **Apple TV (tvOS) system player** (web): today, a swipe down opens Info / Chapters (and Up Next) tabs above the controls. Subtitles and audio moved out of that panel into buttons in the playback controls when tvOS 15 redesigned the player. *Lesson:* chapters behave like a shelf that opens over the picture. Track pickers are separate, small and next to the controls. That's the same split as Unigrid's "chapters above, settings below". ([Apple support](https://support.apple.com/guide/tv/atvb7944597f/tvos), [9to5Mac on tvOS 15](https://9to5mac.com/2021/07/02/tvos-15-introduces-redesigned-video-player-for-apple-tv-app/))
- **Infuse on Apple TV** (web, user forums): users complain most about chapter navigation. Chapters show as a timestamp list with no pictures, and users point to Plex's chapter thumbnails as the better version. Changing subtitles was called a multi-step process. *Lesson:* chapter cards with pictures are worth the cost, and Subtitles should be one press from the band. ([Firecore: chapter images](https://community.firecore.com/t/chapter-images-on-video-playback/21755), [Firecore: playback UI](https://community.firecore.com/t/update-apple-tv-playback-ui/32856?page=2), [Firecore subtitles help](https://support.firecore.com/hc/en-us/articles/215090907))
- **Jellyfin Android TV and third-party clients** (web): users complain that Continue watching mixes posters and thumbnails, and ask for one shape per row. Moonfin's client added a setting that merges Continue watching and Next up into one row. *Lesson:* keep one artwork shape per row (wide for things you're in the middle of, posters for the library). Keep Next up as its own row for now, and note the merge as an option. ([Jellyfin forum](https://forum.jellyfin.org/t-androidtv-control-over-home-page-icons), [Moonfin 1.2.0](https://newreleases.io/project/github/Moonfin-Client/AndroidTV-FireTV/release/1.2.0))
- **Netflix and Google TV players** *(knowledge)*: one timeline at the bottom, title top-left or above the timeline, and a row of text buttons (Episodes, Audio & Subtitles, Speed) under the timeline. Google TV's "Continue watching" uses 16:9 frames with the bar on the frame's bottom edge and the label below. That's the layout that keeps progress and focus apart.
- **Braun hi-fi (Rams' audio 1, T 1000)** *(knowledge)*: a calm face with one scale window and keys in a row under it. A good model for the band: a tuning-scale-like timeline in a recessed window, with the playhead as a fader cap.

## Design (what and why)
**Journey first.** The flow strip at the top of the mockup shows the resume path. It keeps JamFin's invariants:
- Home opens on the first Continue watching card.
- OK opens the film page with focus on Resume.
- OK plays (2 presses; the budget is 3 after the profile).
- Back always restores the focus that opened the screen.
- Taps only. Nothing needs a long or double press.

**Home (1920 × 1080, 1080p px on a scaled stage):**
- A fixed black ribbed **menu band**: Home, Movies, Shows, Blu-ray, Discover, Search, Settings, plus the clock and the profile chip. The walnut trim sits on top. Each tab has a base window cut into the band's bottom edge, so the menu and the cards share one selector.
- Below the band, on a flat ground, is the **sign** for the focused title: an eyebrow (row and type), the title at 68 px, facts (year, runtime, rating, **Ends at**) and one line. It changes with a 50 ms out / 100 ms in opacity step, in its own layer.
- **Session blocks** fill the accent clear zone, right of the sign and between the band and the rows.
- Rows: Continue watching (wide), Next up (wide), Latest movies (posters) and Latest shows (posters). They scroll vertically so the focused row sits under the sign and the next row peeks. The focused row's header shows its position ("2 of 6"); other rows show a count.

**Progress vs selector (the TV pass-1 lesson, D1).**
- Every card is **art + plinth**. Resume progress is a full-width recessed track on the **art's bottom edge**, which keeps JamFin's fixed zone ("always a bar on the card's bottom edge").
- The **selector window** is cut into the **plinth's** bottom edge, half the card's width.
- Between the two sit the title and one line (about 70 px). One is full width and one is centred and half width, so they don't read as two progress bars.
- The face lifts 10 px inside the card's own layer, so the focus rectangle never moves. The label snaps to cream, and a drawn shadow fades in by opacity.
- The comparison switch draws the pass-1 version, with both bars at the plinth's bottom edge, so Isaac can see the difference.

**Said once.**
- The card's bar is the only "how far".
- The sign says **when it would end**, which is a different value, not "42 min left".
- In the player, the playhead carries its own time readout, like a fader cap carries its value. So "1:12:04" appears once, and the band's right side gives the total and **Ends at**.

**Film page:**
- A slim fixed band shows **Back · Home** (where Back goes) and the clock.
- Title and facts sit upper-left, with tech chips (4K · HDR10 · 5.1) in mono.
- Then the action column with plain JamFin wording: **Resume from 1:12:04** (the one orange key on the screen), Play from the start, Audio: English 5.1, Subtitles: Off, Mark as watched, Add to favourites. The last two have square windows that light when on. The primary key's top edge is at y ≈ 372, inside the upper-left quadrant.
- On the right: the backdrop (the same art as the card), the overview clamped to 3 lines, then Director and Cast.
- "More like this" peeks at the bottom.
- Vertical lists use a **leading-edge window** (the same cream window, turned 90°) plus an 8 px drawn shift, so tiles and lists share one focus grammar (D3).
- **Audio / Subtitles** open a chooser **beside** the action. Its rows use the same leading window for focus, and a square window marks the current choice.

**Series page:** same structure. Resume S2 E4 from 31:20 (orange), Mark as watched, Add to favourites. Below them, season keys (the chosen one presses in), then the episode row with the same card. Watched episodes show a full bar and the word "Watched".

**Title card (Play):**
- The flat ribbed shutter halves slide in (460 ms, decelerate).
- The title sits on the seam in Jost capitals: no paper, no grain.
- The eyebrow says what's happening ("Resume · from 1:12:04"), and the **slatted bar shows the stream load**.
- The player is composed behind the opaque card before the halves leave (300 ms, leave curve).
- Stripes run down the right side, clear of the centred title, and line up across the seam.
- Calm: a 140 ms fade, no travel.

**Player band:**
- One fixed ribbed band at the bottom. The first line has a slot light + "Playing / Paused", the title, and "Chapter 6 of 12 · The Archive". On the right are key hints (they change with the zone: ↑ Chapters ↓ Settings / OK Jump ↓ Close…) and Ends at.
- The timeline is a recessed window that fills with cream. Chapter stops are notches, echoing the slatted bar. The playhead is an aluminium cap with its time under it.
- ←/→ seek 10 s, and OK toggles pause.
- **↑ pops the chapter cards above** the band: an opaque band-coloured shelf with the same card and selector, and pictures per chapter.
- **↓ lifts the band** onto the **settings strip below**: Subtitles, Audio, Speed, Picture, Info, Play from the start, Exit. These are keys with base windows.
- A list from a strip key **rises above the band**, anchored over its key, and never covers the timeline.
- A toast confirms changes top-left.
- Back closes one layer at a time: list → strip → band hidden → film page (the new position shows on Resume and on the Home card).
- No orange in the player.

**Phone (390 × 844):** Home in the same parts.
- Header: "Home", Search and the profile chip.
- Continue watching is a snap carousel of big wide cards with "1 of 4". Each card shows art with progress on its edge, an eyebrow, the title and Ends at, then **Resume from …** and Details. **Only the card you've stopped on has the orange button**, and it moves with you (the Callsheet "moving primary").
- Then Next up (wide) and Latest movies (posters).
- The five-tab bar uses a base window at the top edge of each tab (D12).
- Light and dark follow the page control.

**Per-profile look:** JamFin is the bible's exception (looks are saved per Jellyfin profile). Ada's chip is in the band, and the **Covers** switch (Full colour / Toned) is designed as a per-profile setting. Toned pulls saturation and brightness down. That answers "full-colour covers as an option" without making full colour the house default at night.

## Audit
Checked with Playwright (Chromium):
- Page widths 1500 (deviceScaleFactor 1.31, so the TV renders at about 1920 px) and 390 (dark scheme).
- A keyboard run: Home → right/down through all rows → menu → film page → Audio chooser → More like this → Back → series page → episodes → Back → Resume → title card → player → chapters → strip → Subtitles list → Audio list → Back ×4 → Home.
- Day, the same-edge comparison and Toned covers.

Results: no JS errors, no horizontal scroll at 390, and no TV text under 22 px.

The fix pass corrected:
- the page's `data-v` buttons colliding with the strip's value hook (a crash);
- the 20 px avatar letter;
- chapter notches hidden under the lit part of the timeline;
- the series page scrolling the episode row too high;
- the backdrop not matching the card art;
- a lit window vanishing on the Day plinth (it now keeps a 2 px dark rim);
- a bare "12" in the facts (now "Rated 12");
- static player hints.

| # | Problem | Severity |
|---|---|---|
| 1 | **The title card's minimum hold vs "Play never waits for a signature".** The bible says the shutter holds about 1.6 s. JamFin's rule is that Play never waits. In the mockup the stream is "ready" at about 1.1 s and the card still holds to 1.6 s, which adds about 0.5 s to every Resume. Hitches and waiting are what Isaac dislikes most in JamFin. | High |
| 2 | **"Said once" isn't consistent yet.** Home and the player say each value once, but the series page's episode card shows a bar *and* "15 min left". Unigrid shows "1 h 1 min left" on the sign *and* the card. Isaac may miss the minutes on Home, where only "Ends at" is left. | High |
| 3 | **The split selector is still cream on cream.** The split works close up. But a row of six resumable cards has twelve cream marks, and at 3 m the half-width window under the plinth is 9 px tall. It may be too quiet as the only lit focus cue, because the lift is only 10 px. Needs a check on the real TV from the sofa. | Medium |
| 4 | **Home fits about 1.8 rows.** The sign and accent take about 280 px. That's calmer than Unigrid (2.2 rows, with the sign inside the band), but Isaac called early mockups "a lot of wasted space". The accent zone is the obvious place to give back. | Medium |
| 5 | **The accent vs full-colour covers.** With Full colour covers, Session blocks (blue, yellow, **red square**) sit above a wall of coloured art. That's two sources of colour on one screen, and a red decoration where red means alerts. With Toned covers it reads better. | Medium |
| 6 | **Focus on the orange primary is weak.** Resume is orange whether it's focused or not. The only focus cues are the cream leading window and the 8 px shift. From the sofa, "Resume is focused" and "Resume is just orange" look almost the same. | Medium |
| 7 | **TV Day.** The ground is mid-light `#bdb9b1` and the band stays black. It works, but the lit window on a light plinth needs the dark rim to read, and the focused plinth step (`#cfcbc3` → `#dcd8d0`) is faint. Day focus needs its own tuning. | Medium |
| 8 | **The chooser on the film page pops *beside* the action, not above or below.** It overlaps the backdrop and overview. That's fine for a vertical list, but it extends Isaac's "pop above or below the timeline, use that everywhere" to a third direction. | Medium |
| 9 | **Player states not designed:** skip intro, Next episode, Still watching?, loading/buffering after a seek, errors, and the disc player with the strip over a disc menu (the house menu is still missing from JamFin's own screenshots). | Medium |
| 10 | **The lifted band plus the strip covers about 31% of the picture** (band 196 + strip 142 px). Unigrid's strip is shorter because its keys are smaller. Keys could drop to 64 px. | Low |
| 11 | **Toned covers are a CSS filter here.** On the TV this must be a `ColorFilter` on the picture (JamFin allows dims as colour filters), never a blended rect. The cost on a row of 40 cards is unmeasured. | Low |
| 12 | On the series page, scrolling down leaves a sliver of "Add to favourites" under the fixed band. It's a half-hidden focus target. | Low |
| 13 | **Moving phone primary:** the orange Resume jumps between cards on scroll. That's correct by the moving-primary rule, but it may feel like flicker on a fast swipe. It only updates after the scroll settles. | Low |
| 14 | Profile picker (Spiral), menu destinations, Search, Settings > Appearance (where the per-profile look and Covers live) and Discover aren't drawn. Menu items other than Home just say so. | Low |
| 15 | The TV is authored in 1080p px on a 1920 × 1080 stage scaled to fit (like mockup 13's scalers), not in cqw. The sizes are the same, but it differs from the launcher mockup's method. | Low |

## Change suggestions for the next pass
- **Title card:** try "hold only as long as the load, with a 600 ms floor so the shutter can finish". Show both timings side by side. Also try a version that plays only on the first Play of the session (JamFin's "full once per session"), with later plays getting the 300 ms short form.
- **Time words:** pick one rule and use it everywhere. Option A: the bar only on cards, and minutes left in the sign. Option B: the bar only, and "Ends at" in the sign (this pass). Fix the episode card either way.
- **Selector strength:** try a taller window (12 px), a 14 px lift, and the plinth brightening a step more. Test a held-right run with a 6-card resumable row for "twelve cream marks" noise. Try the window in full cream with the progress fill at 70% cream.
- **Orange focus:** give the focused primary a lift plus a darker under-edge (pressed-up), or switch its label to the band's black-on-cream. Check at 3 m.
- **Space:** move the sign *into* the menu band, as Unigrid does (a taller band on Home only, collapsing to the slim band elsewhere), and drop the accent on Home when Full colour covers are on. Aim for 2.3 rows.
- **Accent:** try Stripes or Colour bars in the band's clear zone, and test Session blocks without the red square.
- **Player:** design skip intro (bottom right, above the band, the one orange in the player), Next episode, Still watching?, buffering in the slatted style, and the disc strip over a disc menu. Shorten the strip keys to 64 px.
- **Phone:** add the film page and the landscape player with chapters above and the settings sheet below the band. Try a merged Continue + Next up row as a per-profile option.
- **Settings > Appearance** for a profile: the look, Day/Night/Auto, Covers, and Calm. This is where the JamFin exception lives.

## Bible implications
1. **D1 resolved as "art + plinth".** A focusable card is art plus a plinth. Progress belongs to the art (its bottom edge) and the selector window to the plinth (its bottom edge), with the label between them. They never share an edge. The launcher's cover tiles would change to match.
2. **The title card hold vs Play.** §2 "Minimum hold about 1.6 s" conflicts with JamFin's "Play never waits for a signature". Proposal: on Play, the shutter holds only as long as the load, with a floor long enough to finish the move (about 600 ms). The 1.6 s hold applies only to app launch and milestones.
3. **"Never the same value twice", made precise.** A meter's own readout riding its handle (the playhead time) counts as one value. A bar plus "N min left" on the same card counts as two. "Ends at" is a different value and is allowed.
4. **Pop above or below**, from Isaac's words ("the way the unigrid playback menus pop above or below the timeline we should use that everywhere"). Add it to §7 or a new TV §: on a fixed band, browse layers (chapters, episodes) pop above, settings pop below with the band lifting, and lists from a setting rise above the band and never cover the timeline. Choosers from a vertical list pop beside it. Ask Isaac whether "beside" is OK.
5. **One focus grammar, concretely (D3).** Horizontal tiles light a base window, vertical lists light a leading-edge window of the same size and colour, and both add a drawn lift or shift (never a moved hit box). **In Day palettes, a lit window keeps a dark rim** so it still reads as a window on a light surface.
6. **A focused primary needs its own cue.** "Orange = the one primary" plus "focus = cream window" isn't enough on the TV when the primary is focused. §7 needs a rule for focus on an orange key.
7. **Accents on screens full of art.** §2 Accents should say whether an accent is shown when full-colour artwork fills the screen. Proposal: the accent steps back (hidden or Toned) when Full colour covers are on. Also decide whether Session blocks' red square is allowed on TV home screens, given "red = alerts".
8. **Covers as a per-profile look setting.** The §1 JamFin exception should name what a profile saves: look, Day/Night/Auto, **Covers (Full colour / Toned)** and Calm. "Toned" art is a colour filter on the picture, which keeps the night glare cap without blended overlays.
