# Jam-Dash: rollout plan for the calm-instruments look

> JamDash session, 2026-11-06. **Plan only: nothing in Jam-Dash changes until Isaac says go.** Read against `HANDOFF.md`,
> round 6 (`mockups/pass6/jam-dash.html`, `notes/pass6-jam-dash.md`), pass 7 switches option B, Callsheet `.app` tokens
> and the Jam-Dash source at `1f1baf8`. Isaac: round 3 was his favourite; no skeuomorphism; keep the hover trace.

**In short:** build round 6 as a **new look, "Instrument"** (`web/src/lib/themes/instrument/`) beside the 13 looks,
over the same controllers and copy. When it covers every screen and passes the audits, Isaac decides whether it
replaces Depth as the default. The trace needs data the backend lacks (§3.1), so it gets its own phase and ships last.

## 1. What changes

### 1a. Each HANDOFF rule, in Jam-Dash
| # | Rule | Jam-Dash today (Depth) | Instrument must |
|---|---|---|---|
| 1 | Calm first | Landscape scene, parallax, frosted glass | Flat ground. All fine = "Everything's running." + server band + tiles. No orange, no lines, nothing moving |
| 2 | Less realism | Ridges, sun/moon, glass; NERV/LCARS consoles | No `Scene`, no blur, glass, ribs or shadows. Signature shapes: the **navy server band**, the **trace**, the **readout line** |
| 3 | Callsheet palette | Depth's blues (`#0e2433`, action `#2f6fe4`) | Callsheet `.app` tokens verbatim (§1c) |
| 4 | Jost + Plex Mono | Instrument Sans + system mono | Both bundled (`@fontsource/jost`, `@fontsource/ibm-plex-mono`, OFL). Logs and compose stay mono (Plex) |
| 5 | Calm panels | Glass windows | 1 px hairline, ~10 px radius, no shadow by day or night (round 6's faint day shadow goes) |
| 6 | Almost no lights | Dots in the dock and chips | LEDs only for app/server state and the warn meter. Nav = 2 px ink underline. Selected server = pressed in. Focus = cream/ink outline + 1 px lift |
| 7 | One orange | Blue primary keys everywhere | At most one orange per screen, picked by one shared rule (§1c). Settings, System, Files, Shares: none |
| 8 | Red alert key | Red ring on the window | Newest alert's fix is a solid red key, dark text; nothing orange while it shows |
| 9 | Colour + shape + word | Dot + word (already a hard constraint) | Add the shapes (§1c) |
| 10 | Switches | Plain `role=switch` | Channel-reveal switch, colour by kind (§1c) |
| 11 | TV | NERV at 1920×1080 | Instrument is not a TV look (Q4) |
| 12 | Say it once | Shared copy (`appText.ts`) | Keep the copy; drop repeats (tab badges, the hero count shown twice). Failures already end in Try again + a way home |

### 1b. Screen by screen
- **Home.** Round 6: hero sentence ("Two apps need you.") + mono sub line; up to 3 trouble cards (red key on the newest
  alert); "To look at" line for warns; one navy band per server (state, up time, OS, CPU/Memory/Disk meters; nas adds
  `Shared:` chips); tiles (glyph, name, LED + word, ↗ open key; live previews keep `data-preview`); "n stopped" chips
  with the X5 Start popover; the readout line at the bottom. Density: Tiles → Compact → Rows (Rows only above 24
  running apps). Phone: hero → band → first trouble card → other alerts as rows → "To look at · n" → 2-column tiles.
- **Apps.** Same tiles in a grid, search, filter chips with counts (no lit dots), category chips, Stopped below. Bulk
  sheet unchanged. No orange (a list screen).
- **App detail.** Round 6 header card (glyph, name, server chip, LED + word, Why under the health sentence, actions),
  then Connections map (after phase 7), last log lines, Now (CPU, memory, up) and Facts. New **Behaviour** card with
  switches (§1c). Orange only for the one next step (e.g. "Start"), red key when unhealthy.
- **Store / Custom app.** Not redrawn in round 6. Shelves as calm panels, Get/Open as plain keys, the install sheet's
  Install is that sheet's one orange; checks list uses the state shapes. Code editor in Plex Mono.
- **Files / Shares.** Plain list in a panel, places sidebar with a walnut rule, no orange (Upload is a plain key).
  Sheets keep their flows; delete stays a key + confirm. Shares tab stays when the feature is on (round 6's nav
  dropped it).
- **System.** Fact list + graphs on hairline panels, meters as in the band, warn amber + ▲ on a nearly full disk.
- **Settings.** Look cards (Instrument needs its own preview art), Light/Dark/Automatic as a segmented key (three
  choices, so not a switch), password, devices, Connections rows. Switches: kind colours, see §1c. No orange.
- **Sign in.** Flat ground with the walnut top trim, one panel, password, "Remember this device" as a settings-steel
  switch, Sign in is the screen's orange. Wrong password: one sentence in `--alert-ink`, no shake.
- **Global (HA add-on).** Round 6's Home *is* a two-server view: draw Global Home exactly like it (bands side by side,
  the "Both · home-server · nas" switcher = today's server switcher). Global Apps/System reuse the tiles and panels.
- **Shell.** Top bar on desktop (name, tabs, server switcher, a small Day/Night key for X4), bottom tab bar on phone
  (icon + label, ink underline). Walnut 4 px trim on top. Jobs strip as a flat panel above the tab bar.

### 1c. Components
- **Panels:** `--card` on `--ground`, 1 px `--rule`, radius 10, padding 16/20, one idea each. Server band: `--band`
  (`#1b2230` day / `#070a10` night) with `--band-ink`.
- **State words + shapes** (word from `appText.ts`, unchanged):
  | Jam-Dash state | Shared state | Colour + shape | Word |
  |---|---|---|---|
  | running, healthy | on | ok round LED | "Running · 9 d" |
  | stopped by the person, created | off | hairline ring (no fill) | "Stopped" |
  | unhealthy, exited | alert | red round LED, red edge on the card | "Unhealthy", "Stopped unexpectedly" |
  | partial, waiting on another server, conflict | warn | amber LED + ▲ | "Partly running", "Waiting on nas" |
  | server not answering | offline | dashed ring + dashed card outline | "Not answering" |
  | restarting / starting (a job of ours) | busy (app-local) | slot shape, no colour | "Restarting…" |
  | restarting with no job of ours (crash loop) | alert | red LED | "Keeps restarting" (new copy) |
  | an alert that cleared | past form | grey text | "Fixed 01:53", "Seen 06:20" |
- **One-orange rule:** a small shared helper `ui/loudness.ts` (additive; other looks may ignore it): given the screen's
  facts it returns `{ red, orange }` ids. Red = newest alert's fix; if red exists, orange is null; else the one next
  step (Try nas again, Start the only stopped app the person opened, Install in a sheet); calm screens: none. Keys
  mark `data-loud="red|orange"` so the audit can count them.
- **Red alert key:** `--alert` `#ff5a48` fill, `--on-alert` `#1c0804` text (6.27:1). Alert text elsewhere uses
  `--alert-ink` (`#b3261b` / `#ff8a7a`).
- **Switches** (channel-reveal, pass 7 spec): channel off `#1c2331` / `#05070b` + 1 px `#2a3244`, thumb `#fbf9f4` /
  `#ece5d3`, 180 ms `cubic-bezier(.16,1,.3,1)`, instant in Calm/reduced motion. Desktop 36×22 (hit 48×38), phone 46×28
  (hit 62×44). Kind colours (option B): **settings steel** `#71819c`/`#64738d` (Remember this device, Group by server,
  Show on Home), **automations violet** `#8f72c0`/`#8063b1` (Restart if it stops), **power blue** `#6780b4`/`#5971a4`
  (none today: Start/Stop/Restart are keys, they aren't instant). Per-app override: later, stored with the app on the
  server. **Not a switch:** Home Assistant access (turning it off deletes the key and it can fail) becomes "Allow Home
  Assistant" / "Turn off access…" keys with a confirm (Q7).
- **Hover connection trace** (round 6, unchanged in behaviour): point, focus or tap a tile, chip, share or band → linked
  apps stay full, others dim to 28 %, 1.5 px curves behind the cards with end rings, `NEEDED` / `USES IT` words (≤ 8
  links), the `aria-live` readout names everything with its source. Solid = found, dashed = yours, amber dotted =
  broken. Guesses are asked on the app page, never drawn. Fade in once, 220 ms; none in Calm. No lines in Rows.
- **Type:** Jost 400/500/600 for words (body 15–16, hero 28–40), Plex Mono 500 uppercase labels **13 px**, `.14em`
  tracking; numbers and times in Plex Mono. Nothing under 13 except mono log/graph text (≥ 12).
- **Palette tokens** (Callsheet `.app`, Day / Night): ground `#ece7dd`/`#10141d`, card `#f7f4ee`/`#161c28`, inset
  `#efeae0`/`#1b2230`, ink `#19202e`/`#ece5d3`, ink2 `#343b4a`/`#d2cbb9`, dim `#5b606d`/`#9f9a8b`, rule
  `#d6cfbf`/`#2a3244`, hair `#e0d9cb`/`#232b3a`, orange `#ec7c22`/`#f08a2c` (on-orange `#1a1206`), walnut `#6b4428`,
  ok `#7bd651`, warn `#f2c14e` (warn-ink `#7a5300`/`#f2c14e`), alert `#ff5a48`, lit/cream `#f3e6c8`. Round 6's
  slightly different Jam-Dash values (`#ebe8e1`, `#0c1018`, `#151b27`) give way to these.

## 2. Order of work (one worker per phase; P6 can run beside P1–P5)
| Phase | Work | Done when |
|---|---|---|
| P0 Groundwork | Fonts, `instrument.css` tokens, the look's kit (Panel, StateMark, Key, Switch, Meter, Readout), `ui/loudness.ts`, `meta.hidden` so the look shows only with `?looks=all` until P5; add `instrument` to `tools/audit/run.sh` and an audit check: ≤ 1 `data-loud="orange"`, none beside a red one | `verify.sh` green, kit page shot |
| P1 Shell, Sign in, Settings | Top bar / tab bar, switches, HA access keys, look preview art | type-audit + audit 0 fails |
| P2 Home + App detail (no links) | Round 6 Home at 1440/1280/390, density ladder, trouble cards, readout at rest, Behaviour card | Fit table matches round 6; **Isaac reviews shots** |
| P3 Apps, Store, Custom app | Calm grids and the install sheet | audits 0 fails |
| P4 Files, Shares, System | Lists, places, graphs, meters | audits 0 fails |
| P5 Global Home/Apps/System | Round 6's two-band Home as Global; drop `meta.hidden` | `global-e2e`, `ingress-e2e` pass |
| P6 Backend (Go) | `GET /apps/links`, alert history, mock data, `api_level` 2 (§3.1) | Go tests + mock serve both |
| P7 Trace + Connections map | Trace, Add a connection, guesses, phone select sheet, "Show what waits" | Flows from round 6's audit pass in Playwright |
| P8 Release | Both installs (systemd :8484, TrueNAS Custom App) + the HA add-on; **Isaac decides: default or not** | Isaac's OK |

## 3. Hard or impossible in the real stack, and what to do instead
1. **Connection data doesn't exist.** The backend reads ports, volumes, `NetworkMode` and restart policy only. And in
   Jam-Dash an *app is a compose project*, so `depends_on` mostly joins services *inside one app* (Immich server →
   worker), not two apps; round 6's "Sonarr needs Prowlarr · compose file" only happens when both sit in one file.
   Real cross-app sources: `network_mode: container:/service:` (e.g. a VPN container), legacy `HostConfig.Links`,
   the same host folder mounted by two apps (SABnzbd and Sonarr on `/downloads`), a mount under a network mount
   (nas › media), Proxy Manager hosts (needs its key in Settings › Connections, like Sonarr), Traefik labels. A
   shared user network (`media`) is only a guess. Environment values are never read (keys rule). **Propose:**
   `GET /api/v1/apps/links` →
   `{"links":[{"id","from","to","kind":"needs","source":"depends_on|network_mode|links|shared_folder|mount|proxy_host|traefik|yours","detail":"/downloads","state":"ok|stopped|broken","added_at"}],"guesses":[{"id","a","b","why":"network media"}],"sources":{"proxy":"not_connected"}}`;
   `POST /apps/links {from,to}` and `DELETE /apps/links/{id}` for "yours" (stored on the server, so every browser sees
   them); `PUT /apps/links/guesses/{id} {"answer":"yes|no"}`; WS `links` on change; `api_level` 2. Also read the
   `com.docker.compose.depends_on` label (written by Compose ≥ 2.20) so adopted and TrueNAS apps work without their
   files. Without a Proxy Manager key the readout says "Proxy links need Proxy Manager's key".
2. **One Home, two servers.** A standalone install only knows itself; both servers together exist only under the HA
   add-on (Global). Standalone Home draws one band; cross-server links show as a share node ("nas › media") matched
   from the mount's remote address, with nas's tiles only in Global.
3. **Things the mockup shows with no data:** "Update to 4.0.11" (no image update check: not drawn), "History" and
   "Fixed 01:53" (alerts are live-only `alert`/`alert_clear`: add a small persisted ring buffer, `GET /alerts/history`,
   in P6), "Find ⌘K" (no search: drop), Behaviour "Update by itself" and "Tell me when it's unhealthy" (no updater,
   no pushes: not drawn). "Restart if it stops" can work through Docker's container update for apps Jam-Dash made;
   for adopted and TrueNAS apps a compose `up` would undo it, so it shows disabled with the reason.
4. **Type floor vs round 6.** 13 px uppercase mono labels pass (label floor 13). Below floor in the mockup: `NEEDED` /
   `USES IT` and keycaps at 12 px → 13; trouble-card and tile sentences at 13–14 px that run past 28 characters count
   as body → 15. `type-audit.mjs` will flag them; fix in the look, don't loosen the audit.
5. **The trace vs the audits.** Dimmed cards (28 %) fail contrast on purpose while you point. Audits shoot at rest;
   add one trace shot that checks the `aria-live` readout instead of contrast. Phone first-tap-selects is look-local
   (the shared controllers keep tap = open for the other looks). Rows on the phone would break 44 px, so Rows is
   desktop only.
6. **13 looks.** Each look draws its own markup, so shapes and the one-orange rule land in Instrument only; the other
   looks keep working and saying the same words. The audit's default look list leaves out depth2, braun2, lcars2 and
   riso today: add Instrument explicitly.
7. **Static + ingress: fine.** Fonts bundle through Vite under the relative shell and hash routes; the trace is an SVG
   layer measured in the page. Light/Dark/Automatic = Day/Night. Ok green on day paper is ~1.8:1: the word carries
   the state, and lit LEDs keep round 6's hairline ring by day.

## 4. Questions for Isaac
1. **Instrument as a new look first, then a call on making it the default?** *Recommendation: yes,* review after P2.
2. **The other 12 looks:** keep them all as choices, freeze them (bug fixes only), or retire some once Instrument is
   default? *Recommendation:* keep for now; later retire the originals that have a II (Depth, Braun, LCARS).
3. **Global:** is round 6's two-band Home the Global Home? *Recommendation: yes.*
4. **TV:** Instrument isn't built to the TV floors. Keep NERV as Jam-Dash's TV look until Lobby's direction is set?
   *Recommendation: yes.*
5. **State words:** Jam-Dash keeps its own words ("Unhealthy", "Stopped unexpectedly", "Partly running") under the
   shared states (alert, alert, warn); "Restarting" is a quiet app-local *busy*, unless Docker restarts it with no
   job of ours (a crash loop), which becomes alert "Keeps restarting". OK?
6. **Behaviour card:** ship only the two switches that work today (Show on Home, Restart if it stops)?
7. **Home Assistant access:** keys with a confirm instead of a switch, since turning it off deletes the key?
8. **Phone:** first tap shows the links, second tap (or ↗) opens? (round 6 Q2, still open)
