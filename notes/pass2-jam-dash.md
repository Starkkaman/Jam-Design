# Jam-Dash · Pass 2

Mockup: `mockups/pass2/jam-dash.html` (interactive). Pass 1 (`mockups/pass1/jam-dash.html`) is unchanged.

The page draws:
- **Home** in three frames: desktop 1440 × 900, desktop 1280 × 800 and phone 390 × 844.
- **App detail**: desktop Crafty (alert) and phone Immich (warn).
- **Store and updates**: desktop and phone.
- **Files + Shares**: desktop and phone.
- A **state-words table** and the density ladder.

Page controls:
- **Lighting:** Day / Night.
- **Situation:** Trouble / All good / nas offline / Busy day (40 apps).
- **Readings:** Still / Live.
- **Motion:** Full / Calm.

Each desktop Home caption shows which density step that frame reached and whether it fits.

All apps, numbers, log lines, files and share paths are made-up sample data. The host names are only the README's "home-server" and "nas" (AGENTS rule 5). I dropped "Attic", the third server in the README's Global screenshot, because it isn't one of the README's named sample hosts.

Sources read:
- `notes/OVERNIGHT-BRIEF.md`, `CHANGES.md` A, B and D (all of it), the last ~60 lines of `decisions.md`, and `BIBLE.md` 0.5.
- `projects/jam-dash/README.md` (there is still no PROPOSALS.md), and these screenshots: Global Home desktop and Home alert phone. Also the Jam Braun phone Living (dark) screenshot.
- Every `notes/pass1-*.md`: TV, Callsheet, JamFin, Jam-Dash, NervOS and HA.
- The pass-1 Jam-Dash mockup, which this pass builds on.

## What changed since pass 1
Pass 1's audit was the to-do list. Every High item and every listed Medium is addressed.

