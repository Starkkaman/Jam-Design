# Callsheet

Version 0.9.0 (live on Home Assistant). Staged for the shared design repo; documentation only.

## What it is

Callsheet is Isaac's personal assistant, a Home Assistant app (add-on) shown as an Ingress page. Each morning, and at
check-ins during the day, it reads his mail, calendars, Slack and Signal and writes a **Daily Brief**: what the day
holds, who is waiting on a reply (with a suggested reply to copy), and what is coming up. It also has a read-only
Chat over a local index of his history, and Projects.

It is **read-only and drafts-only**. Nothing is ever sent: "Nothing was sent. Drafts wait for you." is a fixed
promise in the UI, not a setting.

Code: Callsheet repo, `callsheet/app/static/` (`index.html`, `app.js`, `app.css`, `fonts/`). Plain JS and CSS, no
framework, served by a Python stdlib server.

## Surfaces and input

- **Desktop browser**: mouse and keyboard. Ctrl/Cmd+K or `/` opens Find or ask. List keys: J/K move, Enter opens,
  D done, C copy the draft, O open in Gmail, N note, Esc close, `?` shows the key sheet. One at a time adds L later
  and X not for me.
- **Phone**: touch. Under 700 px the tabs move to a bottom tab bar, the detail panel goes full screen, One at a time
  takes swipes (right = done, left = later). Targets are at least 44 x 44 px.
- Phone and desktop matter about equally. No TV.

## Screens

Screenshots: [`screens/`](screens/INDEX.md) (Bold, day and night, 1440 and 390 px).

| Screen | Job | Primary action | Key components |
|---|---|---|---|
| **Briefing** (`#briefing`) | The day in one read: summary, Top of the day, security heads-ups, By area, What changed, Coming up (2 weeks / 2 months), At a glance. | Start your day: "Start: one at a time" | Start your day card, kicker + summary or headline, Weekly review card, Top of the day rows (tick, copy), section lists, Coming up date tiles, At a glance aside, footer |
| **Replies** (`#replies`) | Everyone waiting on a reply. | "One at a time" | header with done meter, density segments, area chips, rows with reason dots, legend behind "?", notepad menu, Done today, toasts with Undo; with AI sorting on: Needs you / For your info / Sorted sections |
| Replies, **detail panel** | One message: what they want, exact details quoted, the suggested reply to edit and copy. | "Open in Gmail" (Copy next to the draft) | panel, tags, fact chips, draft textarea, sender's-claim note, Same person? card (compact) |
| Replies, **One at a time** | Work the list one card at a time; ends in All clear. | "Copy draft" | card with draft, Done, quiet actions (Open, Later, Note, Not for me), count "1 of 7", key hints |
| **Agenda** (`#agenda`) | Today's timeline and invites to answer. | none filled; "Answer in Google Calendar / Gmail" per invite | timeline with time column and messages column, clash marks, invite cards, email-only pins, possible events |
| **Chat** (`#chat`) | Ask about your own mail, chat, calendar and notes; read-only search over the local index. | "Ask" | question box, suggestion buttons, answers with source chips and steps, Copy, Earlier chats, Save card (remember a note, owner-pressed), thinking line with Stop |
| **Projects** (`#projects`) | Projects, slipped items, timeline, weekly review. | none filled in the list; "Add project" on a suggestion, "Start the review" | view chips (List, Timeline, Slipped, Weekly review) with badges, slipped line, project rows with status dots, Suggested list (dashed), project panel with tasks and notes |
| **Setup home** (`#setup`) | Settings in four places, and a settings search. | "Refresh now" | masthead with Last refreshed, place tabs, Find a setting, four place cards |
| Setup, **Connections** | Areas, Google accounts, Slack, Signal, notes folders, GitHub. | "Connect Google account" | area chips, account rows, read chips, connection rows |
| Setup, **Your day** | Name, time zone, brief times, phones to notify, quiet hours, VIPs, needs-a-reply age, never-reply rules, look and sound. | per section | brief-time rows with day chips and switches, VIP list, rules list, Look button |
| Setup, **AI** | Who writes (Off / On this box / Claude), Chat on this device, memory, writing style, AI sorting, What it learned. | per section | radio rows, switches, sorting segments, health line |
| Setup, **Advanced** | Everything rare, each in its own closed drawer (Google sign-in key, model server, presets, chat engine, alerts, writing instructions, memory file, writer evaluation, Signal import, Start over). | none | drawer rows (`.advh` with + / −), Start over in a danger drawer |
| **Know me** (`#knowme`, `#profile`, `#profile-questions`) | Build the local index from your history, check the drafted profile, answer questions. Optional. | "Get to know me", then the step's button | steps, source rows, scan progress, profile cards, question cards |
| **Check the sorting** (`#sorting`) | Spot-check the AI sorter's labels, one card at a time; counts and Copy the numbers. | the right label | sorting card, label buttons, counts; Back to AI |
| **Find or ask** (palette, any screen) | Jump to people, replies, settings and read-only actions, or ask Chat. | Enter on the top result | input, grouped results (People and threads, Settings, Ask), key hints, footer |

