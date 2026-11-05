# Jam-Dash

> Owner: the **JamDash** session. Seeded from its interview on 2026-11-04, corrected and filled in the same day from
> the Jam-Dash source (`web/src/lib/themes`, `web/src/lib/screens`, `web/docs/LOOKS.md`, `docs/design-audit.md`,
> `docs/polish-queue.md`, `PLAN.md`). Screenshots are of the deterministic mock with sample data; host names are
> shown as "home-server" and "nas".

## At a glance
- **What it is:** a web dashboard for a home server that replaces CasaOS. It manages Docker apps (start, stop,
  restart, logs, install from CasaOS-format app stores, custom apps from a form, compose, `docker run` or a GitHub
  URL), and it has a file browser, network mounts, SMB shares and system stats. Home shows live previews for some
  apps (SABnzbd queue, Sonarr/Radarr calendar, Music Assistant now playing). It runs on the home server and on the
  NAS (port 8484). A Home Assistant add-on opens it in the HA sidebar, and a **Global** view shows every server
  at once.
- **Surfaces and input:** desktop browser first (designed at 1440×900, mouse and keyboard), phone a close second
  (390×844, touch). The phone layout starts at 700 px wide (`media.phone`). Files switches to a narrow layout below
  1100 px. NERV is also shot at 1920×1080 for a TV.
- **Stack:** Go binary (REST + WebSocket API, `docs/API.md`) with an embedded SvelteKit (Svelte 5, adapter-static)
  frontend. Hash routing (`#/apps/jellyfin`) so it works under the HA ingress prefix.
- **Theming lives in:** `web/src/lib/themes/<id>/`. See "Theming" below.

## Theming: how looks work
A look is a set of view components over shared data and shared screen logic. The look decides markup, styles and
motion only. Fetching, sorting, validation, error wording and copy are look-independent, so every look behaves
the same and says the same words.

| Path | What |
|---|---|
| `web/src/lib/themes/<id>/` | One folder per look; the folder name is the id. One component per view (`Shell, Home, Apps, AppDetail, System, Settings, SignIn, Store, CustomApp, Files, Shares, GlobalHome, GlobalApps, GlobalSystem, BulkSheet`). |
| `web/src/lib/themes/<id>/index.ts` | `meta: { name, tagline, modes: 'both' \| 'dark' \| 'light', order }` and the views object. |
| `web/src/lib/themes/<id>/<id>.css` | The look's tokens, scoped under `.look-<id>` (Depth: `depth/depth.css` and `depth/global.css`). |
| `web/src/lib/themes/looks.ts`, `registry.ts` | Glob the folders. Adding a folder is all it takes to register a look. Unknown stored ids fall back to Depth. |
| `web/src/lib/screens/*.svelte.ts` | One controller per screen or sheet (Svelte 5 rune classes), shared by all looks. |
| `web/src/lib/ui/` | Shared headless pieces: confirm sheets, focus trap, job buttons, skip link, blink limiter, sparkline maths, app-name annotation. |
| `web/src/lib/util/format.ts`, `appText.ts` | Shared plain-language copy: bytes, durations, state words, alert sentences. |
| `web/src/app.css` | Shared CSS every look uses: `--hit` (44 px on phone/touch, 24 px otherwise), `.jd-hit`, `.jd-skip`, `.jd-blink`. |
| `web/src/lib/global/fallback/*` | Plain Global views for looks that don't draw their own. |
| Fonts | Bundled with the build. Depth and Depth II import `@fontsource-variable/instrument-sans`; other looks declare `@font-face` in their CSS for bundled files. |
| `web/docs/LOOKS.md` | The look makers' guide (controllers, shared helpers X1-X12, what every look must handle). |

**Selecting a look:** Settings › Look, per device. It is stored in the browser's `localStorage` key `jd.prefs`
(`{ look, mode: 'light' | 'dark' | 'auto', autoSource }`). Light/Dark/Automatic is also per device. Automatic
follows the device, or, in Depth, the real sunrise and sunset at the server's location. Looks with `modes: 'both'`
get a light/dark switch in the shell (Depth: sun/moon in the dock).