| Pass-1 item | Severity | What pass 2 does | Result (measured) |
|---|---|---|---|
| #1 Desktop Home only just fits 1440 × 900, with no rule for what shrinks | High | **Density ladder.** After each render, Home checks whether it overflows and gives things up in a fixed order until it fits: (1) tiles drop their CPU · memory line, (2) live previews become normal tiles with a short word ("42 MB/s", "Playing"), (3) stopped chips fold into one "14 stopped" link, (4) faceplates go tight. **Never shrinks:** the hero, trouble cards, the "To look at" line, state words, Open keys, the disk meter. **Columns never grow** (tile ≥ ~190 px). After step 4 the page scrolls. | 1440 × 900: Trouble fits at step 1; All good and nas offline fit at step 0. 1280 × 800: Trouble fits at step 4; nas offline at step 1; All good at step 0. Busy day (40 running, 3 alerts) is still 262 px over at 1440 and 362 px over at 1280, so it scrolls. Trouble stays on the first screen. |
| #2 State words don't fit containers or match the bible | High | **Warn** (D21) added as an amber **triangle window** plus the word. Every state has three lengths: a lab word (On / Off / Working / Warn / Alert / Offline), a **short word of 14 characters or fewer** for tiles ("Running · 12 d", "Unhealthy", "Crashed", "Partly up", "Almost full", "42 MB/s"), and a sentence for cards and detail. The table is in section 3 of the mockup. "Stopped unexpectedly" (20 characters) becomes "Crashed" on tiles and stays in the detail. | No state word is cut off at any frame width, light or dark, in any of the four situations. (Checked by script: scrollWidth vs clientWidth on every state span.) |
| #3 Phone Home ~2,160 px, nas three screens down | High | **Server strip:** a ribbed band at the top of phone Home with one row per server (LED, name, "12 running · 2 alerts", a disk mini-meter). A tap jumps to that server. Tiles become two-column name rows (name, LED + short word, 44 px Open key). Numbers live in the detail. Live previews use their short word. | Trouble: 1,463 px (was ~2,160). The nas section starts at 1,145 px (1.6 screens of a 695 px body), but nas's state and disk are on the **first** screen in the strip. All good: 1,125 px. Offline: 1,353 px. Busy day: 2,228 px. |
| #4 Crafty said twice (card + tile) | Medium | The reason and the fix live **only on the card**. On desktop the alert tile keeps its place as a marker: red ring + LED + short word, with no numbers and no buttons. On the phone the alert app **leaves the grid**, and the server heading says "2 up top". | |
| #5 Warn has no card | Medium | A quiet **"To look at"** line under the trouble cards (desktop). On the phone, warns are rows under the first card. The line says "310 GB left" while the faceplate says "92%", so it's not the same value twice. The hero no longer mentions the disk; it counts "2 to look at" in the sub line. | |
| #6 Which alert gets the orange | Medium | D23 implemented exactly: **alerts newest first → offline servers → warns (an app's before a disk's)**. Busy day shows it: Ollama crashed at 01:51, so it takes the button from Crafty (01:49). nas offline with no alerts: Try again is orange. After both alerts are fixed, the orange moves to "Start the worker" in the "To look at" line. | |
| #7 Destructive style | Medium | D24 applied to **Stop…, Remove… and Delete…**: dark ink, in a sheet that names the consequence. Remove keeps the data folder unless you tick "Also delete its data folder", and the button text changes to "Remove and delete data". | |
| #8 Night faceplates barely separate | Medium | Night band `#0b0b0a` (was `#121211`), a 1 px top highlight (`#ffffff24`), a hairline edge `#43423e`, and stronger night ribs (1 px at ~9% white every 7 px). The same treatment is on the phone strip. | Band vs ground: 1.15:1 (was 1.10:1). Edge vs ground: 1.70:1. band-dim text on the band: 8.0:1. See audit #2: still marginal. |
| #9 Glyphs are mono initials | Medium | **Neutral line glyphs per kind of app** (play, download, music, game, code, shield, photo, git, cloud…) in the toned band frame. Never a brand mark (D34). | |
| #10 Tile numbers at the floor (13 px) | Medium | 14 px mono, and they're the first thing the ladder drops. | |
| #11 Sonarr's week used squares | Low | Small **slots** (D28). | |
| #12 Two oranges behind the veil | Low | While a sheet is open, every primary on the page behind it is drawn as secondary. Only the sheet has orange. | |
| #13 Live values vs "nothing animates per tick" | Low | **Readings: Live** demonstrates the step rule. The readout text updates every 5 s, and the bar moves only when the value changes by 3 or more points (one 400 ms settle, no loop). | |
| #14 Not drawn | Medium | **Files + Shares** are now drawn (one place, two tabs, on both sizes). Apps, System, Settings, Find and Sign in are still stubs. | |
| #16 Offline Try again always succeeds | Low | The first Try again fails ("Still not answering · tried 01:54. Check that it's switched on and its network cable is in."). The second one succeeds. | |
| Store: update all + failure | Suggestion | Each update row has a **one-line "what's new"**. Update all runs: Crafty and Sonarr update, but Immich's new version fails its health check and is **rolled back**. The row turns warn ("It went back to 1.119.0 and is running as before") with Show log and Try again, and Try again takes the orange. A single Update from the detail opens a sheet that shows what's new first. | |

## Research
I used **WebSearch** (15 searches) this pass. Most results were vendor docs, release notes, app-store listings and forum threads, and a few were comparison blogs, which I've flagged. I didn't open any product live. Items marked *(knowledge)* are from my own knowledge, not a search. Pass 1 covered CasaOS, Umbrel (old), Portainer, Dockge (single host), the Unraid Docker tab, Cosmos, Yacht, TrueNAS and Runtipi. This pass goes wider: multi-host managers, status dashboards and phone ops apps.