First run is a three-step wizard (Connect, Your day, Get to know me); after that Setup opens at its home.

## Components

| Component | Classes (app.css) | Notes |
|---|---|---|
| Header | `.top`, `.mast`, `.hmeta`, `.hbtn`, `#find-btn`, `.lookbtn` | wordmark, date, last refreshed; Refresh, Find, Setup, Look with labels under the icons |
| Look panel | `.lookpanel`, `.lookgrp`, `.lookcard`, `.swatches` | Callsheet looks and Jam looks; Auto / Light / Dark |
| Tab bar / bottom tabs | `.tabbar`, `.badge` | top bar on desktop; fixed bottom bar with icons under 700 px |
| Rows | `.row`, `.rmain`, `.ck` + `.bx` (tick), `.np` (notepad), `.tag`, `.row2`, `.row5` | tick, who + one line, age, reason dot, notepad |
| Reason dots | `.rdot`, tokens `--r-vip --r-due --r-men --r-q --r-wait` | same colours in every look; words in the tooltip and legend |
| Legend | `.legend`, `.qbtn`, `.helpq` | behind "?" after first use |
| Done meter | `.meter` | "1 of 8 done today" |
| Detail panel | `.panel`, `.panel-in`, `.facts`, `.fact`, `.pflag` | right column on desktop, full screen on phone |
| Notepad menu | `.pop`, `.popw` (Projects: `.pjpop`) | Note for Callsheet, Doesn't need a reply |
| Toasts | `.toast` (`.toast.bad`) | message + Undo + 44 px Close |
| Buttons | `.btn`, `.btn.primary`, `.act`, `.act.ghost`, `.tbtn`, `.ib`, `.hbtn` | one filled button per screen; outlined; plain text |
| Cards | `.scard` (Setup home), `.rvcard` (Weekly review), `.inv8` (invite cards), `.oatcard`, `.srcard`, `.pfcard` | |
| Chips | `.chip` (filters, aria-pressed), `.schip` (Chat sources), `.pchip`, `.areachips`, `.acb` | chips always click; tags never do |
| Segmented controls | `.seg`, `.chips.seg.dens` | 2 or 3 choices, save at once |
| Switches | `.sw`, `.swrow` | on/off, save at once |
| Palette (Find or ask) | `.fa`, `.fa-wrap`, `.fa-in`, `.fa-list`, `.fa-g`, `.fa-o`, `.fa-foot` | combobox; only reads, copies or opens |
| All clear | `.clear`, `.shapes`, `.stamp`, `.stats` (`.clear.still` after the first time today) | flat shapes drop in, stamp lands once a day; still under reduced motion |
| Start your day | `.startday`, `.sd-h`, `.sd-l`, `.sd-go` | dark band on Briefing until "Not now" or started |
| Top of the day | `.topw`, `.topl`, `.trow` | tick and copy |
| Briefing sections | `.s8`, `.l8`, `.mk8` (marks), `.inv8sec`, `.srt8` (Sorted for you) | Security heads-ups, What changed |
| Coming up | `.hz8`, `.hzg`, `.hzcols` | date tile + title + Got it / Remind me a week before / Not big |
| At a glance | `.glance-w`, `.glance` | Next, Due today, Clash, Answer, Waiting |
| Save card (Chat) | `.csave`, `.cform`, `.ctext`, `.csaved` | a note to remember, saved only when the owner presses Save |
| Same-person card | `.same` (`.same.compact` in the panel), `.pp*` on People | "Same person?" with why and three answers |
| Chat | `.chatcol`, `.msgs`, `.mq` (question), `.ma` (answer), `.macts`, `.compose`, `.sugg`, `.busy` + `.spin`, `.cintro`, `.cearly` | |
| Projects | `.pjhd`, `.vnav`, `.pjrow`, `.sdot`, `.slipsum`, `.bproj` | |
| Setup | `.sheet.wiz`, `.step`, `.shome`, `.scard`, `.sfind`, `.advs`, `.adv`, `.advh`, `.advb`, `.lrow` | |
| Empty text | `.empty`, `.writing` | "Nothing on your calendar today.", "Writing the summary…" |
| Key sheet | `.keysheet` | the `?` keys dialog |

## Theming

