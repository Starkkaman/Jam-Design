# JamFin · Pass 4 (the cinema)

Mockup: `mockups/pass4/jamfin.html`. Passes 1–3 are unchanged.

How to use it:
- Press **Tour** to step through 17 states automatically, about 3 seconds each. Any real key on the TV stops it. **Next step ›** advances one state at a time.
- Or click the TV and use the arrow keys, Enter (OK), Esc or Backspace (Back), M (≡ JamFin menu) and G (Guide), or the remote buttons on the page.
- Page switches: Lighting (Night / Day, normally set by the profile), Motion (Full / Calm), Stream ready after (0.4 / 1.2 / 3 s, which drives the title-card hold) and the page theme.
- Jump buttons cover every state: Tickets, Ticket torn, Home, Marquee · 3rd card, Posters row, Row end, Programme · film, Film · lower view, Programme · show, Season 2 resting, Long season · E21, House lights (Play), Player · Skip intro, Player · Next episode, Player · chapters, Intermission, Still watching, Day Home (Ben), Day programme and Offline Home.
- The status line shows the screen, presses since Home, and what the house lights did (how many big luminance changes, and how far apart).

The TV is 1920 × 1080 written in cqw. The phones are 390 × 844. All titles, people and art are made up. The art is flat generated shapes, and people are a neutral figure in a coloured frame, with no faces or initials.

Sources read: `notes/OVERNIGHT-BRIEF.md` (including the Direction update), the last entries in `decisions.md`, `notes/REVIEW.md`, `CHANGES.md` (A, B and D1–D179), `BIBLE.md` §2–9, `projects/jamfin/README.md` and `PROPOSALS.md`, and `notes/pass3-jamfin.md`. I also looked at the pass-3 TV launcher, NervOS and JamFin mockups to make sure this one doesn't look like them.

## What changed and why (vs pass 3)

Isaac, after passes 1–3: *"Everything should feel like it has the same design language, not necessarily the same design. … I don't really want to see identical cards and backgrounds across designs unless there's a clear reason."* Passes 1–3 had all three TV apps converging on one template: a black ribbed band at the top, a sign in the band, rows of art-plus-plinth tiles under it, and the shutter title card. JamFin pass 3 and the launcher pass 3 were hard to tell apart in a screenshot. Pass 4 keeps the behaviour and replaces the template.