**Depth tokens (default look):** night ground `#0e2433`, dusk `#173a52`, ridge `#3e5f78`, sun `#f0b36e`, window
`#f6f8fa`, action `#2f6fe4`, alert `#ff8f73`, live `#2fb36b`, busy `#e0952f`, danger `#b8432c`. Type is Instrument
Sans Variable, with the system monospace for logs and compose files. Frosted glass windows (`rgba(246,248,250,.82)`)
float over a landscape (`Scene.svelte`: sky with a day/night cross-fade, sun or moon, three ridges, haze). Each
layer moves with a slight pointer parallax (`--mx/--my`).

## Current looks
In Settings › Look order. `modes` is from each look's `meta`.

| Look | id | Tagline | Modes |
|---|---|---|---|
| **Depth** (default) | `depth` | Layers and landscape, the default | light + dark |
| Depth II | `depth2` | Altitude: the nearer it is, the more it needs you | light + dark |
| Braun | `braun` | The quiet appliance | light + dark |
| Braun II | `braun2` | Every app on one tuning scale | light + dark |
| NERV | `nerv` | SIGNAL//DECK, works on the TV | dark only |
| LCARS | `lcars` | The starship console | dark only |
| LCARS II | `lcars2` | An ops console where every light means something | dark only |
| Olympia | `olympia` | After Aicher: the Munich games | light + dark |
| Transit | `transit` | After Vignelli: the subway sign | light + dark |
| Grid | `grid` | After Crouwel: the New Alphabet | light + dark |
| New Wave | `newwave` | After Greiman: a desk of sheets | light + dark |
| Pulsar | `pulsar` | After Saville: the pulse of the server | light + dark |
| Riso | `riso` | Your server, printed in three inks | light + dark |

**Removed:** Kinetic, Aero, Harper, NERV II, Transit II, Olympia II, Grid II, Pulsar II, New Wave II. They are gone from
the source tree. The release noted in Jam-Dash's handoff (2026-11-04 morning) still carried 22 looks.

## Screens
All screenshots are Depth, from the mock (13 running apps, 15 stopped, one alert: Crafty unhealthy, frozen clock at
night server time). Light unless the name says dark. Size suffix: `desktop` = 1440×900, `phone` = 390×844.