- **Token block at the top of `app.css`**: one rule per look for light values (`.app[data-look=bold]{…}`) and a dark
  rule repeated for `data-mode=dark`, for HA's `data-theme=dark` with mode auto, and for `prefers-color-scheme: dark`
  with mode auto. Components use only these tokens.
- **Attributes on `#app`**: `data-look` (bold, clean, easy, depth, braun, nerv, lcars, olympia, transit, grid, newwave,
  pulsar), `data-mode` (auto, light, dark), `data-base` (bold, clean, easy: the structural family; Jam looks borrow
  one). Structure keys on `data-base`, never on `data-look`, except each look's signature rules at the end.
- **Jam looks** come from `~/project/daily-brief/harmony/themes-harmony.css`, generated by `harmony/gen.py` (which
  also writes the contrast report), pasted verbatim into `app.css`. Notes: `harmony/harmony.md`. Look ids are
  JamDash's.
- **Fonts**: `callsheet/app/static/fonts/` (woff2/ttf, latin subsets, SIL OFL 1.1, licence files `OFL-*.txt`). A
  look's faces are fetched only when it is used.
- **Prefs** per device in `localStorage` `callsheet.prefs` = `{look, mode, autoSource: device|sunset}`; the server's
  saved look (Setup) wins on load.
- Motion: `--dur-1/2/3` = 150 / 250 / 350 ms, per-look `--ease`. Phone sizes: `--fs-h1:42px; --fs-stat:34px;
  --fs-h2:23px` for Bold under 700 px.

### Bold tokens

Type and shape (both modes): display `Londrina Solid` (900, uppercase, line-height .92), body `Jost`; labels uppercase,
tracking .14em, weight 600; `--radius`, `--tag-radius`, `--chip-radius`, `--phone-radius` 0px; `--rule-w` 2px,
`--rule-mid` 3px, `--rule-heavy` 6px; `--base-size` 15px, `--lh` 1.4, `--focus-w` 2px; sizes `--fs-xs` 10.5,
`--fs-sm` 12, `--fs-md` 14, `--fs-lg` 16, `--fs-time` 20, `--fs-h3` 24, `--fs-h2` 27, `--fs-h1` 67, `--fs-stat` 42,
`--fs-hero` 50 (px). Cut shapes: `--cut`, `--cut-bar`, `--cut-torn` (clip-path polygons).

| Token | Light (day) | Dark (night) |
|---|---|---|
| `--bg` | `#e3d8bd` | `#0c0b0a` |
| `--surface` | `#ece2c9` | `#1f1c19` |
| `--surface-2` | `#e0d4b5` | `#2a2622` |
| `--text` | `#141210` | `#ece2c9` |
| `--muted` | `#5c5446` | `#9a8f7c` |
| `--rule` | `#b9ab88` | `#34302a` |
| `--accent` / `--on-accent` | `#b52e14` / `#f4ecd8` | `#b52e14` / `#ece2c9` |
| `--alert` | `#ac2c13` | `#f0674a` |
| `--ok` | `#2c7a83` | `#3f9aa5` |
| `--area-1` / on | `#e5a31b` / `#141210` | `#e5a31b` / `#141210` |
| `--area-2` / on | `#b52e14` / `#f4ecd8` | `#b52e14` / `#ece2c9` |
| `--area-3` / on | `#3f9aa5` / `#141210` | `#3f9aa5` / `#141210` |
| `--area-4` / on | `#141210` / `#f4ecd8` | `#e0d4b5` / `#141210` |
| `--sel` / `--on-sel` | `#141210` / `#ece2c9` | `#ece2c9` / `#141210` |
| `--masthead` / on | `#141210` / `#ece2c9` | `#141210` / `#ece2c9` |
| `--eyebrow` | `#e5a31b` | `#e5a31b` |
| `--box` / on | `#ece2c9` / `#141210` | `#ece2c9` / `#141210` |
| `--callbox` / on | `#b52e14` / `#f4ecd8` | `#b52e14` / `#ece2c9` |
| `--panel` / on | `#141210` / `#ece2c9` | `#141210` / `#ece2c9` |
| `--panel-head` / on | `#e5a31b` / `#141210` | `#e5a31b` / `#141210` |
| `--panel-mark` | `#b52e14` | `#b52e14` |
| `--track` / `--fill` | `#b9ab88` / `#141210` | `#2a2622` / `#ece2c9` |
| `--field` / `--field-line` | `#f4ecd8` / `#5c5446` | `#141210` / `#9a8f7c` |
| `--phone` / `--slab` / `--bezel` | `#e3d8bd` / `#ece2c9` / `#000` (10px) | `#141210` / `#2a2622` / `#000` |
| `--tabbar` / `--on-tabbar` | `#141210` / `#b9ab88` | `#000` / `#9a8f7c` |
| `--tab-on` / `--on-tab-on` | `#e5a31b` / `#141210` | `#e5a31b` / `#141210` |
| `--focus` | `#141210` | `#e5a31b` |

