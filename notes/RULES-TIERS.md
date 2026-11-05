# Rules sorted into tiers (after pass 4)

> **A proposal. Nothing here is approved, and BIBLE.md, CHANGES.md and decisions.md are unchanged.** It sorts every rule in BIBLE.md (draft 0.5) and every live item in CHANGES.md (A, B, D1–D179) into tiers, using what the six pass-4 designs kept and broke.

Isaac's direction (decisions.md, last entry): *"Everything should feel like it has the same design language, not necessarily the same design. … A lot of our rules will be broken which means they probably shouldn't be global rules, this is an opportunity to discover holes, and issues."*

**Tiers**
- **Language**: every app, every device. This is what makes moving between apps feel natural. "(floor)" marks a hard limit.
- **Device: TV / kiosk / phone / desktop**: every app on that kind of screen.
- **App-local**: one app's design choice. Other apps don't copy it without a stated reason.
- **Drop**: no longer a rule anywhere (the idea may survive inside one app).

**Evidence codes.** L = TV launcher (Lobby), CS = Callsheet, JF = JamFin, JD = Jam-Dash, NV = NervOS, HA = Jam Home (Jam Theme + Jam Cards). "L3" is row 3 of the "Rules I broke" table in `notes/pass4-tv-launcher.md` (Jam-Dash's rows are unnumbered; JD1–JD12 counts them in order). "6/6" means all six pass-4 designs kept it.

**Sources read:** BIBLE.md, CHANGES.md, decisions.md, notes/REVIEW.md, notes/OVERNIGHT-BRIEF.md, all six `notes/pass4-*.md`, and the six `mockups/pass4/*.html` (checked for fonts, shared colour values, curves, ribs and shutters).

## What pass 4 says, in short
1. **The language held, and the template broke.** All six designs keep the type pair, the indicator windows, the state words, the orange budget, the red alert key, cream focus and walnut. All six replaced the shared alu ground, the card stack and the black top band.
2. **No pass-4 TV app uses the approved shutter title card.** Lobby drew a blind, JamFin house lights, NervOS the media dropping into a slot. Each note assumed the other two would keep the shutter. What survived in all three is the slatted bar showing the real load and the max(load, floor) hold (conflict 4).
3. **Accents are optional in practice.** Four of six apps dropped them (L4, CS3, JD5, HA10).
4. **Shapes are drifting.** Round windows now mean position in two places (JF seats, NV attract lights), and the slot has quietly come to mean "current", not just "running" (conflict 6).
5. **The same house objects are drawn two ways.** Lobby's lamp paddles and thumb-turn vs HA's dimmer plate and door swing (conflict 9). The bible needs "shared objects have one owner".
6. **Holes:** rotated text, objects as UI, object-shaped windows, time-of-day grounds, status boards, reading surfaces, timelines, plans, shadows, idle faces, content-derived colour, and a glossary (four apps used "console", two used "running order" and two used "marquee" for different things).

---

## 1. The language in one page

What every app shares, so moving between them feels natural. Everything else (grounds, surfaces, layout, card shapes, chrome, signature objects) belongs to the app.

| # | The language | Held up in pass 4 |
|---|---|---|
| 1 | **Two typefaces.** Jost for words, IBM Plex Mono for labels, times and numbers. No serifs. | 6/6. Every mockup loads exactly these two. CS leans on them hardest (a sheet with no cards). |
| 2 | **Indicator windows.** Small, always-visible windows. Unlit is a visible recess, and lit is flat colour. They never glow, never grow and never pass their object's edge. | 6/6: empty sockets (L), unlit slats and empty save frames (NV, JF), the all-dark annunciator (JD), the lamp-shade window (HA), the NOW slot (CS). |
| 3 | **Window shapes have meanings.** Round = status, square = chosen, slot = current/running, bar group = count. An object may be its own window. | 6/6 for round and square. The slot's meaning drifted and JF uses round for position (conflict 6). HA adds object-shaped windows (H3). |
| 4 | **Cream is the house light.** Lit, focused, running and "here" are warm cream. | 6/6. The cream token appears in all six sources. |
| 5 | **State is colour + shape + word, never colour alone.** ok green, warn amber + ▲, alert red, offline a broken (dashed) form. Shared state words, each app's short words, and quiet past forms ("Seen 06:20", "Fixed 01:53"). | 6/6. Past forms in CS and JD. Broken offline form in JF, JD, NV, HA and CS. |
| 6 | **Red means alert.** The fix is a solid red key with dark text, and nothing else on that screen is orange. | 4/4 apps that drew an alert (L thumb-turn, CS cue, JD tag, HA Lock). JF and NV drew no alert. |
| 7 | **Orange is the one thing to do now.** At most one per screen. A sheet counts as its own screen and hides the page's orange. Calm, overview and reading screens have none. Orange moves on to the next step. | 6/6 counted. HA measured 0 at rest. CS moves Copy → Done. JD has none in Trouble (the red key is the loud thing). L, JF and NV homes have none. |
| 8 | **Focus is a light at the thing, plus a small lift.** The colour snaps and only transform moves. The light takes the element's shape. | L plaque, needle and socket ring; JF window under the art; NV base window under the spine; CS and JD lit slot in the nav. HA tabs press in instead (HA6). |
| 9 | **Chosen things press in.** They don't change colour; a square window shows the choice if needed. | HA scenes, JF season keys, CS square windows, JD 2 px keys, NV Favourite. |
| 10 | **Walnut is the house wood.** One colour, never grain. It marks ends, joins and furniture; its shape is the app's. | 6/6: L sill and dial stops, CS Wrap rule, JF marquee frame and fold, JD cabinet cheeks and bench lip, NV shelves and bookends, HA key rail and cabinet top. |
| 11 | **Things end visibly.** Rows stop at a visible end, position is shown, long lists have a jump, and "done" is designed. | L end mark and dial stops, JF end mark + All card, NV bookends + dividers, CS "End of day" + Wrap, HA "Goodnight · done". |
| 12 | **Calm is the resting state.** With nothing to do, a screen has no orange, no moving accent and nothing looping. "All fine" looks like nothing. | JD all-dark board, HA 0 orange at rest, L and NV homes with no orange, CS Wrap, JF Home. |
| 13 | **Motion is short, causal, and happens once.** glide / decelerate / settle / leave, transform and opacity, then rest. Calm means the same on every screen. | 6/6 use the decelerate curve. L, JF, JD and NV have a Calm switch; CS honours reduced motion; HA kiosks are one-shot. |
| 14 | **Say it once, in plain words.** No value twice on a screen. Complete button wording. Every failure says what happened and ends with Try again + a way home. | L "menu open ▼", JF sign vs caption, NV port count, HA plan hides the kiosk's own media slot, CS roster numbering as the count. Failure endings in L, JF, JD, NV. |
| 15 | **Honest objects, drawn flat.** Each app draws the real thing its job already has, from Isaac's influences, without material texture (no grain, glow, brushed metal or paper). | 6/6 found one: furniture (L), a call sheet (CS), a cinema (JF), a rack (JD), a console and shelves (NV), a house plan and wall plates (HA). |

Underneath all of this sit the **floors** (contrast, text minimums, targets, flash and glare, Calm, bundled fonts). They are in the table below as Language (floor) or Device (floor).

---

## 2. Tier table

Each rule is reworded to the scope it should have. Sources are in Notes. A D-number index at the end shows where every D-item went.

### Colour and light

| # | Rule | Tier | Evidence | Notes |
|---|---|---|---|---|
| CL1 | Colour is for state and selection; idle chrome stays neutral. Content, and drawn stand-ins for content (covers, spines, media faces), are exempt. | Language | 6/6 kept it for chrome. NV4 broke it for spines → clarified. | §3 colour discipline; B1 (room colours retired). |
| CL2 | Red = alert only. One named exception: the IR transmit flash. | Language | 6/6. Dropping banners took L's saturated red to 0.0%. | §3; D5 (category dots never red); A9. |
| CL3 | Signal colours (ok, warn, alert, info) have separate lamp and ink tones. Values are tokens. | Language | 6/6 use the brief's values. | §3.6 still lists pre-correction values; D38. |
| CL4 | Cream is the light: lit windows, focus, running, "here". Orange is not an indicator colour. | Language | 6/6. | A3. |
| CL5 | Orange is the one action to take now. At most one per screen. A sheet is its own screen and hides the page's orange. None on calm, overview, reading or settings screens. Order: alert → offline → warn within 60 min → routine. It moves to the next step. | Language | 6/6 counted (HA's table). CS moves Copy → Done. HA5 merged the overview rule. | §2 orange row; A4; D7, D23, D39, D64, D82, D95, D97, D129, D137, D139. "One per card" (A4, D39) is dropped. Idle Play is orange only inside a media home (D129). |
| CL6 | The control that fixes an alert is a solid red key with dark text; nothing else on the screen is orange while it shows. | Language | L, CS, JD and HA drew it. JF and NV had no alert. | D42, D84, D119, D138 (a ringed LED beside it is optional). |
| CL7 | Decorative colour stays darker than control orange. | Language | Not re-tested (NV puts Colour bars on its console). | §2 accents; D10 still open (Colour bars' light oranges). |
| CL8 | Paddles are never orange. On = up, plus a light in the device's colour. | Language (colour); App-local (where the light sits) | L kept the D130 paddle window. HA3 moved the light into the lamp shade. | Reverses A4 per D74, D83, D130. See conflict 9. |
| CL9 | Lamp colours are drawn as display colours: whites on an amber-to-cream line, colours near orange drawn lighter. | Language (wherever a lamp's colour shows) | HA; L paddle windows. | D132. |
| CL10 | A lamp's colour lives in its window and fader fill, never in a card tint. | App-local (HA, L) | HA9: the plan fills rooms (plan only). HA drops the fader Band. | B1, B3, D45. **Drop** D85 and D133 (Band). |
| CL11 | Every app has Day and Night, following the device. Grounds follow the light; objects may keep their own colour. How each app does it is its own. | Language (has both); App-local (how) | L5 sky by time of day; JD6 dark cabinet in Day; NV's deck stays black; JF lighting per profile. | §2 light and dark. |
| CL12 | TV defaults to dark, with a mid-light Day option (never paper-white). | Device: TV | JF and NV kept it. L replaced it with the sky plus "Always night". | Isaac's JamFin answers. |
| CL13 | Printed colour codes identify things and people. Never lit, never a state, never orange. | Language | L14 (socket fills), HA11 (people's key tags). | D89; extends D34. |
| CL14 | Contrast is WCAG AA, including secondary text, with a deeper step for text on colour. Focused labels never fall below AA. Peeks aren't readable content. | Language (floor) | 6/6 measured. NV9: dimmed neighbour shelves at 50% need the peek exemption. | §9; D115. |
| CL15 | Real app banners: a 6 px frame, toned at night, never brighter on focus. | App-local (only where banners are shown) | L2 dropped banners. | D122. |

### Indicators

| # | Rule | Tier | Evidence | Notes |
|---|---|---|---|---|
| IN1 | Lights are indicators. A control may carry only a slider's revealed fill, its device's lit power glyph, or its target's state window. A lit indicator may link to its cause, but it never toggles. | Language (amended) | JD1 (legends as links); HA7 (tab windows). 6/6 have no glowing controls. | §3.1–2; the lit-glyph rule (decisions). |
| IN2 | Every light sits in an always-visible window. Unlit is visible. A window never grows and never passes its object's edge. | Language | 6/6. | §3.3–4. |
| IN3 | Lit = flat solid colour. No halo, bloom or hot spot. | Language | 6/6. | A2, A6, A9. JF keeps a baked focus spill (TV2). |
| IN4 | Four generic shapes: round = status, square = chosen mode, slot = current/running, bar group = count. | Language | 6/6 use round and square alike. Slot now also means "current" (CS NOW, L plaques, nav slots). JF4: round = position. | §3 shapes; D28. See conflict 6. |
| IN5 | Object-shaped windows (lamp shade, door swing, socket, IR window, power glyph) are allowed if they behave exactly like windows. | Language (new) | HA4; L sockets; HA remote. | Hole H3. |
| IN6 | Legend window: a word inside a lit rectangle on a fixed board. | Device: desktop, kiosk | JD3. | Not a fifth status shape for rows. Hole H5. |
| IN7 | Warn means "needs a look, not urgent": amber + ▲ + word. | Language (meaning). The shape is conflict 1. | CS7 moved to D158; JD kept D158. | D21, D92, D142, D158. |
| IN8 | Indicator windows in Day. | Conflict 3 | CS11, JD12, JF (D173 everywhere). | D17, D121, D131, D173. |
| IN9 | Bar group: one recess, at most 10 segments, overflow number inside; nearby text never repeats it. Use it only where nothing else counts. | Language (form); optional use | CS5 (the list's numbering counts). HA uses one bar group per room. | D6, D68, D141. |
| IN10 | Meters are read-only: quiet face, lit scale, ladder; one LED per notch. | App-local (HA gauges and appliances) | No pass-4 app drew one. JD shows numbers in a display window. | §5. Keep the needle's top-left light direction (H9). |
| IN11 | Numeric readouts sit in a dark window, with cream digits (not orange). | Language (form) | JD head unit; HA appliances. | The R7 decision said orange digits, which clashes with A4. |
| IN12 | Seven-segment (DSEG) only on appliance-style objects. | App-local (HA appliances) | Only HA used it in pass 4. No title card used it. | §2 type, §5 lit scale, A5, D49. |
| IN13 | A seen alert is an unlit window + "Seen hh:mm". A fixed one is "Fixed hh:mm". | Language | CS "Seen 06:20"; JD grey "Fixed 01:53" tag. | D11, D69, D159. |
| IN14 | A decorative motif may carry one indicator (the grille's dot). | Language (permission) | HA grille; NV machine light. | D50. |
| IN15 | Light arrives by being revealed, once: a window fills or a shutter slides back. Flat. | Language (character) | CS Wrap rule draws in once; JD bench fill; the slatted bar in L, JF, NV. | §3 signature move; A6 (hot spot dropped). |
| IN16 | Glows and soft shadows are pre-rendered sprites, faded by opacity. | Device: TV (perf) | JF's baked spill is the only glow left. | §3. Mostly moot after A2. |
| IN17 | Tuning scale (a day timeline with a needle). | Drop | CS6 replaced it with the running order and day strip. | D8. |
| IN18 | History graph as a chart recorder. | App-local (HA); likely Drop | Not drawn in pass 4. | B7. Probably too skeuomorphic after A1. |

### Controls

| # | Rule | Tier | Evidence | Notes |
|---|---|---|---|---|
| CT1 | A rocker or paddle is on when up (or top pressed). The state is also written. | Language | L wall paddles; HA dimmer plate. | §4. The night graphite paddle is App-local. |
| CT2 | Keys press in about 2 px. One orange primary; secondary keys are neutral. Bevels are the app's choice. | Language | JD 2 px keys; HA; NV. | §4 buttons. "Raised and bevelled" → App-local. |
| CT3 | Chosen keys press in instead of changing colour. | Language | HA, JF, CS, NV. | A4. |
| CT4 | Sliders reveal cream (or the thing's own colour) up to a cap. The number lives on the cap, never beside it. On kiosks, faders are vertical columns. | Language; columns are Device: kiosk | HA kept it (tall columns in kiosk sheets). | §4; A4; D40, D86. HA's phone dimmer is 36 px wide, under 44 (HA audit 3). |
| CT5 | No rotary inputs. Arcs and dials are read-only. A drawing of a real object may rotate to show state. | Language (reworded) | L9 thumb-turn. L's app dial is linear. | §4. |
| CT6 | Never the same value twice on one screen. A panel means a screen. An open layer carries the value (its key shows ▲). A meter's own readout counts once. A timeline isn't a repeat. A summary may count what a foldable list below it names. | Language | 6/6 (L "menu open ▼", NV ports, HA plan, CS roster). Refined by JD9 and JD10. HA audit 4 shows the lit rooms twice. | B2; D15, D25, D33, D41, D56, D76, D80, D105, D140, D176. |
| CT7 | Destructive actions are never orange or red: a dark key in a confirm sheet that names the consequence. Data loss is opt-in. Enter never fires it. | Language | Not redrawn in pass 4. | D24, D70, D98, D153. |
| CT8 | Never hold-only. Every hold has a press-twice path (3 s, with a draining slot). Holds fill the edge opposite focus. | Language; timings are Device: TV | L thumb-turn; NV Quit. | D31, D58, D111, D125, D149, D174. |
| CT9 | A job shows its progress in place, on the thing that started it. | Language | JD's module mirrors the bench. | D29. |
| CT10 | Forms check as you type, and Save says what it costs. Secrets are typed only by the person and never shown back. | Language | Not redrawn. | D165, D167. |
| CT11 | No control restyles another. | Language | HA. | D135. |
| CT12 | One sheet form per device: a bottom sheet on the phone, an inset with no scroll on the kiosk, centred on desktop. Close sits top right. No Done when changes apply live. | Device: phone, kiosk, desktop | HA kept it. | D43, D44, D134. |
| CT13 | Targets are 44 px on touch. On TV, focus is visible from the sofa. | Language (floor) | JD all ≥ 44 px. HA's phone dimmer fails. | §9. |
| CT14 | Key hints are printed on keys, small on quiet keys. Shortcuts are single letters, and `?` opens the key sheet. | Device: desktop | CS12 refined it. | D9, D147. |
| CT15 | HA built-ins are themed only through verified HA keys, with no card-mod. | App-local (HA) | — | D48, D88, D136. |
| CT16 | The remote: soft plastic, red IR flash, lit power glyphs. | App-local (HA) | Kept. | A9. |
| CT17 | Pop-up specifics: white presets show their colour, speaker Group or split, the source tile grid. | App-local (HA) | Kept. | B3, B4, B5. |

### Type

| # | Rule | Tier | Evidence | Notes |
|---|---|---|---|---|
| TY1 | Jost for words, IBM Plex Mono for labels and numbers. No serifs. | Language | 6/6. | §2 Type. |
| TY2 | Text minimums: desk and phone 15 / 13 / 12; kiosk home 18, kiosk sheets 15; TV body 26, minimum 22, hints 24. | Language (floor); values per device | 6/6 measured. | §9; D4. |
| TY3 | Uppercase labels are 13 px with 0.16em tracking. | Language (desktop, phone) | CS kept it. | D30 (settles §2's 12 px). |
| TY4 | Caps titles only at display sizes (≥ 48 px TV, ≥ 24 px phone). | Language (new) | JF12; NV launch title. | — |
| TY5 | Names wrap; they never get an ellipsis. Use short names where space is fixed. | Language | NV spines in two columns; JF posters wrap. L audit 5: plaques fit about 22 characters. | D163. |
| TY6 | Paper texture on headlines. | Drop | Unused. | §2 Texture; A1. |
| TY7 | A reading surface gets a lede size between the headline and the body. | App-local (CS); see H6 | CS8. | — |
| TY8 | HA kiosk sizes (clock 168 / 124, title 22, body 18). | App-local (HA) | HA13 uses 116 on the Echo. | D51. |
| TY9 | Fonts are OFL, bundled, with no CDNs. | Language (floor) | Products bundle them; mockups use Google Fonts. | §9. |
| TY10 | Text is horizontal. Rotated text only on drawn spines. | Device: TV | NV5. | Hole H1. |

### Surfaces and materials

| # | Rule | Tier | Evidence | Notes |
|---|---|---|---|---|
| SM1 | Shared colour roles: ground, raised, rule, ink, dim, band, recess, cream, orange, walnut, signals. Each app sets the values. | Language (roles); App-local (values) | All six broke the alu: CS sheet, JD machine grey, NV wall, HA Braun page, L sky + lacquer, JF plain ground. | §2 Materials; A10; D38. |
| SM2 | Depth is shallow: one raised tone, a soft shadow or a hairline, and pressed-in for chosen. No required three-layer stack. | Language | CS has no cards at all. L and JD use hard offset shadows (H9). | §2 Depth. |
| SM3 | Nothing is more realistic than its neighbours. | Language | JD2's pulled module is an App-local exception. | §3.5. |
| SM4 | No grain, paper, brushed metal or glow. | Language | 6/6. | A1, A2. §2 "Texture (Rich)" → Drop. |
| SM5 | Ribs are fine 1 px lines on dark surfaces. Where they're allowed is conflict 7. | Language (texture) | L6, JF2, HA2, CS2. | §2; A1; D99, D162. |
| SM6 | The black ribbed band as a signature surface. | Device: TV (Guide and player bands); App-local elsewhere (JD tape) | CS2 and HA2 dropped it; L and NV have no top band. | §2 band row. |
| SM7 | Night band values (`#070706`, 14% ribs every 5 px, edge, highlight). | App-local (JD); TV band token | — | D99, D162. |
| SM8 | Walnut is a colour with no grain. Its shape and placement are the app's. "An 8 px trim at the top" is dropped. | Language (colour); App-local (shape) | JF8, NV3, HA12, L10. | §2. |
| SM9 | Soft corners and calm cards (Jam Braun). | App-local (HA) | JD4 uses square fronts; CS has no cards. | A10; the brief. |
| SM10 | Draw the real object the job already has (appliances, media devices), flat, at one realism level. | Language (character) | 6/6. | D49; "media cards as devices" (decisions). Hole H2. |
| SM11 | The retro dose follows purpose: quiet on work tools, louder on play surfaces. | Language | NV is toy-like, CS typographic, JD equipment-like. | decisions R1. |
| SM12 | Kiosk dock as a black ribbed band, or as card blocks by day. | Drop | HA8 replaced it with the plan. | D47, D87. |
| SM13 | Hi-Fi is the default house look. Shared screens show the house look; personal devices show their person's look. JamFin profiles are the exception. | Language (policy) | JF11. | §1; A10 (rename to "Braun Hi-Fi"?); D20, D113, D179. |
| SM14 | Post layers are user-chosen, never over art or video, and off in Hi-Fi. | Language (look policy) | Unused. | §8. |
| SM15 | Saved palettes (Horizon, Mission). | App-local when used | CS's night sheet uses the Mission navy. | §2. |

### Layout

| # | Rule | Tier | Evidence | Notes |
|---|---|---|---|---|
| LY1 | Accents: at most one per screen. Never on or behind a control, a title or navigation. One thing in the clear zone at a time. It steps back on trouble and overlays. Whether an app has one, and where, is the app's call. | Language (limits); App-local (use and place) | 4/6 have none (L4, CS3, JD5, HA10). JF7 puts it on the marquee and title cards; NV9 on the console. | §2 accents; D2, D19, D22, D62, D123. **Drop** D67 and D178/D109's cross-app placement. Conflict 8. |
| LY2 | Every place is visible: all of them on desktop, at most five phone tabs, never "More". | Language | JD lip, CS five places, JF five tabs, HA room strip. | D26, D73, D116. |
| LY3 | The current place has a lit slot. Tabs that carry state press in instead. | Language | CS, JD, JF slot; HA6 presses in. | D12, D46, D91. |
| LY4 | One way in per job per screen. | Language | L: the TV readout is the drawer's way in. | D118. |
| LY5 | The status summary is on the first screen. A board counts as one. | Language | JD11; CS shows row 01 on the first phone screen. | D160. |
| LY6 | Trouble is said once: the reason and fix live in one place, and the item keeps its own place with just the word. | Language | JD tag + pulled module. | D96. |
| LY7 | The cue order (one next action) is shared. A shared card form is not. | Language (order); Drop (card) | CS4, JD8. | D7, D23, D65, D137. |
| LY8 | Step mode: slot-window progress, at most one orange per step, a designed end. | Language (pattern) | JD bench; CS One at a time. | D66, D145. "A reading page is the steps expanded" → Drop (CS9). |
| LY9 | Voice mode. | App-local (CS) | Kept. | D144. |
| LY10 | Dashboards shrink in a published order, ending in Rows. | App-local (JD) | JD console ladder. | D94, D161. |
| LY11 | A phone overview with several servers starts with a server strip. | Drop | JD7. | D102. |
| LY12 | Kiosks never scroll, sheets included. | Device: kiosk (floor) | HA: 0 of 52 states clipped. | §9; D44, D134. |
| LY13 | Kiosk home = clock + facts + dock. | Drop (App-local) | HA8. | D47, D87. |
| LY14 | Kiosk glance size, attention surfaces, a phone monitoring row. | Drop (not adopted) | — | decisions. |
| LY15 | Edge grammar: row things light their bottom edge, column things their leading edge, holds fill the top edge. | Language | NV; L settings rows. | D71, D149. |
| LY16 | Notices never pop up. A change you can see in place gets no toast. | Language | L update light; HA paddles. | D126. |
| LY17 | No bells or unread counts. History lights what's open; finished items are unlit. | Language | CS "no badges"; JD. | D164. |
| LY18 | "Hide this kind of thing" scope and Undo on merges. | App-local (CS) | Kept. | D146. |
| LY19 | Show what's there; focus skips what you can't act on. | Language (new) | L12. | — |

### Motion

| # | Rule | Tier | Evidence | Notes |
|---|---|---|---|---|
| MO1 | One curve table: glide, decelerate, settle (overshoot ≤ 1.3), leave. | Language | 6/6 use decelerate. L's blind leaves on an off-table ease-in `(.5,0,.75,0)`; it should use `leave`. | §8 Curves. |
| MO2 | Stepped 12 fps, for decoration only. | App-local (looks that want it) | Unused in pass 4. | §8. |
| MO3 | Calm has one meaning everywhere. | Language | L, JF, JD, NV switches; CS reduced motion. | §8. Refine: an ambient change slower than a minute may stay a fade (L audit 10). |
| MO4 | Motion happens once and rests. Nothing loops on an active screen. | Language | CS, JD, HA. NV attract runs only when idle. | §8; decisions. |
| MO5 | Kiosk-safe tier: one-shot moves only. | Device: kiosk | HA. | §8. |
| MO6 | Desk gets more motion than phone. | Device: desktop, phone | JD's pulled module is desktop only. | decisions. |
| MO7 | Progress is drawn at its value, static. It animates once, only on the focused item, the timeline or a signature moment. | Language | JF cards; JD download. | §6. |
| MO8 | Shutter and hot spot progress. | Drop the hot spot; the flat fill stays | — | §6; A6. |
| MO9 | The slatted bar shows the real load on launch and title cards. | Language (wherever there is a load) | L, JF, NV. | decisions (title card). |
| MO10 | Live numbers step, they don't stream. Bars move only on a real change. | Language | JD download. | D100, D166. |
| MO11 | Text naming the focus updates at once. Pictures and dependent content wait 500 ms. ↓ / OK commit at once. | Device: TV | NV11; JF; L. | D55, D114, D169. |

### TV

| # | Rule | Tier | Evidence | Notes |
|---|---|---|---|---|
| TV1 | Focus: a flat cream light at the thing + a small lift drawn inside its layer. The focus rectangle never moves. ≤ 150 ms, a snap under key repeat; colour snaps. The focused orange key rises with its window lit. | Device: TV (timing); Language (form) | L3, JF3, NV. | §7; A7; D3, D18, D108. |
| TV2 | The W1 base window with a rib spill as the one selector shape. | App-local (shape) | L3 broke it; JF puts the window on the ground; NV kept it. | §7; A7; D107. Brightness 85 / 65% → App-local. |
| TV3 | TV cards: art, a focus light under it, a label, progress on the art's bottom edge (never the focus light's edge). A plinth is optional. | Device: TV (parts); App-local (plinth) | L1 frames; JF3 no plinth; NV spines. | D1, D13, D53, D107. |
| TV4 | A launch or title card is an opaque, full-bleed cover with the slatted bar showing the real load. Hold max(load, 600 ms) the first time and 300 ms after; 1.6 s only for milestones. B cancels. Calm is a ≤ 150 ms fade. | Device: TV. The cover's form is conflict 4; Day is conflict 5. | L7, JF5, NV8. | §2 title card; A8; D14, D36, D60, D104, D155, D171, D172. |
| TV5 | Guide band: at the bottom, opaque, with a header naming what's underneath, a state slot + word, at most one orange, and choosers that replace the key row. ≡ = options for what's focused. A second way in when another app owns Guide. | Device: TV (behaviour). The face is conflict 10. | NV12 kept it; L8 drew a drawer. | D35, D54, D77, D128 (feasibility), D148, D150, D152. |
| TV6 | One player band for JamFin and NervOS Theater. Prompts sit bottom right; OK on the timeline pauses. | Device: TV | JF, NV. | D112, D157, D168. |
| TV7 | Choosers pop above or below a band or key, hold five rows, then scroll with "n of N ▲▼". "Beside" is conflict 11. | Device: TV | L, JF. | D16, D57, D106, D177. |
| TV8 | Rows stop at a visible end with a nudge, and libraries end with an "All…" card. Carousels only for covers, screenshots and groups, with neighbours visible and position shown; never controls. Wrap is conflict 2. | Device: TV | L, JF, NV all stop. | §9 carousels; D32, D59, D75, D110, D120. |
| TV9 | Position is shown. Its form is conflict 6. | Device: TV | JF4 seats; L "4 of 10"; NV lip. | D59. |
| TV10 | Homes, launchers and focused cards: one title + one line. Detail pages and buttons keep complete words. | Device: TV | L sign, NV stand, JF marquee. | §9 words. |
| TV11 | A TV home names the focused item in one fixed place above the rows. It adds to what the card shows, never repeats it. | Device: TV (rule); App-local (form) | JF1 marquee, L sign, NV stand. | D109, D176. |
| TV12 | The focused item's name is readable horizontally at ≥ 46 px somewhere on screen. No empty ground taller than ~15%. | Device: TV | NV1; JF10; NV audit 5. | Replaces D79 (Drop). D175. |
| TV13 | Safe area 96 / 54 px, band text included. A peeking row isn't readable content. | Device: TV (floor) | All three TV apps checked. | D115. |
| TV14 | Flash and glare floors (§9, 1–7). A picture preview only after a 500 ms rest; Back reverts in one change. | Device: TV (floor); advice for kiosks | L measured 0–1.1% glare. JF's house lights sit at the 2/s limit. | §9; D55. |
| TV15 | Transform and opacity only, no blur, glows as sprites. Texture never behind scrolling rows; cached bitmaps. | Device: TV (floor) | All three TV apps. | §2, §3, §9. |
| TV16 | OK acts on release and presses what's lit. A prompt may take focus only if a mistaken press loses nothing (≤ 8 s). | Device: TV | L, JF. | D125, D168. |
| TV17 | The TV is always on one source. Home may show Apps as current, never an HDMI input it isn't on. Input words: Signal / No signal / Nothing plugged in. | Device: TV | L11. | D61 (replaced), D63, D117. |
| TV18 | Long rows have a jump; its form is the app's. | Device: TV | NV7 dividers; JF range keys. | D170. |
| TV19 | Hints name the last-used input's buttons, at 24 px. | Device: TV | NV, L. | D151; D4. |
| TV20 | Power opens a sheet with focus on Cancel; Sleep is one press. Boot ≤ 1.6 s. Settings and Power open without the cover. | Device: TV | Not redrawn. | D153, D155. |
| TV21 | TV keyboard: 12-unit grid, Done is the one orange. | Device: TV | Not redrawn. | D154. |
| TV22 | Save slots as four picture frames. | App-local (NV) | NV save strip. | D81. |
| TV23 | Profiles save look, lighting, covers, motion, Animate Back and sounds. | App-local (JF) | JF tickets. | D20, D113, D179. |
| TV24 | No suggested content on active screens. An empty Continue is a recess with one line. | Language | L first run. NV10's attract runs only when idle. | D127. |

### Content and words

| # | Rule | Tier | Evidence | Notes |
|---|---|---|---|---|
| CW1 | Plain, complete wording ("Resume from 1:12:04"). No jokes. | Language | 6/6. CS audit 6: "Sent 0" may read as one. | §9. |
| CW2 | Shared state words (on, off, offline, action, alert, + warn) in three lengths: shared label, short word (≤ 14 characters), sentence. Quiet past forms. | Language | 6/6. | §3 state words; D21, D93, D159. |
| CW3 | State is never colour alone: shape + word. | Language (floor) | 6/6. | §9. |
| CW4 | Generated text: ≤ 25 words on a front door, pinned to a source, never restating a value shown on the same screen. A snapshot sentence dims when a live cue says the same thing. | Language | CS footnotes; CS audit 3. | D72. |
| CW5 | No brand marks. Apps and systems are names, their media, or a neutral glyph; never initials. | Language | L2 names on the dial; NV media. | D34, D103. |
| CW6 | A count only counts what it names. | Language | HA plugs vs lights. | D90. |
| CW7 | Every failure says what happened and what to do, then Try again (orange) and a way home. Try again can fail, and then says what to check. | Language | L, JF, JD, NV. | D101, D124. |
| CW8 | Severity: something that fixed itself is warn (a rollback); an open window is amber. | Language | JD rollback; HA window. | D101; B6. The door is conflict 12. |
| CW9 | An app may keep its own section names if the current one shows a plain sub-label. | Language | NV section slide. | D37, D78, D156. |

### States

| # | Rule | Tier | Evidence | Notes |
|---|---|---|---|---|
| ST1 | Hooks: `data-state` on / off / offline / action, plus `data-alert` (and warn). | Language | HA, JD. | §3; D21. |
| ST2 | Offline is a broken (dashed or ringed) form with "last seen" and one Try again. Cached content stays readable and read-only actions still work. | Language | JF marquee, JD ghost modules, NV laptop, HA dashed plate, CS dashed bar. | §3; D27, D52, D143. |
| ST3 | Empty states: a visible recess, one line, at most one key. | Language | L first run; NV empty frames; HA "Free" socket. | D127. |
| ST4 | A whole server offline is drawn as ghost modules. | App-local (JD) | JD. | D27 (the form). |

---

## 3. Conflicts still open (Isaac chooses)

| # | Conflict | Options | Evidence | Recommendation |
|---|---|---|---|---|
| 1 | **Warn shape** | A. Amber triangle window (D142). B. Round amber light + printed ▲ + word (D158). | CS gave up its own triangle in pass 4 (CS7). Every app that drew warn now uses B. | **B, language-wide.** Allow JD's legend window to light amber + ▲ on boards (IN6). This closes REVIEW call #4. |
| 2 | **Row ends: wrap or stop** | A. Stop everywhere at a visible end (D59, D120). B. Group carousels wrap behind a "Start" marker (D75; Isaac approved NervOS's wrapping carousel on 2026-11-03). | All three TV apps stop in pass 4. NV's systems carousel became vertical shelves, at most 7 presses apart. | **A**, with a jump for long rows (TV18). Isaac has to re-confirm, because it reverses something he approved. |
| 3 | **Indicator windows in Day** | A. Shallow recess (D121, TV). B. Hairline groove when unlit; lit = full window in a dark rim (D173, JF and CS). C. Small windows stay dark; long tracks become a light groove (D131, HA and JD). | CS found dark unlit squares on a light sheet read as "checked" (CS11). JD found a groove can't hold a word (JD12). CS audit 1: lit cream on a light sheet is 1.1:1 and reads only through its rim. | **Decide by what the window sits on.** On a light ground: B. On a dark object or board, and for any window holding a word: a dark recess (C). Lit is always flat colour in a dark rim. Drop A. |
| 4 | **Title / launch card form** | A. One shared shutter (approved). B. A shared rule (opaque cover + slatted bar + timings + Calm), with each app drawing its own cover. | No pass-4 TV app kept the shutter: L blind, JF house lights + colour block, NV media into a slot. Each note assumed the others kept it. | **B.** Keep the shutter as the default cover for anything without its own (system apps, updates). Ask Isaac directly, since he chose the shutter. |
| 5 | **Day title card / Day Play** | A. Light, flat card in Day (D172). B. Dim to dark before the card, even in Day (JF6). | JF: two big changes, within 2 per second but at the limit (JF audit 3). | **B for Play**, if Lobby's measurement passes on the panel. Otherwise A. Either way, D172 stops being a cross-app rule. |
| 6 | **Round window: position or status** (and what a slot means) | A. Allow round = position as a named exception (JF seats, NV attract lights). B. Position uses slots (lit cream = here), and the slot is redefined as "current: the one now". C. Position in text only. | JF4 and JF audit 1 flag the clash. Slots already mean "current" in CS (NOW), L (plaques) and nav (D91), as well as "running". | **B.** It keeps round for status only and names what the slot already does. Seats become a row of slots. |
| 7 | **Ribs: where** | A. Only on fixed black bands (§2, A1). B. On any dark surface, including moving opaque covers and drawn screens (L blind, NV deck and vents, HA TV screen, JD tape). C. Also functional rails on light surfaces (JF's Day lightbox). | L6 drops "fixed"; JF2 drops "only black"; HA2 and CS2 keep them off home screens. | **B, language-wide**, plus the TV floor: never behind scrolling rows, always a cached bitmap. JF's light rails are an App-local exception only if Isaac likes them in Day. |
| 8 | **Accents: required or optional** | A. One per screen in every app (§2). B. At most one, optional; where it goes is the app's call. | 4/6 have none. JF and NV attach theirs to their hero objects. | **B.** Isaac picked three accents; they stay as the house set for apps that use one. |
| 9 | **The same house objects drawn twice** (lamp switch, front door) | A. Each app draws its own. B. The app that owns the device (HA) owns its drawing, and others reuse it. | L paddles keep the D130 paddle window, and L claims they are "the same objects the family taps on the kiosk", but HA pass 4 replaced them with the dimmer plate and lamp-shade window. L has a thumb-turn; HA has a door swing. | **B.** A shared object is the clearest "reason to be identical". Lobby's house plate uses HA's lamp glyph window and door symbol. The red Lock key is already shared. |
| 10 | **Guide band: one component or one behaviour** | A. One component with an identical face on every TV app (D148, NV12). B. Shared behaviour and key order; the face follows the launcher (L8's console drawer). | Lobby (Hisense) and NervOS (Aero) are separate machines, so their bands never share a screen. JamFin runs under Lobby. | **B**, with the same key order, header and chooser rules. Lobby's drawer is the band on the Hisense; NervOS's ribbed band is the band on the Aero. |
| 11 | **Menus beside a vertical list** | A. Beside is allowed from a vertical list (D57, D148). B. Never beside; above, below, or drop below (D106). | Pass 4: L and JF choosers rise above or drop below their key. Nobody drew a chooser beside a list. | **B for keys and bands; A only from a row inside a vertical list**, where dropping below would cover its neighbours. |
| 12 | **Unlocked front door: alert or warn** | A. Always alert (the red key), as in HA and L. B. Warn by day, alert after sunset or when nobody's home. | L audit 7: the red key is loud on a calm daytime screen. B6 is open. | **B**, using HA's sun and presence. Isaac's call, since it is about the house, not the design. |

---

## 4. Holes found

Things the bespoke designs needed that the bible doesn't cover yet.

| # | Hole | Proposed rule | Tier |
|---|---|---|---|
| H1 | **Rotated text** (NV spines) | Text is horizontal, except titles on drawn spines: top to bottom, ≥ 24 px, one direction, and only when the focused item's name also shows horizontally at ≥ 46 px. | Device: TV |
| H2 | **Objects as UI** (furniture, rack, console, cinema, sideboard, tags, tickets) | An app may draw the real object its job already has: flat, at one realism level, with the language's windows, words and keys on it. It is never a real product's look, and never decoration that hides what's pressable. | Language (permission); the objects are App-local |
| H3 | **Object-shaped windows** (lamp shade, door swing, socket, IR window) | Allowed if they behave exactly like windows: a visible recess when off, flat fill when on, never growing or glowing. The four generic shapes stay for everything else. | Language |
| H4 | **Sky and time-of-day grounds** (L sky, HA day arc) | Driven by real sun times, falling back to the clock. Flat bands, no gradients. Text only on bands that pass AA in every stop. Never brighter than the mid-tone afternoon or the glare cap. Changes take ≥ 1 minute (Calm keeps the slow fade). An "Always night" option. | Device: TV, kiosk (use App-local) |
| H5 | **Status boards** (JD annunciator, HA lit plan, L patch bay) | Fixed positions, words in the lights, all dark = fine. Lit entries link to their cause and never toggle. Each board states its capacity. | Device: desktop, kiosk |
| H6 | **Reading surfaces** (CS sheet, JF programme) | No cards, no orange, a lede size, sources as footnotes, numbered sections, a line length people can read. It ends in a designed sign-off. | Language (pattern) |
| H7 | **Timelines** (JD tape, CS running order and day strip, HA day arc) | A timeline shows order and duration, so it isn't a repeat. NOW is a cream rule. The past dims or folds. Events use the signal colours. Hit areas ≥ 24 px desktop, 44 px touch. | Language |
| H8 | **Maps and plans** (HA lit plan) | Only from the real layout, from Isaac's sketch, never invented. Areas may fill with a state colour (the one place a whole area may). Rooms, not devices, are the targets. | App-local (HA); the area-fill permission is Language |
| H9 | **Shadows and light direction** (L hard offset shadows, JD pulled module, NV one soft drop shadow, needle shadows) | One fixed light from top-left. Each app picks one shadow kind (soft or hard offset), never on text, and never animated on TV except by transform. | Language |
| H10 | **Idle and ambient faces** (NV attract, L sky, HA night plan, kiosk screen-off) | Only the household's own content. Nothing starts by itself. At most one change per 10 s, static in Calm. Dims after 10 minutes on OLED. Any key wakes it, and that press isn't passed on. | Device: TV, kiosk |
| H11 | **Colour taken from content** (JF house colours, NV spine colours sampled from covers) | Clamp it into the look's lightness band (JF: L ≤ 0.05 for blocks that change with focus), keep it out of the orange and red signal ranges, and pick text colour by contrast. | Language |
| H12 | **Signature moments** (JF house lights, NV media drops in, CS Wrap, HA Goodnight, L blind) | Each app may have one or two. ≤ 600 ms, counted against the flash floor, a ≤ 150 ms fade in Calm, never on focus. | Language |
| H13 | **Visible memory** (L dial needle) | An element may remember the last position only if it shows that memory on screen. | Device: TV |
| H14 | **Connections** (JD patch cords) | Draw connections only when asked (point or focus). Always draw broken ones (dashed amber). Mark each as found or user-made. | App-local (JD); "broken always shown" is Language |
| H15 | **People and players** (HA key rail, NV ports, JF tickets) | People are shown by a printed colour tag + name or initial. No faces, no location: home or away only. | Language |
| H16 | **Capacity and overflow** (L dial full at 10, JD board at 5 subjects, JF seats > 12, bar group 10, CS strip 2 labels) | Every bespoke element states how many it holds and its overflow form before it ships. | Language |
| H17 | **Claims about the real world** (HA plan, JD cords, CS "about 6 min") | A drawing that states a fact about the house or servers must come from real data, or say it is estimated or user-drawn. | Language |
| H18 | **Names for elements** ("console" in L, JD and NV; "running order" in CS and JF; "marquee" in JF and NV attract; "patch bay" in L vs "patch field" in JD) | Keep one glossary in the bible. A shared word means a shared element; otherwise rename one (e.g. JF "episode list", NV "attract board"). | Language (glossary) |

---

## 5. What each app owns

Signature elements from pass 4 that other apps should not copy. Pieces shared on purpose are the Guide and player bands (TV), the red alert key, and house objects drawn by HA (conflict 9).

**TV launcher (Lobby).** The room: a flat **sky window** that follows the time of day, a walnut **sill** with Continue as **picture frames** and plaques, and a dark lacquer **console face** holding the **app dial** (named stations with a needle that remembers), the **patch bay** of sockets, and the **house plate**. Also the **TV readout** key, the **console drawer** TV menu, the **slatted blind** title card, and the CEC **note in the window**. Nobody else gets a sky ground or furniture framing; HA's day arc is the kiosk's own answer to the same question.

**Callsheet.** The **printed sheet** (warm white by day, Mission navy by night, no cards, no band), the **running order** with its NOW rule and **gap cues**, the numbered **roster** with ID boxes and the **THEN** row, the **clash bracket**, the phone **day strip**, **source footnotes**, and the **Wrap** with its walnut double rule. Other apps shouldn't borrow the sheet ground or the Wrap; their "done" states should be their own (HA's Goodnight, JD's dark board).

**JamFin.** The cinema: the **marquee** (letter rails, a house-colour title block with a diagonal cut, caps titles), **seat windows**, **tickets** with look stubs for profiles, the **programme** page with a walnut fold and dotted-leader credits, the vertical **episode list**, **house lights** at Play, the colour-block **title card** and the **intermission** card. Session blocks are its accent. Colour taken from the content is JamFin's alone on TV homes.

**Jam-Dash.** The equipment: a walnut-sided **cabinet** with **racks**, **head units**, 1U/2U **modules** and bare rails, the **annunciator** board of legend windows, **maintenance tags**, the **pulled module**, the **patch field and cords**, the **blanking plate**, the update **bench**, the **event tape**, and **ghost modules** when offline. Its dark cabinet in Day is app-local. Others shouldn't copy rack faces, tags or cords; a status board elsewhere follows H5, not this drawing.

**NervOS.** The games room: the **console** on Home (last game in the slot, Continue on the deck, ports on a walnut front), **media spines** with vertical titles, the **display stand**, **divider cards**, **bookends**, the **section slide**, **media goes in** launches, the **save strip**, **Pick up a controller**, the **attract marquee** and the **New sticker**. Colour bars sit on the console. Rotated text and idle attract stay NervOS's unless H1 and H10 pass.

**Jam Home (HA).** The house: the **lit plan** with "Here" pins, the **day arc**, **dimmer plates** with lamp-shade windows, **outlet plates** and the **power strip**, the **sideboard** and **kitchen radio**, the **key rail**, the **door swing**, the **room strip** of lit room windows, and the **Goodnight round**. It also keeps the appliance cards (the only seven-segment), the soft-plastic remote and the source grid, and Jam Braun's warm white and anthracite with soft corners. Other apps don't copy its surfaces or the plan, but they should reuse its drawings of the house's own objects (conflict 9).

---

## D-number index

Where each CHANGES item went (row IDs above; "C" = conflict, "H" = hole).

| D | Row | D | Row | D | Row | D | Row | D | Row | D | Row |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | TV3 | 31 | CT8 | 61 | TV17 | 91 | LY3 | 121 | IN8, C3 | 151 | TV19 |
| 2 | LY1 | 32 | TV8, C2 | 62 | LY1 | 92 | IN7, C1 | 122 | CL15 | 152 | TV5 |
| 3 | TV1 | 33 | CT6 | 63 | TV17 | 93 | CW2 | 123 | LY1 | 153 | CT7, TV20 |
| 4 | TY2, TV19 | 34 | CW5, CL13 | 64 | CL5 | 94 | LY10 | 124 | CW7 | 154 | TV21 |
| 5 | CL2 | 35 | TV5 | 65 | LY7 | 95 | CL5 | 125 | CT8, TV16 | 155 | TV4, TV20 |
| 6 | IN9 | 36 | TV4 | 66 | LY8 | 96 | LY6 | 126 | LY16 | 156 | CW9 |
| 7 | CL5, LY7 | 37 | CW9 | 67 | LY1 (Drop) | 97 | CL5 | 127 | TV24, ST3 | 157 | TV6 |
| 8 | IN17 | 38 | CL3, SM1 | 68 | IN9 | 98 | CT7 | 128 | TV5 | 158 | IN7, C1 |
| 9 | CT14 | 39 | CL5 | 69 | IN13 | 99 | SM5, SM7 | 129 | CL5 | 159 | IN13, CW2 |
| 10 | CL7 | 40 | CT4 | 70 | CT7 | 100 | MO10 | 130 | CL8 | 160 | LY5 |
| 11 | IN13 | 41 | CT6 | 71 | LY15 | 101 | CW7, CW8 | 131 | IN8, C3 | 161 | LY10 |
| 12 | LY3 | 42 | CL6 | 72 | CW4 | 102 | LY11 (Drop) | 132 | CL9 | 162 | SM5, SM7 |
| 13 | TV3 | 43 | CT12 | 73 | LY2 | 103 | CW5 | 133 | CL10 (Drop) | 163 | TY5 |
| 14 | TV4 | 44 | CT12, LY12 | 74 | CL8 | 104 | TV4 | 134 | CT12, LY12 | 164 | LY17 |
| 15 | CT6 | 45 | CL10 | 75 | TV8, C2 | 105 | CT6 | 135 | CT11 | 165 | CT10 |
| 16 | TV7, C11 | 46 | LY3 | 76 | CT6 | 106 | TV7, C11 | 136 | CT15 | 166 | MO10 |
| 17 | IN8, C3 | 47 | SM12, LY13 (Drop) | 77 | TV5 | 107 | TV2, TV3 | 137 | CL5, LY7 | 167 | CT10 |
| 18 | TV1 | 48 | CT15 | 78 | CW9 | 108 | TV1 | 138 | CL6 | 168 | TV6, TV16 |
| 19 | LY1 | 49 | SM10, IN12 | 79 | TV12 (Drop) | 109 | TV11, LY1 | 139 | CL5 | 169 | MO11 |
| 20 | TV23 | 50 | IN14 | 80 | CT6 | 110 | TV8 | 140 | CT6 | 170 | TV18 |
| 21 | IN7, CW2, ST1 | 51 | TY8 | 81 | TV22 | 111 | CT8 | 141 | IN9 | 171 | TV4 |
| 22 | LY1 | 52 | ST2 | 82 | CL5 | 112 | TV6 | 142 | IN7, C1 | 172 | TV4, C5 |
| 23 | CL5, LY7 | 53 | TV3 | 83 | CL8 | 113 | TV23 | 143 | ST2 | 173 | IN8, C3 |
| 24 | CT7 | 54 | TV5 | 84 | CL6 | 114 | MO11 | 144 | LY9 | 174 | CT8 |
| 25 | CT6 | 55 | MO11, TV14 | 85 | CL10 (Drop) | 115 | TV13, CL14 | 145 | LY8 | 175 | TV12 |
| 26 | LY2 | 56 | CT6 | 86 | CT4 | 116 | LY2 | 146 | LY18 | 176 | TV11 |
| 27 | ST2, ST4 | 57 | TV7, C11 | 87 | SM12, LY13 (Drop) | 117 | TV17 | 147 | CT14 | 177 | TV7 |
| 28 | IN4 | 58 | CT8 | 88 | CT15 | 118 | LY4 | 148 | TV5, C10 | 178 | LY1 (Drop) |
| 29 | CT9 | 59 | TV8 | 89 | CL13 | 119 | CL6 | 149 | LY15, CT8 | 179 | TV23, SM13 |
| 30 | TY3 | 60 | TV4 | 90 | CW6 | 120 | TV8, C2 | 150 | TV5 | | |

**A and B items:** A1 → SM4, SM5 · A2 → IN3 · A3 → CL4 · A4 → CL5, CL8, CT3, CT4 · A5 → IN12 · A6 → IN15, MO8 · A7 → TV1, TV2 · A8 → TV4 · A9 → CT16, CL2 · A10 → SM1, SM9, SM13 · B1 → CL1, CL10 · B2 → CT6 · B3, B4, B5 → CT17 · B6 → CW8, C12 · B7 → IN18.

**BIBLE sections:** §1 → SM13 · §2 materials → SM1, SM8 · depth → SM2 · ribs/texture → SM4, SM5, TV15 · type → TY1, IN12 · accents → LY1, CL7 · saved palettes → SM15 · title card → TV4, C4 · §3 light 1–6 → IN1, IN2, SM3, CL3 · colour discipline → CL1, CL2 · state words → CW2, ST1 · shapes → IN4, C6 · reveal → IN15, IN16, TV1 · §4 → CT1–CT5 · §5 → IN10, IN11 · §6 → MO7, MO8 · §7 → TV1, TV2 · §8 → MO1–MO5, SM14 · §9 floors → TY2, CL14, CT13, TV13–TV15, CW1, CW3, TY9, TV8, TV10 · §10 still open → not rules.
