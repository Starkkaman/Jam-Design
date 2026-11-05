# Jam-Dash · Pass 5 (the whole rack)

Mockup: `mockups/pass5/jam-dash.html` (interactive). Passes 1–4 are unchanged.

What the page draws:
- **Home** at 1440 × 900 or 1280 × 800, plus phone 390 × 844, in four situations: **Trouble**, **All good**, **nas offline** and the new **Busy day · 40 apps** (30 on home-server, 10 on nas, Paperless down).
- **App detail and its cords**: Crafty (alert), Jellyfin waiting on nas, Jellyfin with an update. It has a cord panel with sources, a suggested cord, and a **Draw a cord** sheet.
- **The bench**: the pass-4 Jellyfin update (works / health check fails), now on the Day surfaces.
- **The rest of the app** (new this pass): Store and install, Full log, Edit setup (the rear panel), Files, Shares, First run, History. Desktop and phone for each.

Page controls: Lighting Day / Night (defaults to the device), Situation, Desktop 1440 / 1280, Motion Full / Calm. Pass 4's "Cords: All" switch is gone (audit 5: it isn't a product mode).

All data is made-up sample data. The only host names are "home-server" and "nas"; proxy hosts are `*.example.net`. The one-time codes and the secret (dots) are fake.

Sources read: the last entry of `decisions.md`; the Direction update in `notes/OVERNIGHT-BRIEF.md`; `notes/RULES-TIERS.md` (all of it); `projects/jam-dash/README.md`; `notes/pass4-jam-dash.md` and `mockups/pass4/jam-dash.html`; `notes/pass3-jam-dash.md` (for Edit setup, Full log, History and first run, which pass 4 didn't redraw); `CHANGES.md` D24, D66, D70, D96, D98, D101, D145, D159, D160, D164, D165, D167. No web research this pass: everything new builds on pass 3's research (Dozzle, Komodo, Portainer) and pass 4's (rack elevations, Braun wall units, Apollo MOCR).

## What changed since pass 4

| Pass 4 | Pass 5 | Why |
|---|---|---|
| Cords drawn from data I assumed (audit 1, High) | Every cord has a **source**. Solid = **found**: a mount (Docker shows the container mounts a nas share), a compose link (`depends_on` / `links`) or a proxy host (read from Proxy Manager, only after it's connected in Settings › Connections). Hollow = **yours** (drawn by hand, dated, "Jam-Dash can't check it"). A guess (two apps on the same Docker network) is **asked, not drawn**: "Does Sonarr need Jellyfin?" with Yes / No. | H17. A wrong cord would mislead the housemate it's for. |
| No way to add a cord | **Draw a cord** on the cord panel (detail) and on the rear panel (Edit setup): a sheet with a direction choice (needs / is needed by), search, and a list of apps and shares. The new cord is hollow on the panel and on Home. Yours can be removed. | Shows how a user draws or confirms a cord. |
| "Patch field", cords fan out, "All" = spaghetti (audit 5) | **Cord channel** with **combed lanes**: a pointed module's cords leave its jack, run down one lane 4 px apart and branch at their targets, so they read as a bundle. At most 6 per module; cords to folded apps end on the Running plate with a count ("+13"). Broken cords are always drawn, one lane per source. A **cord note** above the racks says what is drawn and where it came from. Ghost-to-ghost cords (both ends offline) aren't drawn. | H14 at scale, and H18 (L owns "patch bay"). |
| Busy day not drawn (audit 2, High) | **Running plate**: when a rack is taller than the screen (Auto), healthy apps fold into one plate with a lit slot: "Running · 25 · Code Server, Crafty and 23 more". **Show** opens a shelf of half-width modules inside the rack. Never folded: trouble, live previews (2U), jobs, apps you keep in view (Proxy Manager, Jellyfin and Jam-Dash in the sample). | Keeps the rack one column, the real-world reading, and keeps trouble in place. |
| Phone rack at 753 of 782 px (audit 3) | The phone board turns sideways: servers are rows, the five subjects are fixed columns. The rack picker moves onto the rack (home-server \| nas). The phone head unit drops its name and "On" line (the picker and the board's Reach already say them) and shows UP / CPU / MEM / DISK in one window. The rack folds. | Trouble: picker at 574, head unit at 633, **first module at 700 px**. |
| 1280 needed emergency tightening, rack 82 px past (audit 4) | Auto-fold plus the tag ladder. Measured below: **0 px past at both widths in all four situations**. | |
| Tape at 24 h only; marks near now overlap (audit 6) | **24 h \| Last hour** on the tape. At 24 h, marks within 36 min (24 px) merge into one mark with a count; pressing it opens the last hour and says "3 events between 01:12 and 01:49. Showing the last hour." | H7, H16. |
| Day screen mostly dark (audit 8) | **Day = lab grey.** The cabinet is a light enamel (`#c8c4bb`) with light faces; only windows that hold words or numbers stay dark (legend windows, head-unit display, share addresses). The tape is a light strip by day and the black ribbed band at night. Measured share of dark pixels (luma < 0.25) on Home, Trouble, 1440: **4.9 % Day** (pass 4: most of the frame) and 94 % Night. | It now reads as a Day screen. See Language item 4 and question 2. |
| Store, Full log, Edit setup, Files, Shares, first run and History not redrawn (audit 11) | All redrawn in the rack's parts (below). | Isaac: "the whole app feels designed". |

### The new screens, in short
- **Store and install.** The catalogue is a **drawer of unplugged modules** (same faces as the rack, no light, no jack) with category list and search. A **spec plate** says what the app needs before you commit (port, folder, size, architecture, and "no cords found yet"). Installing uses the **bench** beside the target rack, where a **dashed slot** shows where the module goes. Check: server choice (lit square), a port field checked as you type ("8080 is used by SABnzbd on home-server. Pick another." → Install waits), folder, room, name, architecture; choosing nas warns that its pool is 92 % full. Then Fetch → Start → Watch → Done. The slot lights and says "Fetching 330 of 412 MB", then the module racks in.
- **Full log.** The app's **own tape lane is the scrubber** over the lines (press a mark to jump to 01:49). Following / Paused is a slot window; paused counts new lines ("2 new lines · Jump to newest"). All lines / Problems · 6; Last hour / 24 h / Since start; find with cream marks and a count; Wrap; Download. Failing lines have ▲ + alert ink. Light reading surface by day, no orange. The phone fits the controls in two rows and hides line numbers.
- **Edit setup = the rear panel.** The module turned round (a 280 ms slide-in, none in Calm): Name on Home; **Ports** as jacks with the host number in a field and "→ 8989 inside", checked as you type; **Folders** with exists/mounted and a Read and write / Read only pair; **Environment** as a terminal strip; the **secret** as dots + Replace, "Set by you on Oct 2. Never shown back." (D165; Replace takes a password field and "Keep it"); **Cords** with sources, Remove for yours, the suggestion, Draw a cord; **Power**: restart rule (pressed-in keys) and memory limit with "used 610 MB at most this week". A sticky **save bar** counts changes and says the cost ("Sonarr restarts and is away about 20 s. Its data folder stays."), waits on a failing check, and is orange only when Save can run (D167). **Remove Sonarr…** opens a confirm sheet: Keep Sonarr has focus, the dark "Remove Sonarr" key, data loss opt-in by a checkbox that renames the key ("Remove Sonarr and its folder"), Enter doesn't fire it (D24, D70, D98).
- **Files.** Places are **drive bays** grouped by machine, with the free space said once per machine (not per folder). Folders that apps mount say "Used by Jellyfin and Radarr" (found mounts, in words). Upload, New folder, Share this folder; preview panel with facts and Download / Rename / Move / Delete…. The list ends visibly. In nas offline the folder shows "Can't read nas · media" with orange Try again + Go to Home. No orange at rest. On the phone, places open in a sheet and **Files and Shares share one tab**.
- **Shares.** "Shared from nas" as plates: address in a dark window + Copy, who can open it, "Mounted by Jellyfin, Radarr and Sonarr on home-server (found)" with a small cord. CasaOS-made shares say "Made by CasaOS" and are left alone. "Network shares on home-server" lists the mounts; in nas offline they go amber "Waiting on nas".
- **First run.** An **empty cabinet**. Step 1 sets a password (10 characters). Step 2 racks home-server's apps in once, 25 ms apart (under 600 ms in all): "26 of them came from CasaOS. They keep running as they are. Jam-Dash changes nothing until you ask." Step 3 adds another server with an address and a one-time code; the first code fails ("That code didn't match. Codes last 10 minutes…"), Try again connects with three checks and the second rack fills. Step 4: "Both servers are in." with orange Go to Home.
- **History.** A **week of tape** (one strip per day, two lanes, a hatched rest after "now" on today's strip) over a **reading list** grouped Tonight / Wed 4 Nov / Earlier this week. Open items are lit with "Open now" and Go to it; finished items are unlit and say how they ended. Everything / Problems / Changes. Overlapping marks merge with a count and select every item they cover. It ends with a walnut rule: "Jam-Dash keeps 7 days." No bells, no unread counts (D164).

### Measured fit (Playwright, Chromium)
| Size | Trouble | All good | nas offline | Busy day |
|---|---|---|---|---|
| 1440 × 900 | 0 px past · tag ladder step 1 · no fold | 0 · step 0 · no fold | 0 · step 0 · no fold | 0 · step 0 · home-server folded |
| 1280 × 800 | 0 · step 2 · home-server folded | 0 · step 0 · folded | 0 · step 0 · folded | 0 · step 0 · folded |
| Phone: first module at | 700 px | 561 px | 642 px | 600 px |

In every case the board, every tag and both head units are on the first desktop screen. The phone's first screen ends at 782 px.

## Language check (the 15 items)

| # | Item | Held / adjusted |
|---|---|---|
| 1 | Two typefaces | **Held.** Jost and IBM Plex Mono only. |
| 2 | Indicator windows | **Adjusted (Day).** Round LEDs, slots and squares on a light face are a hairline groove when unlit and flat colour in a dark rim when lit (conflict 3, B). Legend windows, the head-unit display, share addresses and progress tracks stay dark recesses because they hold words or numbers (conflict 3, C). Night is unchanged. |
| 3 | Window shapes have meanings | **Held.** Round = status, square = chosen (server pick, cord pick, Files/Shares), slot = current/running (nav, tabs, jobs, Following, the Running plate). No new status shape. The hollow cord is a line style, not a window. |
| 4 | Cream is the house light | **Adjusted (value).** By day a lit cream window on a light face is 1.1:1 and read only by its rim, so Day uses a deeper cream `#ebcd8a` for lit windows (1.44:1 to the face, ink on it 11.05). Night keeps `#f3e6c8`. Same role, an app-set value (SM1). |
| 5 | Colour + shape + word | **Held.** Every LED has a word; warn has ▲; offline is dashed; broken cords are dashed amber over a dark under-stroke; tape marks have a rim. |
| 6 | Red means alert | **Held.** Red key on the newest alert (Restart Crafty / Restart Paperless). Nothing else on that screen is orange. |
| 7 | One orange | **Held.** Home calm/Trouble: none; offline: Try again; detail: one; bench, install and first run: one per step; Edit setup: Save only when it can run; Store: Set up (or Install); Files, Shares, log, History: none. A sheet hides the page's orange (the Draw a cord sheet has its own). |
| 8 | Focus is a light at the thing | **Held.** Keyboard focus is an ink outline; focusing a module also draws its cords (point = focus). |
| 9 | Chosen things press in | **Held.** Filters, ranges, restart rule, read/write, categories, the selected file row and history item press in. |
| 10 | Walnut | **Held.** Cabinet cheeks, bench lip, the end rule on lists. |
| 11 | Things end visibly | **Held and extended.** Bare rails end each rack; "6 items · end of folder", "4 shares · end of list", "Jam-Dash keeps 7 days", the catalogue says "The list ends here; search for the rest", today's strip shows a hatched rest after now. |
| 12 | Calm is the resting state | **Held.** All good: dark board, no orange, no motion. |
| 13 | Motion once | **Held.** Pulled module (400 ms), racking in (under 600 ms), rear-panel slide (280 ms), cord fade (300 ms); all off in Calm. The log adds six sample lines and stops. |
| 14 | Say it once | **Held, one fix.** The phone head unit dropped "home-server · On" (the picker and Reach said it). Files says free space per machine, not per folder. |
| 15 | Honest objects, drawn flat | **Held.** Rack, rear panel, drive bays, drawer of unplugged modules, empty cabinet. No texture. |

## Conflicts assumed (RULES-TIERS §3, all "assumed, pending Isaac")
1. **Warn shape → B.** Round amber + ▲ + word; legend windows light amber + ▲. *Assumed, pending Isaac.*
2. **Row ends → A, stop.** Racks, lists and the catalogue stop at a visible end. *Assumed, pending Isaac.* (No TV rows here.)
3. **Windows in Day → by what they sit on.** Light faces: hairline groove, lit = colour in a dark rim. Windows holding words or numbers: dark recess. Applied everywhere in Day. *Assumed, pending Isaac.*
4. **Title card form → B.** Not used (no TV surface). *Assumed, pending Isaac.*
5. **Day title card → B for Play.** Not used. *Assumed, pending Isaac.*
6. **Round = status only; slot = "current".** Applied: slots mark the current place, running jobs, Following and the Running plate. *Assumed, pending Isaac.*
7. **Ribs → B, any dark surface.** The tape is ribbed at night only; Day's tape is a light strip with no ribs. *Assumed, pending Isaac.*
8. **Accents → B, optional.** Jam-Dash has none. *Assumed, pending Isaac.*
9. **House objects owned by HA → B.** Jam-Dash draws no house objects. *Assumed, pending Isaac.*
10. **Guide band → B.** Not used. *Assumed, pending Isaac.*
11. **Menus beside a list → B for keys.** The drawer, the plate's shelf and the cord sheet open below or as a sheet. *Assumed, pending Isaac.*
12. **Front door → B.** Not used. *Assumed, pending Isaac.*

## Holes applied (H1–H18)
- **H2 Objects as UI.** Rack, rear panel, drive bays, catalogue drawer, empty cabinet: flat, one realism level, the language's windows and keys on them.
- **H5 Status boards.** Fixed positions, words in the lights, all dark = fine, lit legends link to their cause and never toggle. **Capacity stated:** desktop 3 servers as columns; phone 4 servers as rows; beyond that, calm servers fold into one row. A sixth subject needs a redraw (unchanged from pass 4).
- **H7 Timelines.** The tape, the log scrubber, the detail's lane and the week. NOW is a lit rule in a dark rim; events use the signal colours with a rim; hit areas ≥ 24 px desktop (the phone tape is one 44 px target to History).
- **H9 Shadows.** One kind: a hard offset shadow, light from top-left, only on the pulled module and sheets. At night the pulled module also gets a 1 px edge (pass-4 audit 9).
- **H12 Signature moments.** Two: the pulled module (400 ms) and racking in (first run and install, under 600 ms). Both a 120 ms change in Calm.
- **H14 Connections.** Drawn only on point or focus; broken always; marked found or yours; combed lanes; ≤ 6 per module with the rest counted on a plate.
- **H16 Capacity.** Board (above); rack (Auto fold past one screen); Running plate (any n; names 2 + "and n more"); tag rail (ladder: later alerts to one line, then warns to one row); cords (6); tape (24 h merges marks within 24 px; Last hour); week (merged marks with a count).
- **H17 Claims about the world.** Cords say found / yours / asked. "Waiting on nas" comes from the mounts. Proxy cords exist only while Proxy Manager is connected. "Used by" on folders and shares is from mounts.
- **H18 Names.** "Patch field" → **cord channel** (L owns "patch bay"). "Console" → **status column** (L, NV use "console"). "Patch board" (detail) → **cord panel**. Tags hang on the **tag rail**. "Console ladder" → **tag ladder**.
- Not applicable: H1, H3, H4, H6 (the log and History follow its spirit: no cards, no orange, a designed end), H8, H10, H11, H13, H15.

## Rules I broke

| Rule (source) | What I did instead | Why Jam-Dash needed it | Verdict |
|---|---|---|---|
| **CL4 / brief cream `#f3e6c8`** for every lit window | Day lit windows use `#ebcd8a` | Cream on a light face is 1.1:1 and reads only through its rim; a lit job slot must be seen at a glance | **Language (role); value app-local per mode.** Worth checking Callsheet's Day sheet against the same problem. |
| **CL11 note "JD6 dark cabinet in Day"** (my own pass-4 choice) | Day is lab grey: light cabinet, dark windows only | Pass 4's Day read as "night mode stuck on" | Pass-4 break **withdrawn**; CL11 holds as written. |
| **CT12 One sheet form per device** | Updates, installs and first run use the **bench**, a full panel beside the rack, not a sheet | They are long jobs that change a rack; you need to see where | **App-local** (pass 4 had it for updates; now installs and first run too) |
| **LY2 / D26 "every place visible, ≤ 5 phone tabs"** | Shares lives inside the Files tab on the phone; Settings is a gear in the top bar | Seven places, five tabs | **Device: phone**, with the rule reworded: "a place may live inside another tab if that tab shows it on its first screen" |
| **IN1 lights are indicators** | Focusing or pointing at a module draws its cords | A cord is a drawing, not a light; nothing toggles | Not a break; noted for H14 |
| **CT6 never the same value twice** | The Running plate says "Running · 25"; the board says "All up" (no number) | — | Held. The plate is the only count. |
| **D140 a count once** (pass-4 refinement) | The cluster mark shows "3" and the readout says "3 events…" after pressing | The mark is a control; the readout is its result | **Language clarification:** a control's label may state the count its result names |
| **TY5 names wrap** | Held, but the phone Running plate and Stopped plate names wrap to 2 lines at 450 px | — | Held |
| **SM6 the black ribbed band** | Tape is a light strip by day | Same Day reason | **App-local** (night keeps the band) |

## Audit
Checked with Playwright (Chromium, `chromium.launch()`, no options): page widths 1500 (light scheme) and 390 (dark scheme); all four situations × Day / Night × 1440 / 1280; phone frames; every screen in section 4 in Day and Night. Flows: cord focus on Proxy Manager (Trouble and Busy) and Sonarr; tape cluster → Last hour; Running plate open; Draw a cord (pick Music Assistant, add); answer the suggestion; update flow; install with a port conflict then success; Edit setup port conflict, Replace secret, Remove sheet + Escape; first run with the failed code then connect; log pause, new-line count and search; History mark select. Screenshots are in the scratchpad (`p5jd/shots/`).

**Results:** no JS errors; no horizontal page scroll at 390; no text under 12 px (the ▲ and ⌘K glyphs are 12); every phone target ≥ 44 × 44 after the fix pass; no overflowing phone bodies.

**Fix pass (one round):** the cabinet's walnut cheek landed in the wrong grid column (a definite-row item auto-placed first) and the same bug hit the Running plate's ears; the page's `.row` class gave the phone's tag rows a 16 px top margin; the phone head unit repeated the server name; the tape label wrapped the zoom keys; the History axis collapsed; the setup save bar didn't stick (an `overflow` on its parent); week marks overlapped and stole clicks (now merged); the Day ghost outline was 2.72:1 (now 3.49); two phone keys were 43 and 34 px wide; ghost-to-ghost cords cluttered the offline rack.

**Contrast (computed from tokens):** legend on recess 7.46 day / 6.85 night · ink2 on face 8.08 · cab-ink2 on cabinet 6.31 day / 9.25 night · warn-ink 6.45 · alert-ink 6.22 (log 6.39 day / 7.58 night) · tape labels 7.59 day / 9.66 night · cords on channel 7.25 · ink on red 5.52, on orange 6.06 / 6.79, on amber 10.15, on day lit 11.05 · address cream on recess 13.46 · groove ring 3.43 · ghost outline 3.49 · night ink3 on face 4.93.

| # | Problem | Severity |
|---|---|---|
| 1 | **Proxy cords need Proxy Manager's API**, which means a key typed in Connections. Without it Jam-Dash shows no proxy cords, and the note says so. Other proxies (Caddy, Traefik labels) aren't covered: Traefik labels are readable from Docker, Caddyfiles aren't. | Medium |
| 2 | **A bundled lane hides which branch is which** until you look at the partner outlines and the note. Six cords 4 px apart are traceable at 1440; at 1280 scale they're close. | Medium |
| 3 | **The Running plate hides healthy apps' live state at a glance** (uptime moves into the shelf). An app that turns unhealthy leaves the plate and takes its place, which reorders the visible rack, though not your saved order. Needs a motion rule: it should slide out of the plate once. | Medium |
| 4 | **Phone Trouble still spends 570 px before the rack**: board 2 × 5, one full tag, two rows. The rack starts on the first screen, but only two modules show. | Low |
| 5 | **Overlapping spans on one tape lane** (Immich warn, then Code Server and Crafty alerts) read as one red block in Last hour; only the bars' rims separate them. A second row per lane, or start ticks, would fix it. | Medium |
| 6 | **Day lit windows rely on a deeper cream** that no other app uses yet. If Isaac wants one cream everywhere, the alternative is a dark-recess slot in Day (conflict 3 C) for running jobs only. | Medium |
| 7 | **Edit setup is drawn for Sonarr only.** An app with several containers (Immich: server + machine learning + database) needs one rear panel per container or a tabbed panel. Not drawn. | Medium |
| 8 | **Install on nas while its pool is 92 % full** only warns (it fits). There's no rule yet for when Jam-Dash should refuse. | Low |
| 9 | **Store catalogue size:** 11 apps drawn of "1,206". Search and categories carry it, but a long category (Media has hundreds) needs paging or a jump, which isn't drawn. | Medium |
| 10 | **Still not drawn:** Apps (the full list), System, Settings (Connections, Servers, Look), Global views, Custom app. Apps is partly answered by the Running plate's shelf and Find ⌘K. | Medium |
| 11 | **History groups**: "Tonight" spans two calendar days (Wed 18:00 to Thu 01:52). That's how people talk, but the strip labels are calendar days. | Low |
| 12 | The first-run code fails on purpose; a real wrong address ("nothing answered at nas:8484") has its own wording, not drawn. | Low |
| 13 | The mockup loads Jost and Plex Mono from Google Fonts; the product bundles them. | Low |

## Questions for Isaac
1. **Cords from real data only, with "yours" drawn hollow and guesses asked, never drawn?** *Recommendation: yes.* It keeps every line on screen honest (H17) and gives a housemate the right answer to "why is Jellyfin down?".
2. **Jam-Dash's Day as lab grey** (light enamel cabinet, dark windows only where there are words or numbers) instead of pass 4's dark cabinet? *Recommendation: yes.* It reads as Day (4.9 % dark pixels), and it still isn't Jam Home: lab grey and square rack faces, not Braun warm white with soft cards. Night stays the dark cabinet and black ribbed tape.
3. **A deeper Day cream (`#ebcd8a`) for lit windows on light faces?** *Recommendation: yes, as the Day value of the cream role,* and check Callsheet's Day sheet with it.
4. **The Running plate (Auto fold when a rack is taller than the screen)?** *Recommendation: yes,* with Auto / Always / Never in Settings and "Keep in view" per app.
5. **Edit setup as the module's rear panel?** *Recommendation: yes.* It keeps setup on the same object, and cords and secrets live where wiring lives.
6. **Phone: Shares inside the Files tab, Settings behind the top-bar gear?** *Recommendation: yes,* and reword LY2 so a place can live inside another tab that shows it on its first screen.
7. **History's week of tape over a reading list?** *Recommendation: yes.* The same marks at every zoom (tape, log scrubber, week) make it one thing.
8. **Should Jam-Dash refuse an install when a disk is over 95 %?** *Recommendation: warn up to 95 %, refuse above, and say how much to free.*
