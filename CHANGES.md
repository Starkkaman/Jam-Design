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

### Pass 1 · NervOS
- D31. A hold-to-confirm key fills on the edge opposite its focus window, and every hold needs a non-hold path (remotes that can't hold).
- D32. Group carousels need an end rule: wrap or stop, and how the wrap point is shown.
- D33. Decide whether a pop-up showing the current value may sit over the key that already names it (a "never twice" case).
- D34. Systems and sources are drawn as their media or a neutral device glyph, never a brand mark.
- D35. On a launcher, Guide opens one house menu for every kind of content.
- D36. The load-length title-card hold (D14) applies to every launch, not just JamFin's Play.
- D37. Plain words vs each app's own vocabulary on shared screens (the mockup proposes Retro / Steam / Streaming / Films over ARCHIVE / HANGAR / UPLINK / THEATER; Isaac decides).

### Pass 1 · Home Assistant (Jam Theme + Jam Cards)
- D38. §2 materials become the Jam Theme (Braun-based) token set, with separate lamp vs word colours for ok/warn/alert (`warn-ink`, `alert-ink`).
- D39. Orange counting: one primary per card, at most one per popup/sheet; paddles count separately. Is there a screen-level cap?
- D40. Faders carry their own number (on the cap while dragging; big faders may print it). No number beside a fader.
- D41. "Never twice" scope: is a "panel" a card or a whole view?
- D42. Alert outranks primary: when one tap fixes an alert (lock the door), that control is alert red, not orange.
- D43. One popup sheet for every device: phone bottom sheet; kiosk inset, two columns, no scroll; page centred. Close top right, Esc and veil close. No orange Done when changes apply live.
- D44. Kiosk no-scroll covers sheets and popups; kiosk sheets fill the screen.
- D45. A light's colour lives in its slot window and fader; card tint retired (confirms B1/B3).
- D46. Base-window selector on HA's top tabs (extends D12).
- D47. Kiosk dock = black ribbed band, indicator window top-right of each block, action blocks outlined.
- D48. HA built-ins get colours only (`primary-color` orange, `accent-color` ink); HA's own switches are the one place without rockers, or card-mod them.
- D49. Name the appliance exception: appliance cards may be more object-like, with seven-segment.
- D50. Decorative motifs may hold one indicator (the speaker grille's dot lights while playing).
- D51. Type in HA: Jost + IBM Plex Mono replace Archivo at rollout, self-hosted; kiosk sizes clock 168/124, title 22, body 18, label 13.
- D52. Offline lights still open a sheet ("Can't be reached since…", Retry).

### Pass 2 · TV launcher
- D53. TV cards are art + plinth everywhere; on a banner the plinth may shrink to a strip that only holds the focus window.
- D54. On a launcher, Guide always opens one bottom TV menu over whatever is playing; apps never take that button (confirms D35).
- D55. A full-screen preview applies only after focus rests ≥500 ms; Back reverts in one change (new flash/glare floor; NervOS uses 450 ms for large previews).
- D56. D33 settled: while a list is open, its button shows ▲ instead of the value.
- D57. D16 extended: lists pop below a top band, above a bottom band, beside a vertical list, in one shared dark sheet.
- D58. D31 concrete: hold 600 ms for options, 1 s to unlock/delete; non-hold path = ≡ or "press OK again within 3 s".
- D59. D32 for launcher rows: stop at the ends, walnut end mark, a nudge on an extra press, "n of N" on the focused row only.
- D60. One launch rule: hold = max(load, 600 ms), then 300 ms to open; system apps may skip the shutter.
- D61. New shared component: the source window (a recessed display naming the current input).
- D62. The accent's clear zone holds one thing at a time; the accent hides while a toast or menu needs the space.
- D63. Input words: Signal / No signal / Nothing plugged in; every no-signal screen ends with Try again + Home.

### Pass 2 · Callsheet
- D64. The moving primary gets a time scope: time-bound warns take the orange only within ~60 minutes.
- D65. The Next card becomes a shared "one next action" component (same grammar as Jam-Dash's trouble card).
- D66. Step mode becomes a shared pattern (slot-window progress, ≤1 orange per step, an end card), separate from carousels.
- D67. Callsheet's accent is Stripes only, shown when calm.
- D68. Bar group caps at 10 plus the number, and nearby text must not repeat that number (refines D6).
- D69. A seen alert is an unlit light plus "Seen hh:mm": still listed, no red, no button (refines D11).
- D70. A form sheet may hold one orange; a destructive sheet holds none, and Enter never fires a destructive button.
- D71. Selected rows in desktop lists light a leading-edge slot window.
- D72. Content rule for AI text: ≤25 words on a front door, never restating a value a meter on the same screen shows.
- D73. Callsheet navigation: Today, Replies, Agenda, Ask, Projects + a labelled Setup ("Chat" becomes "Ask"). Desktop Replies returns to list + detail (needs Isaac's OK).
- D74. Decide whether rocker paddles in long settings lists stay orange or go graphite (see D76).

### Pass 2 · NervOS
- D75. Group carousels wrap behind a non-focusable "Start" marker; a held key stops there, a fresh press goes round (answers D32 for group carousels; launcher rows stop instead, D59).
- D76. Two keys acting on one value share a tray that names it once (D33).
- D77. Guide band: paused content shows an unlit slot + "Paused"; running content a lit slot + "Running" and a lighter veil.
- D78. An app may keep its approved section names (Archive · Hangar · Uplink · Theater) on shared screens if set in house type with a one-line description on focus (D37, Isaac decides).
- D79. A TV home shows at least 2.5 rows at 1080p (cards ~15% of width, labels 26/22 px).
- D80. The resume point appears once, on the main button.
- D81. Save states: four picture slots; empty = dark recess, current = lit square.

### Pass 2 · Home Assistant
- D82. Orange is budgeted **per screen**: one primary, chosen playing > on > idle, then page order; a popup or sheet counts as its own screen (answers D39).
- D83. Rocker paddles are never orange: on = paddle up + a lit window on the paddle in the device's colour. (Big change to A4; Isaac decides. Mockup shows pass 1 / adaptive / quiet side by side.)
- D84. The control that fixes an alert is a solid red key with dark text at every size, and nothing else on that screen is orange while it shows (merges D42 + TV's alert-ring version; pick one form).
- D85. A lit light card may tint the strip behind its fader ("Band"); whole-card tint stays retired. Options Band / Edge / Wash shown for Isaac.
- D86. Kiosk light faders are vertical columns printing their own number on the cap.
- D87. Day kiosk dock = card blocks with indicator windows; the black ribbed dock is night only (amends D47).
- D88. HA's `primary-color` reaches only confirm buttons; switch/state keys map to dark and cream (keys unverified).
- D89. Keys may carry a printed colour code for identification (never lit, never a state, never orange).
- D90. A count only counts what it names ("Lights · 3 on" leaves out the Tree).
- D91. Tab bars draw only the lit window (extends D12/D46).

### Pass 2 · Jam-Dash
- D92. Warn = amber **triangle** window + word; alert stays round, red, ringed (a new indicator shape; refines D21).
- D93. State words come in three lengths: shared label, per-app short word (≤14 characters, e.g. "Crashed", "Partly up", "Almost full"), and a sentence.
- D94. Dashboards shrink in a fixed, published order, with a named list of what never shrinks (headline, trouble cards, state words, Open).
- D95. D23 precise: alerts → offline → warns → routine, only on screens that own an action; a calm overview has no orange.
- D96. Trouble is said once: the reason and fix live on the card; the tile keeps its place with just the word (desktop) or leaves the grid (phone).
- D97. One orange per frame: the page behind an open sheet loses its orange (agrees with D82).
- D98. Data loss is opt-in inside the confirm sheet, and the button names the result (extends D24).
- D99. Black bands at night get a hairline edge, a top highlight and stronger ribs.
- D100. Live meters update text continuously but move the bar only on a real change (≥3 points), with one settle.
- D101. A rolled-back update is warn, not alert; Try again can fail and must say what to check (refines D27).
- D102. A phone overview with several servers starts with a strip of one row per server.
- D103. Apps without art get a neutral category icon in a dark frame, never initials or a brand mark (extends D34).

### Pass 2 · JamFin
- D104. Title card on Play: full shutter once per session (600 ms floor), ≤300 ms after; 1.6 s hold only for app launch and milestones (refines D14/D60).
- D105. An open layer carries the value: while a chooser or shelf is open, the key/band text naming it hides (answers D33; same as D56/D76).
- D106. Menus pop above, below, or drop below their key, **never beside** (closes D16; conflicts with D57's "beside a vertical list", pick one).
- D107. Selector numbers: 12 px full-cream window on the plinth; progress 70% cream on the art's edge (settles D13).
- D108. Focused orange key: rises 6 px, deeper under-edge, black label, window lit on a brown recess (closes D18; same as NervOS).
- D109. TV homes put the sign in the menu band, and the accent sits in the band's clear zone, never touching art (D2/D19).
- D110. Library rows end with an "All …" card (with D59 row ends).
- D111. Two-press confirm with a draining slot for tap-only remotes, only for hard-to-undo actions (JamFin 4 s vs TV 3 s: pick one).
- D112. Player prompts sit bottom right as the player's only orange; still-watching and errors are a centred panel on a dimmed picture.
- D113. Profile saves look, lighting, covers, motion, Animate Back, sounds. Isaac decides whether a profile's Day may override the house look on the shared TV.
- D114. When focus changes other content (season → episodes), it waits for a 280 ms dwell.
- D115. TV safe area includes band text; slim bands 108 px with bottom-aligned text; a peeking next row isn't readable content.
- D116. JamFin phone tabs: Home, Movies, Shows, Search, Downloads; Discover and Settings behind the profile chip.

### Pass 3 · TV launcher (final form)
- D117. The TV is always on one source; Lobby and its apps share "Apps". Home never marks an HDMI input current (replaces D61).
- D118. One way in per job per screen (inputs are keys in Home's bottom row; the band window is gone).
- D119. The alert fix on TV is D84's solid red key, focused like D18. No rings.
- D120. Rows stop on every TV screen (D59 wins over D75 for the TV; NervOS's wrap needs Isaac's call).
- D121. Windows by lighting: dark recess at night, shallow recess in Day, lit window in a dark rim.
- D122. Real app banners: 6 px frame, colour-filter toning at night, never brighten on focus.
- D123. Accents show only where no cover art is in view, and step back on trouble and overlays.
- D124. Every failure screen ends with what happened, what to do, Try again (orange) and Home.
- D125. OK acts on release; holds always have an on-screen press-twice path.
- D126. Notices never pop up: an update is a light on Settings; a device turning on gets one prompt, never repeated. Changes that show in place get no toast.
- D127. An empty Continue is a recess with one line; first run holds "Arrange Home". No suggested content.
- D128. Feasibility: a TV menu over other apps needs an accessibility service + draw-over permission and a capturable remote key (Isaac decides).

### Pass 3 · Home Assistant (final form)
- D129. Orange per screen goes playing → on → idle; keys that lose it keep their place and size; music gets a place where Play is always primary (Music tab/sheet).
- D130. Paddle window 18×7 (20×8 kiosk) lit in the device's colour; never orange (confirms D83).
- D131. Small indicator windows are dark in both modes; long tracks are a light groove by day, dark at night.
- D132. Lights are drawn in a display colour: whites on an amber-to-cream line, colours near orange drawn lighter, same value everywhere.
- D133. A lit light's colour lives in its slot, paddle window and a 30% fader band, only while on (Band chosen over Wash/Edge).
- D134. Kiosk sheets use kiosk sizes (keys ≥20 px text, 60 px tall) and never scroll.
- D135. No control restyles another (adaptive paddles decided once per view open).
- D136. HA built-ins are themed only by verified HA 2026.10 keys (`ha-switch-checked-*`, `ha-color-primary-*`, `state-*-active-color`); no card-mod.

### Pass 3 · Callsheet (final form)
- D137. The Next card order: alert → offline → warn within 60 min → routine → calm; every non-routine card ends with a "Then" line.
- D138. Alert key form: solid red key with ink text and a ringed LED; nothing else on that screen is orange.
- D139. Calm screens, reading pages and settings carry no orange.
- D140. A count appears once per screen: no badges that repeat a meter.
- D141. Bar group = one dark recess holding up to 10 segments, overflow number inside.
- D142. Warn = amber triangle window + word; drop the ▲ glyph from words beside a window.
- D143. Offline service: a dashed bar over cached content; read-only actions still work.
- D144. Voice mode is a shared pattern: starts only from a tap, current line only, three big keys, Pause/Play the one orange, can never send, accept or delete.
- D145. Step mode is reused for checks, weekly review and first-run setup; a reading page is the steps expanded, with no orange.
- D146. "Hide this kind of thing" defaults to one item; wider scope is deliberate, locked for VIPs, listed with Remove and Undo. Every merge has Undo.
- D147. Shortcuts are single letters; `?` always opens the key sheet.