| Product | What I found | Lesson for Jam-Dash |
|---|---|---|
| **Komodo** (web: komo.do docs, virtualizationhowto review) | One Core plus a small "Periphery" agent on each server, with no limit on servers. The **Containers page shows every container from every host together**, so you don't need to know which host runs it. It alerts on CPU, memory and disk per server. Reviewers call it more than a single small host needs. | Confirms "Home *is* the global view" (one list across hosts, the server as a fact on the row). Komodo's per-server resource alerts are the same idea as the disk warn. |
| **Dockge 1.4+ agents** (web: fork READMEs, bitdoze guide; the version is disputed, 1.4 vs 1.5) | Remote hosts run a Dockge agent and are added on an Agents page. Their stacks then **appear in the main list alongside local ones**. | Multi-host managers converge on a merged list. What none of these show is a calm per-server summary, which is where the faceplates and strip come in. |
| **Portainer Home** (web: docs.portainer.io 2.41 and 3.0) | One **card per environment** with an Up/Down badge (Heartbeat/Down for Edge agents), a container count, and CPU/memory. | The environment card is a faceplate. A **word on the badge** (Up/Down) is the norm, not just a colour. |
| **Coolify v4** (web: coolify.io docs; CooliApp, Coolifer and Coolify Manager App Store listings) | One instance manages many servers over SSH. The docs say **running apps keep running if the dashboard goes down**. Its third-party phone apps lead with "which servers are online", deployment states (queued / in progress / completed) and **home-screen health widgets**. | The offline copy ("Its apps may still be running; Jam-Dash just can't see them") is the right truth. On phones, people want the server-level answer first, which supports the strip. |
| **Umbrel 1.x** (web: umbrelOS 1.0 release notes, nobsbitcoin) | Home-screen widgets, ⌘K search everywhere, right-click quick actions, and **update progress drawn inside the app icon**. | Progress in place (D29), on the thing itself. Jam-Dash puts it in the button's slot and the tile's LED. |
| **ZimaOS / CasaOS** (web: ZimaSpace's own comparison guides, which are marketing; one third-party review) | IceWhale frames them as **parallel products**: CasaOS is a dashboard on your own Linux, and ZimaOS is a full NAS OS that keeps the same store and UI. They mention widgets for quick system monitoring, but nothing about health states. | The CasaOS lineage still doesn't show health well. Jam-Dash's job is CasaOS's simplicity *plus* state. |
| **TrueNAS SCALE apps** (web: TrueNAS docs 24.04/24.10/25.04, linuxiac) | Apps moved from Kubernetes to Docker in 24.10. The Installed screen flags updates with a **yellow "!" badge** and Update / Update All buttons. Every app has Application Info and Workloads widgets. Apps on 24.10.2.1 or earlier stopped receiving updates. | An "update ready" mark has to be true, and it isn't a warning colour (a TrueNAS yellow "!" reads as trouble). Jam-Dash keeps "update ready" a fact with no light. |
| **Unraid 7** (web: Unraid forum bug reports, a Chrome-extension listing) | Recurring forum reports of **"update available" that isn't real** (an apply re-creates the container and pulls nothing), and API update status returning null until a fix. A third-party extension shows updates as an orange dot. 7.2.5-rc.1 hides stale dead containers. | The same lesson as pass 1, now with more evidence: badge trust erodes fast. A failed or rolled-back update must say exactly what happened. |
| **Homepage / Dashy / Homarr** (web: gethomepage repo, dashy.to docs, homarr.dev docs; Homarr's 1.0 status was unclear) | Homepage: container status and stats via the socket and **labels**. Dashy: an optional status **dot next to each item, with the reason on hover** (response time, the error). Its colours come from `--success / --warning / --danger`. Homarr: a What's Up Docker integration counts containers with updates. | Status dashboards rely on a coloured dot, with the reason hidden on hover. Jam-Dash should do the opposite: **word + shape on the tile, reason on the card**, nothing behind hover. |
| **Uptime Kuma status pages** (web: its internal API wiki, a community post) | Monitors are grouped, with per-monitor uptime (24 h) and a heartbeat history. A community description of its colours: green = operational, **yellow = retry pending**, blue = maintenance. *(knowledge)* The page headline says "All Systems Operational" (or degraded). | A calm **headline sentence** is the standard "all good". Kuma's yellow "retry pending" is a real third state between up and down, which matches **warn**. |
| **Phone ops apps** (web: App Store listings for Unraid Deck, unArgus, Unraid Manager; NOVA on F-Droid) | All lead with **server state → containers list with start / stop / restart**, batch actions, and push notifications for system alerts. None is official from Unraid. | The phone's first job is "which server, and is it OK", then one tap to act. That's the strip plus the first trouble card. |
| **Jam Braun** (this repo) | Calm charcoal cards, an orange primary, scene pills. | The calm baseline. Pass 2 keeps the trouble card as the only loud element. |

Sources: [komo.do docs](https://komo.do/docs/intro), [virtualizationhowto on Komodo](https://www.virtualizationhowto.com/2024/12/portainer-alternative-komodo-for-docker-stack-management-and-deployment/), [Dockge agents (bitdoze)](https://www.bitdoze.com/dockge-install/), [Portainer Home docs](https://docs.portainer.io/sts/user/home), [Coolify docs](https://coolify.io/docs/core/what-is-coolify), [CooliApp](https://apps.apple.com/th/app/cooliapp/id6759116923), [umbrelOS 1.0](https://nobsbitcoin.com/umbrelos-v1-0), [Umbrel releases](https://github.com/getumbrel/umbrel/releases), [CasaOS vs ZimaOS (ZimaSpace)](https://shop.zimaspace.com/en-ca/blogs/zima-campaign-hub/casaos-vs-zimaos-choice-guide), [TrueNAS apps UI reference](https://www.truenas.com/docs/scale/25.04/scaleuireference/apps/), [TrueNAS 24.10 Docker move](https://linuxiac.com/truenas-scale-24-10-shifts-from-kubernetes-to-docker/), [Unraid false "update available"](https://forums.unraid.net/bug-reports/stable-releases/docker-containers-showing-update-available-when-there-is-none-r2027/), [Unraid API update status](https://forums.unraid.net/topic/199493-issue-getting-available-docker-updates-via-the-apiconnect/), [Homepage repo](https://github.com/gethomepage/homepage), [Dashy status indicators](https://dashy.to/docs/status-indicators), [Homarr WUD integration](https://homarr.dev/docs/integrations/whats-up-docker), [Uptime Kuma internal API](https://github.com/louislam/uptime-kuma/wiki/Internal-API), [Unraid Deck](https://apps.apple.com/app/unraid-deck/id6757081677), [unArgus](https://glls.github.io/projects/unargus).

## Design (what and why)
**Home: three situations, one structure.** From the top:
1. **Hero sentence.** It counts and never names: "Two apps need you." / "One server isn't answering." / "Nothing is down. Two things to look at." / "Everything is up." The mono sub line: "17 running fine on 2 servers · 2 to look at · checked 01:52". "Running fine" excludes warn apps.
2. **Trouble cards**, only for alerts and offline servers, in D23 order. Each card has the state LED, a lab ("Alert · home-server · 01:49" — the time is what sorts them), the title, one sentence of reason, then the actions. With three cards the actions move under the text so the reason stays readable. More than three adds a "N more need you" link.
3. **"To look at"**: one line of warns (triangle + sentence + one quiet action). This is where "needs a look, not urgent" lives. It isn't a card, so it never competes with the alerts.
4. **A faceplate per server** (the only ribbed surface): name, LED, "On · up 12 days", and CPU / Memory / Disk meters with their readouts riding them (D25). In a narrow column the meter labels stack.
5. **Tiles.** Glyph, name (full width), then LED + short word with the Open ↗ key at the end of that line. Moving Open off the name line was the fix pass's biggest win: names stopped truncating at 1440, except "Nginx Proxy Manager" at 1280 and on the phone.
6. **Stopped chips**, or "14 stopped" from ladder step 3.

**The three situations:**
- **Trouble:** Crafty unhealthy (01:49) and Code Server crashed (01:31) are cards. Immich partly running and nas's pool almost full are warns. Restart Crafty is orange. Restart → the button fills its cream slot → the card turns "Working", blinks 3 times, holds → turns "On" for 1.3 s → leaves (FLIP). The orange moves to Start Code Server, then to "Start the worker", and the hero follows ("Nothing is down. One thing to look at.").
- **All good:** no cards, no "To look at", **no orange**. The Stripes accent draws in once, top right, clear of the nav (D2, D22). Calm means there is no next thing to do: Open is on every tile.
- **nas offline:** "One server isn't answering." There's one dashed card with an orange Try again. nas's faceplate and every nas tile go dashed together, and "last seen 01:40" appears **once**, on the faceplate (D27). The tiles just say "Offline". The first Try again fails, and the card says what to check. The second one brings nas back.
- **Busy day** (stress test): 40 running apps and three alerts. Ollama is newest, so it gets the orange. The ladder runs to step 4 and the page scrolls. The hero, three cards and the warn line stay on the first screen.

**Phone Home.** Hero, then the **server strip** (both servers on the first screen, with a disk mini-meter that turns amber with ▲ at 90%), then the first trouble item as a card with the full-width orange button. The rest are rows (alerts, then warns, each with its lab line). Then each server: a heading ("home-server · 12 running · 2 up top") and a two-column grid of name tiles with 44 px Open keys, then "14 stopped". Alert apps leave the grid while their card is up top.

**App detail.** Same structure as pass 1, with the state words applied ("● ALERT Unhealthy", "▲ WARN Partly running", "● ON Running for 9 days").
- Immich gets a **Parts** card (four containers, each with its own LED and word), so "partly running" is concrete.
- Actions: the orange fix, Open, Update to x (opens a sheet showing what's new and the rollback promise), Stop… and Remove… (dark ink).
- The log has All lines / Problems only, and failing lines carry ▲.

**Store.**
- Updates first, each with a one-line "what's new". **Update all 3** is the orange button.
- The run shows success and a rollback (warn, not alert: the app is running as before).
- Then the catalog with neutral glyphs, and the install sheet with live checks. The nas pool shows the warn triangle "Apps pool is almost full · 310 GB left".
- The page behind the sheet loses its orange.

**Files + Shares.**
- Places from both servers plus network shares, crumbs, the list, and a preview panel.
- **Upload** is the screen's orange (the routine primary on Files). Delete… is dark ink in a sheet ("deleted for good; nas has no bin for shared folders").
- Shares is the second tab: share cards with the address and Copy. A share made in CasaOS gets a "Read-only here" badge. Network shares mounted here have an LED.
- With nas offline, nas places, shares and the mount go dashed, and the list says "Can't read this folder" with Try again / Go to home-server.

**Navigation.** Six places on desktop (Home, Apps, Store, Files, System, Settings), all visible, with an alert count on Home and a neutral update count on Store. Phone: five tabs with base windows, plus a labelled gear and Find in the header. Nothing sits behind "More" (D26).

**Look.** Simplified Braun Hi-Fi as before (CHANGES A1–A10). Jost and Plex Mono, flat cards, windows always a dark recess, ribs only on faceplates and the phone strip, one orange per screen (zero on a calm Home). Labels are 13 px (Jam-Dash's own floor, D30). The only 12 px text is the keycaps.

## Audit
Checked with Playwright (Chromium, `chromium.launch()`) at 1500 px (deviceScaleFactor 1.4) and 390 px (dark scheme). I ran all four situations in Day and Night, plus these flows: Restart Crafty → card leaves → the orange moves; Update all in the Store → Immich rolls back; the install sheet on nas; Remove… on desktop; Stop… on the phone; and a scrolled phone Home.

Results:
- No JS errors.
- No horizontal page scroll at 390, and no horizontal overflow inside any frame body.
- No text under 13 px inside the frames (keycaps are 12 px and excluded).
- No phone button or input under 44 × 44.
- No state word truncated. The only truncated name is "Nginx Proxy Manager" (1280 and phone).

Contrast (computed):
- warn-ink `#7a5600` on the day card: 5.79. On the day ground: 5.09.
- dim on the day card: 5.22.
- band-dim on the night band: 8.01.
- Night band vs ground: 1.15 (was 1.10). Night edge vs ground: 1.70.

The fix pass corrected:
- tile names truncating everywhere (the Open key moved to the state line);
- ladder step "more columns" squeezing names to 60 px (the step was removed; columns never grow);
- nas faceplate meters overflowing their column (label + readout now stack in narrow columns; a cascade bug had overridden the container query);
- 1280 Trouble being 32 px over at the last step (tighter Home spacing);
- the hero repeating the offline card's title (now "One server isn't answering.");
- "Last seen 01:40" printed on every offline tile (now once);
- three trouble cards squeezing their reasons (actions go under the text);
- "running fine" counting the partly running app;
- the default file preview not matching any file;
- long live-preview words truncating (they use the short word on the state line).

| # | Problem | Severity |
|---|---|---|
| 1 | **A busy day still doesn't fit.** With 40 running apps and 3 alerts, the ladder runs out at step 4 and Home is 262 px over at 1440 and 362 px over at 1280. nas's tiles are below the fold on desktop. That's the honest limit of "every app as a tile". The hero, cards and warn line stay visible, but monitoring 40 tiles at a glance isn't solved. | High |
| 2 | **Night faceplates are better, not solved.** A black band on a near-black ground can't get far: 1.15:1. The "equipment front" now reads mostly because of the 1.70:1 hairline edge and the top highlight. On a dim, low-quality display the edge may vanish. | Medium |
| 3 | **Phone: the nas section is still 1.6 screens down** (1,145 px in Trouble). The strip puts nas's state and disk on the first screen and jumps there in one tap, but you still can't see nas's apps without scrolling. | Medium |
| 4 | **A calm Home has no orange.** This bends D23, whose last step is "the routine action". I put the routine primary only on screens that own one (Store: Update all; Files: Upload; detail: Open). It needs Isaac's call: is "nothing orange" calm or empty? | Medium |
| 5 | **The warn line can hold the screen's orange.** Once the alerts are fixed, "Start the worker" in the "To look at" line becomes orange. It works, but it's a small button in a quiet line, and it changes the line's weight. A warn card might be clearer at that moment. | Medium |
| 6 | **Two card layouts.** Two trouble cards have actions on the right; three have actions underneath. That's the same component in two shapes depending on count. | Low |
| 7 | **The triangle window is new** and small (13 × 12). It reads well lit, but it adds a fifth indicator shape to the bible's table, and its unlit form isn't defined (warn is always lit when shown). | Medium |
| 8 | **Generic glyphs repeat.** Crafty and Terraria share the game glyph, and Gitea and Gitea Runner share the git glyph. That's better than initials, but it isn't identity. The real product would tone each app's store icon. | Medium |
| 9 | **Long names truncate** ("Nginx Proxy Ma…") at 1280 and on the phone. The full name is in the title and the detail. A "short name" field in the app's setup would fix it. | Low |
| 10 | **Store heading:** "Updates ready · 1" sits over a row whose update *failed*. It should read "Updates · 1 didn't take". The toast also sits over catalog cards for 3.6 s. | Low |
| 11 | **Unlit phone tab windows** read as a row of black dashes in Day (same as HA pass-1 #10). | Low |
| 12 | **Offline nas tiles include Duplicati**, which was stopped before nas went away. It's correct (Jam-Dash can't know), but the dashed list grows by stopped apps, and the tile order shifts. | Low |
| 13 | **Live readings** only move the faceplate CPU meters. Tile numbers and the detail sparklines are static. The step rule isn't shown for disk crossing 90%. | Low |
| 14 | **Not drawn:** Apps (the dense table), System, Settings, Sign in, Find ⌘K, Custom app, the full-log sheet, the jobs strip, upload progress, move/rename sheets, and the phone file preview (a toast stands in). | Medium |
| 15 | **Hero count vs tiles:** the alert apps are counted in the hero, carded, and ringed in place on desktop. It's one value (the count) and two positions, but on a small desktop it still feels like a lot of red for two apps. | Low |
| 16 | Fonts load from Google Fonts in the mockup. The product bundles them (README constraint). | Low |

## Change suggestions for pass 3
- **Busy-day mode (#1, High).** Try a ladder step 5 that turns tiles into **one-line rows** in columns (LED + name + short word + Open, 40 px). Test it against Isaac's "can't monitor anything". Also try a compact server summary that collapses an all-green server to its faceplate plus "26 running, all fine · Show" while the other server has trouble. Measure both at 1280 × 800 with 40 apps.
- **Night faceplate (#2).** Try the faceplate a step *lighter* than the night ground (a card-coloured face with a ribbed band only behind the name), and compare it side by side with this pass.
- **Phone (#3).** Try the strip as a **sticky** header that collapses to one line on scroll, and server tabs (home-server / nas, base windows) instead of one long list.
- **Calm orange (#4) and warn weight (#5).** Show Isaac two calm Homes (no orange vs "Review 3 updates" orange) and two post-alert states (warn line vs a warn card).
- **Draw Apps** as the dense table (state word, server, address as a link, update column, a bulk bar). **Draw System** as faceplates enlarged with 10-minute graphs and the disk crossing 90% live.
- **Store:** the "1 didn't take" heading, a changelog sheet per update, and "Update all" across both servers with one server offline.
- **Icons:** real store icons toned into the band frame, checked against D34 (no brand marks) and the glare rule.
- **Trouble card:** one shape at every count (actions always under the text), or switch to rows above 2.
- Shared component with Callsheet: the trouble card and "To look at" line as one Hi-Fi component (LED + lab + title + reason + one action).

## Bible implications
1. **Add warn to the state words (confirms D21)**, with its own shape: an **amber triangle window** plus the word. Alert stays round + red + ring. The indicator-shape table gains a row (triangle = "needs a look").
2. **State words come in three lengths.** A shared lab word (On / Off / Working / Warn / Alert / Offline), a per-app **short word of 14 characters or fewer** for tiles and rows, and a sentence for cards and detail pages. The hook is shared; each app writes its own table (Jam-Dash's is in the mockup).
3. **A density ladder for dashboards.** When a dashboard doesn't fit, it gives things up in a fixed, published order (numbers → previews → collapsed lists → tight headers), and it names what never shrinks (the hero, trouble, state words, the primary keys). Columns never grow past the minimum readable tile.
4. **D23, made precise.** Alerts newest first → offline → warns (an app's warn before a disk's) → the routine action, **but only on screens that own one**. A calm overview has no orange.
5. **Trouble is said once on a screen.** The reason and the fix live on the trouble card. The item's own tile keeps its place as a marker (word only) on large screens and leaves the grid on phones. The hero counts and never names.
6. **One orange per frame, including behind sheets.** While a sheet is open, the page's primary is drawn as secondary (settles D39 "at most one per popup or sheet").
7. **Destructive actions (extends D24).** Data loss is opt-in inside the confirm sheet (a checkbox, off by default). The button wording names the result ("Remove and delete data"), and the sheet always says what stays.
8. **Night bands need an edge.** A black ribbed band on the night ground gets a hairline edge and a 1 px top highlight, and night ribs are stronger than day ribs. (Band `#0b0b0a`, edge `#43423e`, highlight `#ffffff24`.)
9. **Live meters step, they don't stream.** Readouts update as text. A bar moves only on a real change (≥ 3 points) with one settle, and crossing a threshold changes the state in one step. This is the dashboard form of "nothing animates per metrics tick".
10. **A group says "last seen" once (refines D27).** The offline group's header or card carries "Last seen" and Try again. Member items show only the word "Offline". Try again can fail and must say what to check.
11. **A rolled-back change is warn, not alert.** Alert means something people rely on is down now. A failed update that put the old version back is "needs a look".
12. **Phone overviews with several groups start with a group strip.** One ribbed row per group (state, count, its key meter) that jumps to the group. This is per group, not the rejected per-app monitoring row.
13. **Apps without art get a neutral category glyph** in the toned band frame, never initials and never a brand mark (extends D34).
