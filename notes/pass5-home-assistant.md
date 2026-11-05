# Home Assistant (Jam Theme + Jam Cards) · Pass 5

Mockup: `mockups/pass5/home-assistant.html` (new; pass 4 unchanged). Nothing here changes Home Assistant.

Pass 5 builds on pass 4's house: the lit plan, day arc, dimmer plate, outlet plate and power strip, sideboard, kitchen radio, key rail, door swing, room tabs and the Goodnight round. It also keeps what Isaac already liked: the air purifier, the remote with the red IR at the top, the source tile grid, speaker Group or split, white presets that show their colours, colour picks that recolour the lamp window, a popup on every light and media card, lit power symbols, no glow or metal, and seven-segment only on appliances.

The work this pass was to make the house **honest** and to finish the screens pass 4 didn't redraw.

## What changed since pass 4

| Pass 4 | Pass 5 | Why |
|---|---|---|
| An invented floor plan, drawn like a survey (walls, windows, door swing) | **A labelled placeholder.**<br>• An 8 × 7 grid, tagged "Sample layout" in its own top row.<br>• Only the openings HA knows: front door, back door, kitchen window. The decorative windows are gone.<br>• An **outside row** holds the Car port. | H8, H17: a plan of the wrong house is worse than none (pass-4 audit #1, High) |
| No way to get the real plan | **Draw the house** (Settings › Plan), four steps on a phone:<br>1. Rooms<br>2. Place: tap two corners on a grid of 44 px squares<br>3. Doors and windows: room, wall, position<br>4. Check: with the lights on, then Save plan<br>Saving relabels every plan "Drawn by Isaac". Before anything is drawn, the product shows **room tiles**: no walls, no geometry (Plan switch on the page). | The plan has to come from the people who live there, and say so |
| Room fill = the brightest lamp only, at an opacity over the floor (night: tan/brown, about L 0.68) | **Flat bands**, one per lamp colour (up to 3). Each band is **clamped** in OKLab:<br>• night L 0.84–0.90, day L 0.93–0.89;<br>• brightness moves only chroma, so a dim lamp is paler, never darker;<br>• the orange guard is re-checked.<br>Examples: cozy 40 % at night is `#e7ceab` (L 0.86); Marissa's fairy lights now show pink. | Audit #6. H11 |
| Phone slide dimmer 36 px wide | 48 px (all 6 phone sliders measure ≥ 48) | Audit #3. CT13 |
| Paddle with no window ("top pressed = on") | The paddle prints **ON over OFF** in Plex Mono (12 px phone, 16 px kiosk). The pressed half is the state, and its legend reads in ink; the raised half's legend is dim. | Audit #9. CT1 |
| The House tab lit the rooms twice (tabs + plan) | On House, the room-tab windows step back to **outlines**. Not dark windows: dark would mean "off". | Audit #4. CT6 |
| One colour per tab window | The two-pane tab window shows **up to two** lamp colours | Same data as the bands |
| Key-tag initials 9–11 px | 13 px on phones, 18.8 px iPad, 18.2 px Echo (measured) | Audit #7. H15 |
| Sun = Braun yellow `#e8b12a` (OKLab 0.045 from warn amber) | Sun = an **ink ring with eight rays**, filled with the plate colour. The moon is a cream crescent. A dotted hairline drops from the sun or moon to the horizon. | Audit #8. Shape, not colour |
| Day arc: past solid ink, future dotted dim | Past **dims**; what's ahead is dotted ink. Mark labels sit on the clear side of the arc. | H7 |
| Door always red when unlocked | **Warn by day** while someone is home: amber light, ▲, "Unlocked", amber door swing, orange Lock key.<br>**Alert** after sunset or with nobody home: red, the solid red key. | Conflict 12 (assumed) |
| Window open = amber light + word | Amber light + **▲** + "Open" | Conflict 1 (assumed) |
| Door plate and key rail as two plates (dead space) | One **"By the door"** plate: door swing + word, a rule, then the key rail | Audit #14 |
| Goodnight: one toggle per row, guessed defaults; orange only when nothing plays | Each row has a **key pair** (Turn off / Leave on) that presses in, with a square window. Explicit defaults, printed in the sheet. Kiosk version: preview, door/window and keys on the left; rows on the right; no scroll. "Goodnight · done 9:41" afterwards. Fade 600 ms (was 700), 150 ms with reduced motion. Defaults:<br>• shared rooms and outside: off;<br>• bedrooms: left on;<br>• TV: left on **while it plays**, otherwise off;<br>• purifier: night speed 25 %;<br>• front door: always locks;<br>• window: reminder only. | Audit #10. H12 |
| Clock/Photos screensaver unchanged | **Night face** (9–11 pm): clock, night arc, door, lit rooms only. Static, no orange, touch to wake. | Carries the plan into a screen pass 4 didn't redraw. H10 |
| Lamp and door drawings inside cards | **House objects** sheet, Jam Home's reusable set:<br>• 7 lamps, the door (locked / warn / alert), the window and the plug;<br>• phone 30, kiosk 40 and TV 64 px;<br>• a TV rest and a TV focused variant. | Conflict 9 (assumed): Jam Home owns these drawings |
| — | **Rollout table**, card by card (17 rows): what changes, and what kind of HA work it is | Process rule: nothing changes now |
| "Room strip" | **Room tabs** | H18: "strip" was also the power strip, and close to Callsheet's "day strip" |
| Kiosk plan 660 px wide | Plan 536 (iPad) / 430 (Echo), set by the 8 × 7 grid; the right column gained ~90 px | The Echo radio label no longer wraps (audit #11) |

**Unchanged on purpose:**
- the air purifier and dehumidifier (the only seven-segment);
- the remote (soft plastic, red IR flash at the top, lit power glyphs);
- the source tile grid with "On now";
- the speaker's Group or split;
- the light popup: five whites with their colours, the hue keys, "Your colours", members, the off timer;
- the sideboard and kitchen radio;
- the solid red alert key;
- no brushed metal, glow, grain or paper;
- no accent.

## Screens in the mockup
- **Phones, 390 × 844:**
  - Living · Day, House · Day, Living · Night, House · Night (every room via the tabs);
  - Draw the house (5 states, interactive).
- **iPad, 1024 × 768:**
  - Day, Night, Night face;
  - every room sheet, the Outside light, the Sideboard sheet, TV/source, remote, PC, speaker + Group or split;
  - light popup, offline popup, All lights off, Goodnight.
- **Echo, 961 × 601:** Day, Night, Night face, and the same sheets, sized down.
- **Also:**
  - Plan switch (drawn / not drawn yet: tiles) and door switch (locked / unlocked);
  - library of every card in Day and Night;
  - tokens, house objects, rollout table, and the 15-item language check.

### Orange (measured live, Playwright)
| Screen | Locked | Unlocked |
|---|---|---|
| Phone Living · Day | 0 | 1 (orange Lock: warn) |
| Phone House · Day | 0 | 1 (the header's Lock; the doors list shows only the word) |
| Phone Living · Night | 1 (Pause) | 0 (red key) |
| Phone House · Night | 0 (film playing) | 0 (red key) |
| iPad Day / Night | 0 / 1 (Pause) | 1 (Lock) / 0 (red) |
| Echo Day / Night | 1 (radio Pause) / 1 (Goodnight) | 1 (Lock) / 0 (red) |
| Night faces | 0 | 0 |
| Setup steps 1–4 / end | 1 (Next or Save plan) / 0 | — |

## Language check (the 15 items)
| # | Item | In Jam Home | Held / adjusted |
|---|---|---|---|
| 1 | Jost + Plex Mono | Jost for words. Plex Mono for numbers, paddle legends and the plan tag. | Held |
| 2 | Indicator windows | Day: an unlit window is a hairline groove; lit = flat colour in a dark rim. Night: dark recess. Lamp shades follow the same rule. | Adjusted (conflict 3) |
| 3 | Shapes have meanings | Round = door/window status. Square = chosen (scenes, speeds, Goodnight pairs, setup keys). Slot = playing / setup step. Bar group = a room's lamps (max 10, then "+n"). The "Here" marker is a printed walnut pin, not a round light. | Adjusted (conflict 6) |
| 4 | Cream is the house light | Grille dot, playing slot, setup steps, TV focus sill | Held |
| 5 | Colour + shape + word | Window: amber + ▲ + "Open". Door: light + swing + word. Offline: dashed plate + word. | Adjusted (conflict 1) |
| 6 | Red means alert | The solid red key only for the door at night or with nobody home | Adjusted (conflict 12) |
| 7 | One orange, the thing to do now | 0 at rest. Order: red alert (no orange) > Lock (warn) > Pause > Goodnight. A sheet counts as its own screen. | Held |
| 8 | Focus is a light + lift | Touch: keys press in. TV objects: a cream sill + 6 px lift. | Held (TV variant new) |
| 9 | Chosen things press in | Scenes, whites, sources, Goodnight pairs, setup keys | Held |
| 10 | Walnut | Key rail, cabinet top, room rule, "Here" pin | Held |
| 11 | Things end visibly | "Goodnight · done 9:41", "Plan saved", the strip's "Free" socket | Held |
| 12 | Calm at rest | No orange at rest, nothing loops; the night face is static | Held |
| 13 | Motion: short, causal, once | Goodnight fade 600 ms (H12), 150 ms with reduced motion; sheets 180–220 ms | Adjusted |
| 14 | Say it once | House tab no longer repeats the lit rooms; the kiosk plan hides its own media; one Lock key per screen | Adjusted |
| 15 | Honest objects, drawn flat | The plan says "Sample layout" or "Drawn by Isaac", shows only real openings, and shows tiles before it's drawn | Adjusted (H17) |

**Within a second, someone from another app recognises:**
- the windows (dark at night, grooves by day);
- the type pair;
- On / Off / Offline under every name;
- one orange key or none;
- the red key for the door at night.

**Jam Home's own:**
- the plan and its setup;
- the day arc;
- the dimmer and outlet plates;
- the sideboard;
- the key rail;
- the room tabs;
- Goodnight;
- the night face;
- Jam Braun's warm white and anthracite.

## Conflicts assumed (all "assumed, pending Isaac")
| # | Recommendation adopted | Applied here |
|---|---|---|
| 1 | Warn = round amber light + printed ▲ + word | Kitchen window everywhere (plan line, doors list, Goodnight); the day door |
| 2 | Rows stop at a visible end | No carousels in HA; the source grid and the shelf stop |
| 3 | Windows by ground: on light grounds a hairline groove (lit = colour in a dark rim); on dark objects a recess | Day plates, keys, tabs and lamp shades use the groove; night, the TV screen, grilles and the radio keep the recess |
| 4 | Title cards: shared rule, own cover | Not applicable (no TV title card in HA) |
| 5 | Day Play dims first | Not applicable |
| 6 | Round = status only; slot = "current"; position by slot or print | Playing and setup step are slots. "Here" is a printed pin (no light). |
| 7 | Ribs on any dark surface, never behind scrolling rows | Ribs only inside the drawn TV screen |
| 8 | Accents optional | None in Jam Home |
| 9 | The device's owner (HA) owns its drawing | The house objects sheet (section 5), with TV variants for Lobby |
| 10 | Guide band: shared behaviour | Not applicable |
| 11 | Menus not beside keys | No menus beside lists; sheets rise from the bottom (phone) or inset (kiosk) |
| 12 | Unlocked door: warn by day, alert after sunset or nobody home | `doorSev()`: Day frames (Isaac and Marissa home) = warn; Night = alert |

## Holes applied
| Hole | How |
|---|---|
| H2 Objects as UI | Plates, sideboard, radio, key rail: flat, one realism level, no real product's look |
| H3 Object-shaped windows | Lamp shade, door swing, window glyph and plug glyph behave exactly like windows: groove/recess off, flat fill on. TV variant rims an unlit shade so it stays visible. |
| H4 Time-of-day grounds | The day arc is not a ground. Driven by `sun.sun`; static between minute ticks |
| H5 Status boards | The plan has fixed positions, all dark = fine. A lit room links to its sheet and never toggles; the Car port opens its light popup. Capacity is stated below. |
| H7 Timelines | Arc: the past dims; the now is the sun/moon + a hairline. Cream NOW isn't used on the day ground (1.1:1); see "Rules I broke" |
| H8 Plans | A labelled sample in the mockup, tiles before setup, and "Drawn by Isaac" after. Only room-level targets. The area fill is the plan's alone. |
| H9 Light from top-left | Plate shadow `1px 2px 8px` (was straight down). One soft shadow kind. |
| H10 Idle faces | Night face: household content only, nothing starts by itself, a minute tick, a touch wakes it and isn't passed on. HA's 11 pm screen-off stays. |
| H11 Content colour | Lamp colours clamped into L 0.84–0.90 at night (0.89–0.93 by day), orange distance ≥ 0.15 (measured 0.17–0.24). Ink chosen by contrast (dark ink on all fills). |
| H12 Signature moments | Goodnight: rooms fade out once, 600 ms, 150 ms reduced. Never on focus. |
| H15 People | Printed colour tag + name; tag initials ≥ 12 px (13 / 18.8 / 18.2); home or away only, no location |
| H16 Capacity | • Plan: 8 × 7 squares, ≤ 10 zones (more: busiest floor + tiles).<br>• Bar group: 10, then "+n".<br>• Key rail: 5 hooks.<br>• Power strip: 5 + "Free".<br>• Room tabs: House + 4 rooms (a 5th room is reached through the House plan).<br>• Sideboard: 3 objects.<br>• Kiosk Goodnight: 7 rows (9 lamp zones would need grouping). |
| H17 Real-world claims | Plan tag; openings only from locks/sensors; "ends 11:02" from the media's duration; the arc from `sun.sun` |
| H18 Names | "Room strip" → "room tabs". Kept: sideboard, radio, key rail, lit plan, day arc, Goodnight round, night face. None clash with the glossary candidates (console, running order, marquee, patch bay). |

H1, H6, H13 and H14 don't touch Jam Home.

## Rules I broke
| # | Rule (source) | What I did instead | Why Jam Home needed it | Verdict |
|---|---|---|---|---|
| 1 | H8 "only from the real layout … never invented" | The mockup still shows a sample layout, tagged "Sample layout" | Isaac has to see the idea before he draws. The product shows tiles until a plan exists. | **App-local**: mockups may use a labelled sample; products never ship one |
| 2 | IN3 "lit = flat solid colour" (one colour per window) | Room-tab windows have two panes with two lamp colours; plan rooms split into up to 3 bands | One room, several lamps; showing only the brightest hid the pink fairy lights (audit #6) | **App-local** (multi-pane windows for things with several sources; each pane flat) |
| 3 | TV14 glare advice for kiosks (< 10 % of screen above L 0.5 at rest) | The night home plan covers **21.7 %** (iPad) and **19.1 %** (Echo) at L ≥ 0.84 | The other way to stay under 10 % is lit rooms darker than L 0.5, which is the brown pass 4 had | **Device: kiosk** needs its own glare rule: home screens may exceed 10 % when the backlight is dimmed by automation; idle faces stay < 10 % (measured 8.7 %) |
| 4 | H7 "NOW is a cream rule" | The arc's now is the sun/moon itself + a dotted dim hairline | Cream on the day ground is 1.1:1 | **Language, amended**: "NOW is marked at the thing; cream where the ground is dark" |
| 5 | CL4 "cream is the light" / IN4 shapes | "Here" is a printed walnut pin (a position) | Conflict 6 bars round lights for position; a printed marker isn't a light | **Language**: printed markers may show position; lit windows may not |
| 6 | LY2 "every place visible, ≤ 5 tabs" | A 5th room has no tab; it's reached through the House plan | Tabs carry state windows, and 5 is the phone's limit | **Language holds** if the plan counts as "visible". Note it in LY2. |
| 7 | SM1 Jam Braun night ground `#1c1c1a` | Night face ground `#121211` | An idle face at night should be the darkest thing in the room | **App-local** |
| 8 | CL5 order (alert → offline → warn → routine) | Followed, but the warn door takes the orange from a playing Pause by day | That's the order working as written. Flagged because a film-night Pause losing its orange to the door could surprise people. | **Language** (keep) |

## Audit
Checked with Playwright: Chromium, `chromium.launch()` with no options, screenshots in the session scratch dir (not the repo).
- **Viewports:** 1440 (light) and 390 (dark scheme).
- **Opened:**
  - on all four kiosks: every room sheet, the Outside light, the light, offline and action popups;
  - on the iPads: Sideboard, TV/source, remote, PC, and speaker + Group;
  - on the Echos: radio + Group;
  - the night faces;
  - door unlocked;
  - Plan "not drawn" (tiles);
  - phone popups: light, TV, speaker, PC, remote, Goodnight;
  - the setup flow through all five states (one corner pair, one wall change, Save);
  - Goodnight run on the night iPad, and a fader drag.

**Results (after one fix pass):**
- **No JS errors.** No horizontal scroll at 1440 or 390, and none inside phones, sheets or the setup body.
- **Kiosks:** 0 elements clipped or outside the screen. Nothing under 18 px on kiosk homes and faces, SVG text included (computed through the scale). Nothing under 15 px in kiosk sheets (remote engraving excepted, as in pass 4). Nothing under 12 px anywhere on the page.
- **Phone sliders:** smallest side 48 px.
- **Key tags:** 13.0 / 18.8 / 18.2 px.

**The fix pass corrected:**
- arc text at 17.8 px on the iPad (the viewBox was wider than the box);
- TV source "Input/App" and the TV screen's state word at 13–14 px in kiosk sheets (now 15);
- a 148 px page overflow at 390 (the objects table and rollout table had no `min-width:0`);
- a 20 px phone overflow at night (the sideboard's min-content);
- two orange Lock keys on the phone House tab;
- arc labels drawn over the dotted arc;
- TV lamps not lighting in the objects sheet;
- the night face plan above 10 % glare (narrowed to 340 / 290 px).

| # | Problem | Severity |
|---|---|---|
| 1 | **Night glare vs the brown fix.** Lit rooms at L ≥ 0.84 cover ~20 % of the kiosk at night (21.7 % iPad, 19.1 % Echo), double the TV glare cap that kiosks take as advice. The night face is 8.7 %. Needs a look at the real iPad with HA's night backlight. | Medium |
| 2 | **Bands can read as geography.** A Living room half cream, half blue might read as "the left half is lit". It's flat and capped at 3, but nothing says "these are lamps, not areas" except the bar group. | Medium |
| 3 | **The plan still isn't the house.** The setup flow is mocked: no storage and no HA areas API. Until Isaac draws it, the product would show tiles. | Medium |
| 4 | **Goodnight capacity.** The kiosk sheet fits 7 rows without scrolling. A night with every zone lit plus TV and purifier (9 rows) needs grouping ("Bedrooms · 2 rooms"), which isn't drawn. Defaults are still my assumption. | Medium |
| 5 | **Paddle legends still need a hallway test.** ON/OFF are printed at 12 px on phones; "pressed half = state" is real-world logic, but untested with the family. | Medium |
| 6 | **New HA work, not a theme.** Five new cards (sideboard, plan, setup editor, room tabs, Goodnight sheet) plus a script; see the rollout table. The room tabs bring back a custom tab card. | Medium |
| 7 | **Setup openings use keys** (room → wall → position), not tapping a wall. It's slower but stays above 44 px. Doors always open inward; the hinge side isn't chosen. | Low |
| 8 | **Car port lives in two places:** HA's Kitchen area (the kitchen sheet lists it) and the plan's outside row. Needs a sentence in the kitchen sheet, or an HA area change (Isaac's call). | Low |
| 9 | **Day windows as grooves** (conflict 3) change every scene key and tab by day. A lit cream square on a light key now reads only through its dark rim. Fine at 1:1 here; check on the real iPad. | Low |
| 10 | **TV variants are untested on a TV.** 64 px glyphs and the 6 px lift are guesses for Lobby's house plate; the labels must be 26 px there (shown at 13 px in the sheet). | Low |
| 11 | **Echo cost:** up to 3 band rects per room, ~45 SVG nodes, one 600 ms opacity fade. Unmeasured on WebView 139. | Low |
| 12 | **The sun lost its Braun yellow.** The ET66 yellow is a Jam Braun pack constant Isaac's look uses elsewhere; on the arc it's now ink. | Low |
| 13 | **Plan labels stay 18–22 px** on kiosks; from 3 m the plan reads by colour and shape (pass-4 #12, unchanged). | Low |
| 14 | **Library popups are phone-size only** (pass-4 #15, unchanged). | Low |

**Pass-4 audit status:**
| Pass-4 # | Status |
|---|---|
| 1 (High) | Fixed: labelled sample, tiles, setup |
| 2 | Listed in the rollout table |
| 3 | Fixed |
| 4 | Fixed |
| 5 | Fixed (outside row) |
| 6 | Fixed (bands + clamp) |
| 7 | Fixed |
| 8 | Fixed |
| 9 | Partly: legends added, test pending |
| 10 | Partly: explicit defaults and the film case, Isaac to confirm |
| 11 | Fixed |
| 12 | Unchanged (accepted) |
| 13 | Open |
| 14 | Fixed |
| 15 | Open |

## Questions for Isaac
1. **Will you draw the house** in the four-step setup (or send a rough sketch: room names and positions, no address)?
   *Recommendation:* yes. Until then the kiosks show room tiles, never the sample.
2. **Night brightness:** lit rooms are drawn light (never brown) and cover about 20 % of the kiosk at night. OK with HA's night backlight?
   *Recommendation:* yes for the home screen. Keep the night face under 10 %.
3. **Rooms with two lamp colours as flat bands** (up to three), or one colour plus the bar group?
   *Recommendation:* bands. They're what fixed Marissa's room.
4. **Unlocked door: amber by day while someone's home, red after sunset or when nobody's home** (conflict 12)?
   *Recommendation:* yes, using HA's sun and presence.
5. **Goodnight defaults:**
   - shared rooms and the car port off;
   - bedrooms left on;
   - TV left on while it plays;
   - purifier to 25 %;
   - the door always locks;
   - windows a reminder.

   *Recommendation:* yes. Please name anything else that should always go off (porch, Tree).
6. **Night face from 9 to 11 pm** instead of the Clock/Photos screensaver in the evening?
   *Recommendation:* yes; Clock/Photos stay for the day.
7. **Sun as an ink ring with rays** (no yellow)?
   *Recommendation:* yes. It can't be mistaken for warn, and it matches the moon.
8. **A hallway test of the ON/OFF paddle** with Amber and Marissa on the iPad before the rollout?
   *Recommendation:* yes. If either reads it backwards, fall back to pass 3's paddle window.
