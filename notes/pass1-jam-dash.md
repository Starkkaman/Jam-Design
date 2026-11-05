# Jam-Dash · Pass 1

Mockup: `mockups/pass1/jam-dash.html` (interactive). It has a jobs table, then Home across both servers (desktop 1440 × 900 and phone 390 × 844), App detail for an unhealthy app (desktop and phone), and the Store with its install sheet (desktop and phone). The page controls switch:
- **Lighting:** Day / Night.
- **Situation:** two apps down with the disk filling / everything up / nas not answering.
- **Motion:** Full / Calm.

The apps, numbers and log lines are made-up sample data. The host names are the README's "home-server" and "nas", not the real ones (AGENTS rule 5, and the product must be shareable).

Sources read: `projects/jam-dash/README.md` (there is no PROPOSALS.md yet) and these screenshots: Home alert (desktop, phone), App detail alert, Global Home, Store and System. Also `BIBLE.md` 0.5, `CHANGES.md` A–D, the end of `decisions.md`, `_hifi-base.css`, the Callsheet pass-1 mockup (for the shared shell), the Jam Braun phone screen, and the pass-1 notes for TV, Callsheet and JamFin.

## Research
I ran three web searches. The results were mostly community threads and comparison blogs, not vendor docs. Items marked *(knowledge)* come from my own knowledge, not from a search. I didn't open any of these products live.

