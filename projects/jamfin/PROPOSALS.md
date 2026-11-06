# JamFin: rollout plan for the handoff look

> From the JamFin Agent, 2026-11-06. Answers `HANDOFF.md` (2026-11-06), `mockups/pass6/jamfin.html` and
> `notes/pass6-jamfin.md`. **Plan only:** nothing in Jamfin has changed. Code facts are from Jamfin `mobile` at
> `bbf00df` (TV 0.3.3). Sizes: the TV UI is 960×540 dp, so 1 dp = 2 px at 1080p.

## 1. What changes

| Where | TV | Phone |
|---|---|---|
| **Profile picker** | Each profile is a flat colour field with a name; focus is the ring. The spiral iris is replaced by the launch shutter (below). | The same fields in a list. |
| **Home** | Text tabs (the current tab gets a short underline). The focused title stands on its **title field**: two deep tones from its own art, one small bright shape in the right third, on a 1 dp floor line. Mono eyebrow ("01 CONTINUE WATCHING · FILM"), facts with "Ends at". The words change on the key press; the field cross-fades after a 500 ms rest. Numbered mono row heads, "3 of 6", and a walnut mark + "End of row". **No orange.** | Field + title + one orange **Resume**; rows below. |
| **Grids, Organise** | The screen title on a small field, count in mono, posters on panels with soft corners. Sort / Filter / View are plain keys; their columns are hairline panels; chips are removable with "×". A–Z strip in mono. | Same sheets, restyled. |
| **Film, series, person** | The "programme": eyebrow, title on its field, facts, **Resume** (else Play) as the one orange, then a ruled list of actions with the values in mono at the right. The art is shown large on the right, with the synopsis, credits with dotted leaders and a thin walnut fold. Series: the season index at the left and the episodes at the right. Person: the name on a field and filmography rows. The fixed zone holds (title and primary key upper-left). | Field, title, one orange Resume, ruled list. |
| **Player band, chapters, strip** | A navy band with a state word (Playing / Paused), title and chapter; a timeline with chapter ticks and a **plain cream head** (no amber bullet); time and "Ends at". Chapters above the band, centred on the current one. The strip below: plain keys, chosen = ✓, **no lit edges or dots**. Skip intro is a plain key. Toasts and INFO sit on panels. | The same band in landscape. |
| **Disc house menu** | Hairline panels in the Jam palette. Today it's Cut Paper in every look. The disc's own BD-J/HDMV menus aren't touched. The strip and "Resume at 0:21:24" over a disc menu are in mono. | — |
| **Search, keyboard** | One search line with a caret, a quiet key grid (same QWERTY layout), and results with leaders. No orange. "Nothing found" is one line and one key. | Field + results, restyled. |
| **Discover, requests** | Status as colour + shape + word: Available (ok ✓), Partly available (ok ◐), Requested / Pending / Processing (dim ○ + word), Failed (alert ▲ + word). **Request** is the request page's one orange. | Same. |
| **Settings** | Categories at the left, rows at the right with their choices on the row. Every two-way, instant setting (Animate Back, Toned covers and similar) becomes a **channel-reveal switch in settings steel** (`#71819c` Day / `#64738d` Night): 76×44 px (38×22 dp), 34 px thumb, ~180 ms. Row focus = the ring round the switch. These stay choice keys: Lighting, Motion, Interface sounds and the new **Title shapes: Bold · Quiet · Off**. Sign out and Remove server stay keys with a confirm. No orange. | Same switches, 46×28 px. |
| **Loading, empty, error** | Under 1 s: a static skeleton (hairline panels, no shimmer). From 1 to 10 s: the slatted bar under the screen's title. Over 10 s: one sentence + **Try again** + **Go to Home**. Empty: one line + the action that fills it. Library offline: the **one light** left, an amber ▲ + "Not answering". | Same words. |
| **Split shutter: launch and Play** | Flat navy halves carrying the title's field close (top half from the left, bottom half from the right), with the title on the seam and the **slatted bar** under it showing the real load. Then they part. Launch: cold start until Home (or the picker) is ready. Play: from the press until the first video frame. | Play: a 150 ms fade with the bar (see 4). |
| **Focus** | A cream ring (2 dp gap + 2 dp ring, ink on Day) in 110 ms, plus a 4 dp lift **drawn inside the item's layer** in 140 ms. Both snap under key repeat. Chosen = pressed-in fill or ✓. No lit dots anywhere. | Pressed state + haptics (unchanged map). |
| **Back** | The entry played in reverse, ≤ 250 ms; a cut if "Animate Back" is off. **Not a shutter** (see Q5). | As today. |
| **Interface sounds** | A new "Jam" set: soft, short focus tick (≤ 60 ms), select, back, and one shutter sound on the close. Never during playback. | — |
| **Calm** | Shutter → a 150 ms fade over a static cover; title fields snap; switches instant; focus snaps; Back cuts. | Same. |

