# Home Assistant (Jam Theme + Jam Cards) · Pass 6

Mockup: `mockups/pass6/home-assistant.html` (new; earlier rounds unchanged). Nothing here changes Home Assistant.

Round 6 builds on round 5 (`mockups/pass5/home-assistant.html`). It keeps the controls Isaac liked and removes the drawn house around them.

## How I read Isaac's notes

| Isaac (after round 5, verbatim) | What I did |
|---|---|
| "I like the new toggles, but I liked it better with the symbols from version 5." | Kept round 5's ON/OFF paddle on every light and switched device, drawn flat. The pressed half carries the state: it's deeper paper with an ink edge at the split, and its legend reads in ink. The other legend is dim. Round 5's symbols are back on every card name: lamp glyphs whose shade is the lamp's window and takes its colour, plus Tree, fan and a lit power symbol. TV, speaker, PC and All off got glyphs in the same 30-unit stroke style. |
| "Lets back off on the realism and incorporate the color palette from Callsheet a little bit more." | No wall plates, plug modules, power strip, sideboard, cabinet, key rail, door swing, day arc or plan. Cards are hairline panels with no bevels or drop shadows. The palette is Callsheet round 5's: paper ground with navy ink `#19202e` by day, and its dark navy `#10141d` with cream ink `#ece5d3` by night. Type is Callsheet's: Jost, plus Plex Mono labels tracked .12–.16em. |
| "Including the air purifier. It looks a little different from everything else and I think we need to make some sleight changes." | Slight changes only. It keeps the grille, the seven-segment PM2.5 readout and the round power key with the green-lit symbol. The changes: the body is a normal card (no gradient, bevel or inner shadow); the grille is printed dots in the hairline colour (not recessed); the readout window is navy; the speed keys are house keys with no square lights (chosen = pressed). The dehumidifier follows. |
| "I don't like the sideboard at all. It's requires too much imagination to know what to do." | Gone. Media is back to plain cards, each saying what it is and what's on. TV: title, a thin progress line, transport, volume, Remote and Source. Speaker: Jam Braun's grille as its face, title, transport, volume. PC: one row. Each card opens a popup. |
| "I really like the remote" | Unchanged, CSS and markup copied from round 5: soft plastic, red IR window at the top, lit power symbols, input keys with square windows. On the iPad it opens as its own panel with the remote beside its title and Close. |
| "Don't need or use layout views in look 5" | Removed: the lit plan, Draw the house, the room tabs with lamp-colour windows, the House tab, and the night face that showed the plan. Rooms are plain text tabs on the phone (ink underline) and a heading on the kiosk. |
| "Don't like the keys." | The key rail is gone. Who's home is printed names with a small colour tag, and an outlined tag + "out" for someone away. |
| "The kiosk looks way too busy in look 5. Should be very minimalistic." | Each kiosk shows a room name, the front door (round window + word), a big clock, the date with one weather line, and three keys: iPad = Lights / TV / Music; Echo = Lights / Music / All off. That's Jam Braun's live kiosk layout, which Isaac uses. A key shows only a Pause while something plays. Sheets cover the whole screen and never scroll. |
| (all apps) "too much reality is poking through" / Braun + Flight Instrument calm / "scrap almost all the lights" | Lights only where they're status: a lamp's shade, the power symbol, the door's round window, the purifier digits, one grille dot while a speaker plays, and the remote. No lights on scenes, speeds, sources, tabs or kiosk keys. |

Not in his notes, but kept because he liked them before: white presets show their colours (each key carries a colour band); colour picks recolour the lamp's shade and fader; every light and media card has a popup; the source tile grid; speaker Group or split; lit power symbols; no glow or metal; one orange or none per screen.

## What changed since round 5