Reason dots (every look and mode): `--r-vip #d23a2a`, `--r-due #e07a12`, `--r-men #16999e`, `--r-q #c9971a`,
`--r-wait #8b8f96`.

Other looks: Clean (IBM Plex Sans, cool greys, blue `#2457d6`), Easy read (Atkinson Hyperlegible, high contrast), and
the nine Jam looks (Depth, Braun, NERV, LCARS, Olympia, Transit, Grid, New Wave, Pulsar; NERV and LCARS are dark only).

## Constraints

- **Offline**: no CDNs, no analytics, no outside requests from the page. Fonts and icons are bundled (icons are inline
  SVG in `index.html`'s `<template id="icons">`).
- **Fonts**: SIL OFL only, latin subsets, licence text shipped beside them.
- **Data is text**: everything from mail, chat or the AI is rendered with `textContent` (`h()` in app.js), never
  `innerHTML`.
- **Relative URLs only**: the page lives under `/api/hassio_ingress/<token>/`, so `app.css`, `api/brief`,
  `fonts/x.woff2`, never a leading `/`.
- **Contrast, the deeper-step rule**: text and text-bearing fills meet WCAG AA (4.5:1, 3:1 for large text). Where a
  look's colour falls short, text-bearing fills use a deeper step of it; the original colour stays for dots, bars,
  marks and focus wherever it reaches 3:1. 0 failures across 22 look x mode combinations.
- **Targets**: at least 44 x 44 px on phones in every look (24 px on desktop).
- **Plain words**: no film-production jargon (Areas, VIPs, Review; "Call times" is the one approved exception).
- **Read-only, drafts-only**: copy and open only; nothing sends, answers invites, or writes to an account.
- Motion 150 to 350 ms, nothing loops, reduced motion turns it off; sound is opt-in (the All clear tick).

## Isaac's words

From the design-unification answers, the design audit and HANDOFF:

- "The 3 looks definitely work!"
- "the red could be darker"
- "lets get rid of the cheeky production nods"
- "way too much text on screen" (layouts v5, 29 Oct)
- "The menus are getting a bit dense and I want this to be fun to use." (3 Nov, asking for the design audit)
- "emphasize clarity without sacrificing fun"
- "I want callsheet and JamDash in design harmony", so that "moving between callsheet and JamDash is fluid".
- Decided against: Bold and Easy read in JamDash, and app-switch links.

Voice the audit set (plain, warm, brief; no exclamation marks, no jokes about failures): "Good morning, Sam. 6 replies,
one clash at 11." · "All clear. Nobody is waiting on you." · "Nothing booked. A clear run."

## Design principles

Verbatim from the Callsheet repo's `CLAUDE.md`, section "Design" (from design-audit-2026-11.md), one check each:

1. One loud button: one job per screen, one filled button; the rest outlined or plain text.
2. Say it once: a heading and at most one sentence; help hides behind "?"; let values speak.
3. Defaults first: works before Setup; each setting in one place; rare ones in one closed Advanced drawer.
4. Space groups, lines separate: spacing 4, 8, 12, 16, 24, 32 px; rules only where space can't do it.
5. Three sizes a screen: display face for the one headline and big numbers, body face for reading, small caps for
   rare labels; targets 24 px, 44 px on phones.
6. Make the end feel good: design the peaks, celebrate once and briefly, never guilt.
7. Motion explains: 150 to 350 ms, cause and effect only, nothing loops, reduced motion turns it off, sound opt-in.

## Open questions

From the design audit (section 10) and harmony.md (section 8), still open as far as these notes show:

1. Your day heading: "Call times" or "Briefs"?
2. Should the time zone default from Home Assistant without asking?
3. The All clear tick is built as an opt-in (Your day › Look and sound): keep it?
4. Later in One at a time: back at the next brief (built) or tomorrow morning?
5. A gentle week row: welcome, or too close to a streak?
6. Will JamDash adopt the AA deeper steps, or should Callsheet's text-bearing fills differ on purpose?
7. A shared look setting between the apps: wanted at all? (JamDash is per device; Callsheet saves per user on the
   server and per device.)
8. Plain copy in NERV and LCARS (no in-character labels): OK?
9. A shared line icon set so the phone tab bars match?
10. For this repo: is the Bold-only screenshot set enough, or are Clean, Easy read and the Jam looks wanted too?