## 2. Where it lives in Jamfin

**A new, ninth look: `Design.Jam` ("JAM"),** added after the eight. Nothing is removed or renamed (stored by name).
It follows the Unigrid/Olympia pattern:
- `JamLook.kt` in `ui-common/.../ui/theme/`: palettes, type and tokens, `texture = None`, and a `JamSkin` for the ring, panels and timeline;
- `JamTv` in `app/.../ui/jam/`, registered in `TvDesigns.of`;
- `JamPhoneLook` in `mobile/.../ui/`, registered in `PhoneLooks.of`;
- `DiscTones` gets the look through the Intent, next to the existing `EXTRA_NIGHT`.

New palette roles, with defaults so that the eight looks don't change:
- `action` / `onAction`;
- `walnut`;
- `ok`, `warn`, `alert` / `onAlert`;
- `switchAccent`, `switchOff`.

| Jamfin role | Night | Day |
|---|---|---|
| `ground` | `#10141d` | `#ece7dd` |
| `slab` (panel) / `strip` (inset) | `#161c28` / `#1b2230` | `#f7f4ee` / `#efeae0` |
| `focusFill` (pressed, chosen) | `#202838` | `#e8e2d5` |
| `onGround`, `onSlab` / muted / dim | `#ece5d3` / `#d2cbb9` / `#9f9a8b` | `#19202e` / `#343b4a` / `#5b606d` |
| `rule` (hairline) | `#2a3244` | `#d6cfbf` |
| `focusEdge` (ring), `timeline` head, resume bar | `#ece5d3` | `#19202e` (the player band stays navy) |
| `band` (player) | `#10141d` | `#10141d` (dark over video, as today) |
| `action` / `onAction` (new) | `#f08a2c` / `#1a1206` | `#ec7c22` / `#1a1206` |
| `walnut` (new) | `#6b4428` | `#6b4428` |
| `ok` / `warn` / `alert` (new) | `#7bd651` / `#f2c14e` / `#ff5a48` | same; text forms `#7a5300` warn, `#b3261b` alert |
| `switchAccent` / `switchOff` (new) | `#64738d` / `#05070b` + 1 px `#2a3244` | `#71819c` / `#1c2331` |

Every text role still has to pass `EveryPaletteContrastTest` (≥ 4.5:1). By my sums, dim on ground is about 6.5:1 at Night and 5.1:1 by Day.

**Fonts.** Jost is already bundled (`jost.ttf`, 135 KB). **IBM Plex Mono** (OFL 1.1) has to be added:
- Regular and Medium, Latin subset;
- its OFL text goes in assets beside the others.

Roles:
- words: Jost 400/500;
- labels: Plex Mono 500, uppercase, 0.14 em;
- times and numbers: Plex Mono.

**Default for new installs.** Today a fresh install falls back to Cut Paper (`Design.parse`). Isaac's TV stays on Unigrid until he switches. Making Jam the default for new installs is his call (Q3).

## 3. Order (each step ships as a TV build and is checked on the TV)