| Product | Good at | Bad at | Lesson for Jam-Dash |
|---|---|---|---|
| **CasaOS** (web + knowledge) | Opening an app: the tile *is* the launcher. One-click store install. Friendly to non-technical people, which is why it's the usual "beginner" pick. | Health is barely shown: a tile looks the same running or unhealthy. Logs and ports are buried. One machine only. Updates are opaque. | Keep "the tile opens the app", and add the state that CasaOS hides. |
| **Umbrel** (web: It's FOSS review, forum) | A polished home screen and a curated store. | A forum user calls it "very basic"; you quickly reach the limits of what it can do. There's little depth for troubleshooting, and it's one device. | Calm is fine, but trouble must have depth one click away. |
| **Portainer** (web + knowledge) | A full container table with state badges (running, stopped, healthy, unhealthy) and quick actions (logs, inspect, stats, console). Published ports show as links in the row. Multi-environment. | Dense and full of jargon, with small text. "Is everything up?" means reading a table. It feels like an admin tool, not a house tool. | Ports as links is the right "Open". The state needs a word and a shape, not just a badge colour. |
| **Dockge** (web: dev.to, Big Bear forum) | Compose-first. The stack list sits on the left, the editor and live terminal output on the right, so you watch an install or update happen. Light (it reports about 30 MB idle, unverified). | No resource overview, no store, nothing about "everything up". | Show a job's progress *in place* (the button and the card), not in a hidden jobs page. |
| **Unraid Docker tab** (web: Unraid forum + plugin pages; knowledge) | One row per container with icon, state, an **update-ready column**, port mappings and autostart. "Check for updates" and "Update all". Plugins add batch update and changelog chips. | Forum bug reports of stale "update available" badges, and of containers flagged when the image was current. Trust in the badge erodes. | Updates are a first-class list with a batch action, and the badge has to be true. |
| **Cosmos** (web: comparison blogs) | Gateway plus manager: reverse proxy, HTTPS, SSO and monitoring, with each app's URL first-class. Imports compose stacks. | More gateway than dashboard. A launcher is not its focus. | An app's address belongs on the app, with Copy. |
| **Yacht** *(knowledge)* | Portainer-lite, with templates and per-container resource charts. | Development slowed. Few states shown. | Nothing new. Confirms per-app resource graphs belong on detail, not Home. |
| **TrueNAS SCALE Apps** *(knowledge; the search found nothing)* | The Installed list shows state, CPU and memory per app, an "Update available" badge and Update all. Each app has a **Web Portal** button. | The detail splits into many cards (workloads, history, notes). Errors show as a state with the reason hidden in events. | "Open" (Web Portal) is the first button, and the reason for an error must be on the first screen. |
| **Runtipi** (web: comparison blogs) | A simple single-box store with per-app update status. | Adding a custom stack to the catalog is reported as hard (sources disagree). | Custom apps stay first-class (Jam-Dash already has Form / Paste / GitHub). |

**What goes wrong today, from Jam-Dash's own screenshots and README:**
- On desktop, Depth's dock shows Home, Apps, Store, Files, Shares and System but **no Settings**. Global's dock shows only Home, Apps and System. Settings is reachable only from somewhere else. That is the "hidden items" problem.
- The dock floats over content (Store and Global tiles sit under it).
- On the phone, Home shows 1 of 13 running apps on the first screen (README open question 5).
- In Global, the nas pools at 95% and 92% are shown only as long bars and red-ish numbers, not as something that needs you.

## Design (what and why)
**The jobs first.** The table at the top of the mockup lists five jobs:
1. **Is everything up?** Most visits.
2. **Open an app.** Everyone.
3. **Fix the broken one.**
4. **Install or update.**
5. **Check disk.**

Isaac does all five. The housemates mostly do 1 and 2, and they arrive when something they use is down. So Home has to answer "is it up?" in one sentence, open any app in one click, and put the fix one click away.

**Home (both servers on one screen).** From the top:
1. **One sentence** ("2 apps need you, and nas is almost full."), with a mono line under it: "18 apps running fine on 2 servers · checked 01:52". This is the same hero as Callsheet's Today.
2. **Trouble cards**, only for things you fix now: alert apps and unreachable servers. Each card has the state LED, a lab ("Alert · home-server"), the title, one sentence of reason, and its actions. **The first card holds the one orange button** ("Restart Crafty ↵"), with "Why?" under it. The order is alerts first, then offline servers.
3. **A black ribbed faceplate per server**: name, LED, "On · up 12 days", then three read-only meters (CPU, Memory, Disk / Apps pool). Each meter's readout rides it. A disk at 90% or more turns its meter amber and adds "▲ Almost full". The faceplate is the only ribbed surface on the page.
4. **Every running app as a tile** under its server: a glyph, the name, LED + words ("Running · 12 d"), and CPU · memory in mono. **Every running tile has an ↗ Open key.** The tile body opens the detail.
   - Live previews: SABnzbd (slot light + speed + queue bars) and Music Assistant (slot + now playing) are wide tiles. Sonarr is a normal tile with a week strip.
   - Alert tiles keep their place in the grid, with a red ring and the word, so the layout never reshuffles when something breaks.
5. **Stopped apps** as one line of chips (unlit LED + name), then "All 14 in Apps".

**Jobs in place, and the moving primary.** Restart Crafty shows the job where you pressed it:
- The button turns into "Restarting…" with a cream slot filling along its bottom (the light reveal, flat).
- The card and the tile switch to **action**: a cream LED that blinks 3 times, then holds.
- Then the card turns **on** ("Crafty is running again"), holds 1.3 s, and leaves. The remaining cards slide into place (FLIP, transform only).
- The orange button moves to "Start Code Server". A toast says "Crafty is running again" with Show log.
- When nothing is left, the sentence becomes "Everything is up." and **the Stripes accent draws in once**. The accent shows only when everything is up. While there's trouble, decoration steps back.

**Servers.** The desktop header has three pressed-in keys with square windows: Both / home-server / nas. This replaces Depth's separate Global view: Home *is* the global view, and one key narrows it. In the offline situation, nas's faceplate and its tiles take Jam Braun's offline form (dashed outline, no face, "Offline", "Last seen 01:40"), and a dashed trouble card offers Try again. That card animates through action and back to on.

**Navigation never hides.** On desktop, all seven places (Home, Apps, Store, Files, Shares, System, Settings) sit in the top bar, with an alert count on Home. Find ⌘K is in the bar too. On the phone there are five tabs with base windows (D12): Home, Apps, Store, Files, System. Settings is a labelled gear in the header, and Shares moves into Files as its second tab. Nothing sits behind "More".

**App detail (Crafty, unhealthy).** It reads top to bottom:
- Crumb: "‹ Home / home-server / Crafty".
- A head card with a red ring: name, server chip, "● ALERT Unhealthy", then the reason as a sentence.
- Actions: **Restart Crafty ↵** (orange), Open ↗, Update to 4.4.5, Stop… (asks first), and an Edit setup link.
- The log card (live slot light; All lines / Problems only keys; Full log). Failing lines carry a ▲ as well as the colour.
- On the right: Resources (CPU now + 10 min sparkline, memory "of a 4 GB limit" + sparkline), Address and ports (the address with Copy, then each port mapping and what it's for), and Facts (image and version, "4.4.5 is ready", data folder, 10 health-check windows with "Last 3 failed", restarts, server).

On a healthy app, **Open becomes the orange button** and Restart becomes secondary. On a stopped app, it's Start. Stop opens a sheet: "Stop Crafty? Anyone playing on the Minecraft server is disconnected…", with **Stop Crafty in dark ink** (not orange, not red) and Keep it running. On the phone the same page stacks, the primary is full width, and log lines wrap.

**Store.**
- It opens on **Updates ready · 2**: Crafty 4.4.4 → 4.4.5 ("it's unhealthy now; updating restarts it") and Immich. **Update both** is the screen's one orange button. Per-row Update is secondary.
- Then search and every category as keys. They wrap; nothing scrolls sideways.
- Then catalog cards with Get / Open / Details.
- **Get** opens the install sheet:
  - Where: home-server / nas keys.
  - Live checks, each with an LED and words: port free, folder to be made, disk space (warn on nas: "Apps pool is 92% full"), processor.
  - Install, then a progress bar through "Pulling the image… / Starting… / Installed and running", then Open (orange) + Done.

**Shared shell with Callsheet (siblings).** Both apps use:
- the same walnut trim and card header with underlined tabs, and Find with a ⌘K keycap;
- the same hero (40/36 px sentence + mono sub line);
- the same phone stoprows for the second and later items;
- the same toast;
- the same base-window phone tab bar;
- the same moving orange primary, with the ↵ keycap printed on it.

Keys on desktop: Enter = the orange button, 1–7 = places, Esc = back / close. As agreed in the Callsheet harmony note, Jam-Dash adds no app-switch links.

**Look.** Simplified Braun Hi-Fi (CHANGES A1–A10): flat cards with soft corners, Jost and Plex Mono, no grain, no glow, and ribs only on the faceplates. Windows are always a dark recess and light with flat colour. Orange appears once per screen. Jam-Dash's own floors apply: labels are 13 px (not the bible's 12), body 15+, 44 px targets on the phone.

## Audit
Checked with Playwright (Chromium) at page widths 1500 (light) and 390 (dark scheme), with Day and Night frames and all three situations. I ran these flows: Restart Crafty → card leaves → primary moves; Install sheet with nas chosen; Stop sheet on the phone. There were no JS errors and no horizontal page scroll at 390. Inside the app frames, nothing is under 13 px except the keycaps (12 px). Every phone button and input measures at least 44 × 44.

Key contrast pairs, measured:

| Text | On | Ratio |
|---|---|---|
| dim | card, day | 5.22 |
| dim | ground, day | 4.59 |
| dim | key, day / night | 4.68 / 4.70 |
| band-dim | band | 6.93 |
| alert ink | card, day / night | 5.70 / 5.44 |
| ink | orange, day / night | 6.06 / 6.79 |
| log failing lines | log box | 8.25 |

The fix pass corrected these: the trouble order (Crafty now comes first); faceplate meters overflowing in the narrow nas column and on the phone (now a container query that stacks them); the desktop Home running 186 px past the fold; the address row wrapping; the phone detail actions being clipped; the category keys scrolling sideways on the phone; the accent touching the header and the nas faceplate; and phone links narrower than 44 px.

| # | Problem | Severity |
|---|---|---|
| 1 | **The 1440 × 900 Home only just fits.** In the trouble state, the body's content is 834 px for an 832 px viewport. The stopped line sits at the fold. A third trouble card, a third live preview or a third server (the README's Global shows "Attic") pushes running tiles below the fold, which is exactly the "can't monitor anything" complaint. There's no density rule yet for what shrinks first. | High |
| 2 | **State words don't match the bible's list.** Tiles show "Running", "Stopped", "Restarting…" and "Unhealthy", with on/off/action/alert only as `data-state`. The detail mixes them ("● ALERT Unhealthy", "● ON Running for 9 days"). Jam-Dash also has states with no shared word: **partly running** (Immich in today's mock), **update ready** and **disk almost full** (warn). The bible says "same words", which doesn't survive contact with containers. | High |
| 3 | **Phone Home is long** (about 2,160 px). The first screen shows the trouble card, the Code Server row and the home-server faceplate. nas is about three screens down. The phone monitoring-row rule was not adopted, but without something like it, the second server is effectively hidden on the phone. | High |
| 4 | **Said twice, across panels.** Crafty is in the trouble card *and* as an alert tile. The tile keeps its place on purpose (spatial memory), and "never twice" is per panel, but on the phone they're a few hundred px apart and read as a repeat. The hero sentence and the faceplate's "▲ Almost full" also repeat the disk warn. | Medium |
| 5 | **Warn has no card.** I kept trouble cards for things you fix *now*. The disk warn lives in the sentence and on the faceplate meter. That's calm, but on the phone the nas faceplate is far below, so the only signal on the first screen is the sentence. | Medium |
| 6 | **Which alert gets the orange button.** The order here is: alerts newest first, then offline servers. You could argue "stopped" (Code Server, down entirely) beats "unhealthy" (Crafty, still half-working), or that an offline server beats both. It needs Isaac's call and a bible rule (D7). | Medium |
| 7 | **Destructive style is new.** Stop is a dark ink button in a confirm sheet. Jam-Dash today uses a red danger button, but red is reserved for alerts, and orange is the primary. The bible has no destructive style. | Medium |
| 8 | **Night faceplates barely separate.** The band `#121211` on the night ground `#1c1c1b` is a small step, and the ribs are nearly invisible at night. The faceplates lose their "equipment front" read. | Medium |
| 9 | **Glyphs are mono initials**, the same placeholder feel the TV audit flagged (#5). The real product would use each app's store icon, toned into the lightness band. | Medium |
| 10 | **The tile numbers sit at the floor.** CPU · memory is 13 px mono. Isaac's first complaint was "the text is too small". These numbers are the first thing to drop (into the detail) if tiles need to compact, which would also help #1. | Medium |
| 11 | **Sonarr's week strip uses square windows**, but in the bible a square means "a mode that's selected". Here it means "an episode that day". That's a shape misuse. | Low |
| 12 | **Two oranges behind the veil.** With the install sheet open, the Store's "Update both" is still orange under the 42% veil. It's one per layer, but two in the frame. | Low |
| 13 | **Live values vs "nothing animates per tick".** The meters fill once on arrival. In the real app, CPU changes every few seconds, so the bar will jump. Static redraws are allowed, but they need a smoothing or step rule so they don't flicker. | Low |
| 14 | Not drawn: Find ⌘K, Apps, Files, Shares, System, Settings, Sign in, Custom app, the full-log sheet, the jobs strip, and a third server. Global as a mode of Home (not a separate view) is a change to how Jam-Dash's HA add-on route works. | Medium |
| 15 | The mockup loads Jost and Plex Mono from Google Fonts. The product bundles its fonts (README constraint), so the real build must ship them. | Low |
| 16 | In the offline situation, "Try again" always succeeds and brings nas back with its pool at 92%. The failure path ("Still not answering · tried 01:54") isn't shown. | Low |

## Change suggestions for the next pass
- **Density ladder for Home** (fixes #1, #10): define what compacts first when the screen is full. (1) Tiles drop the numbers line. (2) Live previews shrink to normal tiles. (3) The stopped line collapses to "14 stopped". (4) Tiles go to 5 or 6 columns. Show a 3-server, 30-app stress case at 1440 × 900 and at 1280 × 800.
- **Phone Home** (#3): try a compact **server strip** at the top (one row per server: LED, name, "13 running · 1 alert", disk word) that jumps to that server's tiles. Also try two columns of name-only tiles with the Open key, and the numbers in the detail only.
- **Warn on the phone** (#5): a quiet warn row under the trouble card (amber LED, "nas apps pool almost full"). Compare it with the sentence-only version.
- **State words** (#2): write the Jam-Dash display table. Hook → lab word → tile phrase: on → On → "Running · 12 d"; off → Off → "Stopped"; action → Working → "Restarting…"; alert → Alert → "Unhealthy" / "Stopped unexpectedly"; offline → Offline → "Last seen 01:40"; warn → Warn → "Almost full" / "Partly running"; update ready → no state (a fact, shown in Store and Facts). Use it everywhere.
- **Night faceplate** (#8): try `#0f0f0e` with a 1 px top highlight, or the card colour with the ribbed band only as a 28 px strip behind the name.
- **Store**: design the "update everything" flow with a failure case (one update fails and rolls back), and a changelog line per update.
- **Apps and System** in the same parts: Apps as the dense table people reach for (state, server, ports as links, update column, the Unraid lesson); System as the faceplates enlarged with 10-minute graphs.
- **Callsheet ↔ Jam-Dash**: try one shared component on purpose, the trouble card. Callsheet's "Worth knowing" alert and Jam-Dash's alert card would use the same LED + lab + title + reason + one action grammar. Decide whether a Jam-Dash alert should appear in Callsheet's Worth knowing (not decided; Callsheet harmony currently says no cross-links).
- Real icons in a toned frame instead of initials, and an animation pass on the tile → detail transition (the tile grows into the head card; a window growing over a still picture is flash-safe).

## Bible implications
1. **State grammar needs "warn" and display words.** The five shared hooks stay, but the bible should add **warn** ("needs a look, not urgent": amber + ▲ + word). Callsheet's clashes (D5) and Jam-Dash's disks and "partly running" all need it. It should also say that the hook is shared and the *visible* word comes from a per-domain table ("Running" for a container, "On" for a light), with the lab word in small caps where space allows.
2. **Accents step back during trouble.** Extend D19: an accent shows only when its screen is calm. While any alert is open, the clear zone stays empty, and the accent draws in once when the screen becomes calm. That makes "everything is up" feel like an event, the way Callsheet's All clear does.
3. **Moving primary: an order.** Make D7 concrete: alert (newest first) → offline → warn → the routine next action (Open). It needs Isaac's call on stopped vs unhealthy.
4. **Destructive actions** are never orange and never red: a dark ink button inside a confirm sheet that names the consequence ("Anyone playing… is disconnected"). Red stays for alerts.
5. **A meter's readout riding it counts once.** Extend D15 from the player timeline to dashboard meters (CPU, memory, disk), so a faceplate can show a bar and its number.
6. **Navigation floor: no hidden destinations.** On desktop, every top-level place is visible in the bar, with no overflow menus or icon-only docks. Phone tab bars have five tabs at most, with the rest reachable from a *labelled* header control, never "More". This comes straight from "the navigation in depth is atrocious".
7. **Group offline form.** Extend Jam Braun 0.10's offline form (dashed hairline, no face, "Offline") from a card to a group: a server's faceplate and all its tiles go dashed together, with "Last seen" and Try again on one trouble card.
8. **Shape vocabulary gap.** The square means "selected mode". Day-presence strips (Sonarr's week, Callsheet's day band) need a defined shape. Proposal: small slots, which already mean "something running / scheduled".
9. **Jobs show progress in place.** A long action fills a cream slot along the bottom of the button that started it, and the item's LED goes to action, blinks 3 times, then holds. This is the flat light reveal for buttons, and it would serve Callsheet's Refresh and HA's scripts too.
10. **Label floor differs by app.** Jam-Dash's README sets labels at 13 px. The bible's §9 says 12 (labels 13 in the desk column, but §2 Type says uppercase labels at 12 px). Settle on 13 px for uppercase labels everywhere.