| Round 5 | Round 6 |
|---|---|
| Jam Braun warm white / anthracite (`#e7e3da` / `#1c1c1a`) | Callsheet paper / navy (`#efebe2` ground, `#f9f7f2` card, ink `#19202e`; night `#10141d` / `#161c28`, ink `#ece5d3`) |
| Dimmer plate: raised plate, paddle with shadows, fader in a groove | Flat card, flat paddle (pressed half = deeper paper + ink edge), flat fader with a 1.5 px ink-rimmed cap |
| Outlet plate (plug module) + power strip | The same paddle as a light, without a fader |
| Air purifier: gradient body, recessed grille, raised keys with square lights | Card body, printed grille, navy readout, house keys (see above) |
| Sideboard, kitchen radio | TV card, speaker card, PC row |
| Lit plan, Draw the house, room tabs with windows, House tab | Text tabs, no plan |
| Day arc | One line: inside, outside, high/low |
| By the door: door swing + key rail | House strip: round window + word + Lock when needed; printed names |
| Kiosk: clock, arc, plan, door plate, key rail, sideboard, Goodnight | Clock, date, weather line, door, three keys |
| Goodnight round, night face | Not drawn this round (see questions) |
| Scenes / speeds / Goodnight keys with square windows | Pressed keys, no windows |
| Source tiles with a lit slot + "On now" | Pressed tile + "On now" in ink (no slot light) |

## Design

**Tokens.**
- Ground, ink, dim and hairline are Callsheet's values.
- Cards are one step off the ground: lighter paper by day, lighter navy at night.
- Pressed keys are deeper paper by day and near-black navy at night.
- Orange `#ec7c22`/`#f08a2c`, alert `#ff5a48`, cream `#f3e6c8` and walnut `#6b4428` are the house constants.
- The lit power symbol is green-ink `#3c8a28` by day (the old `#7bd651` is 1.6:1 on paper) and `#7bd651` at night.