| # | Step | Check on the TV |
|---|---|---|
| 1 | `Design.Jam` with fonts, palette and type on token-driven screens (Cut Paper's code path). Jam is selectable, navy and Jost/Plex everywhere, with no lights. | Contrast test; fixed zones at 960×540 dp; hold Right 3 s, p90 ≤ 16.7 ms |
| 2 | Focus ring + lift, chosen and current forms | Twenty presses land twenty along; focus ≤ 150 ms |
| 3 | Home: tabs, focused title, numbered rows, row ends | Home rows ≤ 2 % janky |
| 4 | Programme pages (film, series, person) with the one orange | Film open warm ≤ 6 % (Unigrid's today); Back restores focus |
| 5 | Player band, chapters and strip without lights | Menus above/below; nothing covers the timeline |
| 6 | Split shutter on Play + slatted bar | Press → first frame no later than Unigrid's (logcat); late frames during the close |
| 7 | Title fields: Home → programme → shutter, plus the Title shapes setting | Hold Right: no cross-fade under repeat; p90 unchanged |
| 8 | Settings switches (steel) | Calm = instant; one node per row |
| 9 | States + the shutter at launch | Cold start to Home no slower than today (~434 ms to rows) |
| 10 | Grids/Organise, Search, Discover/requests, disc house menu | Per screen, as above |
| 11 | The Jam sound set | Never during playback |
| 12 | Phone (`JamPhoneLook`), after the TV | 7 Pro gfxinfo, screenshots |
| 13 | The default (Isaac) | — |

## 4. Hard or impossible in our stack, and what we'd do instead

| Item | Our numbers | What we'd do |
|---|---|---|
| **Text ≥ 22 px** | 22 px = 11 sp. The base label is 12 sp (24 px). Shared code goes lower: `PlayerOverlays` "◀ ▶ CHANGE" and the house menu's chapter times are 10 sp (20 px); the strip, Organise and `TvCapabilities` are at 11 sp (exactly 22 px). | Jam floor 11 sp, mono labels 12 sp. Lift the two 10 sp spots in shared code (all looks gain 2 px). Long uppercase mono labels in strip tiles go through `FitText`. |
| **Shutter halves over a live screen** (Mali-G57) | Two full-width layers over a full redraw, with GPU already at 6.5–11 ms of 16.7. The mockup's 620 ms close + 460 ms part exceeds the 600 ms signature budget. | Each half is recorded once into a cached bitmap (2 × 1920×540, about 8 MB) when Play is pressed, then moved by `translationX` only. The title and the bar are small layers of their own. Once the halves have closed, stop drawing the screen under them. Close ≤ 350 ms, part ≤ 250 ms. |
| **Slatted bar = real load** | Today nothing reports stages. | 16 slats, in steps, never a smooth fake fill. **Play:** press 0 → PlaybackInfo answered 4 → source prepared 8 → buffering 8–15 → `onRenderedFirstFrame` 16. **Disc:** opened → title chosen → first frame. **Launch:** session restored → Home data → first pictures (`Arrival` released). A stage stuck over 10 s → a sentence + Try again + Home. |
| **Play vs first frame** | Rule: Play never waits for a signature. The handoff says hold = max(load, 600 ms). | The halves start parting on the first frame. The 600 ms floor applies to **launch only**. If the first frame arrives before the close has finished, the close reverses at once. A load under ~300 ms (a warm resume) gets a 150 ms fade instead of the shutter. Q4. |
| **Soft corners** | Cheap if static; costly if animated or clipped offscreen. | Panels: a round rect drawn once. Cards: an outline clip on their own layer (no offscreen pass). The radius never animates. The ring is a cached nine-patch per radius (5 dp art, 3 dp keys). |
| **Hairlines at 1080p** | 1 px = 0.5 dp. `#2a3244` on `#161c28` is about 1.3:1: gone at 3 m, and it shimmers while scrolling. | TV edges are 1 dp (2 px) on whole pixels. The phone uses 1 px. |
| **Title-field cross-fade** | A 1728×400 px alpha change. Tones come from the art. | Two cached bitmaps faded with `ModulateAlpha`, never under a held key. Tones are taken off the main thread from the decoded thumbnail and cached per item. A per-title seed varies the composition so titles don't repeat. |
| **Programme page cost** | Kinetic's full-screen hero premeasure takes 26–29 ms, so its film open is about 11 % janky; Unigrid's is about 6 %. | Build on Unigrid's sliced hero and `RowSlices`, with `FitCache`. Target ≤ 6 %, stretch ≤ 3 %. |
| **Calm** | Acceptance check: nothing over 150 ms. | See section 1 (Calm). The slats still step: they show state, not motion. |
| **Accessibility** | 3–7 ms per changed frame. | One node per card, as today. Fields, shapes, slats and walnut marks get no semantics. The shutter is one node, set once ("Loading Arrival") and cleared at the first frame. Slat progress is read only in draw, so the slat steps cost no semantics diff. A switch is one node per row (role Switch). |
| **Invariants the mockup bends** | The mockup's grid has 7 columns; ours has 5. The mockup's keyboard is a–z; ours is QWERTY. Ours says "Retry now"; the handoff says "Try again". | Keep 5 columns and QWERTY: they're the focus graph and the presses. The wording is shared by every look, so `ActionLabels.RETRY` becomes "Try again" (plus "Go to Home") in all looks at once. |
| **Phone** | No GPU limit like the TV's (the 7 Pro's p90 is 6–7 ms). The newer looks have never been seen on a phone. | The phone gets the same tokens and Jost/Plex. Its Play shows the slatted bar on a 150 ms fade, since rotating to landscape is already a transition. The haptics map is unchanged. It's built after the TV and checked with screenshots. |

## 5. Questions for Isaac

1. **Is Jam a ninth look beside the eight, or does it replace some of them?** I recommend a ninth look; nothing goes until you say.
2. **Once Jam ships, which looks stay?** I'd suggest at least Unigrid, Olympia and Kinetic, your motion references.
3. **Should Jam be the default for new installs, and when should your TV switch to it?**
4. **Shutter on every Play, or only on cold starts?** I recommend every Play from a page, with no 600 ms floor on Play, and no shutter for Next episode.
5. **"Split shutter back":** I read it as "bring the shutter back" (for Play and launch). Do you also want it on Back? Back is already about 10 % janky, and it has a 250 ms budget.
6. **Is the film page's one orange Resume (else Play)?** I recommend yes.
7. **Do Day palettes still apply on the TV?** I recommend keeping Day as Callsheet's paper, with Night the TV's default.
8. **What lighting should the phone default to?** I recommend Auto.
9. **Profile colours:** should they stay only on the profile's own field in the picker, with no per-profile accent in the UI?

---

# Older notes: these answer the Hi-Fi draft (BIBLE 0.2), superseded by HANDOFF.md

> From the JamFin Agent, 2026-11-04. Read against `BIBLE.md` draft 0.2 and `tokens/hifi.tokens.json`. Hi-Fi isn't
> approved; these are the places where, as drafted, it would break Jamfin's TV performance budget or an invariant of
> Jamfin's `docs/experience-system.md`. Each has the reason, the numbers and a suggested fix that keeps the look.

**The budget behind the numbers.** TV: MT9690, Mali-G57, 32-bit, 3.7 GB, 1080p UI (960×540 dp). HWUI redraws the whole
1920×1080 frame every frame, so every layer on screen costs GPU every frame. Frames today are 17–19 ms total with
6.5–11 ms of GPU, against a 16.7 ms vsync. Targets: janky ≤ 3 %, p90 ≤ 17 ms, p99 ≤ 25 ms. Unigrid today: film open
about 6 % (cold 11 %), Back about 10 % (first frame 22–34 ms), home rows 1–3 %. Compose's accessibility pass adds
3–7 ms after every changed frame.

## 1. Ribs on the band as the TV ground (§2 Materials, "band … TV ground")
- **Conflict:** if the ribbed band is the whole TV ground, it is a full-screen texture under scrolling rows. Measured on
  the Mali-G57: a full-screen grain costs **3–9 ms of GPU a frame**, blended or opaque. That alone takes a 17 ms frame past vsync.
- **Proposal:** TV grounds are flat colour. Ribs only on fixed, non-scrolling surfaces (the menu band, the player band),
  painted once into a cached bitmap per size (as Unigrid's enamel band already is: one bitmap per size, LRU 40), never animated.

## 2. Glows and soft shadows (§3 lights, §2 depth, §7 spill)
- **Conflict:** the mockups draw lights and depth with blurred `box-shadow` (glow 4 px + 12 px, card shadows 6–16 px,
  the band's upward shadow). The TV has **no blur** and only **transform + alpha** may animate.
- **Proposal:** every glow and soft shadow is a pre-rendered sprite (nine-patch or cached bitmap) on its own layer, and
  "lighting up" is that sprite's alpha going 0 → 1. Hard shadows as drawn strips are fine (Jamfin uses them now).

## 3. TV selector: the rib-masked spill and the glowing label (§7)
- **Conflict (cost):** "the spill lights the panel's rib texture (rib-masked glow layer)" implies a masked blend at run
  time: an offscreen layer per focused tile. Render-target switches are expensive on the tiled Mali (Jamfin had to move
  every fade to `ModulateAlpha` for this reason).
- **Conflict (invariant):** "the label picks up an uneven warm glow" is an effect on body-size text. Jamfin: "Text sits
  still": effects only on headlines ≥ 32 dp; card labels are body-size text (12–18 sp, i.e. 24–36 px).
- **Proposal:** bake "spill on ribs" into one bitmap per tile width and fade it by alpha. Warm the label by switching its
  colour (snap, or a ≤ 150 ms colour step) rather than a glow on the glyphs; keep focused labels ≥ 4.5:1 throughout.

## 4. Focus timing: "light reveal" and the selector (§3, §7, tokens `lightIn` 420 ms)
- **Conflict:** the light reveal is 420 ms in / 180 ms out. If the selector's window lights with it, focus exceeds
  Jamfin's budget: **focus settles ≤ 150 ms from the key-press frame; under key repeat ≤ 80 ms or snap**; twenty quick
  presses must land twenty items along.
- **Proposal:** on the TV, the selector window lights in ≤ 150 ms (Glide) and snaps under a held key; the 420 ms reveal
  is kept for signature moments (film-page reveal, Play, milestones), which have a ≤ 600 ms / 300 ms budget.

## 5. Selector lift (tokens: `scale(1.05..1.07) translateY(-1cqw)`)
- **Not a conflict in itself**, a rule to write down: on Compose TV a lift applied as a transform ahead of the focus
  target moves its focus rectangle, and D-pad search then walks the wrong way (a real Cel '88 bug, fixed in tv-fixes).
  The lift must be drawn inside the tile's own layer. Suggest the bible says "lifts are drawn, they don't move the hit box".

## 6. Progress shutter (§6, tokens `shutter` 1400 ms)
- **Conflict:** a 1.4 s shutter on every card's progress bar would put many things in motion at once when a row appears.
  Jamfin: at most one thing moves besides the focused item; loading under 1 s shows a static skeleton; screen enter ≤ 350 ms.
- **Proposal:** card progress bars are static (drawn at their value). The shutter can play once on the focused item, the
  player timeline or a signature moment, inside its budget.

## 7. Easing with overshoot (tokens `rocker` (.3,1.5,.5,1), `settle` (.16,1,.3,1))
- **Conflict (small):** Jamfin allows at most a little bounce (spring dampingRatio ≥ 0.7). Its Settle is (.3,1.3,.5,1);
  the rocker's 1.5 overshoot is more. The bible's settle (.16,1,.3,1) has none, so the two "settle" names mean different curves.
- **Proposal:** one shared curve table with names that mean the same in every project; cap overshoot at Jamfin's 1.3.

## 8. Lounge words: "one title + one line", "tiles = one word" (decisions R2; §8 Words)
- **Conflict (invariant):** Jamfin's plain verbs are fixed in every look: "Resume from 1:12:04", "Play from the start",
  "Audio: English 5.1", "Subtitles: Off". The film page shows title, facts, actions, overview and credits.
- **Proposal:** apply the one-title-one-line rule to home cards and the focused-title sign; let the film page and buttons
  keep plain, complete wording ("one word" is too short to say what Resume does).

## 9. Flash limit (§8: ≤ 2 big luminance changes a second)
- Jamfin's rule is ≤ 3 a second. Not a conflict in direction: Jamfin can adopt 2 if the bible keeps it.

## 10. TV always dark (§2)
- Jamfin has a Day palette per look on the TV (mid-light, never paper-white) and Day / Night / Auto in Settings. Retiring
  TV Day would change a shipped setting: a decision for Isaac, listed in the README's open questions.
