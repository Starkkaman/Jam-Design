# JamFin · Pass 5 (the whole cinema)

Mockup: `mockups/pass5/jamfin.html`. Passes 1–4 are unchanged.

How to use it:
- **▶ Tour** steps through 27 states, about 3.4 s each. Any real key stops it. **Next step ›** moves one state at a time.
- Or click the TV and use the arrow keys, Enter (OK), Esc or Backspace (Back), M (≡ JamFin menu) and G (Guide). On Search, letters and digits type (the K400) and Backspace deletes. The remote buttons on the page do the same.
- **Hold → for 2 s** sends key repeat (28 presses at 70 ms) along the films row, to show the marquee keeping its colour under a held key.
- **Jump to** has 40 states in five groups: Home and tickets, Programme, Play, Library and search, Settings.
- Page switches: Lighting (Night / Day; jumps reset it to the profile's), Motion (Full / Calm), Stream ready after (0.4 / 1.2 / 3 s) and the page theme.
- The status line shows the screen, presses since Home, what the marquee colour did, and what the house lights did.
- **Phones:** six working 390 × 844 phones (Home, a long show's programme, Downloads, Movies, Offline Home, Search) and the landscape player at its real 844 × 390. Each phone's tabs, cards, chips and keys work. Tapping an episode, the programme's Resume key or the marquee's Resume plays it in the landscape player.

The TV is 1920 × 1080 written in cqw (`--u` = one design px). All titles, people and art are made up. The art is flat generated shapes, people are names only, and profiles are a printed colour band and a name.

Sources read: the last entry of `decisions.md`; `notes/OVERNIGHT-BRIEF.md` including the Direction update; `notes/RULES-TIERS.md` (the 15 language items, tier table, 12 conflicts, H1–H18, what each app owns); `notes/pass4-jamfin.md` and `mockups/pass4/jamfin.html`; `notes/pass3-jamfin.md`; `notes/REVIEW.md`; `projects/jamfin/README.md` and `PROPOSALS.md`; the D-items in `CHANGES.md` that touch JamFin (D106, D157, D168–D170, D177).

## What changed since pass 4

### Fixes to pass 4's audit

| Pass 4 # | Problem | Pass 5 |
|---|---|---|
| 1 (Medium) | Round "seat" windows meant position, against "round = status". | **Seat slots.** Position on the marquee is a row of slots, one per card, with the one you're on lit cream. The slot now means "the one now" (conflict 6 B). Round windows only mean status again: watched, and the broken offline ring. Over 12 cards, the slots give way to "4 of 15" in mono. The phone marquee has a column of slots. |
| 2 (Medium) | The marquee's colour block swapped on every move, at key-repeat rate under a held key. | **The words follow focus at once; the colour waits for a 500 ms rest** (MO11's rule, extended from pictures to large colour changes). The block then cross-fades in 150 ms: alpha on a second cached layer, never a repaint of the whole board. Measured with the hold button: **28 focus moves made no colour change**, then one change 500 ms after the keys stopped. A held key can't change the block more than twice a second by construction. On the TV, the diagonal is a cached `Path`, not a clip per frame. |
| 3 (Medium) | House lights made two big changes at the 2-per-second limit. | **One step.** Lights-down is a single fade (300 ms at night, 360 ms by day). Pass 4's 42 % pause is gone. By day, the picture waits until at least **1 s after the lights started down**, so at most one big change lands in any second. Measured mean screen luminance, Playwright, 1.2 s load:<br>• **Night:** 0.026 → 0.004 at lights-down (Δ 0.02, not a big change: the programme is already dark), card 0.02, picture 0.108 at 1.5 s. 0 big changes for this picture, at most 1 for a bright one.<br>• **Day:** 0.457 → 0.009 in 360 ms (1 big change), card 0.017, picture 0.137 at 1.56 s, 1.2 s after the lights.<br>**Next episode never dims the lights.** The band loads it in place (the reel change): "Next · E2 · …", the slatted bar on the band, then the picture cuts over. |
| 4 (Medium) | Day Play dimmed to dark, against pass 3's light card (D172). | **Kept dark, now assumed under conflict 5 B, pending Isaac.** It's one measured big change (above). D172 stops being a cross-app rule either way. |
| 5 (Medium) | The episode list needed 15 × ↑ to get back to the season keys. | **← from any episode goes to the season index, in one press.** The season keys are now a column to the left of the list (the **season index**), so ← is also where they are on screen. Back does the same. A hint under the list says "← Seasons · ↑ Ranges from the first row". → from the season index (or OK) shows that season at once and enters the list. |
| 6 (Medium) | The season and range row didn't fit 5+ seasons. | **The season index is a column:** 7 keys show, then it scrolls with "9 of 9 ▲▼". **Ranges moved to the episode list's header:** tens up to 50 episodes, twenties up to 100, fifties up to 250, so it's never more than 5 keys. Tested with *Parish Notices*: 9 seasons, and a 64-episode season 9 (1–20 · 21–40 · 41–60 · 61–64). |
| 7 (Low) | Intermission after 60 s was a guess. | Settings › Playback › **Intermission: 1 min · 5 min · Off**, with a note that explains it. |
| 8 (Low) | The film's lower view leaves the left half empty. | Not fixed (Audit 12). |
| 10 (Low) | Ticket stubs used settings words. | Stubs are plain: "Night lighting · Colour covers · Full motion", "Toned · warm". |
| 11 (Low) | Very long titles were clipped. | A third step: over 28 characters, the title sets in **two lines** at 46 px (*The Lighthouse Keeper's Second Daughter*). The programme and the title card step the same way. |
| 13 (Low) | The phone marquee was static. | It **follows the Continue watching row as you swipe it**: words, house colour, the orange Resume key and the lit slot. |
| 14 (Low) | Grids, Search, Settings and the player menus still looked like pass 3. | Redrawn (next section). Organise's Filter and People columns, Discover, the disc house menu and Add profile are still not redrawn. |

### The cinema carried into the rest of the app
- **Library grids (Movies, Shows).**
  - A **slim marquee** (132 px, the same board, walnut rules and house-colour block) names the focused title at 48 px and gives its facts and "10 of 43".
  - Under it, the **Organise keys** (Sort, Filter, View) and the **letter rail**: 27 marquee letters on one line. The focused title's letter has a lit slot. Letters with no titles are dim, and focus skips them (LY19). The rail is off unless the sort is A–Z.
  - Then a 7-column poster grid. The focused row sits at the top and the next row peeks.
  - Choosers drop below their key: five rows, then "1 of 6 ▲▼". The chosen option presses in and lights a square window.
  - The grid ends with a walnut end mark and "End of the list · 43 films". Home's "All films" card opens it.
- **Search.**
  - What you type goes onto a **letter board**: caps letter tiles on the rails, a cream slot as the cursor, and the counts on the right ("1 show · 3 films · 2 people").
  - The keyboard is a **letter case** in a walnut frame: a 12-unit grid (TV21) with Space, ⌫, Clear, Voice and **Done** (the one orange).
  - People come back as **credits** with dotted leaders ("Harriet Vance ······ 9 titles"), under the case. Titles come back as covers, beside it.
  - Names update at once; covers wait for a 500 ms rest (a recess until then). Matching is by word start.
  - Nothing found is a recess, one line and one key ("Look for it in Discover").
- **Settings › Appearance** edits **the profile's own ticket.**
  - A wide ticket at the right shows the stub updating as you choose. Under it, a small preview of Home in that look (lighting, toned covers, artwork shape).
  - Rows have their choices **on the row** as keys. Chosen keys press in with a square window. Choices apply at once and are saved to the ticket, with no Done.
  - Print colour is dimmed and skipped by focus unless covers are Toned (LY19).
  - **Playback** (for everyone on this TV) has Intermission, Skip intro prompt, Next episode and Still watching?, with a programme note beside the focused row.
  - Categories are reordered with Appearance and Playback first. Settings › Appearance is **2 presses from anywhere** with ≡ (≡ → OK).
- **Player menus.**
  - ↓ lifts the band and shows the **Options strip**: Subtitles, Audio, Speed, Picture, Info, Play from the start, Stop. The band's fill now continues under the strip, so the keys never sit on the picture.
  - OK on a key opens its list **above the band** (TV7), aligned to the key, with a walnut rule along its bottom and a lit edge on the key. Five rows, then "2 of 7 ▲▼". The chosen one presses in.
  - Choosing changes the key's label in place, with no toast (LY16). Info opens a fact list in the same frame.
- **≡ JamFin menu** drops below the profile chip: "Appearance · Ada's ticket", Switch profile, Settings.
- **Tabs:** Search, Home, Movies, Shows, Blu-ray, Discover, Settings. Search moved left of Home, so it's 3 presses from Home (Back, ←, OK).
- **Tickets (H15):** the neutral figure is gone. A ticket is a printed colour band, the name and "Ticket 1", with the look on the stub.
- **Phone, fully:**
  - **Home**, with the marquee following the row.
  - **Programme** for a long show: season chips that scroll to a walnut end and open on the chosen season; a pinned episode header with range chips; tap an episode to play it.
  - **Movies:** Sort, Filter and View as chips that open bottom sheets (Close top right, no Done); a 44 px letter rail; three columns; an end mark.
  - **Search:** an input on a small letter board, people as credits, covers in rows.
  - **Downloads as a reel:**
    - Every title is a frame on one film strip. A download fills its frame to its percentage and steps on a real change (MO10), with "62 % · about 4 min left (estimated)" (H17).
    - Waiting for Wi-Fi is an unlit slot.
    - Storage is a read-only bar, and low space is a **warn**: an amber light, ▲ and "Low space".
    - Remove asks in a sheet that names the cost ("It frees 4.1 GB"), with a dark Remove key (CT7).
  - **Offline Home:** the marquee carries the state (broken ring, "Not answering", the retry countdown) with **Try again** (orange) and **Downloads**. What's on the phone shows as a horizontal reel and still plays. The rest waits, dimmed, in a dashed outline.
  - **Landscape player:** the same band, Subtitles and Audio lists rising above it, chapter cards above it, and Skip intro as the one orange while it shows.

## Language check (the 15 items)

| # | Item | Held / adjusted | Where |
|---|---|---|---|
| 1 | Jost + IBM Plex Mono | Held | The only two fonts loaded. Mono for eyebrows, counts, positions, the stub, letter-rail letters. |
| 2 | Indicator windows: visible recess, lit flat | Held | Every window is a recess when unlit (a groove on light Day grounds), flat cream when lit. None glow or grow. The downloads frame works like a window: a recess that fills to its value (H3). |
| 3 | Shape meanings | **Adjusted** | Round now means status only (watched, offline ring, "On this phone", low space). **Position moved to slots** (seat slots, the letter rail's current letter, the phone's slot column), and slot also means running (Playing, Downloading). Square = chosen (season keys, ranges, choosers, settings). |
| 4 | Cream is the house light | Held | Focus windows, lit slots, the cursor slot, chosen squares, the timeline head. |
| 5 | State = colour + shape + word | Held | Warn = amber round light + ▲ + "Low space" (conflict 1 B). Offline = broken ring + "Offline". Playing/Paused/Downloading = slot + word. |
| 6 | Red means alert | Held (no alert drawn) | JamFin has no alert state. Red only appears inside the Session-blocks accent (a printed shape, not a light). |
| 7 | One orange at most | Held | Programme primary, Done on Search, Try again offline, intermission Resume, Skip intro while it holds focus, the phone marquee's Resume (a media home, D129). None on TV Home, grids, Settings, player menus, Downloads. The phone page loses its orange under a sheet. |
| 8 | Focus = light at the thing + small lift | Held | The window under covers, a lit leading edge on list rows and chooser rows, a lit bottom edge on row keys. Lifts are drawn inside the layer; colour snaps; a held key snaps (no transitions). |
| 9 | Chosen things press in | Held | Season keys, ranges, Organise choices, settings choices, chooser rows, phone chips. |
| 10 | Walnut | Held | Marquee rules, programme fold, row and list end marks, letter-case frame, chooser edges, the open strip key's lip, the phone chip row's end. |
| 11 | Things end visibly | Held | End marks, "End of the list", "n of N ▲▼" on long columns and choosers, "9 of 9". |
| 12 | Calm at rest | Held | TV Home has no orange and nothing moving. The marquee changes only after a rest. The accent is static. |
| 13 | Motion short, causal, once | Held | Lights one step, card one slide, 150 ms cross-fades. Calm = ≤ 150 ms fades. Downloads step, they don't stream. |
| 14 | Say it once, plain words | Held, one exception noted | Complete key words ("Resume S9 E38 from 10:09", "Remove download", "Look for it in Discover"). The marquee repeats a card's *name* (not its values); see Rules I broke #7. Failures end in Try again + a way home (TV Home on TV, Downloads on the phone). |
| 15 | Honest objects, drawn flat | Held | Cinema objects only: marquee, letter board, letter case, tickets, programme, film strip. No grain, glow or paper. |

**What someone from another app recognises in a second:** the cream window lighting under what they're on, the orange key with its little window, the Jost and Plex Mono pair, walnut joining things, and square windows for what's chosen. **What's JamFin's alone:** the marquee and letter boards, tickets, the programme, house lights, the intermission, and the reel.

## Conflicts assumed (all "assumed, pending Isaac")

| # | Conflict | Assumed | How JamFin applies it |
|---|---|---|---|
| 1 | Warn shape | B | Phone low space: a round amber light + ▲ + "Low space". |
| 2 | Row ends | A (stop) | Every row and the grid stop at a walnut end. Long rows use slots → "n of N", and the grid has a letter rail (TV18). |
| 3 | Day windows | By surface | On light Day grounds, an unlit window is a groove and a lit one is a full window in a dark rim. On dark objects (title blocks, keys, the player band) and for any window that holds a word, a dark recess. The Day tab slot is cream in a dark rim. |
| 4 | Title card form | B | House lights + colour-block card + the slatted bar on the real load + max(load, floor) + Calm fade. |
| 5 | Day Play | B (dim to dark) | One measured big change; the picture ≥ 1 s after the lights started (see Rules I broke #3). |
| 6 | Round vs position | B | Seat slots; slot = "the one now". |
| 7 | Ribs | B | Rails on the dark marquee, letter board and player band (fixed surfaces, cached bitmaps, never behind scrolling rows). **The Day lightbox loses its rails**, since the app-local exception waits on Isaac liking them. |
| 8 | Accents optional | B | Session blocks on the Home marquee and the phone marquee, the title card and the intermission card. None on grids, search, settings or the player. |
| 9 | House objects drawn twice | N/A | JamFin draws no house devices. |
| 10 | Guide band | B | Guide stays the launcher's. JamFin's player band keeps the shared key order (TV6). |
| 11 | Menus beside a list | B for keys and bands | Player lists rise above the band; Organise lists drop below their key; ≡ drops below the chip. Settings needs no beside-chooser, because choices sit on the row. |
| 12 | Front door | N/A | — |

## Holes applied

| Hole | Applied how |
|---|---|
| H1 Rotated text | None. All text is horizontal. |
| H2 Objects as UI | The cinema's own objects, flat, one realism level, with the language's windows and keys on them. |
| H3 Object-shaped windows | The downloads **reel frame**: a recess when nothing's downloaded, filling flat to the percentage, never glowing. |
| H6 Reading surfaces | The programme's right page: no cards, synopsis at a lede size (28 px vs 24 px credits), credits as leaders, and a source line ("Synopsis and credits: the server's library data"). The left page keeps the orange key (Rules I broke #1). |
| H7 Timelines | The player timeline isn't a repeat of the time text. Its head is a square window, lit while the timeline has focus. |
| H9 Shadows | One kind: a hard drop straight down under orange keys (light from above). No soft shadows; the focus spill is a baked sprite (IN16). |
| H11 Colour from content | Sampled cover colours are clamped in code (`clampHouse`): hues in the red/orange band (< 50° or ≥ 340°) are desaturated to ≤ 0.30, then lightness drops until relative luminance ≤ 0.05. Results, all against cream `#f3e9d4`: `#6e3a22 → #50372b` (9.1:1), `#7a5a2a → #493c28` (8.9:1), `#5a2430 → #522c35` (9.8:1), `#3f4a2a → #374024` (9.1:1). The other four were already in range (9.6–11.3:1). The eyebrow `#d8ccb3` is ≥ 6.7:1 on all eight. |
| H12 Signature moments | Two: the ticket tear (300 ms) and the house lights (lights + card ≤ 600 ms: 300 + 280 at night, 360 + 240 by day). Both count against the flash floor and are ≤ 150 ms fades in Calm. The reel change is not a signature: it's a load on the band. |
| H13 Visible memory | The programme's primary says what it remembers ("Resume S9 E38 from 10:09"). The season index opens on that season and the list on that episode. |
| H15 People | Profiles are a printed colour band + name; the figure is gone. Cast are names only. |
| H16 Capacity | See the table below. |
| H17 Claims | "about 4 min left (estimated)"; "Ends at" comes from the clock and the runtime; synopsis sourced. |
| H18 Glossary | Pass 4's **running order is renamed the episode list** (Callsheet keeps "running order"). **Marquee** stays JamFin's (RULES-TIERS suggests NervOS renames its own to "attract board"). New names: *seat slots*, *season index*, *letter rail*, *letter board*, *letter case*, *reel*, *reel change*. None clash with the glossary so far. |

H4, H5, H8, H10 and H14 don't touch JamFin.

**Capacities (H16)**

| Element | Holds | Overflow form |
|---|---|---|
| Marquee title | 17 characters at 76 px, 28 at 58 px | Two lines at 46 px (about 60 characters), then clipped |
| Seat slots | 12 | "n of N" in mono |
| Season index | 7 keys | Scrolls, "n of N ▲▼" |
| Range header | 5 keys | Range width grows: 10 → 20 → 50 (up to 250 episodes), then it scrolls |
| Choosers | 5 rows | Scroll, "n of N ▲▼" |
| Letter board (search) | 22 letters | Typing stops at 22 |
| Search result rows | 5 covers in view | The row moves; the label says "n of N" |
| Tickets | 4 profiles + Add | The row scrolls, "n of N" |
| Options strip | 7 keys (≈ 1690 px with the longest labels) | No more keys; the eighth would go in Info |
| Phone slot column | 12 | "n of N" |

## Rules I broke

| # | Rule (source) | What I did instead | Why JamFin needed it | Verdict |
|---|---|---|---|---|
| 1 | H6: reading surfaces have no orange | The programme's left page keeps the orange Resume key; the right page follows H6 | A programme is reading plus one action. Splitting the action onto another screen would cost a press on the most-used path. | H6 stays **Language** for pure reading surfaces. "Reading half + action half" is **app-local**. |
| 2 | H6: numbered sections and a designed sign-off | No numbers. The sign-off is the fold's end tick and the source line. | A film page has one section; numbering it is noise. | Numbered sections → **app-local** (CS). Sign-off → **Language**, its form app-local. |
| 3 | TV4: hold 300 ms after the first Play | By day, the hold stretches so the picture comes ≥ 1 s after the lights started (up to 640 ms after the lights) | Keeps a Day Play to one big change in any second | **Device: TV.** Rewrite TV4 as hold = max(load, floor, flash spacing): the flash floor outranks the hold floor. |
| 4 | JamFin's own "Play never waits for a signature" | A Day Play on a warm stream (< 0.64 s) waits up to ~0.6 s for the flash spacing | Same as #3 | **App-local** exception, pending a measurement on the Hisense |
| 5 | TV7: choices open a chooser above or below their key | Settings rows put 2–3 choices on the row as keys | Fewer presses, and every choice is visible | **Language:** "three or fewer choices sit on the row; more open a chooser" |
| 6 | MO11 limits the 500 ms rest to pictures and dependent content | The marquee's colour block waits for the rest too | A large colour change following focus is a flash risk, like a picture | **Device: TV:** any large area that changes colour with focus waits for the rest |
| 7 | TV11 / CT6: the sign never repeats what the card shows | The marquee repeats the focused card's *name* (never a value) | TV12 needs the name at ≥ 46 px, and the caption is the card's label | **Device: TV:** "names may repeat; values may not" |
| 8 | D157: one band key set for JamFin and NervOS Theater | JamFin's Options strip has 7 keys, including Picture, Info and Play from the start | JamFin plays films with several tracks and formats | The band and key order stay **Device: TV**; the key set is **app-local** |
| 9 | SM4: no texture or decoration | Sprocket holes on the downloads reel | They are the object (film), flat and static, on the phone only | **App-local** |
| 10 | Tab order as shipped (Home first) | Search sits left of Home | Search becomes 3 presses from Home | **App-local** (a question for Isaac, since it changes muscle memory) |

## Audit

Checked with Playwright (Chromium, `chromium.launch()` with no options):
- Every one of the 40 jumps at 1500 × 1000 (scale 1.3), with a screenshot of each.
- A keyboard path: ticket → Home → Search → type → Back → ≡ → Appearance → change Lighting → long show → ← → season rest → grid letter rail → Play → Options → Subtitles → Stop.
- The full 27-step Tour.
- Luminance sampled every ~110 ms through a Night and a Day Play.
- The hold button.
- 390 × 844 in the dark and light schemes.

Results:
- **0 JS errors.**
- **TV text minimum 22.0 px in every state.** Hints are 24 px (TV19; pass 4 had 22).
- **No horizontal overflow at 390** (scrollWidth 390 in both schemes).
- **Phone:** text ≥ 12 px and every tap target ≥ 44 px. Pass 4's 11 px phone eyebrows are now 12 px.
- **Safe area:** the only flags are peeking cards at the row edges (content) and, in the film's lower view, text scrolled under the solid top bar (hidden).

The fix pass corrected:
- search captions crossing the bottom safe line (covers 136 × 204, and names wrap to three lines instead of showing a year);
- titles truncated with an ellipsis in search (TY5);
- duplicate generated titles;
- substring matching ("har" found *Orchard*; now word starts);
- a missing space in the grid marquee;
- the Options strip floating on the picture when the band lifted;
- the "← Seasons" hint crossing the fold;
- the phone Back target at 41 px;
- the phone season chips not showing the chosen season;
- the offline ring invisible on the Day block;
- the ≡ press not counted.

| # | Problem | Severity |
|---|---|---|
| 1 | **Two ways up from the episode list.** ← goes to the season index, and ↑ from the first row goes to the range keys. Both are printed under the list, but someone who only uses ↑ never meets the season index from the list. | Medium |
| 2 | **Settings categories past the fourth are more than 6 presses from Home** (About: ≡, ↓, ↓, OK, then 11 × ↓). Appearance (2 presses) and Playback (5) are inside the budget. | Medium |
| 3 | **Day Play can wait for the flash spacing**, up to ~0.6 s on a warm stream. That bends "Play never waits for a signature", and it needs Lobby's panel measurement to confirm that one change in a second is the right floor. | Medium |
| 4 | **The marquee's colour lags its words by 500 ms**, so while you move, the block shows the last title's colour under the new name. The text always passes contrast on any house colour (≥ 8.9:1), but it's a small mismatch on purpose. | Low |
| 5 | **The letter rail's 27 targets are 38 px wide** at 1080p. Focus is a plate plus a slot, so it shows from the sofa, but it's the smallest focus target in JamFin. | Low |
| 6 | **The Night picture can still be a big change** if the first frame is bright (this art measured Δ 0.087). Lights-down isn't a big change at night, so a Play still makes at most one, but nothing caps the picture itself. | Low |
| 7 | **Moving Search left of Home** changes muscle memory for a shipped app. | Low |
| 8 | **Search covers no longer show a year**, so two films with the same name can't be told apart in results. | Low |
| 9 | **The phones are only drawn dark.** Day exists for the phone (CL11) but isn't drawn. | Low |
| 10 | **A part-filled reel frame** might read as a cropped picture rather than progress. The percentage beside it carries the meaning. | Low |
| 11 | **The grid holds the focused row at the top**, so ↑ moves the whole page by a row and the row above is never visible. | Low |
| 12 | **The film's lower view** still leaves the left half empty (pass 4 #8). | Low |
| 13 | **Still not redrawn:** Organise's Filter values and People columns, Discover and requests, the disc house menu, Add profile, the person page, phone Settings. | Low |
| 14 | **Mockup artefacts:** timers stand in for loads, jumps reset the profile and lighting, the View chooser only draws Posters, and generated library titles are word pairs. | Low |

## Questions for Isaac

1. **Seat slots for row position** (round windows only mean status)? *Recommendation: yes.* It's conflict 6 B, and it keeps the marquee's row of lights.
2. **The marquee changes colour only after a 500 ms rest**, words at once? *Recommendation: yes.* A held key never swaps the block, which settles pass 4's flash worry.
3. **Day Play dims to dark, with the picture at least 1 s after the lights go down?** *Recommendation: yes, if the Hisense measurement agrees.* Otherwise, use a light card by day.
4. **A season index column beside the episode list**, with ← reaching it in one press? *Recommendation: yes on the TV.* The phone keeps chips.
5. **Search moves left of Home in the tabs?** *Recommendation: yes.* Search goes from 7 presses to 3, and Home still opens on Continue watching.
6. **Settings choices on the row, applied at once to the profile's ticket**, with a preview of Home? *Recommendation: yes for three choices or fewer.* More than three open a chooser.
7. **Rails on the Day lightbox?** *Recommendation: no.* Keep the Day board plain, as conflict 7 B says, unless you liked them in pass 4.
8. **Downloads as a reel** (frames on a film strip that fill as they download)? *Recommendation: yes, on the phone only.*
9. **Next episode without house lights** (the band loads it in place)? *Recommendation: yes.* The lights are for choosing to watch, not for the next episode of something already playing.
10. **Settings categories reordered with Appearance and Playback first**, and ≡ → Appearance in 2 presses? *Recommendation: yes,* and add a category jump to ≡ later if About and Server need to stay inside 6 presses.
