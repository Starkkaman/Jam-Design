# JamFin · Pass 3 (final)

Mockup: `mockups/pass3/jamfin.html`. Passes 1 and 2 are unchanged.

How to use it:
- Press **Tour** to step through 16 key states automatically, about 3 seconds each. Any real key on the TV stops it.
- Or click the TV and use the arrow keys, Enter (OK), Esc or Backspace (Back), M (Menu, ≡) and G (Guide), or the remote buttons on the page.

Page controls:
- Profile, Lighting, Covers, Motion, Server and Stream ready after, as in pass 2.
- Four comparison switches for the decisions in this pass:
  - **Skip intro and OK:** Pass 3 (takes focus for 8 s), Strict (OK always pauses) or Pass 2.
  - **Season change:** after a 500 ms rest, or only on ↓ or OK.
  - **Day windows:** Groove (pass 3) or Recess (pass 2).
  - **Day title card:** Light (pass 3) or Dark (pass 2).
- Jump buttons for every screen. New ones: Film · lower view, Long season (22), Offline Home.

The TV is 1920 × 1080 in cqw. The phones are 390 × 844 (Home, show page) and 844 × 390 (player). All titles, people and art are made up, and the art is flat generated shapes. People are a neutral figure in a dark frame, with no faces or initials.

Sources read:
- `notes/OVERNIGHT-BRIEF.md`, all of `CHANGES.md` (A, B, D1–D116), and the end of `decisions.md`.
- `projects/jamfin/README.md` and `PROPOSALS.md`.
- `notes/pass1-jamfin.md` and `notes/pass2-jamfin.md`. Pass 2's Audit and Change suggestions were the to-do list.
- `notes/pass2-tv-launcher.md` and `notes/pass2-nervos.md`, so the three TV apps share one grammar.

Isaac's JamFin answers, applied throughout:
- a plain background behind the rows;
- warm colour plus a baked spill for focus;
- accents on Home and launchers only;
- keep a TV Day option;
- each profile saves its preferred look.

## What changed since pass 2