| Screen | What it does | Key components | States | Screenshot |
|---|---|---|---|---|
| Home | The monitor. Summary glass (greeting, running count, CPU, memory, disk ring), alert pills, then every app on three **terraces**: front = windows for apps that need you or have a live preview (big CPU/memory numbers, Restart/Start, Show logs); middle = the other running apps as tiles with sparklines; back = stopped apps as dim chips ("+N more" on desktop, "Stopped (n)" on phone). | Summary glass, alert pill, window, tile, chip, live previews, dock | alert, calm, loading, error, dark | [alert](screens/home-alert-light-desktop.png), [alert phone](screens/home-alert-light-phone.png), [dark](screens/home-alert-dark-desktop.png), [dark phone](screens/home-alert-dark-phone.png), [calm](screens/home-calm-light-desktop.png), [calm phone](screens/home-calm-light-phone.png), [calm dark](screens/home-calm-dark-desktop.png), [calm dark phone](screens/home-calm-dark-phone.png), [loading](screens/home-loading-light-desktop.png), [loading phone](screens/home-loading-light-phone.png), [error](screens/home-error-light-desktop.png), [error phone](screens/home-error-light-phone.png) |
| Apps | Every app: search, filter chips with counts (All, Running, Stopped, Needs attention), category chips, running grid then Stopped. Rows have a `…` menu, and stopped rows can be started in place. Bulk actions in a sheet. | Search field, filter chips, app tile, menu, bulk sheet | default, empty search, loading (skeleton tiles), error ("Docker is not answering" + Try again) | [desktop](screens/apps-light-desktop.png), [phone](screens/apps-light-phone.png), [empty](screens/apps-empty-light-desktop.png), [empty phone](screens/apps-empty-light-phone.png), [loading](screens/apps-loading-light-desktop.png), [loading phone](screens/apps-loading-light-phone.png), [error](screens/apps-error-light-desktop.png), [error phone](screens/apps-error-light-phone.png) |
| App detail | One app as a large window: health sentence, "Why" (last 5 log lines when unhealthy), CPU/memory/uptime, pinned live log tail, Restart / Full logs / Edit setup / Stop, facts panel (address, image, data folder, restarts, started). Tabs stay visible, plus Back. | Window, stat numerals, log box, job buttons, facts glass, confirm sheet, full-log sheet | alert (unhealthy), running, stop confirm | [alert](screens/detail-alert-light-desktop.png), [alert phone](screens/detail-alert-light-phone.png), [running](screens/detail-running-light-desktop.png), [running phone](screens/detail-running-light-phone.png), [stop confirm](screens/detail-stopconfirm-light-desktop.png), [stop confirm phone](screens/detail-stopconfirm-light-phone.png) |
| Store | Search across five CasaOS-format catalogs, "For you" plus category shelves, a featured hero, Get/Open per app. Install sheet: port, folders, live checks (ports, folders, disk, names, architecture), install job. | Search, shelf, store tile, featured hero, install sheet, checks list | default, loading, error | [desktop](screens/store-light-desktop.png), [phone](screens/store-light-phone.png), [loading](screens/store-loading-light-desktop.png), [loading phone](screens/store-loading-light-phone.png), [error](screens/store-error-light-desktop.png), [error phone](screens/store-error-light-phone.png) |
| Custom app | Store › Custom app: tabs Form / Paste / From GitHub. Highlighted compose editor and a live preview card ("This is how it'll look on your Home screen"). | Tabs, code editor, preview card, form | default (Paste) | [desktop](screens/custom-light-desktop.png), [phone](screens/custom-light-phone.png) |
| Files | Places sidebar (folders, network mounts, shared folders), crumbs, list, preview panel (a sheet when narrow). Upload, New folder, Share this folder. Mount and share sheets, rename, delete, move with folder picker, upload progress, drag and drop. | Places list, crumbs, file rows, preview panel, sheets, folder picker | default, error ("Could not read this folder" + Go to Home) | [desktop](screens/files-light-desktop.png), [phone](screens/files-light-phone.png), [error](screens/files-error-light-desktop.png), [error phone](screens/files-error-light-phone.png) |
| Shares | "Shared from here" (SMB shares with address + Copy, who can open them, read only) and "Network shares on this machine" (mounts). Share a folder / Add a network share. Shares made by CasaOS show read-only. | Share cards, badges, copy button, share/mount sheets | default | [desktop](screens/shares-light-desktop.png), [phone](screens/shares-light-phone.png) |
| System | Host facts (OS, kernel, CPU, memory, Docker, version, uptime), processor and memory graphs (10 min), network graph, disks with bars. | Fact list, graph cards, disk bars | default | [desktop](screens/system-light-desktop.png), [phone](screens/system-light-phone.png) |
| Settings | Look picker (preview cards), Light/Dark/Automatic, password, signed-in devices, Connections (one row per app with a live preview: Connect / Sign in / Paste a token / Disconnect, each in a sheet), Home Assistant access (switch, one-time key with Copy). | Look cards, radios, device list, connection rows, key sheets, switch | default, Connections | [desktop](screens/settings-light-desktop.png), [phone](screens/settings-light-phone.png), [connections](screens/settings-connections-light-desktop.png), [connections phone](screens/settings-connections-light-phone.png) |
| Sign in | One password and "Remember this device". First run sets the password. The landscape fills the background. | Glass card, password field, switch | default, wrong password | [desktop](screens/signin-light-desktop.png), [phone](screens/signin-light-phone.png), [error](screens/signin-error-light-desktop.png), [error phone](screens/signin-error-light-phone.png) |
| Global Home | All servers at once (through the HA add-on): server cards (running, CPU, memory, disks), cross-server alerts, every app with a server badge. One mountain range per server in the scene. Unreachable servers say so with Try again. | Server switcher ("All servers"), server cards, server badges, alert strips | default (one server offline) | [desktop](screens/global-home-light-desktop.png), [phone](screens/global-home-light-phone.png) |
| Global Apps | Every app on every server: filters, categories, "Group by server", bulk restart across servers. | As Apps, plus server badges and the bulk sheet | default | [desktop](screens/global-apps-light-desktop.png), [phone](screens/global-apps-light-phone.png) |
| Global System | Servers side by side: CPU and memory (10 min), disks and pools, uptime, warnings. | Graph cards per server column | default | [desktop](screens/global-system-light-desktop.png), [phone](screens/global-system-light-phone.png) |

