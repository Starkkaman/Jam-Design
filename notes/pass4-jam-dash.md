# Jam-Dash · Pass 4 (bespoke: the equipment rack)

Mockup: `mockups/pass4/jam-dash.html` (interactive). Passes 1–3 are unchanged.

What the page draws:
- **Home** at desktop 1440 × 900 or 1280 × 800, plus phone 390 × 844, in three situations: **Trouble** (Crafty and Code Server down, Immich partly up, nas's pool at 92%), **All good**, and **nas offline**.
- **App detail**, which follows the situation: Crafty (alert), Jellyfin waiting on nas, or Jellyfin with an update ready. Any module on Home also opens its own detail.
- **Flow:** update Jellyfin on the bench (Check → Download → Swap → Watch → Done). A failure branch rolls back.
- **The new parts**, as a labelled list.

Page controls:
- Lighting: Day / Night
- Situation: the three above
- Desktop: 1440 / 1280
- Cords: When pointed at / All
- Motion: Full / Calm
- In the flow section: Update works / Health check fails, and Start over

All data is made-up sample data, and the only host names are "home-server" and "nas".

Sources read:
- `notes/OVERNIGHT-BRIEF.md`, including the Direction update
- The last entry in `decisions.md`
- `notes/REVIEW.md`
- `CHANGES.md` §D (D1–D179)
- `BIBLE.md` §3–§9
- `projects/jam-dash/README.md`
- `notes/pass3-jam-dash.md`
- Screenshots of the pass-3 Jam-Dash, Callsheet, JamFin and HA mockups. I only looked at those to avoid them.

## What changed and why (vs pass 3)
Isaac said: *"I don't really want to see identical cards and backgrounds across designs unless there's a clear reason."* Pass 3's Home used the alu ground, rounded light cards, black ribbed faceplates and a grid of name tiles. That is the same kit as JamFin's and HA's pass-3 pages. Pass 4 keeps pass 3's **functional decisions** and replaces the **surfaces and layout**.

| Pass 3 | Pass 4 | Why |
|---|---|---|
| Hero sentence + ribbed server faceplates + tile grid | **Two racks in one walnut-sided cabinet.** Each server is a rack, its **head unit** carries the server's meters in a dark display window, and each app is a 1U module (2U with a live preview) | Jam-Dash's subject *is* equipment: two boxes with things in them. A rack elevation is how people already draw that. It also shows where everything is, and that has more value than a grid of equal tiles. |
| Server strip (phone) / faceplates (desktop) as the status summary | **Annunciator:** a fixed board of 5 subjects (Reach, Apps, Disk, Memory, Updates) × 2 servers. All dark = fine. | One glance answers "is everything OK, and where isn't it" for both machines at once. Fixed positions build muscle memory. The calm state is literally dark, which fits "calm looks like nothing to do". |
| Trouble card (shared shape with Callsheet's Next card, D65) | **Maintenance tag** in the console: coloured stub, punched hole, then LED + label, title, sentence, fix | Same grammar (it's the language) but its own shape (that's the design). A tag is what you hang on equipment that needs work. |
| History reached from the hero's sub line | **Event tape** always along the bottom: 24 h, two lanes, a plain-words readout | "Is it OK?" is often "was it OK overnight?" The tape answers that without a page change, and History is one click from it. |
| Dependencies not shown | **Patch field + cords** between the racks (desktop). There's a **patch board** on every app detail (desktop and phone) | The second user ("why is Jellyfin down?") needs the cause, and the cause is often another app or the other server. |
| Stopped chips | **Blanking plate:** stopped apps share one plate at the foot of the rack and open as a drawer of Start keys | Stopped apps take no rack space, as in a real rack. |
| Alert tile with red ring | **Pulled module:** it slides 12 px out of line once, with a hard shadow, and keeps its place | Draws the eye to the module without reordering the rack. The reason stays on the tag (D96, said once). |
| Store update list / Update all | **Bench:** the update runs on a walnut-lipped bench next to the rack it belongs to, and the module mirrors the job | You see *what* is being changed and *where*, and the steps are step mode (D66, D145). |

**Kept from pass 3:**
- the red alert key (D84/D138) on the newest alert only;
- one orange per screen in D23/D95 order, with no orange on a calm Home (D139);
- warn = amber round LED + printed ▲ (D158);
- the first-screen promise (D160);
- names wrap and never get an ellipsis (D163);
- "Name on Home" short names ("Proxy Manager");
- quiet past forms "Fixed 01:53" (D159);
- live text steps (D166);
- rollback = warn (D101);
- secrets and Edit setup as specified in pass 3 (not redrawn).

## Purpose
- **Main job:** is everything OK on home-server and nas, and if not, fix it. That's mostly Isaac, at a desk or on the phone, often late at night.
- **Second user:** someone else in the house checks why Jellyfin (or Immich) isn't working. They need a plain sentence and the cause, not numbers.
- **Occasional jobs:** install, update and configure. These are rarer, deliberate, and should feel safe.
- **Not the job:** watching graphs. Grafana and Netdata are the anti-reference here: walls of time-series, gauges and colour for its own sake. The tape is the only time-series, and it records *events*, not metrics.

## Research
Four WebSearch queries, plus knowledge for the rest (marked).
- **Apollo MOCR** (Space Center Houston restoration pages; NASA JSC MCC restoration; collectSPACE). The room had a fixed layout for most of Apollo, with each station owning a related group of functions. Search found nothing reliable about event-lamp wiring, so I didn't copy any. *From knowledge:* the consoles used grids of small backlit legend tiles that lit on a condition. That's the annunciator idea, used here as fixed, labelled positions, not as a look.
- **Rack elevation diagrams** (AV Solution Hub guide; ConceptDraw examples, which are vendor material and secondary). An elevation is a scaled front view, with heights in U (1U = 1.75 in) and every device in its place, so people can *locate devices and trace cables*. Used for: 1U/2U modules, ears and rails, empty U as visible room, cords as traceable lines.
- **Braun audio** (Science Museum Group: audio 308 is a 1973 Rams music centre; hifi.fan on Regie 308; 1stdibs/designundtext on the 1960s Braun wall units). The search didn't confirm a modular "308 rack". The real lesson is the Braun wall system: separate components on one aluminium structure with wooden ends. Used for: walnut cabinet cheeks, light faceplates on a dark structure.
- **Teenage Engineering OP-1 field** (Sound On Sound, New Atlas, Backfill reviews). The screen graphics were redrawn screen by screen, they're playful and illustrative, and a parameter pop-up appears only when a value isn't obvious. Used for: cords that appear only when you point, and the readout line that shows one event at a time.
- **Grafana / Netdata** *(knowledge, no search):* what to avoid is dense multi-panel time-series, needle gauges, and colour as decoration. Jam-Dash shows three meters per server, once, in the head unit.

Sources: [Space Center Houston: restoring Apollo Mission Control](https://spacecenter.org/restoring-apollo-mission-control/), [NASA JSC: Apollo MCC restoration](https://www.nasa.gov/johnson/history/apollo-mcc-restoration/), [collectSPACE: consoles restoration](https://www.collectspace.com/news/news-012518a-apollo-mission-control-consoles-restoration.html), [AV rack elevation guide](https://sites.google.com/view/avsolutionhub/blog/how-to-create-a-professional-wall-mount-av-rack-elevation-diagram), [ConceptDraw rack front view](https://www.conceptdraw.com/examples/server-rack-front-view), [Science Museum Group: Braun](https://collection.sciencemuseum.org.uk/search/objects/makers/Braun%20GmbH), [hifi.fan Regie 308](https://hifi.fan/braun-regie-308), [designundtext: Braun wall unit](https://www.designundtext.com/en/2.1.6_wall-unit-braun-design-bddp.php), [Sound On Sound: OP-1 field](https://www.soundonsound.com/reviews/teenage-engineering-op-1-field), [New Atlas: OP-1 field](https://newatlas.com/music/teenage-engineering-op-1-field/?amp=true), [Backfill: OP-1 field](https://desirabilitylab.com/backfill/backfill-2022-104-teenage-engineering-op-1-field).

## Design

### Desktop Home (1440 × 900)
The screen has four parts:
- **Lip:** wordmark; every place visible (Home, Apps, Store, Files, Shares, System, Settings, D26) with the base-window selector; Find ⌘K; and the server clock in mono.
- **Console (380 px, left):** headline sentence → annunciator → tags.
- **Cabinet (right):** home-server rack | patch field (64 px) | nas rack, with walnut cheeks at the outer edges.
- **Tape (92 px, foot):** black ribbed band.

The deck scrolls between the lip and the tape. Measured:

| Size | Situation | Deck past the fold | Board, every tag and both head units on the first screen |
|---|---|---|---|
| 1440 × 900 | All three | 0 px | Yes |
| 1280 × 800 | Trouble | 82 px (rack only) | Yes, at console ladder step 2 |

**Console ladder** (new; a smaller version of pass 3's density ladder):
- Step 1 folds later alerts to one-line tags with their key.
- Step 2 folds warns into one row, "To look at · 2: Immich, nas", which opens in place.
- At 1440, Trouble lands on step 2. At 1280 it also needs the w1280 tightening: 30 px legends, an 80 px tape and a 25 px headline.

### Phone Home (390 × 844)
The order is: headline → board → first tag → further alerts as rows → "To look at · n" folded → the chosen server's rack (48 px modules) → tape as one tap target (opens History) → tabs (Home, Apps, Store, Files, System, with base windows).
- The board's **two column heads are the server picker.** A lit square marks the one shown. Square = selected mode, the bible's meaning.
- The phone has no patch field. A waiting module names what it waits on ("Waiting on nas"), and the detail page carries the patch board.
- Where the rack starts:

| Situation | Rack starts at | First screen ends at |
|---|---|---|
| Trouble | 753 px | 782 px (only the head unit's top is visible) |
| All good | 564 px | 782 px |
| nas offline | 651 px | 782 px |

### App detail
The module is drawn large, **"on the bench"**: ears, LED + word + server, the name at 34 px, one plain sentence, and keys.
- Below it, the **patch board**:
  - "Needs": each row is a cord drawing from a jack, then the provider's name (a link to it) and its state.
  - "Needed by": the same, the other way round.
- On the right: this app's own lane of tape ("Jellyfin today"), its last lines (failing lines in ink with ▲), and its facts.
- Orange per screen:
  - Crafty's detail has the red key and no orange.
  - Jellyfin waiting on nas has orange "Try nas again" (offline outranks warn, D23).
  - Jellyfin running has orange "Update to 10.11.2", the screen's routine action.
  - A plain running app has none.

### Flow: update on the bench
- **Check:** what's new (3 lines) and what was checked: disk room, nas · media answering, the data folder stays, and the old version is kept 7 days. Orange "Update Jellyfin", link "Not now", and the cost "Jellyfin is away about 40 s".
- **Download:** a cream fill in a recess and "755 of 1,180 MB", stepping as live text (D166). Jellyfin keeps running. Cancel is plain.
- **Swap:** it can't be stopped halfway, so there are no keys. Each line lights a slot while it runs and an LED when it's done.
- **Watch:** answering, health check ×3, reads nas · media.
- **Done:** "Jellyfin 10.11.2 is running", orange **Done**, and "Go back to 10.10.7".
- **Failure:** the health check fails 3 times, 10.10.7 goes back by itself, and the screen says it's **warn**, not alert (D101). It shows the log lines that explain why, with orange **Try again**.
- The rack's Jellyfin module mirrors every step with a lit slot + word (Downloading 10.11.2 / Swapping · back in ~40 s / Checking / Rolled back ▲). The tape gets a cream tick (success) or an amber span (rollback).
- On the phone, the bench is one full screen with a sticky key bar, and the step names collapse to numbers except the current one.

### New elements
The seed gave three of these (rack, patch bay, tape). **Five are mine**, marked ★.
1. **★ Annunciator.** Fixed legend windows, subject × server.
   - Dark = fine, with the calm word readable in the recess (legend ink 7.0:1 day / 6.9:1 night).
   - Lit red = down ("2 down").
   - Lit amber + ▲ = needs a look ("Almost full ▲").
   - Lit cream = waiting for you ("2 ready").
   - Dashed cream = not answering.
   - Dashed grey = unknown.
   - Lit legends are **links to their cause** (the tag and module flash an ink outline once). They never toggle anything.
2. **Rack + head unit + modules.**
   - Modules come in 1U (34 px desktop / 48 phone) and 2U (live preview: SABnzbd's bar and speed, Music Assistant's "now playing" slot).
   - Ears with screw slots sit over rails with holes.
   - The empty rack below nas's modules shows bare rails, which reads as room to grow.
   - The order is the user's, and Jam-Dash never reorders it.
3. **★ Pulled module.**
   - An alert module slides 12 px out of line toward the console, once, in 400 ms on the decelerate curve, and gets a hard 4 px shadow.
   - Not on the phone, and Calm turns it into a 120 ms change.
4. **Patch field + cords.**
   - Every module has a jack ring on the ear that faces the field.
   - Cords are flat cream lines, drawn while you point at or focus a module. Its partners get an ink outline.
   - **Broken cords are dashed amber and always shown.** In "nas offline", five cords run from nas's ghosted shares to Immich, Jellyfin, Radarr, SABnzbd and Sonarr.
   - Same-rack cords loop into the field, and cross-rack cords S-curve across it.
5. **★ Blanking plate.** "Stopped · 14 · Audiobookshelf, Bazarr and 12 more" + Show, which opens a drawer of Start keys. On nas offline it has no key.
6. **★ Maintenance tag.**
   - Stub colour: red / amber / dashed / grey when fixed.
   - Punched hole.
   - Fixed tags turn grey and stay ("Crafty · Fixed 01:53 · restarted by you").
7. **Event tape.**
   - Black ribbed band (night ribs per D162), 24 h, two lanes.
   - Marks: red blocks for time down, amber for warn, a dashed box for not answering, cream ticks for changes.
   - The readout says the latest event, or the one you clicked, in plain words.
   - Hit areas are ≥ 24 px.
8. **★ Bench.** A walnut lip under a light panel, with procedure steps in slot windows and one orange per step. It sits beside the rack the module lives in.
9. **Ghost modules / closed rack** (offline). They're dashed outlines with the last-seen names and no states, and a dashed note says "What's in this rack is how it was at 01:12". The head unit's meters read "—".

### Colour and loudness
- **Red** is only on alerts: the LED, the lit legend, the tag stub, the red key and the tape blocks.
- **Orange** appears at most once per screen:
  - Trouble: none (the red key is the loud thing).
  - Offline: "Try again".
  - Warns only: the first warn's key.
  - Calm: none.
  - Detail and flow: one each.
- **Hover and ping outlines are ink, not orange.** Pass 4's first draft used orange there, and I took it out.
- **Cream** marks lit slots (running/job), the selected-server square, lit "ready" legends, cords and the tape's ticks.

## Language check
**What ties it to the family:**
- Jost for words and IBM Plex Mono for labels and numbers.
- Indicator windows that are always a dark recess and lit flat, in exactly the bible shapes: round = status, square = selected server, slot = job running.
- The shared state words (on / off / offline / action / alert + warn) with the D93 short words ("Unhealthy", "Partly up", "Waiting on nas").
- The red alert key with dark text.
- One orange per screen.
- Warn = amber + ▲.
- Offline = dashed.
- A black ribbed band (the tape).
- The walnut rule, here as cabinet cheeks and the bench lip.
- The base-window selector in nav and tabs.
- Rectangular keys that press in 2 px.
- Calm motion that happens once and rests.
- Plain sentences.

**What someone from another app recognises within a second:**
- The red key on the alert tag (identical in HA and Callsheet).
- The lit LED + word pairs.
- The black ribbed band at the bottom (HA's dock, TV bands).
- The type pair.

**What is deliberately not shared:**
- The alu ground and rounded light cards (here: a warm machine-room grey and square rack faces).
- The tile grid.
- The faceplate band.
- The accents (none).
- The trouble-card shape.

## Rules I broke
| Rule (source) | What I did instead | Why Jam-Dash needed it | Verdict |
|---|---|---|---|
| **BIBLE §3.1** "Lights are for indicators, never controls" | Lit annunciator legends are **links**: a click takes you to the cause | The board is the summary, and its fastest use is "show me that". It's still not a switch: nothing toggles. | **Language-wide, amended:** "a lit indicator may link to its cause; it never changes state" |
| **BIBLE §3.5** "Nothing is more realistic than its neighbours" + D96 (tile keeps its place with just the word) | The **pulled module** steps out of line and casts a hard shadow | In a rack of 20 equal modules, the word alone is easy to miss at a glance. The module keeps its place and the reason stays on the tag. | **App-local** |
| **D158 / §3 "four indicator shapes"** | A **legend window** (a word inside a lit rectangle) on the annunciator | A board of fixed subjects needs the word in the light, or it's an unlabelled grid of dots | **Device family** (desktop/kiosk status boards). Other apps may adopt it, but it's not a fifth status shape for rows. |
| **Brief: "calm, flat cards with soft corners"** (Jam Braun) | Square rack faces, clipped tags, rectangular 4 px keys | Equipment has square fronts. Soft rounded cards are what made pass 3 look like HA. | **Drop as a language rule** (soft corners are Jam Home's/HA's) |
| **Brief / BIBLE §2 Accents** (one per screen: Stripes, Session blocks, Colour bars) | No accent at all | An ops screen's colour must mean state. The cabinet's walnut and the tape are Jam-Dash's signature instead. | **App-local** (an app may have an accent, not must) |
| **BIBLE §2 materials** (alu ground, card colours) and "Day = light screens" | Day has a large **dark cabinet** on a warm grey ground (`#d9d5cc`), with light faceplates | The dark structure with light faces is what makes it read as a rack, and it makes cream cords and lit legends work in both modes | **Language-wide as roles** (ground, face, structure, band, recess, ink), **values app-local** |
| **D102** "phone overview with several servers starts with a strip, one row per server" (+ pass-3 strip as picker) | The board's column heads are the picker, and the board comes first | One element instead of two. The picker is the same light grammar. | **Drop globally**, app-local |
| **D65 / pass-3 implication 4** (one trouble/Next card shared with Callsheet) | **Maintenance tag**: same grammar, its own shape | Isaac: no identical cards without a reason | **Grammar language-wide; shape app-local** |
| **D140** "a count appears once per screen" | The board says "2 down" and two tags sit below it | The board must hold its answer when the tags fold or scroll (console ladder, phone) | **Language-wide, refined:** a summary may count what a foldable list below names |
| **D15 / B2** "never the same value twice" | The tape draws Crafty's down-span from 01:49, and the tag says "at 01:49" | A timeline shows duration and order, which is a different value from a timestamp | **Language-wide clarification:** a timeline isn't a repeat |
| **D160** first-screen promise "…and every server's faceplate" | On the phone in Trouble, the rack's head unit starts at 753 of 782 px. The board carries each server's state instead. | The board *is* the per-server summary | **Language-wide, reworded:** "the status summary" may be a board, not necessarily faceplates |
| **D121 vs D173** (windows in Day) | Annunciator windows stay a **dark recess in Day** (HA's D131 choice), and so do every LED and slot | Lit legends need the dark contrast. A hairline groove can't hold a word. | Supports **D131 language-wide** |

## Audit
Checked with Playwright (Chromium, `chromium.launch()`):
- **Coverage:** page widths 1500 (light) and 390 (dark); all three situations, Day and Night; 1440 and 1280.
- **Flows exercised:**
  - the cord hover on Proxy Manager;
  - Restart Crafty (the red key moves to Code Server, and a grey Fixed tag and a tape tick appear);
  - update success and failure;
  - the phone server pick (nas);
  - unfolding "To look at";
  - phone detail;
  - the phone flow.

Screenshots are in the scratchpad (`p4jd/`).

**Results:**
- **No JS errors.**
- **No horizontal page scroll at 390**, and no clipped text inside phone frames.
- **No text under 12 px.** The only 12 px items are the ▲ glyph and the ⌘K keycap. Labels are 13 and body is 15.
- **Every phone target ≥ 44 × 44**, page controls included (the "All" segment was 42 px wide before the fix).

**Fix pass (one round):**
- A class clash: `.hl` was both the headline and the module highlight, which made highlighted modules' keys huge.
- The head-unit meters overlapped ("MEMORY 9.5 GB" ran into DISK), so they now stack.
- The 1280 console overflowed, so I added ladder step 2 and the w1280 tightening.
- The bench footer was hidden under the tape (the bench is now sticky with a fixed height).
- The muted ink failed AA (4.12), so it's now `#6a655d`, 4.99 on the day face, and `#9b968c` at night, 4.93.
- Hover/ping outlines were orange, now ink.
- There was a duplicate back link on the phone detail.
- The sticky page controls covered a third of the 390 screen, so they're no longer sticky below 900 px.
- The flow clock didn't match the flow's own times.

**Contrast (measured):**

| Pair | Ratio |
|---|---|
| Legend ink on recess | 7.02 (day) / 6.85 (night) |
| Ink on lit red | 5.52 |
| Ink on orange | 6.06 / 6.79 |
| Ink on lit amber | 10.15 |
| Ink on cream | 13.76 |
| warn-ink on face | 5.97 |
| alert-ink on face | 5.76 (day) / 5.73 (night) |
| Tape labels | 8.98 |
| Cream on band | 16.28 |
| Patch-board words | 8.62 |
| Log failing lines | 7.81 |

| # | Problem | Severity |
|---|---|---|
| 1 | **Where cords come from is my assumption.** Mounts (nas shares) and compose `depends_on`/networks are knowable. Proxy hosts need Nginx Proxy Manager's API (a key in Connections). "Sonarr needs Prowlarr and SABnzbd" only comes from the apps' own settings or a hand-drawn cord. A wrong or missing cord would mislead exactly the housemate it's meant for. | High |
| 2 | **Busy day (40 apps) not redrawn.** home-server's rack would be about 1.4 screens tall at 1440. The rack *is* already rows (34 px), so pass 3's Rows step has nowhere left to go. The likely answer is two module columns per rack (a "double-width rack") or folding healthy 1U modules into a "Running · 22" plate. | High |
| 3 | **Phone Trouble: the rack starts at 753 of 782 px.** The board costs about 290 px, and pass 3's apps started at 607. The glance is better (both servers, five subjects), but browsing apps needs a scroll. | Medium |
| 4 | **1280 × 800 Trouble needs console ladder step 2 and the w1280 tightening** to keep every tag above the fold, and the rack runs 82 px below. Even 1440 Trouble folds the warns into a row. | Medium |
| 5 | **Cord fans.** Proxy Manager has 5 cords, and with "All" on, cords cross. At 40 apps, "All" would be spaghetti, so it should stay a review aid, not a mode. | Medium |
| 6 | **Tape at 24 h scale:** a 3-minute outage is 2 px wide. Events near "now" cluster (01:31, 01:49) and their 24 px hit areas overlap. The readout shows one at a time. A zoom ("last hour") or merged marks may be needed. | Medium |
| 7 | **Annunciator scale:** the desktop console would fit about 3 server columns, and the phone only 2 (the column heads are the picker). The five subjects are fixed. A sixth (temperature, backups) means redrawing the board. | Medium |
| 8 | **A large dark cabinet in Day.** It's intentional, but it's the one Jam app whose Day screen is mostly dark. Next to Jam Home it may read as "night mode stuck on". | Medium |
| 9 | **The pulled module is subtle at night** (a dark shadow on dark). It's never the only cue (LED + word + tag), but it does less at night. | Low |
| 10 | **No patch field on the phone.** Dependencies there are words on modules and the detail's patch board. | Low |
| 11 | **Not drawn this pass:** Apps, Store (only the update flow), Files, Shares, System, Settings, Edit setup, Full log, History (the tape links to it), install flow, stop confirm, the drawer's Start flow and Find. Pass 3's versions of most of these stand, but they now need re-skinning to the rack language. | Medium |
| 12 | **Lit legends repeat counts** that the tags show (the D140 refinement above). It's a deliberate break, and Isaac should confirm it. | Low |
| 13 | The mockup loads Jost and Plex Mono from Google Fonts. The product bundles them. | Low |

## Questions for Isaac
1. **The rack as Jam-Dash's own design?** Servers as racks, apps as modules, a walnut-sided cabinet. *Recommendation: yes.* It's the clearest "bespoke to purpose" layout of the passes, and nothing else in the house looks like it.
2. **The annunciator** (5 subjects × servers, dark when fine) instead of a hero card and server strip, on the phone too? *Recommendation: yes.* Keep the positions fixed even on the phone, and accept the 290 px.
3. **Lit lights as links** (the §3.1 amendment)? *Recommendation: yes, language-wide.* A light may take you to its cause but never toggles.
4. **Cords:** show them only when you point at a module, and always when broken? *Recommendation: yes.* Keep "All" out of the product. Infer cords from mounts and compose, and let you add or remove them in Edit setup, marked "found" vs "yours" (audit 1).
5. **The tape always on screen** (desktop foot, phone at the end of Home)? *Recommendation: yes.* Add a "last hour" zoom before calling it final (audit 6).
6. **A dark cabinet in Day** for Jam-Dash only? *Recommendation: yes,* as an app-local choice. If it feels wrong next to Jam Home, the fallback is a graphite-grey cabinet (`#5a5853`) with the same light faces.
7. **Accents:** may an app have none? *Recommendation: yes.* Accents become optional per app, and Jam-Dash's signature is the walnut cabinet and the tape.
8. **The pulled module** (an alert steps out of line, once, desktop only)? *Recommendation: yes, app-local.*
9. **Busy day:** two module columns per rack, or fold healthy modules into a "Running · n" plate? *Recommendation: the plate.* It keeps the rack a single column (the real-world reading) and leaves trouble in place. Draw it next pass.
10. **Updates on the bench** with automatic rollback (warn, not alert) and the old version kept 7 days? *Recommendation: yes,* and use the same bench for installs from the Store.