| Pass 2 # | Problem | Pass 3 |
|---|---|---|
| 1 (High) | OK changed meaning while Skip intro or Next episode showed. | **OK presses what is lit**, and that never changes. On the timeline, OK pauses.<br>**Skip intro** takes the focus for 8 seconds when it appears (Jellyfin's own 0.18 popup also lasts 8 s), and it is drawn as focused: it lifts, its window lights, "OK" is printed on it, and a slot drains at its trailing end. A note above it reads "↓ keeps OK on the timeline". After 8 s, or on any arrow, focus returns to the timeline and the key prints "↑" instead. ↑ reaches it again until the intro ends, and Back hides it.<br>**Next episode never takes focus**, because a stray OK there would leave the episode. It starts by itself when its countdown ends. OK pauses the episode and the countdown with it ("Paused · it waits for you"). ↑ then OK starts the next episode now, and Back stays for the credits.<br>The band hints change with the state: "OK Pause · ↑ Skip intro", or "OK Skip intro · ↓ Timeline". The Strict and Pass 2 versions are on the page switch for comparison. |
| 2 | The season → episode dwell cost decodes. | Nothing loads while focus passes over season keys. The episode row dims, and its header says "Rest on Season 3, or press ↓, to show it". The row follows only after focus **rests 500 ms**, the same preview rule the launcher uses. **↓ or OK opens the season at once.** The 280 ms dwell survives only as JamFin's invisible prefetch. The switch offers "Only on ↓ or OK" for Isaac to compare. |
| 3 | The Day short title card was near the flash limit. | **The title card takes the profile's lighting.** In Day the shutter halves are light (`#c3bfb7`, flat, no ribs), with dark type and Stripes. Page → card is no longer a big luminance change, so a Day Play makes one big change (card → picture) instead of two. The status line counts the changes, and the Dark switch shows pass 2's two changes 600 ms apart. |
| 4 | Unlit selector windows read as dark dashes in Day. | **In Day, an unlit window on a light surface is a hairline groove** of the same width. Lit, it opens into the full dark-rimmed window with cream inside. Windows on black bands keep the recess. The Recess switch shows pass 2's version. |
| 5 | The accent sat next to full-colour covers. | It stays where pass 2 put it, on the black band, right of the sign and under the tabs. **It never shares a surface with art**, so it shows with both cover modes. It hides for offline, toasts and menus. JamFin, NervOS and the launcher each placed their accent differently; see "One grammar" below. |
| 6 | There was empty space under the lower views. | **Lower views work like Home:** a sign (eyebrow, title, facts and two lines), the focused row, then the next row with its name and cards. That's More like this + Cast for films, Seasons, episodes + Cast for shows, and Chapters + Extras for discs (Extras was pass 2 #14). Rows scroll only as far as the focused row needs to end above the bottom safe line. |
| 7 | Offline Home had nothing playable. | The TV has no downloads, and nothing on it can play without the server, so pass 3 is honest about that and gives the household somewhere to go:<ul><li>**Try again** (orange).</li><li>**TV Home**, which goes back to Lobby, where other apps and inputs still work.</li><li>A quiet **automatic retry every 30 s**, with the countdown in words ("Tries again by itself in 24 s").</li></ul>The last-synced Continue watching row stays visible, dimmed by a colour filter inside one dashed outline, labelled "waiting for the server · last synced 9:12 PM". It isn't focusable, because nothing in it would play. |
| 8 | The phone had no route to Discover or Settings. | **The profile chip opens a labelled sheet:** the profile and its saved look, then Switch profile, Discover, Settings and Download quality. There is still no "More" tab. The page behind the sheet gives up its orange (D97). |
| 9 | There was no way to jump ahead in long seasons. | **Range keys.** When the shown season has more than 12 episodes, the season row continues after an "Episodes" divider with 1–10 · 11–20 · 21–22. ↓ from a range key lands on its first episode, and ↑ from an episode returns to the range that holds it, which stays pressed in while you're inside it. Episode 21 is now 4 presses from the season key instead of 20. The phone gets the same ranges as chips that scroll the list. |
| 10 | The sign repeated the card. | **The sign never repeats a value the focused card's plinth shows**: the year, S/E, runtime, role or start time. Home's sign for a film is now "2 h 31 min · Rated 12 · 4K · Ends at 11:06 PM", while the card says "1984". Names may still repeat. |
| 11 | The next row's name crossed the bottom safe line. | Rows are 12 px tighter, so the third row's name sits at y ≈ 984–1012. |
| 12 | Tall chooser lists. | A chooser shows **at most 5 rows**, and longer lists scroll with "Subtitles · 4 of 7 ▲▼" in the heading. Subtitles now has 7 options to show this. |
| 13–14 | Toned is a CSS filter; disc extras were missing. | Toned is unchanged (see Audit). Extras are drawn as a row in the disc lower view. |
| 15 | The phone list had no title. | Phone lists carry their heading and scroll after about 3.5 rows, so they never leave the frame. |
| 16 | The profile picker always shows. | Not drawn. It's a Question for Isaac. |
| 17 | Slow-load wording. | Kept. Back stops the load, as in pass 2. |

### One grammar for the three TV apps

| Rule | Launcher | NervOS | JamFin pass 2 | **Pass 3 pick** | Why |
|---|---|---|---|---|---|
| Guide | One TV menu over everything | One Guide band for all content | JamFin used M only | **Guide is the launcher's. JamFin never takes it.** G shows a note; JamFin's own menu is ≡ (M). | One button, one meaning, on the TV the family shares (D54). |
| Visible content that follows focus | 500 ms rest (picture preview) | 450 ms (big preview) | 280 ms (episode row) | **500 ms rest for anything visible. 280 ms is only for invisible prefetch. A press commits at once.** | One number. 500 ms also caps a held key at 2 swaps a second, which is the flash floor. |
| Hold / press twice | Hold 600 ms or 1 s; press twice within 3 s | Hold 1 s or press A twice; disarms after 3 s | Press twice, 4 s drain | **Press twice, 3 s, for everyone.** JamFin stays taps-only, with no holds. | Two of the three already used 3 s, and a shorter armed window is safer. |
| Launch / Play | max(load, 600 ms) every launch | Load, 600 ms floor | Full form once per session, 300 ms short form after | **max(load, floor).** The full shutter (600 ms) for app and game launches and the first Play of a session; the short form (300 ms) for later Plays; Calm a 140 ms fade. | App launches are rare, but Plays come in runs (episode after episode), so one rule with two floors covers both. |
| Row ends | Stop, walnut end mark, nudge, "n of N" | Group carousels wrap behind a bookend | Stop, "All …" end card | **Content rows stop with the walnut mark and a nudge** (not in Calm). Library rows put the "All …" card before the mark. Group carousels may still wrap (NervOS). | The end card is a destination, not an end marker, so both are kept and each says one thing. |
| Accent | Below the band on the ground | Hidden with Full colour covers | In the band | **On the black band only**, so it can show in both cover modes. | Isaac wants accents on Home and launchers. On the band, the accent never touches art, which settles D19 without hiding it from Full colour profiles. |

## Research
I used WebSearch (4 searches) and fetched no pages, so the findings below come from the search results' summaries. Items marked *(knowledge)* come from my own knowledge, not from a search.

- **Skip intro and OK, as users expect it.**
  - Plex users on Android TV and the Shield repeatedly complain when OK *doesn't* skip: OK opens the player overlay instead, and they have to move focus right to Skip intro. A Plex moderator replied that the button "should have focus when it appears so that when you press select/ok you automatically toggle" it. Users with Harmony remotes and Bluetooth keyboards report needing several presses. ([Plex: Shield interface bug](https://forums.plex.tv/t/interface-bug-with-skip-intro-on-nvidia-shield-2017/603647), [Plex: opens overlay instead](https://forums.plex.tv/t/android-tv-shield-skip-intro-opens-overlay-instead/803736), [Plex: multiple presses](https://forums.plex.tv/t/skip-intro-requires-multiple-button-presses-with-harmony-remote-or-bt-keyboard/596628))
  - One Apple TV user reports that the centre button just toggles play and pause there.
  - Jellyfin Android TV 0.18 shows a segment popup that is skipped "by pressing the OK button", and it **disappears after 8 seconds** or on Back. ([Jellyfin blog](https://jellyfin.org/posts/androidtv-v0.18.0/))
  - JellyWatch lets each segment type be Off, Auto-skip or Button. ([JellyWatch](https://jellywatch.app/blog/jellyfin-intro-skipper-chapters-plugins-quality-of-life-2026))
  - *Lesson:* the mainstream convention is one press to skip, and an extra press is a known complaint. Pass 3 keeps one press while the prompt is visibly focused (8 s, matching Jellyfin's popup) and keeps the invariant by drawing the focus. Strict "OK always pauses" costs a press that users notice.
- **Long seasons.**
  - Plex's picker opens long seasons on episode 1 instead of the next unwatched one, and loads thumbnails in batches. ([Plex forum](https://forums.plex.tv/t/picker-defaults-to-first-ep-rather-than-latest-unwatched-ep-in-seasons-with-long-episode-counts/613656))
  - A Tablo user on a Fire Stick has to scroll through every earlier episode to reach a later one, while the iPad has a tab per season. ([Tablo forum](https://community.tablotv.com/t/seasons-tabs-inconsistencies-between-platforms/17791))
  - *(knowledge, not confirmed by search)* Anime-heavy services group long seasons into episode ranges.
  - *Lesson:* land on the next-up episode (already JamFin's rule) and give a jump. Range keys are the D-pad-friendly jump.
- **Flash** *(knowledge)*. WCAG 2.3.1 counts general flashes by pairs of opposing luminance changes over a large share of the view. A light page → dark card → picture sequence inside a second is the risky shape. Matching the card's lightness to the page removes one change.

## Design (what and why)
**Player prompts.** The rule is written so it stays true in every state: *OK presses what is lit.* The timeline is lit by default, so OK pauses.
- A prompt can take the light only if pressing it by mistake costs nothing you can't get back in one move. Skip intro qualifies: the intro is still in Chapters, and the toast says so.
- It takes the light visibly, with the full orange-key focus cue (D108), and only for 8 s. The draining slot shows that the exception is temporary.
- Next episode fails that test, so it never takes focus. Its countdown carries the action, and pausing holds the countdown.
- With the band hidden, the prompt sits alone bottom right. OK there either presses the focused prompt or pauses and shows the band, never both.

**Seasons and long seasons.**
- The season row holds Season 1 · 2 · 3, then an Episodes divider, then range keys for the shown season.
- The sign above the row describes whatever is focused: a season ("22 episodes · 2021 · Not started · ↓ opens it"), a range ("↓ or OK lands on episode 21"), or an episode.
- Seasons follow the house preview rule (500 ms rest, ↓ or OK commits).

**Lower views.**
- The sign is at y 128–330. Rows start at y 336.
- Film: More like this (wide) and Cast (compact, 260 px cards). Show: season keys, episodes, Cast. Disc: Chapters and Extras.
- The film and disc lower views fit both rows above the safe line. The show view scrolls the season keys away only when Cast is focused.

**Day.** Ben's profile shows both Day fixes:
- the groove windows (Home and pages);
- the light title card.

The black band stays black in Day. Isaac asked to keep a TV Day option and didn't ask for a light band.

**Offline Home.** See the table above. The dimmed row uses the same colour-filter dim as Toned covers, which is cheap on the Mali, with no blended rect.

**Phone.**
- **Home:** the profile chip sheet (Switch profile, Discover, Settings, Download quality).
- **Show page:** opens on Season 3 with range chips, and the season sheet says "22 episodes · not started".
- **Player:** touch has no focus problem. Skip intro is a button you tap, and lists carry their heading.

## Audit
Checked with Playwright (Chromium, `chromium.launch()`):
- **1500 px at deviceScaleFactor 1.31** (the TV at about 1920 px). 36 scripted TV states:
  - Home, the row end and the end card;
  - the film page, the Subtitles drop (7 options), and both lower-view rows;
  - the disc's Chapters and Extras;
  - series episodes, a pending season, and the season shown after the rest;
  - the long season's range keys, episode 21, and Cast;
  - the two-press confirm and Settings;
  - the player band, chapters and a list;
  - Skip intro taken, released, OK, ↑ OK, and Back;
  - Next episode, and Next episode paused;
  - Still watching, error, loading, and the hidden band with skip;
  - Offline, and TV Home focused;
  - Day Home, Day film, the Day title card (light and dark), Day with recess windows, and the Day long season.
- **The full 16-step Tour.**
- **The three phones**, including the chip sheet, the season sheet, a range jump and the player list.
- **390 × 844 in the dark scheme.**

Results:
- No JS errors.
- No TV text under 22 px in any state (the minimum measured was 22.0).
- No horizontal scroll at 390.
- The only TV text outside the safe area belongs to peeking cards at the left and right edges, which are content, not chrome. In the show page's lower view, the peeking Cast row also crosses the bottom line (#7).
- Title-card status: at 4 s in Day, "1 big luminance change (Day card matches the page)". With the Dark card, it reports 2. At 0.4 s, the Dark card reports "600 ms apart (over the 2-per-second floor)".

The fix pass corrected:
- the profile chip text at y 52 (the tab line moved down 4 px);
- the Subtitles drop's footer crossing y 1027 (the ▲▼ moved into the heading);
- base windows showing on the non-focusable cached cards;
- the phone range chips collapsing to 0 px (a grid scroll-container quirk);
- the phone subtitle list running off the top of the landscape frame;
- the orange behind open phone sheets;
- a cast name that matched a profile name;
- the luminance message calling 4.2 s apart "over the floor".

| # | Problem | Severity |
|---|---|---|
| 1 | **Skip intro still bends OK for 8 s.** Someone pressing OK to pause in the first 8 s of an intro skips 90 s instead. It's drawn and reversible (Chapters has the intro), but it's an exception to "a key never changes what it does", now explicit rather than hidden. Isaac decides between this and Strict. | Medium |
| 2 | **None of the pass 3 timings is measured on the Hisense:** the 500 ms season rest, the 8 s take, the 30 s retry. The decode burst still happens once on rest. JamFin needs its late-frame measurement for a season swap on the Mali-G57. | Medium |
| 3 | **The Day title card isn't the bible's ribbed shutter.** Light flat halves follow "ribs only on black bands", but they change the title card Isaac signed off (shutter + slatted bar + Stripes) for Day profiles. The black menu band (about 23% of the screen) still goes dark → light, under the 25% area most flash definitions use, but close. | Medium |
| 4 | **Groove windows bend the window rule in Day.** "Windows are always a dark recess" becomes "a recess on dark surfaces, a groove on light ones". The focus cue grows from a hairline to a 12 px window, which is stronger and also a bigger change per move. It needs a 3 m look. | Medium |
| 5 | **The offline TV still has nothing to play.** The dimmed row tells you what's waiting but isn't focusable, and someone may press at it and get nothing. TV Home assumes Lobby is the launcher (elsewhere it's Android's Home). | Medium |
| 6 | **Range keys belong to the shown season only.** Resting on Season 4 shows its ranges after 500 ms; before that, the ranges still describe Season 3. The divider label doesn't name the season. | Low |
| 7 | **The show page's lower view lets the Cast row's plinth text cross the bottom safe line** (y 1022–1053) while episodes are focused. It's a peek, as on Home, but its text is fully legible there and may be cut on an overscanning panel. | Low |
| 8 | **A windowed chooser can scroll the current choice out of view** ("Off" when you're on Español). The lit square is the only place the value is said (D105), so for a moment it isn't said at all. | Low |
| 9 | **Next episode starts 30 s before the end** in the mockup. With Jellyfin's Outro segment it should start at the outro, and without one it may cut a scene. | Low |
| 10 | **The draining slot is motion during playback.** It's small and transform-only, and within "one thing moves besides the focused item", but it's the only animated thing over the picture. | Low |
| 11 | **Names still repeat** between the sign and the focused card (title, episode name). Values no longer do. Accepted as a name, not a value. | Low |
| 12 | **The phone's Discover is one tap deeper** than pass 1's More. The labelled chip sheet keeps D26, but nobody has said whether the household finds it. | Low |
| 13 | **Toned covers and the offline dim are CSS filters** here. On the TV they're `ColorFilter`s, with the cost on a 40-card row unmeasured (carried). | Low |
| 14 | **Mockup artefacts:** a prompt from the previous player can fade out behind the title card's exit, and Tour screenshots can land mid-transition. Neither affects the design. | Low |

## Questions for Isaac
1. **Skip intro and OK:** should the prompt take focus for 8 s, so OK skips while it's visibly lit? Or should OK always pause, so skipping is ↑ then OK? *Recommendation: take focus for 8 s* (the page switch's default). It matches what users of other apps expect, and Next episode never takes focus.
2. **Seasons:** should the episode row follow a season after a 500 ms rest, or only on ↓ or OK? *Recommendation: the 500 ms rest*, if JamFin's measurement shows the swap stays under its late-frame target. Otherwise only on ↓ or OK.
3. **Day title card:** may a Day profile's shutter be light and flat, which makes one luminance change, or must the card always be the black ribbed shutter? *Recommendation: light in Day, ribbed black at Night.*
4. **Day windows:** is a hairline groove OK for unlit windows on light surfaces in Day? *Recommendation: yes, Day only.* Black bands keep the recess.
5. **Accent placement:** the JamFin accent sits on the black band so it can show with Full colour covers. Should the launcher and NervOS move theirs onto their bands too, so the rule is the same everywhere? *Recommendation: yes.*
6. **Offline TV:** should the last-synced row be shown dimmed and not focusable, with Try again, TV Home and an automatic retry every 30 s? *Recommendation: yes.* Never fake a playable row.
7. **Who's watching?** Should the picker show every time JamFin opens, or only when the TV wakes after a long idle? *Recommendation:* add "Ask who's watching: when the TV wakes / never". Default to when the TV wakes, and otherwise reopen on the last profile. tvOS 26 users found an always-on picker irritating.
8. **Remove from Continue watching** (Plex users asked for it): add a key to the page actions, for in-progress titles only? *Recommendation: yes.* It acts at once and says "Your place (1:12:04) is kept", so no confirm is needed.
9. **Next episode start:** should it start at Jellyfin's Outro segment when there is one, and 20 s before the end otherwise? *Recommendation: yes*, with "Stay for the credits" on Back as now.

## Bible implications
Final form, for BIBLE.md if Isaac agrees.

1. **TV card (settles D1, D13, D53, D107).** A focusable TV card is art + plinth, on a plain ground. Progress is a track on the art's bottom edge, filled at 70% cream. The selector is a 12 px full-cream window, half the card's width, on the plinth's bottom edge. Focus lifts the face 14 px inside its own layer, the label goes warm cream, and a baked spill fades in by opacity.
2. **OK presses what is lit (new; closes JamFin pass 2 #1).** On a player timeline, OK pauses. A prompt may take focus only when it appears, only if pressing it by mistake loses nothing, only visibly (orange-key focus cue, "OK" printed, a draining slot), and for at most 8 s. Prompts that leave the title (Next episode) never take focus: they act on their own countdown, pausing holds the countdown, and ↑ reaches them.
3. **Focus-driven content waits 500 ms (replaces 280 / 450 / 500; extends D55, D114).** Anything visible that changes because focus moved waits for focus to rest 500 ms. Invisible prefetch may start at 280 ms. A deliberate press (↓, OK) commits at once.
4. **Range keys for long rows (new).** A row of more than 12 items in a fixed order gets range keys (1–10, 11–20, …) at the end of the key row above it. ↓ lands on the range's first item, and the range that holds focus is pressed in.
5. **One launch rule (merges D14, D36, D60, D104).** The hold is max(load, floor). The full shutter (600 ms floor) is for app and game launches and the first Play of a session. Later Plays use the short form (300 ms floor). Calm is a ≤ 150 ms fade. The 1.6 s hold is only for milestones.
6. **The title card takes the lighting (new).** In Day the shutter halves are light and flat (ribs belong to black bands), so the only big luminance change is card → picture. At Night they stay black and ribbed.
7. **Windows in Day (amends D17).** On light surfaces, an unlit window is a hairline groove, and a lit window opens to the full window with a dark rim. On black bands and dark surfaces, windows stay a dark recess.
8. **Row ends (merges D59, D110; D75 unchanged).** Content rows stop with a walnut end mark, nudge on an extra press (not in Calm), and show "n of N" on the focused row only. Library rows put an "All …" card before the mark. Group carousels may wrap behind a bookend.
9. **Press twice (settles D111).** Taps-only confirms use "Press OK again to …", disarm after 3 s with a slot draining on the edge opposite the focus window, and apply only to hard-to-undo actions.
10. **Guide is the launcher's (confirms D54 for apps).** Apps never bind Guide. Their own menu is ≡ (Menu).
11. **Lower views work like Home (new).** A page's lower view is a sign (title + facts + up to two lines) above the focused row, with the next row below it. A TV screen never leaves a band of empty ground taller than about 15% of the screen.
12. **The sign adds, never repeats (refines D15).** A sign for a focused card never repeats a value its plinth already shows (year, S/E, runtime, role, start time). Names may repeat.
13. **Choosers hold five rows (extends D106).** A chooser drops below its key, shows at most 5 rows, and longer lists scroll with "n of N ▲▼" in the heading.
14. **Offline with nothing playable (extends D27).** The screen shows one orange Try again, a way out (TV Home), and an automatic retry with its countdown in words. Last-synced content stays visible, dimmed by a colour filter, inside one dashed outline, and it isn't focusable.
15. **Accents on TV homes live on the black band (settles D19, D109; refines D62).** On the band, the accent never touches art, so it shows with Full colour and Toned covers alike. It hides for offline, toasts and menus. Accents appear on Home screens and launchers only.
16. **No "More" on phones (settles D116).** Places that don't fit five tabs live in a labelled profile sheet: Switch profile, Discover, Settings, Download quality. The page behind any open sheet gives up its orange (D97).
17. **What a JamFin profile saves (settles D20, D113).** A profile saves its look, Lighting (Night / Day / Auto, with Day allowed on the shared TV), Covers, Motion, Animate Back and Interface sounds. This is the one exception to "one house look on shared screens".