Sheets and overlays, not shot separately: stop confirm (shot), container-name conflict, install sheet, mount sheet,
share sheet, rename / delete / move / new folder, folder picker, file preview (a sheet when narrow), full log,
connection sheets (API key + address, Music Assistant sign-in or token, disconnect), HA key, bulk actions, the jobs
strip (long jobs that outlive a sheet), and the stopped-chip Start popover on Home.

## Components
All are custom; there is no UI kit. The behaviour is shared across looks and each look draws its own.

| Component | Custom? | Notes |
|---|---|---|
| Dock / tab bar | yes | Depth: floating glass dock at the bottom (Home, Apps, Store, Files, Shares, System, Settings, sun/moon). Phone: icon + label bar. Stays on detail screens. |
| Server switcher | yes | Pill top right; "All servers" opens Global. |
| Window | yes | Large frosted card for one app (Home front terrace, detail). Red ring when it needs you. |
| Tile | yes | Running app on Home's middle terrace and in Apps: icon, name, state dot + words, CPU, memory, sparkline. |
| Chip | yes | Stopped app on Home's back terrace, with a one-line Start popover. |
| Alert pill / strip | yes | Top right on desktop, a strip with inline Restart on phone. Live region. Blinks at most 3 times. |
| Summary glass | yes | Greeting, running count, CPU, memory, disk ring. |
| Live previews | yes | SABnzbd queue (speed, progress), Sonarr/Radarr week calendar with posters, Music Assistant now playing. They take the generic window body's place without a layout shift. "Connect Sonarr" link when no key is stored. |
| Buttons / job buttons | yes | Primary (dark), secondary (tint), danger (red). The label follows the job ("Restarting…", "Restarted"). `min-block-size: var(--hit)`. |
| Filter chips / segmented tabs | yes | Counts in the label; arrow keys on tabs and radios. |
| Search field | yes | Debounced (Store 250 ms). |
| Switch | yes | `role=switch` (Remember this device, HA access, Group by server). |
| Sparkline, graph, ring, bars | yes | 60 s sparklines on tiles, 10 min graphs on System, disk ring on the summary, disk bars. |
| Log box | yes | Monospace, pinned tail, full-log sheet. |
| Code editor | yes | Compose / `docker run` with highlighting (`ui/highlight.ts`), secrets masked. |
| Sheets (dialogs) | yes | `role=dialog`, labelled, focus trap, Escape closes, focus returns. |
| Jobs strip | yes | Long jobs (install, move, mount) that outlive their sheet. |
| File list, crumbs, places, preview | yes | Keyboard: arrows, Home/End, Enter, Backspace, Delete. |
| Look picker cards | yes | Hand-made preview art per look. Newer looks show placeholder art (see Settings shot). |
| Skeletons / "Looking…" | yes | Skeleton tiles on Apps and Store, a glass "Looking for apps on this machine…" on Home. |
| Toasts | no | None. Feedback is inline (job buttons, sheets, the jobs strip). |
| Skip link | yes | Shared "Skip to what needs you", the first Tab stop. |
| Landscape scene | yes | Depth only: sky, sun/moon, ridges, haze, lights at night, one range per server in Global. |

## Hard constraints
- **Contrast:** WCAG AA with **0 fails**. Every text run is measured over the real pixels behind it (glass,
  gradients, images), light and dark, desktop and phone (`web/tools/audit`).
