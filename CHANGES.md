# Possible changes

> Proposals waiting for Isaac's yes or no. **Nothing here is approved, and nothing in BIBLE.md has changed because of it.**
> Each item says where it came from. When Isaac decides, the item moves to `decisions.md`, and BIBLE.md is updated if needed.

## A. From the course correction on 2026-11-05 ("too much skeuomorphism again")

Isaac's words: ditch the brushed metal and the glowing, ditch a lot of the seven-segment displays, too much orange,
"I like the minimalist simplicity of the current design" (Jam Braun), keep the ribs, no grain, no paper.
Mockup 13 applies this to Jam Home. If he keeps it, the bible needs these edits:

| # | Bible section | Today (draft 0.5) | Proposed |
|---|---|---|---|
| A1 | §2 Texture (Rich) | Coarse grain, brushed metal, paper headlines, machined seams, bezels | **Remove grain, paper and brushed metal.** Ribs stay, only on black bands (fixed surfaces on TV). Depth comes from soft shadows and pressed-in states, not materials. |
| A2 | §3 Light | Lights glow (halo sprites); lighting up = glow fading in | **Flat lights.** A lit window fills with solid colour, with no halo. The window is always a dark recess, in day and night. |
| A3 | §3 Light colours | Active = orange `#ff7a2e` | **Active = warm cream `#f3e6c8`.** Orange stops being an indicator colour. |
| A4 | §4 Controls / colour roles | Orange for anything you press; sliders reveal orange light | **Orange only on rocker paddles (on) and the one primary action per card or screen.** Sliders reveal warm cream, or the light's own colour for lights. Chosen keys (scenes, sources, modes) press in instead of turning orange. |
| A5 | §5 Meters / type | Seven-segment for big live readouts and the lit scale | **Seven-segment only on appliances** (air purifier, dehumidifier) and maybe the TV title card. Everywhere else, numbers in plain type. |
| A6 | §2 Signature move "light reveal" | Shutters with hot spots, glows warming in | Keep the *reveal* (shutter sliding back, a window filling) but **flat**: no hot spot glow, no bloom. Decide whether the hot spot survives on the TV title card only. |
| A7 | §7 TV selector (W1) | Base window lights; label warms with a glow; spill lights the ribs | **Flat W1:** the base window fills with cream, the label switches to full white, and the spill (if kept) is a flat, low-contrast lighter patch on the ribs, not a glow. Needs a TV mockup check. |
| A8 | TV title card | Rich texture, paper title, brushed shutter halves | Same shutter + slatted bar + stripes, **without** grain, paper or brushed metal. Keep the ribs on the halves. |
| A9 | Remote | Soft plastic, red IR flash, lit power symbols | Keep the shape. Power symbols "lit" = solid green colour with no halo. IR flash = solid red window, no bloom. |
| A10 | §2 Looks | Hi-Fi as a new look | **Hi-Fi is built on Jam Braun:** Braun's calm cards, soft corners, pill/keys and type, plus Hi-Fi's rockers, indicator windows, ribbed bands, walnut rule, appliance and device cards. Consider renaming the base look (e.g. "Braun Hi-Fi"). |

## B. From the Jam Home rounds (mockups 11–13)

| # | Item | Proposed |
|---|---|---|
| B1 | Room colours | Retired (colour discipline). Light colour lives only in its slot window and slider. Confirm Isaac doesn't miss them. |
| B2 | Never the same value twice on one panel | Already a rule; keep. |
| B3 | Light pop-up | White presets show their colour; colour picks recolour the slot and sliders. Five presets 2200K–5000K. |
| B4 | Speaker | "Speakers" button opens group/split with rockers. |
| B5 | TV source | Tile grid with coloured slots, not a list. |
| B6 | Open doors/windows | Amber, not red. Open question: is an open door at night an alert? |
| B7 | History graph | Chart-recorder style: confirm or drop (may be too skeuomorphic after the correction). |

## C. Open items not decided yet
- Look shelf: after the lookbook is done.
- Interface sounds: not yet.
- Token pipeline: undecided.
- Callsheet has not documented its folder yet.

## D. From the overnight mockups
Added after each pass. Full audits are in `notes/pass<N>-<app>.md`.


### Pass 1 · TV launcher
- D1. A focusable card can't show two same-coloured bars at one edge (progress + selector). Define where progress lives on focusable cards.
- D2. Accent clear zones exclude navigation and chrome, not just titles and buttons.
- D3. One focus grammar per device: tiles and list rows use the same window logic.
- D4. The TV minimum (22 px at 1080p) applies to hints and sub-labels too; hints 24 px.

### Pass 1 · Callsheet
- D5. Calendar clashes and due items use amber + shape + word; category dots never use red.
- D6. Bar-group (count) indicators need a maximum (~10) and an overflow form.
- D7. "Moving primary": the one orange action moves to the next thing to do, with a defined order when two compete (e.g. an open security alert vs. replies).
- D8. New read-only meter: the tuning scale (day timeline with a needle for now).
- D9. Key hints printed on buttons as a shared desktop component.
- D10. The Colour bars accent's lighter oranges conflict with "decorative oranges stay darker than control orange" — darken or drop those bars.
- D11. A quieter form for an alert the user has already seen ("Seen 08:20").
- D12. The base-window selector extends to phone tab bars.

### Pass 1 · JamFin
- D13. Progress vs. selector settled proposal: progress on the art's bottom edge; selector window on the label strip's bottom edge (half width). Never the same edge.
- D14. On Play, the title card holds only as long as the load, floor ~600 ms; the 1.6 s hold stays for app launch and milestones.
- D15. Make "never twice" precise: a bar plus "N min left" counts twice; "Ends at" is a different value.
- D16. "Pop above or below" (Unigrid player menus) becomes a house TV rule; choosers from a vertical list pop beside it (needs Isaac's OK).
- D17. Lit windows keep a dark rim in TV Day.
- D18. The orange primary button needs its own focus cue on TV.
- D19. Decide whether accents step back on art-heavy screens, and whether Session blocks' red square is allowed on TV homes.
- D20. Per-profile looks save: look, Day/Night/Auto, Covers (Full colour/Toned), Calm.

### Pass 1 · Jam-Dash
- D21. Add **warn** ("needs a look, not urgent": amber + ▲ + word) to the shared state words; the five names stay shared but each app picks the visible word ("Running" for a container, "On" for a light).
- D22. Accents step back while a screen shows trouble, and draw in once when it's calm again (see also D19).
- D23. Order for the moving primary (D7): alert (newest first) → offline → warn → routine action.
- D24. Destructive actions are never orange or red: a dark button inside a confirm sheet that names the consequence.
- D25. A meter's own readout counts once ("never twice" exception: a bar plus its own number on a faceplate).
- D26. No hidden destinations: every place visible on desktop, at most five phone tabs, never "More".
- D27. Whole-server offline: the faceplate and all its tiles go dashed together, with "Last seen" and one Try again.
- D28. A shape for "something on this day" (calendar strips): small slots, since squares mean "selected mode".
- D29. Jobs show progress in place, on the button that started them.
- D30. Uppercase labels are 13 px (settles 12 vs 13).
