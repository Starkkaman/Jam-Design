# JamFin · Round 6 (the dark room)

Mockup: `mockups/pass6/jamfin.html`. Rounds 1–5 are unchanged.

How to use it:
- **▶ Tour** steps through 20 states, about 3.6 s each (the shutter step gets 5.2 s). Any real key stops it. **Next step ›** moves one state at a time.
- Or click the TV and use the arrow keys, Enter (OK), Esc or Backspace (Back). On Search, letters type (the K400). The remote buttons on the page do the same.
- Page switches: Lighting (Night / Day), Motion (Full / Calm), **Title shapes (Bold / Quiet / Off)** and the page theme. The status line shows the screen, the focused item, presses since Home, whether the title shapes have settled after a rest, and how many lights are on screen.
- **Phones:** Home, a show's programme and Downloads (offline) at 390 × 844, plus the landscape player at 844 × 390. Season chips, tabs, Try again and Pause work.
- Below the TV, a **Title shapes** strip shows the five compositions side by side.

The TV is 1920 × 1080 written in cqw (one design px = 1/1920 of the width). All titles, people and art are made up. The art is flat colour fields with no people, logos or text.

Sources read: the last entry of `decisions.md` (Isaac's notes after round 5); `notes/OVERNIGHT-BRIEF.md` including "Round 6 direction"; `mockups/01-directions.html` panels B and D; `mockups/pass5/callsheet.html` (Night tokens and type); `projects/jamfin/README.md` and `PROPOSALS.md`; `notes/pass5-jamfin.md`, `notes/pass3-jamfin.md`; `mockups/pass5/jamfin.html`, `mockups/pass3/jamfin.html`, `mockups/09-tv-title-card.html`.

## How I read Isaac's notes

| Isaac said | What I did |
|---|---|
| "I think round 5 looks the best, but I honestly don't really like any of them very much." | Kept round 5's structure and behaviour (screens, focus graph, Home → OK → OK, words now / colour after a 500 ms rest, season index one press to the left, settings choices on the row, player lists above the band, Options strip below it, "Ends at"). Redrew every surface from scratch with fewer things per screen. |
| "The geometric shapes are interesting especially behind the titles." | Made them the signature. Every title stands on a **title field**: two deep colours from its own art and one small bright shape, standing on a hairline floor. Five compositions (Disc and beam, Steps, Cut and half-moon, Rainbow arch, Session bars), one per title, the same everywhere: Home, programme, shutter, phone. Screen titles (Films, Appearance) get a small field too. Flat, static, no motion except a 150 ms cross-fade after a rest. |
| "I miss the split shutter animation." | Play closes the **split shutter** again (mockup 09's motion: top half in from the left, bottom half from the right, 620 ms; out the other way, 460 ms). The title sits on the seam; the **slatted bar** under it is the real load and fills in slat steps. The halves carry the title's field so it lines up when they close. Flat: no ribs, grain, glow, brushed metal or bezel. Calm = a 150 ms fade. |
| "The lights just look dumb and cheesy on the TV menu (honestly all menus) think we need to scrap almost all the lights." | **Zero lights in menus, rows, keys, tabs, choosers and the player.** Focus = a cream ring with a 4 px gap plus an 8 px lift drawn inside the item. Chosen = pressed in (a filled surface), or a ✓ in lists. The current tab = a short underline. The timeline head is a plain cream bar. **One light left:** amber, with words, when the library isn't answering (TV Home and phone Downloads). The status line counts lights on screen (0 everywhere else). |
| "I like the theater direction, but let's be a little less literal." | Dropped the marquee board, letter rails, tickets, seat slots, house lights, letter case, intermission card and the reel. Kept the feeling: a **dark room** (navy ground), **the art as the screen** (the programme shows the art large on the right, the player is the art), and a **programme** page set like a printed theatre programme (mono eyebrow, big title, a ruled list of actions, credits with dotted leaders, a thin walnut fold). |
| "I just keep thinking about how good the color palette is in the dark version of call sheet [round 5]." | Callsheet Night is JamFin's base: ground `#10141d`, surface `#161c28`/`#1f2636`, rule `#2a3244`, cream ink `#ece5d3`, ink2 `#d2cbb9`, dim `#9f9a8b`, orange `#f08a2c`, walnut `#6b4428`. Same type: Jost 400/500 for words, IBM Plex Mono for eyebrows, numbers and times, with Callsheet's numbered section heads ("01 Continue watching"). Day = Callsheet's paper and ink, kept simple. |

Also from the round 6 brief: no drawn real-world objects; calm of Braun Instrument / Flight Instrument (quiet surfaces, mono labels, one accent, space); refinement to the level of Callsheet's Ask page.

## What changed since round 5

| Round 5 | Round 6 |
|---|---|
| Marquee board with rails, a house-colour block and seat slots | A title field (shapes on a hairline) behind plain type. Position is mono text in the row header ("3 of 6"). |
| Tickets (profiles) | A colour field and a name. |
| Programme with a lit leading edge on rows and square windows | A ruled list; focus is the ring, state is the words ("Watched · undo", ✓). |
| House lights + colour-block title card | The split shutter + slatted bar. |
| Letter rail, letter board, letter case on Search and grids | One plain search line with a caret, a quiet key grid; a plain 7-column grid with Sort / Filter / View keys. |
| Ticket preview in Settings › Appearance | Choices on the row only; new **Title shapes: Bold · Quiet · Off**. |
| Player: lit square head, lit key edges, walnut rules on lists | Plain cream head, ring focus, ✓ for the chosen track. Chapters centre on the current one with neighbours visible. |
| Phone: marquee, film-strip reel downloads | Field + title + one orange Resume; Downloads as a plain list with bars; offline as one boxed note with the amber dot. |
| Charcoal ground `#1c1c1b`-ish | Callsheet navy `#10141d`. |

Not carried over this round (still in round 5): Organise's Filter and People columns, Discover, the disc house menu, Add profile, Intermission, Still watching?, Next episode, key-repeat test button.

## Design

**The title field.** The one new element. Each title has a composition (`fk`) and a palette index. Two deep tones (relative luminance under 0.08) may sit behind type; the small bright shape (gold or cream) always sits in the right third, clear of type. The shapes stand on a 2 px rule, like a set on a stage floor, and are clipped by it. Cream text on any deep tone is at least **6.4:1**; facts in ink2 at least **5.0:1**. Day mixes the deep tones 68 % toward the paper so ink stays at least **7.4:1** and ink2 **5.1:1**. Quiet halves the colour and drops the bright shape. Off removes the field but keeps the floor line. On the phone, the bright shape moves to the top edge because titles fill the width.

**Home.** Nav (text tabs), then the focused title on its field (eyebrow names the row and kind, facts include "Ends at"), then numbered rows. Words change on the key press; the field cross-fades after a 500 ms rest, so a held key never changes colour. Rows slide up under the title; each row ends with a walnut mark and "End of row".

**Programme.** Film: eyebrow, title, facts; Resume as the one orange; then Play from the start, Audio, Subtitles, Mark as watched, Add to favourites as a ruled list with values in mono on the right. Right page: the art large (the screen), synopsis at 28 px, credits with leaders, source line. Show: Resume names the episode and time; season index at the left, episode list at the right, ← from any episode to the index in one press, ↓ from the keys lands on the episode you're on.

**Play.** Shutter (above). Ready → the halves part over the player.

**Player.** A navy band over the picture: state word (Playing / Paused), title, chapter, the key legend; timeline with chapter ticks; time and "Ends at". ↓ lifts the band and shows Options; OK on a key opens its list above the band, aligned to the key. ↑ shows chapters above the band, centred on the current one. Skip intro is a plain key that takes focus while it shows.

**Library, Search, Settings.** Films: the word on a small field, count and position in mono, seven posters a row, scrolling by whole rows. Search: one line, a quiet key grid (a–z, ⌫, 123, Space, Clear, Voice), covers and people with leaders; nothing found is one line and one key. Settings › Appearance: categories, then rows with their choices on the row.

**Focus.** Ring: `0 0 0 4px ground, 0 0 0 8px cream` (ink on Day), 110 ms; lift 8 px, 140 ms; both snap in Calm. On the real TV the ring is a cached nine-patch and the lift is drawn inside the item's layer (PROPOSALS 2 and 5), never a transform on the focus target.

## Audit

Checked with Playwright (Chromium): every Jump state at 1500 px, the Tour for 20 s, a real key flow (programme → Play → shutter → Options → Subtitles → English → timeline → chapters → OK → Back ×3), and the page at 390 × 844.

| # | Finding | Severity | Status |
|---|---|---|---|
| 1 | No JS errors in any state, the Tour or the key flow. No horizontal overflow at 390 (scrollWidth 390). | — | Pass |
| 2 | TV text floor: no text under 22 px at 1080p in any of the 20 states. Phone: nothing under 12 px at 390. | — | Pass |
| 3 | The player's list class `.lst` collided with the page's `ul.lst` and threw the "What's gone" list over the controls at 390. | High | Fixed (renamed `.plist`) |
| 4 | Offline status in the nav wrapped the clock onto two lines. | Medium | Fixed: the status line (dot + words) became the hero's eyebrow. |
| 5 | Day shapes under ink2 facts measured 3.7:1. | Medium | Fixed: Day mix 55 % → 68 %, now ≥ 5.1:1. |
| 6 | The library grid scrolled by card edge and showed a cut row of posters under the header. | Medium | Fixed: scrolls by whole rows. |
| 7 | Phone programme: the bright shape sat behind the end of the title. | Medium | Fixed: on narrow fields the bright shape moves to the top edge. |
| 8 | Chapter strip showed a sliver of a card at the safe edge. | Low | Fixed: centred on the current chapter, neighbours visible at both edges. |
| 9 | Disc composition's beam crossed the facts line on the programme. | Low | Fixed: beam lowered. |
| 10 | The film programme's right arrow goes nowhere (the right page has no focus targets; "More like this" isn't drawn). | Low | Open |
| 11 | Two titles sharing a palette and composition look alike (e.g. Glass Orchard and Signal Street both Steps). With 5 × 8 combinations, a real library repeats often. | Low | Open: seed position/scale per title in the app. |
| 12 | The shutter halves are full-screen layers sliding; on the Mali-G57 they must be two cached bitmaps moved by transform (one layer each), with the title and bar composed before the move. | Medium (app cost) | Note for rollout |
| 13 | Title field cross-fade is a full-width alpha change on a 1728 × 400 layer; cheap only as two cached bitmaps. | Low (app cost) | Note for rollout |
| 14 | Settings › Covers and Artwork shape are drawn but don't change the mockup. | Low | Open |

**Fresh-eyes pass ("is this calm? would Isaac call anything cheesy or too literal?").** No objects are drawn anywhere. The only cinema traces are words ("Programme"), the art shown as a screen, and the shutter, which is motion, not a drawn object. Removed after the first look: the clipped chapter sliver and the boxed corners on the ruled list (rows are now open lines). The one remaining risk is the Bold fields on Home being loud on a bright title; Quiet is one setting away.

## Rules I broke

| Rule | What I did instead | Why | Verdict |
|---|---|---|---|
| Indicator windows as the shared vocabulary (RULES-TIERS §1 item 2/3) | No windows at all in JamFin except the offline dot | Isaac: scrap almost all lights in menus | Drop for menus language-wide; keep for real device/status |
| Focus = light at the thing + lift (§1 item 8) | Focus = cream ring + lift | Same | Language-wide (the ring is the new "light at the thing") |
| Accents in a clear zone, never behind titles (BIBLE §2 accents) | Shapes stand **behind** titles | Isaac named "behind the titles" as what he liked | App-local for JamFin (and any media app); contrast floor stated above |
| Walnut joins things | Walnut only for the programme fold and row-end marks | Fewer things | App-local |

## Language check

Ties to the family: Callsheet Night's navy, cream and rules; Jost + Plex Mono; numbered mono section heads; the one orange key per screen; chosen things press in; things end visibly ("End of row", "n of N"); plain complete verbs; amber + words for a real warn. What's JamFin's alone: the title fields, the shutter with the slatted bar, the programme page.

## Questions for Isaac

1. **Title shapes default: Bold or Quiet?** Recommendation: **Bold** on the programme and the shutter, and keep Bold on Home too; Quiet stays a setting for anyone who finds it loud.
2. **One composition per title, or one per kind** (e.g. all films Disc, all shows Arch)? Recommendation: **per title**, picked from its art's colours, so a title always looks like itself.
3. **Is the cream ring enough focus on the TV from the sofa**, or does it want a slightly thicker ring (6 px)? Recommendation: keep 4 px with the lift, check on the real TV before deciding.
4. **Keep a TV Day option?** Recommendation: **yes, kept simple** (Callsheet paper and ink, lighter shapes), since profiles can already pick it.