| Area | Pass 3 | Pass 4 | Why |
|---|---|---|---|
| Home header | Black ribbed menu band holding the tabs, the sign and the Stripes accent | **Marquee**: a separate board under a slim tab line. The focused title is set in caps on a colour block cut from the title's own colour, the facts go underneath, and a row of round "seat" windows on the right shows where you are in the row. The Session blocks accent sits at the marquee's right end. | The sign is JamFin's main job (what is this, how long, when does it end), so it gets the most considered object on the screen, not a strip of a shared band. |
| Cards | Art + plinth (a slab under the art), window on the plinth | **Art + caption on the plain ground.** The focus window sits on the ground just under the art, half its width, with the baked warm spill under it. Continue watching uses wide stills; Latest films and shows use posters. | The art is the star. A plinth under every cover is the launcher's tile; JamFin's covers stand on their own like one-sheets in a lobby. |
| Row position | "1 of 6" text on the focused row | **Seat windows** on the marquee, one per item, the focused one lit. Text ("14 of 40") only after 12 items. | Shows the position without another line of text over the art. See Rules I broke #4. |
| Profile picker | Rounded tiles | **Tickets.** Each profile is a ticket whose stub states that profile's saved look (Night / Full colour / Full motion). OK tears off the stub (300 ms, transform + opacity), then Home opens in that profile's lighting. | Per-profile looks (D179) are JamFin's one exception to the house look, so the picker says what each profile will look like before you pick. |
| Film and show pages | Actions on the left, art on the right | **Programme**: a folded programme with a walnut fold line. The left page holds the title block, facts and keys (the fixed zone: title and primary in the upper-left quadrant). The right page holds the art, synopsis and credits with dotted leaders. | Gives the page a reading order people already know from a printed programme. Credits are set like a programme, not a data table. |
| Episodes | Horizontal episode row under season keys + range keys | **Running order**: a vertical list (number, title, runtime, watched window, progress), 7 rows visible. Season keys and range keys sit above it in one row with a walnut divider. The right page shows the focused episode's still and synopsis after a 500 ms rest. | Episodes are read as a list (numbers and names), not browsed as covers, and a vertical list fits 7 at a time instead of 4. The still still gets the big panel. |
| Play | Shutter title card (600 / 300 ms), light in Day | **House lights.** The page dims in two steps (to 42% in 180 ms, then out in 220 ms), then a colour-block title card cuts in from the left with the title in caps, the episode name and the **slatted bar** showing the real load. The picture follows after max(load, floor). Stop brings the lights back up (a 240 ms fade to the programme). | Pressing Play in a cinema is the lights going down. It's the one moment JamFin can be theatrical, and Isaac allows delight at Play. |
| Long pause | The band stays up | **Intermission card** after 60 s paused: a colour-block card over the colour-filtered picture with "Paused at 1:12:29", "Resume now and it ends at 11:06 PM", Resume (orange, focused) and Stop for tonight. The same card answers **Still watching?** after 3 episodes in a row. | Says when the film will end if you go back now, which is the decision people are actually making in a pause. |
| Offline | Dimmed row in a dashed outline + Try again + TV Home | Same behaviour, but **the marquee carries the state**: "SERVER · OFFLINE" with the broken-ring window, "NOT ANSWERING" as the title, the retry countdown in words, and every seat window dark (the lights are out). | Offline is told in the same place as everything else on Home. |
| Day | Light Day title card (D172), groove windows | Groove windows kept (D173), now applied to every indicator on light surfaces. The marquee becomes a **lightbox** (a light board with dark letters, like a daytime letter board). Play in Day **dims to dark** (reverses D172). | A cinema is dark when the film starts. The two big changes are counted and kept within the floor (see Audit #3). |

**Kept from pass 3 unchanged (functional decisions):**
- OK presses what is lit (D168), including Skip intro taking focus for 8 s with the draining slot and "↓ keeps OK on the timeline".
- Next episode never takes focus; pausing holds its countdown, and ↑ then OK starts it now.
- The 500 ms rest for visible content (D169): season → running order, and episode → right page. ↓ or OK commits at once.
- Range keys over 12 episodes (D170).
- max(load, floor) with the 600 ms floor for the first Play and 300 ms after (D171). Only the shutter visual is replaced.
- Row ends: the walnut end mark, a nudge on an extra press (not in Calm), and "All …" end cards (D110).
- Guide belongs to the launcher; JamFin's menu is ≡ (D54).
- The sign never repeats a value from the caption (D176). The marquee says "2 h 31 min · Rated 12 · 4K · Ends at 11:06 PM", and the caption says "1984".
- The offline screen offers Try again, TV Home and a retry every 30 s, and the last-synced row isn't focusable.
- Phone: five tabs, no More, and the profile sheet (D116). The page behind the sheet loses its orange (D97).
- Player prompts sit bottom right, chapters pop above the band, and Options drop below (the band lifts).

## Purpose

Choosing something to watch together, then getting out of the way. Three people on a sofa, at night, with one remote.
- **Choosing** happens on Home and the programme page. The marquee answers "what is it, how long, when would it end" for whatever is focused, in type big enough to read from the far end of the sofa. The covers carry the rest.
- **Getting out of the way** is the house lights. Every Play ends in black and then the picture, with no UI left on screen. The band only comes back when you ask for it.
- **The art is the star.** No plinths or frames on covers. The marquee is the only large non-art object on Home, and it sits above the rows, never behind them (Isaac: a plain ground behind rows).

## Research

I used WebSearch (3 searches) and fetched no pages, so the findings come from the search summaries. Items marked *(knowledge)* come from my own knowledge, not from a search.

- **Changeable-letter marquees.** Interchangeable outdoor letters date to the early 1920s. 1930s theatre boards were black enamelled cast aluminium with slotted letters, and staff placed every letter by hand from a ladder. The film historian Ben M. Hall called marquees "electric tiaras". The backlit letter board ("readograph") is described as being as important as the poster. The boards are being replaced by LED message centres, but some restorations keep them for authenticity. ([Urban Remains: 1930s Chicago marquee sign](https://urbanremainschicago.com/products/intact-american-depression-era-c-1930-s-single-sided-black-enameled-cast-aluminum-exterior-chicago-theater-marquee-with-word-sign), [Film-Tech forum](https://film-tech.com/vbb/forum/ground-level/36744-slotted-letters-change-pole-arm), [Watchfire: York Theatre](https://www.watchfire.com/our-work/york-theatre))
  - *Lesson:* the letters sit on **rails**. That turns the bible's ribs into something functional (Rules I broke #2). The board is dark at night and backlit by day, which is the Night / Day pair.
- **Cowboy Bebop's opening.** Art of the Title describes flat pink, blue, yellow and green planes behind black silhouettes, with free-form type. Anime News Network and Slashfilm credit Saul Bass's title sequences, Seijun Suzuki's *Tokyo Drifter* and pop art. One unverified comment points to Reid Miles's Blue Note covers. ([Art of the Title](https://www.artofthetitle.com/title/cowboy-bebop/), [Anime News Network](https://animenewsnetwork.com/feature/2023-11-29/the-1960s-graphic-designer-who-inspired-your-favorite-anime-ops/.204797), [Slashfilm](https://www.slashfilm.com/1125746/how-cowboy-bebop-broke-the-anime-opening-mold))
  - *Lesson:* bold type plus flat colour planes, with a hard edge for the "cut". Kept calm: one block per card, one diagonal edge, no silhouettes, no motion beyond a 320 ms slide.
- **MUBI.** MUBI adds one film a day and keeps each for 30 days, a hand-picked programme rather than an endless catalogue. App Store reviews are split between "simple" and "terrible" for the TV app, and some users miss search. ([MUBI on iPad](https://mubi.com/notebook/posts/mubi-for-ipad), [Kimola review analysis](https://kimola.com/reports/unveil-the-truth-mubi-app-customer-feedback-analysis-app-store-us-141803))
  - *Lesson:* "programme" works as a frame for a small library like the household's. Search stays one tab away.
- *(knowledge)* **Criterion disc menus** use a single still or loop with the title set large and very few options. **Saul Bass** title sequences cut flat shapes against plain grounds. **Theatre programmes** set credits with dot leaders, and a running order lists acts in sequence. **House lights** in cinemas dim in stages before the feature.

## Design

### New elements (five)
1. **Marquee** (Home, offline).
   - A board 1728 × 240 framed top and bottom by 4 px walnut rules. It carries 1 px letter rails every 10 px at 7% (fixed surface, cached bitmap on TV).
   - On the left is a title block in the focused title's house colour, cut on the right with an 84 px diagonal. It holds an eyebrow in mono (row and kind), the title in Jost 600 caps at 76 px (58 px over 17 characters) and the facts at 26 px.
   - **House colours are pulled dark** (relative luminance ≤ 0.05) so the block can change on every focus move without a big luminance change (Audit #2).
   - On the right are the Session blocks accent and the seat windows.
   - The marquee updates with the focus in one frame. It is text and a flat fill, not a picture, so the 500 ms rest doesn't apply.
2. **Seat windows**: round windows along the marquee's bottom edge, one per item in the focused row, with the focused item's window lit cream. The row label carries no count. Above 12 items, a mono "14 of 40" replaces them. Offline, all are dark.
3. **Tickets** (profile picker).
   - Each ticket is 300 × 480: a main part (figure and name), a perforation with notches, and a **stub** listing the saved look in three mono lines.
   - Focus works the family way: the ticket lifts 14 px inside its layer, a cream window under it lights, and a baked spill appears.
   - OK slides the stub off (40 px, 300 ms, opacity) and opens Home in that profile's lighting. Calm: a 140 ms fade.
   - On the phone, the profile sheet is the same ticket: the stub shows the look, and the sheet rows sit under the perforation.
4. **Programme** (film and show pages).
   - Two pages with a walnut fold line (with small end ticks).
   - Left page: title block (house colour, diagonal cut, caps), facts, keys.
   - Right page: art, synopsis and credits set with dotted leaders ("Directed by ········ Mara Lindqvist").
   - Shows add the **running order** and season/range keys. Chosen keys press in and light a small **square** window (square = selected mode). The divider between seasons and ranges is a walnut bar.
   - While a season key waits for its 500 ms rest, the running order dims and a panel over its first row says "Season 2 · rest here, or press ↓, to show it".
   - Lower view (↓ past the last key): the page scrolls 560 px. The last key and the credits stay in view above More like this.
5. **House lights + title card + intermission** (Play and pause).
   - **Lights down:** the screen layer's alpha goes to 0.42 (180 ms, leave curve), holds 60 ms, then goes to 0 (220 ms) over the black stage. On the TV this is the screen layer's `ModulateAlpha` over a black ground, never a blended black rect.
   - **Title card:** a house-colour block 1300 × 368 enters from the left edge (−60 px → 0, 320 ms decelerate) with the Session yellow bar and red square. The eyebrow ("Season 3 · Episode 1"), title in caps (96 px), episode name, and the **slatted bar** (16 slats, unlit slats faint) fill with the real load. "Loading" turns to "Ready".
   - **Picture:** after max(load, floor), with the floor at 600 ms for the first Play of the session and 300 ms after.
   - **Lights up** on Stop: a 240 ms fade back to the programme, which keeps its focus.
   - **Intermission:** after 60 s paused, or for Still watching after 3 episodes in a row without a key press. The picture gets a colour filter (brightness 0.4, a filter, not a rect). The card is a sibling of the title card: a house-colour block with "INTERMISSION" or "STILL WATCHING?" in caps, and a panel with the slot window, "Paused at 1:12:29", the title, "Resume now and it ends at 11:06 PM", **Resume from 1:12:29** (orange, focused) and **Stop for tonight**. Back closes the card and stays paused.

### Everything else
- **Top line:** JamFin, tabs (24 px), the profile chip drawn as a tiny ticket, and the clock. The current tab has a lit slot under it (D91). The focused tab gets the key-coloured plate. ↑ from the first row goes there, and Back from any row goes there (Home invariant).
- **Rows:** Continue watching (wide, 400 × 225, progress at 70% cream on the art's bottom edge), Latest films and Latest shows (posters, 216 × 324, names wrap to two lines rather than ellipsis, D163). The "All films" / "All shows" card comes before the walnut end mark. The focused card is held at the left safe line, and the row stops where the end mark meets the right safe line.
- **Player:** the shared TV band (D157) with the timeline on its top edge, chapter stops, a square head window that lights when the timeline has focus, "Playing" / "Paused" with a slot window, the title, time / duration and "Ends at", and hints that change with the state. Skip intro, Next episode, chapters (↑) and Options (↓) behave as in pass 3.
- **Day (Ben's profile):** ground `#c9c4ba`, the marquee as a lightbox `#e3dac8` with dark letters and rails at 9% black, and every unlit window on a light surface as a groove ring (lit opens to the full window with a dark rim). Title blocks keep their dark house colour in Day, so cream type stays readable.
- **Phone:**
  - Home: the marquee is compact and holds the phone's one orange action ("Resume from 1:12:29"), with seat windows in a 3 × 2 grid. Rows scroll sideways, and the five tabs have a lit slot over the current one.
  - Profile: the ticket sheet, opened from the chip.
  - Show: the programme, with the title block, art, Resume S3 E1 from 12:13 (orange), Watched / Favourites keys, season and range chips (chosen ones pressed in), and the running order. Tapping 21–22 scrolls the list to episode 21.

## Language check

What ties JamFin pass 4 to the family:
- **Type:** Jost for words, IBM Plex Mono for eyebrows, numbers and stubs.
- **Indicator windows** with the same meanings: round for status (watched, offline ring), square for a chosen mode (season and range keys, Watched / Favourite), slot for running (Playing). They are always visible, lit with flat cream, and grooves in Day (D173).
- **Focus:** a cream window under the focused thing, a 14 px lift drawn inside its layer, the baked warm spill, and the label switching to warm cream. Isaac's pass-2 answer ("warm colour + baked spill") is unchanged.
- **One orange per screen:** Resume / Play on the programme, Try again offline, Resume or Keep watching in the intermission, Skip intro while it holds focus. Home has none. The focused orange key rises 6 px with its window lit on a brown recess (D108).
- **Walnut** as the material that joins things: the marquee's frame, the programme's fold, the row end mark, the range divider.
- **Session blocks** (Isaac's pick) as JamFin's accent.
- **Motion:** transform and opacity only, focus within 150 ms, nudges at row ends, Calm = ≤ 150 ms fades.
- **State words:** Playing / Paused / Offline / Watched / Not started.
- The **player band** is the same component NervOS Theater uses (D157), on purpose: same remote, same muscle memory.
- The **slatted bar** is on the title card.

Someone arriving from Lobby would recognise within a second the cream window lighting under what they're on, the orange key with its little window on the left, the Jost type, and the walnut line. The marquee, tickets, programme and house lights are JamFin's own.

## Rules I broke

| # | Rule (source) | What I did instead | Why JamFin needed it | Verdict |
|---|---|---|---|---|
| 1 | TV homes put the sign in the black menu band (D109); one Guide/menu band grammar for TV apps | A separate **marquee** board under a slim tab line | The sign is JamFin's main tool for choosing, and it reads better as an object than as band text. It also stops JamFin looking like Lobby. | **Device family** (a TV home names the focused item in one fixed place above the rows); the **form** of that place is **app-local** |
| 2 | Ribs only on black bands (A1, BIBLE §2) | Ribs as **letter rails** on the marquee, including on the light Day lightbox | On a letter board, rails are what the letters hang on. They mean something there. | Keep "texture only on fixed surfaces on TV" as **device family**; **drop** "only on black bands" |
| 3 | TV cards are art + plinth everywhere; the base window is cut into the tile's base (D53, D107, BIBLE §7) | Art + caption on the plain ground; the window sits on the ground under the art | The art is the star; a slab under each cover is chrome | The **parts** (art, focus window under it, label, progress on the art's edge) are **device family**; plinth or no plinth is **app-local** |
| 4 | Show position as "n of N" on the focused row (D59, BIBLE §9 carousels) | **Seat windows** (round, one per item) on the marquee; text only beyond 12 | Position without more text over the covers | "Position is shown" stays **device family**. Round windows meaning position is **app-local** and clashes with "round = status" (Audit #1). |
| 5 | TV title card = shutter + slatted bar + Stripes (BIBLE §2, decisions 2026-11-05); full shutter on the first Play (D171) | **House lights** + colour-block title card + slatted bar | JamFin's Play is the cinema moment. The shutter suits app and game launches in Lobby and NervOS. | **App-local** form. The **slatted bar showing real load** is **language-wide**. max(load, floor) with 600 / 300 ms stays **device family**. |
| 6 | The Day title card is light and flat (D172, pass 3) | Day **dims to dark** before the card | The dark is the point of Play; kept within 2 changes per second (Audit #3) | **Drop** D172. Keep the flash count as **device family**. |
| 7 | Accents on Home screens and launchers only (Isaac's JamFin answer, D178); accent on the black band | Session blocks on the marquee's right end, **and** the yellow bar + red square on the title card and intermission card | The title card already carries an accent in the bible (Stripes). The intermission is its sibling. | Accent **on Home** = **language-wide**. On the title card = already allowed. On the **intermission** = **app-local** (Question 6). |
| 8 | Walnut is an 8 px trim line at the top (BIBLE §2) | Walnut frames the marquee, folds the programme and divides keys; no top trim | It joins objects rather than capping the screen | Walnut as a material: **language-wide**. "Trim at the top": **drop**. |
| 9 | Pass 3's episode row: ↑ from an episode returns to its range key (pass 3 #9) | Vertical running order; ↑ moves up the list, and **Back** returns to the range key that holds the episode | Lists move vertically, so ↑ must mean "previous" | **App-local** |
| 10 | Lower views work like Home: a sign above the focused row (D175) | The film's lower view keeps the last key and the credits above More like this, with no new sign | The programme already says everything the sign would | "No empty band over ~15%" stays **device family**; the sign form is **app-local** (Audit #8) |
| 11 | One house look on shared screens, Day/Night per device (decisions) | Lighting comes from the ticket; the page switch overrides it for review | Already JamFin's exception (D179) | **App-local** (as D179) |
| 12 | Headline effects: "text sits still", effects only on headlines ≥ 32 dp (JamFin experience system) | Titles set in **caps with tracking** at 58–96 px on colour blocks | Bebop/Bass title language; only at headline sizes | **Language-wide** as "caps only at ≥ 48 px TV / ≥ 24 px phone" |

## Audit

Checked with Playwright (Chromium, `chromium.launch()`):
- **1500 × 1000 at deviceScaleFactor 1.3**, with every jump in Night and the Home and programme jumps also in Day: 31 TV states.
- Five frames through the house lights (0.12, 0.33, 0.7, 1.3 and 2.2 s).
- A keyboard path (Tickets → Home → row 2 → nav), a Calm Play, and Stop from the Options strip.
- The full 17-step Tour.
- The three phone states (Home, ticket sheet, range jump).
- **390 × 844 in the dark and light schemes.**

Results:
- No JS errors.
- **Minimum TV text 22.0 px** in every state.
- No horizontal overflow at 390 (scrollWidth 390 in both schemes).
- Safe area: no chrome text outside 96–1824 × 54–1026. The checker flagged three cases, all explained:
  - text scrolled under the solid top bar in the film's lower view (hidden);
  - a focused caption 2 design px left of the line from offsetLeft rounding at 1.3×;
  - peeking cards at the edges, which are content.
- House lights status, 1.2 s load: "2 big changes (lights down, then picture), 1202 ms apart". In Calm the lights go out in 140 ms.

The fix pass corrected:
- the series credits running past the right safe line;
- the season and range row crossing the fold (the fold moved to x 1060, and the "Episodes" label became a walnut bar);
- a 500 ms season timer leaking into the next page;
- the pending-season note printing over row 01 (now a panel with a walnut rule);
- chosen season keys not reading as chosen (they now light a square window);
- unlit windows in Day reading as solid black dots (all indicators now use the D173 groove);
- the ticket stubs wrapping mid-phrase;
- "INTER-MISSION" hyphenating;
- the Skip intro jump landing a second before the prompt;
- the phone rows snapping cards to the frame edge;
- text peeking above the solid top bar.

| # | Problem | Severity |
|---|---|---|
| 1 | **Round windows mean position on the marquee** but "one thing's status" everywhere else (BIBLE §3 shapes). A lit round window could be read as "this one is on". The marquee is the only place it happens, and the lit one is always the focused one, but it's a shape-meaning clash. | Medium |
| 2 | **The marquee block changes colour on every focus move.** House colours are clamped to L ≤ 0.05, so a change is under the 0.10 big-change threshold. But under a held key the 1180 × 240 block swaps at key-repeat rate. That's unmeasured on the Hisense, and so is the cost of the diagonal clip (it should be a cached Path, not a per-frame clip). | Medium |
| 3 | **House lights make two big changes**, lights out and then the picture, at least `hold` apart (300 ms for later Plays, 600 ms for the first). That's within "≤ 2 per second", but at the limit, and if the picture is bright it is a dark→light pair. In Day the lights-out change is light → black over 460 ms. It needs Lobby's measurement method on the real panel. | Medium |
| 4 | **Day Play reverses pass 3's light Day card (D172)**, which is still an open question to Isaac (pass 3 Q3). The two passes now disagree. | Medium |
| 5 | **The running order changes the ↑ path.** From episode 15, the season keys are one Back or 15 × ↑ away. Pass 3 needed one ↑. Someone who doesn't think of Back walks up the list. | Medium |
| 6 | **The season and range row doesn't scale.** Three seasons plus three ranges fit in 96–1040. A show with 5+ seasons and a long season won't fit, and needs the row to scroll or the ranges to move into the running order's header. | Medium |
| 7 | **The intermission after 60 s** hides the band and dims the picture. Someone pausing to talk for a minute gets an overlay they didn't ask for. It's one change, and Back dismisses it, but the 60 s is a guess. | Low |
| 8 | **The film's lower view leaves the left half empty** between y ≈ 180 and 400 (the right half has the credits). It's under D175's 15% band only because the band isn't full width. | Low |
| 9 | **Rows of different shapes** (wide, then posters) change the row pitch, so the focused card's top moves between rows. It's consistent per row, but the eye has to find the window again. | Low |
| 10 | **Ticket stubs use JamFin's settings words** ("Full colour", "Toned", "Calm motion"), which may mean little to Ben or Cleo. | Low |
| 11 | **Very long titles:** the marquee steps from 76 to 58 px over 17 characters, but a 30+ character title is still clipped. It needs a third step or two lines. | Low |
| 12 | **Caps titles** lose any stylised casing a film uses, and caps read slower. They're only used at 58–96 px, so the cost is small. | Low |
| 13 | **The phone marquee is static.** It always shows the first Continue watching item, and doesn't follow what you scroll to. | Low |
| 14 | **Not redrawn in pass 4:** grids, Organise, Search, Discover, Settings, choosers, the disc house menu and the profile-add flow. Pass 3's versions still hold, but they still look like pass 3. The tabs and toasts say so. | Low |
| 15 | **Mockup artefacts:** the Tour can land mid-transition, timings are page timers rather than real loads, and the Lighting switch overrides the profile. None of this affects the design. | Low |

## Questions for Isaac

1. **The cinema as JamFin's frame** (marquee, tickets, programme, house lights, intermission): is it the right bespoke direction? *Recommendation: yes.* The marquee and house lights carry most of the purpose: what is this and when does it end, then get out of the way.
2. **Seat windows for row position** on the marquee, or keep "3 of 8" text? *Recommendation: seat windows up to 12 items, text beyond, on the marquee only.* Write it down as the one place a round window means position.
3. **House lights instead of the shutter for JamFin's Play**, with the slatted bar shared? *Recommendation: yes.* Lobby and NervOS keep the shutter for launches. The shared part across the family is the slatted bar showing real load and the max(load, floor) hold.
4. **Day Play dims to dark** (this pass) or uses a light card (pass 3)? *Recommendation: dim to dark.* It's two changes, at most two a second, and it's what a cinema does. Measure it on the panel first.
5. **Intermission after 60 s paused** (and as the Still watching card after 3 episodes)? *Recommendation: yes, at 60 s, with "Show intermission when paused" On / Off in Settings,* default On.
6. **Session shapes on the title card and intermission card**, outside Home? *Recommendation: allow them on those two cards only* (they're title cards, and the bible's title card already carries an accent). Never on pages, rows or the player band.
7. **A vertical running order** instead of the episode row, with Back to reach the season keys? *Recommendation: yes on TV and phone,* and print "Back · Seasons" in the list's corner once you're 8 or more rows down.
8. **Tickets instead of the Spiral picker** (the shared spiral iris JamFin has today)? *Recommendation: tickets in the base look,* since they show each profile's saved look. The Spiral stays in the alternate looks until the shelf decision.
9. **Titles in caps** on the marquee, programme and title card? *Recommendation: yes, at 48 px and up on TV (24 px on phone) only.* Captions, rows and buttons stay in normal case.
