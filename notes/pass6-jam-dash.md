# Jam-Dash · Round 6 (round 3's calm, with connections you can see)

Mockup: `mockups/pass6/jam-dash.html` (interactive). Earlier rounds are unchanged.

What the page draws:
- **Home**: desktop at 1440 × 900 or 1280 × 800, and phone 390 × 844. Four situations: **Trouble**, **All good**, **nas offline** and **Busy day · 40 apps**. Day and Night.
- **How the links work**: three short spec notes.
- **App detail** with its **Connections** map. It follows Situation: Crafty (alert), Jellyfin (waiting on nas) or Sonarr (all good, with an update, a guess Jam-Dash asks about, and Add a connection).
- **The density ladder on a busy day**: a fixed 1280 × 800 frame.
- **Not redrawn**: Store, Files, Shares, Full log, Edit setup, History and first run stay as round 3 drew them. Their tabs open a placeholder.

Page controls: Lighting Day / Night (follows the device until pressed), Situation, Desktop 1440 / 1280, Density Auto / Rows, Motion Full / Calm.

Sources read: the last entry of `decisions.md` (Isaac's notes after round 5), the Round 6 direction in `notes/OVERNIGHT-BRIEF.md`, `mockups/01-directions.html` panels B and D, `mockups/pass5/callsheet.html` (tokens, Day and Night), `notes/RULES-TIERS.md` §1, `projects/jam-dash/README.md`, `notes/pass3-jam-dash.md`, `notes/pass5-jam-dash.md`, `mockups/pass3/jam-dash.html` and `mockups/pass5/jam-dash.html`. I rendered both earlier mockups and pointed at Sonarr in round 5 to see the cords. I did no web research this round. The connection sources (Docker mounts, compose `depends_on`, Proxy Manager hosts) are the ones round 5 already set.

All data is made-up sample data. The only host names are "home-server" and "nas". Proxy hosts are `*.example.net`.

## How I read Isaac's notes

| Isaac said | What I did |
|---|---|
| "I think jam dash V3 is my favorite design" | I started again from round 3: the hero sentence, trouble cards with the actions underneath, "To look at", one server panel per server, tiles with the LED + state word and an Open key, app detail, and the density ladder. I reused the same sample data, words and loudness rules (red key on the newest alert, otherwise one orange, none when all is calm). |
| "the skumorphism is just too cheesy to work every day" | Round 4 and 5's rack, modules, cords, plates, tags and tape are gone. I also dropped round 3's own bits of realism: the ribbed black faceplates became a **flat navy band**, the dark glyph boxes became quiet tinted squares, there are no raised key shadows, and the top nav uses a plain 2 px underline instead of a lit slot. |
| "I do really like seeing how the different containers connect when I drag my mouse over one" | **The trace.** Pointing at an app (or Tab focus, or a tap on the phone) keeps the apps it **needs** and the apps that **use it** at full strength. Everything else dims to 28 %. Thin 1.5 px curves join them, ending in small rings at the card edges. The lines run **behind the cards**, so they only show in the gutters and faintly through dimmed cards. They never cross on top of a lit card. Each linked card gets one small word, `NEEDED` or `USES IT`. A **readout line** at the bottom of Home says it in words: "SONARR · Needs Prowlarr compose file · SABnzbd yours · nas › media mount … · Used by Bazarr compose file, stopped". |
| "Maybe there's an interesting way to do something in between?" | The "in between" is: lines only on request, flat and thin, with no objects to plug into. The data honesty from round 5 is kept (below). The app page gets a still version of the same idea, the **Connections map** (needs on the left, the app in the middle, used by on the right). That map replaces round 5's cord panel and its "Draw a cord" sheet. |
| (Round 6 direction) "Back off realism … bring the calmness back" from Braun / Flight Instrument | Flat surfaces with 1 px hairlines and no shadows at night. Mono labels. A single readout line like an instrument's. No accent graphic. Calm Home has no orange and no lines. |
| (Direction) Callsheet round 5's palette | Applied lightly. Day uses Callsheet's paper (`#f8f6f1` cards on `#ebe8e1`) with navy ink `#19202e`. Night uses Callsheet's navy (`#0c1018` ground, `#151b27` cards, `#ece5d3` ink). The server bands are navy ink by day and near-black navy at night. The walnut trim, one orange and red alert key are unchanged. |
| (Direction) "scrap almost all the lights … in menus" | There are no lights in the nav, tabs, pickers or keys. The LEDs that are left carry real status: an app's or server's state and the warn meter. Selected nav = an ink underline. Selected server = pressed in. |
| (Direction) "dense information … visually broken up" | Separate trouble cards, a "To look at" line, a band per server, and the tiles as separate cards. The readout is one line, not a panel. |

## What changed since round 3 (and what I kept from round 5)

| Round 3 | Round 6 | Why |
|---|---|---|
| Ribbed black faceplates (5 px ribs at night) | Flat navy band, no ribs. The name and up-time sit beside the meters on one row when the column is 640 px or wider. nas's band also lists its **shares** as small chips | Less texture. Shares need a place on Home so links to them can be drawn |
| Glyphs in dark squares, tiles with drop shadows | Glyphs in a tinted square, tiles with a 1 px hairline, shadow only by day and very faint | Calm. A screen of 20 dark squares was the noisiest thing in round 3 |
| Lit slot under the current nav item, count badges on tabs | Ink underline, no badges (the hero already says the count) | "Almost no lights in menus" |
| No connections | **Trace on Home** + **Connections map** on detail + **readout line** | Isaac's note |
| Five-step ladder | **Three steps**: Tiles (with live previews) → Compact (previews become plain tiles, stopped apps fold into a count) → Rows (37 px lines, 3 columns for home-server and 2 for nas, no link lines). **New floor:** Auto goes to Rows only with more than 24 running apps. Below that, Home scrolls under the panels instead | Round 3 audit 1: a laptop with 20 apps lost its tiles. Tiles are also where the lines work |
| Phone: the strip was the server picker | The phone band has a two-key picker (home-server \| nas) above that server's meters | Same job, no lights |
| (round 5) Cords: found / yours / asked | **Kept as data, redrawn as lines**: solid = found (mount, compose, Proxy Manager host); dashed 6/5 = yours (drawn by hand, dated, "Jam-Dash can't check it", Remove); amber dotted = broken right now. A guess is asked on the app page ("Does Sonarr tell Jellyfin to rescan? Both sit on the Docker network "media"") and never drawn | H17: a wrong line would mislead a housemate |
| (round 5) Broken cords always drawn | Broken links show as each waiting app's **state word** ("Waiting on nas", amber ▲) and in the offline card. Lines appear on point. **Show what waits** on the nas card pins the trace: every link across to nas, dotted amber, converging on nas's band, until Close or Esc | Always-drawn lines at rest broke "all good looks like nothing". The state words keep it honest at rest |

## Design

**Home (desktop).** From the top: hero sentence and a mono sub line ("17 running fine on 2 servers · 2 to look at · checked 01:52 · History"), then up to three trouble cards, then "To look at" (warns), then the servers side by side (home-server 2/3, nas 1/3). Each server is a navy band (state, up-time, OS, CPU / Memory / Disk meters; nas adds `Shared: media photos downloads music`), then its app tiles, then "n stopped". The **readout line** (50 px) is pinned to the bottom of the window. At rest it shows a one-line legend (found / yours / broken). In nas offline it says "6 apps on home-server wait on nas … Point at nas, or press Show what waits".

**The trace, exactly.**
- *Trigger:* mouse over a tile, row, stopped chip, share chip or server band, or keyboard focus on one (desktop). On the phone a first tap selects and a second tap opens. The ↗ key always opens the app.
- *What lights:* the focused node (ink border), the nodes linked to it (darker border), everything else at 28 % (chips inside the bands at 40 %). The hero, cards and "To look at" go to 55 %. The bands stay at full strength.
- *Lines:* cubic curves from edge to edge, bent away from the card (up to 110 px). Chips anchor top or bottom so lines don't run along the chip row. Lines sit under the cards and the end rings sit over them. They fade in once over 220 ms (none in Calm or with reduced motion).
- *Words:* `NEEDED` (the focused app needs it) or `USES IT`, on the linked tile's top-left corner, only when there are 8 links or fewer. The readout always names everything, with the source, and adds "stopped" or "nas isn't answering" where true. More than 6 on one side become a count: "Used by 13 apps Proxy Manager host: Jellyfin, Immich, Code Server, Home Box, Crafty and 8 more".
- *Server bands:* pointing at nas lights everything that crosses servers. Lines run to the band itself, not to each share, so they converge on one point. Stopped apps are left out and counted.
- *Rows:* no lines. The highlight and the readout carry it.

**Home (phone).** Hero → navy band with the server picker and that server's meters → the first trouble card → other alerts as one-line rows → "To look at · n" folded → that server's tiles in two columns. A tap selects a tile: links light, lines join the tiles of that server, and a **sheet** above the tab bar shows Needs / Used by with a "Sonarr's page" key and ×. The page scrolls so the tile stays above the sheet.

**App detail.** It's round 3's header card (glyph, name, server chip, LED + state, the why sentence, actions: the fix key, Open, Full log, Edit setup, Stop…). Then two columns. Left: **Connections** (the map, then "Asked, not drawn", then **Add a connection**: the app + needs / is used by + a list of apps and shares + Add, which draws it dashed as yours), then the last log lines. Right: Now (CPU, memory, up) and Facts. On the phone the map stacks vertically with vertical curves. Loudness: Crafty's Restart is the red key. Jellyfin while nas is away gets an orange "Try nas again". Sonarr gets an orange "Update to 4.0.11". The connection keys are plain.

**New elements that only make sense here:** the trace (dim + lines behind cards + NEEDED / USES IT), the readout line, the Connections map, and "Show what waits" (a pinned trace).

**Fit (Playwright, measured).**

| Size | Trouble | All good | nas offline | Busy day |
|---|---|---|---|---|
| 1440 × 900 | Compact, fits | Tiles, fits | Tiles, fits | Rows, 22 px below |
| 1280 × 800 | Compact, 117 px below (floor: 20 running < 24) | Tiles, fits | Compact, 128 px below | Rows, 122 px below |

In every case both server bands are on the first screen (round 3's first-screen promise). On the phone in Trouble the first row of tiles starts at about 690 px, just above the tab bar (round 3: 607 px).

## Language check
Jost + IBM Plex Mono only. Round LEDs for status only, each with a word; warn = amber LED + ▲; offline = dashed ring and dashed outline. Red key on the newest alert and nothing orange while it shows; one orange otherwise; none at rest. Walnut trim on top. Things end visibly ("14 stopped · Show them", "and 3 more"). Someone coming from Callsheet would recognise the paper and navy, the mono labels and the one-line readout within a second.

**Rules I broke**

| Rule | What I did | Why | Verdict |
|---|---|---|---|
| LY "every value once" | An app's state shows on its card and, when you point at a linked app, again in the readout ("stopped") | The readout is the answer to a question you asked; it's transient | App-local |
| RULES-TIERS #2 "unlit window is a recess" | Unlit (stopped) LEDs are a hairline ring in both themes, as Callsheet's Day sheet does | A dark dot on paper reads as "on" | Language (Day), as Callsheet already has it |
| Round 3 "Night bands with ribs" | Flat navy, no ribs | Isaac: less realism | Drop ribs here; other apps decide for themselves |
| D84 alert key — nothing else orange | Offline "Try again" is orange only when no alert shows | Unchanged from round 3 | Held |

## Audit
Checked with Playwright (Chromium, `chromium.launch()`): page at 1500 px (light scheme) and 390 px (dark scheme). Every situation × Day / Night × 1440 / 1280, plus phone and detail frames. Flows: point at Sonarr and Proxy Manager; focus Radarr by keyboard; Show what waits; point at Jellyfin and at the media share while nas is offline; phone tap on Sonarr; Restart Crafty; answer the guess (Yes) and Remove; Esc. Screenshots are in the scratchpad (`p6jd/`).

**Results:** no JS errors; no horizontal page scroll at 390 (scrollWidth 390); no text under 12 px (the smallest is the 12 px mono tag words and keycaps; body text is at least 13 px); every phone button ≥ 44 × 44 after the fix pass.

**Fix pass:** Trouble at 1440 fell to Rows because of the readout bar (51 px over), so I tightened the tiles to 77 px and put the band on one row. The phone memory reading ran into "DISK", so the meter reads 28 % instead of 9.5 GB. "Pool" replaced "Apps pool" (it was clipped in nas's band). Dimming also dimmed the server bands, which are now excluded. Lines across the share chips ran along the chip row, so chips anchor top/bottom. Lines drawn over lit cards were noisy, so they now run behind the cards. A `<button>` inside a `<button>` in the map broke the layout of "yours" nodes. Two phone links were under 44 px. A re-trace loop kept the phone sheet at opacity 0.

**Fresh-eyes pass ("would Isaac call any of this cheesy?"):** the bordered `NEEDED` / `USES IT` boxes read like little luggage tags, so they're now plain mono words on the ground colour. The stopped chips were cut from 7 to 6 so "All 14" stays on the line. The phone's "Waiting on nas" was cut off, so the phone tile says "Waiting" (the hero says "on nas"). Jellyfin's `WRN` log lines no longer use the alert ▲.

**Contrast (computed from tokens):** dim on card 5.82 day / 6.13 night; dim on ground 5.14 / 6.77; warn-ink on card 6.34 day; alert-ink 6.06 day / 7.53 night; band-dim on band 6.46 / 7.05; ink on red key 6.27; ink on orange 6.60; trace line on ground 13.3 / 14.3; broken (amber) line on ground 3.14 day / 11.35 night.

| # | Problem | Severity |
|---|---|---|
| 1 | **Dimmed cards are deliberately below contrast floors** (28 % opacity) while a trace is up. Their state words can't be read until you move away. That's acceptable for a transient highlight, but a screen reader user gets the same facts only from the readout (it's `aria-live`), not from the cards. | Medium |
| 2 | **Lines behind cards hide where they pass under a lit card.** Two linked apps with a third lit app between them (Proxy Manager's fan) show a line that disappears and reappears. The end rings and the words carry it, but tracing one line by eye is harder than in round 5's lanes. | Medium |
| 3 | **Proxy Manager's fan** (13 links in Trouble, 17 in Busy) is the busiest the screen gets: 7 lines plus 6 named only in the readout. It stays readable because the other cards dim, but it's still a fan. | Medium |
| 4 | **1280 × 800 now scrolls in Trouble (117 px) and nas offline (128 px)** because of the new floor (Rows only above 24 running apps). The bands stay on the first screen, but the last tile row is below it. | Medium |
| 5 | **The readout costs 50 px** of every desktop Home. Without it Trouble at 1440 fits at step 1. | Low |
| 6 | **Phone: first tap selects instead of opening.** It's a change from round 3, where a tap opened the app. The ↗ key still opens the app itself, and a second tap opens its page. | Medium |
| 7 | **Links to stopped and folded apps have no line**, only a name in the readout ("Bazarr compose file, stopped"). | Low |
| 8 | **Proxy Manager links depend on its API key** (Settings › Connections). Without it there are no proxy links, and the readout would need to say so. That wording isn't drawn. Caddy files and Traefik labels aren't covered (round 5 audit 1). | Medium |
| 9 | **Add a connection** is an inline row with a long `<select>` of every app. At 40 apps it needs search. | Low |
| 10 | The server bands keep a green LED beside the server name. It's real status, but on a calm day it's 2 of the screen's ~22 green LEDs. | Low |
| 11 | Store, Files, Shares, Full log, Edit setup, History and first run aren't redrawn in this look. Round 3's versions still have ribs and dark glyph squares. | Medium |
| 12 | The mockup loads Jost and Plex Mono from Google Fonts; the product bundles them. | Low |

## Questions for Isaac
1. **Is this the right "in between"?** Lines only while you point, thin and behind the cards, with everything unrelated dimmed and a one-line readout. *Recommendation: yes.* It keeps the part you liked (seeing what connects) and leaves an everyday screen with no lines at rest.
2. **Phone: tap once to see links, tap again to open?** *Recommendation: yes,* with the ↗ key still opening the app directly. The alternative is a long-press, which nobody finds.
3. **On a small laptop with about 20 apps, keep tiles and let Home scroll under the server panels** (instead of switching to Rows)? *Recommendation: yes.* Rows only above 24 running apps. Tiles are where the links read best.
4. **When nas is down, should the broken lines draw by themselves, or only on "Show what waits"?** *Recommendation: only on request.* The waiting apps already say "Waiting on nas" in amber, and the card says which ones.