- **Type floor:** body ≥ 15 px, labels ≥ 13 px, **nothing under 12 px**. Annotation hints ("port 7790") ≥ 13 px in
  the look's muted ink, never faded with opacity.
- **Touch:** 44 px targets on phones and touch (`--hit`), 24 px otherwise. No horizontal page overflow.
- **Reduced motion** respected in every look. Motion happens only on change, then rests. Nothing animates per
  metrics tick. Blinking stops after 3 cycles.
- **State is never colour-only:** state words beside every dot ("Running for 12 days", "Stopped unexpectedly",
  "Unhealthy").
- **Fonts bundled** with the build, no web font CDNs at runtime. No franchise logos.
- **Keys are entered only by the person** (Settings › Connections). Jam-Dash never reads API keys or tokens from
  apps' config files, volumes or environment. Keys are never shown back.
- **Shareable product:** nothing tied to one host, user or network; it must work the same for anyone.
- Keyboard: visible focus everywhere, the alert first after the skip link, Escape closes menus and sheets.
- Every screen handles loading, empty and error, and every error offers a way out (Try again, Go to Home).
- Every look ships Home, Apps, App detail, Store, Custom app, Files, Shares, System, Settings, Sign in and the three
  Global views, in light and dark unless the look is dark-only.
- Safety copy and flows: destructive actions ask first; containers never stop because of Jam-Dash itself.

## What Isaac has said
- "I love all the looks!"
- "Remember I want to see excellent design and cool animations in all of these"
- "The text is too small on most of them, and the navigation in depth is atrocious because the homescreen is all 1
  carousel meaning you can't monitor anything". (That was the earlier carousel Home. Depth's Home is now the v10
  terraces, with every app on one desktop screen; the phone Home is still a tall stack, see the audit.)
- "clarity without ever sacrificing fun"
- On the II redesigns and new looks:
  - Liked: "Depth II, Braun II, Lcars II - Much better!"
  - "Kinetic - no / Aero - no, but makes me think something inspired by what inspired mirrors edge would be cool /
    harper - no / reso - interesting..."
  - Rejected: "I think the rest are just not for me" (NERV II, Transit II, Olympia II, Grid II, Pulsar II, New Wave II,
    since removed with Kinetic, Aero and Harper).
- "I might share this with other people, so no automatic token extraction"
- "I'm gonna do some thinking on what I actually want from a redesign"
- Callsheet harmony (via the Callsheet session, 2026-11-03): Jam-Dash adds no Bold/Easy read and no app-switch
  links. A shared look setting between the two apps is still open; each app keeps its own setting for now.

## Open questions for the bible
1. **Originals vs their II:** which stay? Depth and Depth II, Braun and Braun II, LCARS and LCARS II all ship side by
   side today.
2. **Runner** (`jam-dash/mockups/v11-runner.html`): white modernist planes standing off a concrete wall, lit by one
   sun. Red marks only the path to the next action. It came out of the "something inspired by what inspired mirrors
   edge" remark. Is that a direction to pursue?
3. **Global views for the originals:** Depth, Depth II, Braun II, LCARS II and Riso draw their own Global
   Home/Apps/System. Braun, NERV, LCARS, Olympia, Transit, Grid, New Wave and Pulsar use the plain fallback
   (`lib/global/fallback`). Each needs a designed Global view.
4. **Look-picker preview art:** the picker cards are hand-made per look. Newer looks show placeholder art. Should
   previews be data-driven (a swatch in `meta`) or a small component each look provides?
5. Phone Home: the audit found no look shows all running apps on the first phone screen (Depth: 1 of 13). Should the
   bible set a phone monitoring rule (one ≤ 56 px row per app)?
6. Known look bugs waiting in `docs/polish-queue.md`: Depth II's phone dock crams 9 items, Braun II's scale labels
   crowd, and Transit's Sonarr strip overlaps. Jam-Dash's handoff also lists Riso's inner screens as unfinished.