**The paddle.** Two halves, ON over OFF in Plex Mono (12 px on phones, 16 px on kiosks). The pressed half is the state, as in round 5. There's no shadow now, so "pressed" is shown three ways: a deeper fill, an ink edge at the split, and an ink legend. The lamp's level lives only on the fader (the card's word is "On" or "Off"), so nothing is said twice. Kiosk faders print the level on the cap, and show nothing there when the lamp is off.

**Media.** The TV card says what's on in words (title, source, "ends 11:02"), with one thin progress line, transport, volume (labelled "Vol") and Remote / Source. The speaker's face is Jam Braun's dot grille, which Isaac already lives with. The PC is one row with Sleep/Wake. Popups:
- TV: summary, transport, volume, Remote, power, and the source tile grid.
- Remote: round 5's.
- Speaker: now playing, transport, volume, and Group or split, which opens a list of speakers, each with a mini ON/OFF paddle.
- PC: actions and controller.

**Kiosks.** iPad 1024 × 768 and Echo 961 × 601.
- A 3 px walnut rule at the top, like Jam Braun's room bar.
- The room name in mono, top left; the door top right.
- The clock: Jost 300 at 200 px (iPad) / 150 px (Echo). Date at 30 px; one weather line at 22 px.
- Three keys, 150 / 122 px tall.
- Sheets:
  - Lights: scenes, light cards with tall paddles and faders, Tree, the purifier, and "All lights off…" with a confirm.
  - TV: summary, transport, volume, Remote, power and a PC line, with the source grid beside them.
  - Music: player beside the speaker list.
- Light and remote popups are centred.
- Nothing scrolls.

**Orange.** One per screen at most, in this order: red alert key (no orange) > Lock (warn) > Pause where something plays > nothing. A sheet is its own screen, so the Lock on the home screen doesn't take the Pause's orange inside the TV or Music sheet. The door keeps round 5's rule: amber ▲ + orange Lock by day while someone's home, and red with the solid red key after dark or with nobody home.

## Audit

Checked with Playwright: Chromium, `chromium.launch()` with no options, screenshots in the session scratch dir.
- **Viewports:** 1440 (light scheme) and 390 (dark scheme).
- **Opened, in Day and Night, locked and unlocked:**
  - every kiosk sheet and popup: iPad Lights / TV / Music / Remote / Light / All off / Offline; Echo Lights / Music / All off / Light / Offline;
  - phone light and TV popups;
  - a hue pick (the card's shade turned `#5ab8ff`);
  - a kiosk fader drag (75 → 70);
  - a library popup in the page modal, opened and closed.

**Results:**
- No JS errors.
- No horizontal page scroll at 1440 or 390.
- Kiosks: no element outside the screen, and no sheet, popup or home scrolls.
- Floors (measured in device CSS px):
  - kiosk homes ≥ 18 px;
  - kiosk sheets and popups ≥ 15 px, the remote's engraving excepted (12 px, as in rounds 4–5);
  - everything else ≥ 12 px.
- Phone sliders: smallest side 48 px. No phone target under 44 px.

**Orange measured live:**
- iPad: Day 0 (TV idle); Night 1 (Pause); Day unlocked 1 (Lock); Night unlocked 0 + the red key.
- Echo: Day 1 (radio Pause); Night 0.
- Phones at rest: 0, because Pause is below the fold. Day unlocked: 1 (Lock).

**The fix pass corrected:**
- 12 px "PM2.5" and mini-paddle legends in kiosk sheets (now 15 px; kiosk mini paddles are 64 × 60);
- popup sliders at 36–44 px (now 44 small, 48 standard);
- a kiosk fader cap printing "Off" while the paddle also said OFF (the cap is now blank at 0);
- Pause losing its orange inside the TV/Music sheet when the door was unlocked;
- unlabelled volume faders on cards (now "Vol");
- phone scenes wrapping into a ragged second row (now a 4-up grid).

**Fresh-eyes pass ("is this calm? cheesy? too literal?").** The kiosk is now as quiet as Jam Braun's. The remote is the only drawn object left, and it's kept on purpose. The slot light on the current source tile and the square lights on the purifier keys are gone, because they read as decoration. Nothing else read as cheesy to me.

| # | Problem | Severity |
|---|---|---|
| 1 | **Night "pressed" is subtle.** On navy, the pressed half (`#0a0e15` on `#161c28`) is carried mostly by the ink edge and the ink legend. It reads in the mockup; check it on the real iPad at night brightness before rollout. | Medium |
| 2 | **Goodnight and the night face are gone with the plan.** Round 5's Goodnight round (key pairs, defaults) was built around the plan preview. It isn't drawn here. A plain list version would fit the Lights sheet. | Medium |
| 3 | **The kiosk door is small from 3 m.** A 22 px word and an 18 px round window. Unlocked, the Lock key (60 px tall) carries it. Locked is meant to be quiet. | Low |
| 4 | **Phones show no orange at rest** because the TV Pause sits below the fold. That's correct by the rule, but the playing film is three scrolls down. A "Now playing" line in the house strip would fix it, and would also say the film twice on the Living tab. | Low |
| 5 | **Speaker grille dot** is the only light in the speaker card. By day the lit dot (cream in an ink rim) reads as a small ring. Fine at phone size, unmeasured on the Echo. | Low |
| 6 | **Callsheet's paper is warmer and lighter than Jam Braun's.** The kiosk ground is `#efebe2` (Braun `#e7e3da`). On the iPad in daylight that's brighter. Glare isn't an issue by day, but worth a look. | Low |
| 7 | **The remote's palette is still round 5's** (warm grey plastic, not navy). That's intentional ("I really like the remote"), but it's the one object not in Callsheet's palette. | Low |
| 8 | **Rollout is mostly theme + restyle,** but the flat paddle in jam-light/jam-tile and the glyph set are card code (jam-cards), not theme keys. | Low |

## Questions for Isaac

1. **Is the flat paddle still "the new toggle"?** Round 5's paddle had shadows. Here the pressed half is shown by a deeper fill and an ink edge.
   *Recommendation:* yes, keep it flat. If it reads backwards on the iPad at night, add a 2 px ink bar on the pressed half's outer edge.
2. **Bring Goodnight back as a plain list** (in the Lights sheet and the phone's top strip, with no plan preview)?
   *Recommendation:* yes, as a list of "Turn off / Leave on" rows with round 5's defaults.
3. **Should the remote take Callsheet's navy at night** (navy plastic, same shape and keys), or stay exactly as it is?
   *Recommendation:* leave it exactly as it is. You named it as the thing you like.
4. **Kiosk keys: Lights / TV / Music on the iPad and Lights / Music / All off on the Echo**, as today?
   *Recommendation:* yes. Add a fourth key only for something you reach for daily, like the purifier, which lives in the Lights sheet now.
