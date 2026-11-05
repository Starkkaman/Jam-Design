# JamFin: proposals for the bible

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
