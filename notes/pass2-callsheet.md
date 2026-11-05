# Callsheet · Pass 2

Mockup: `mockups/pass2/callsheet.html`. Pass 1 (`mockups/pass1/callsheet.html`) is unchanged.

The page has four parts:
1. **A flow player.** Seven flows from `projects/callsheet/FLOW.md`, each a series of steps that drive a live desktop frame (1440 × 900) and a live phone frame (390 × 844).
2. A flow table and the content rules.
3. A day/night gallery: eight phone frames and four desktop frames, each with its lighting fixed.
4. Stress and empty cases: a long day (19 replies, 7 events, 5 security heads-ups) and a quiet day.

Page controls switch Lighting, Time (08:15 / 12:40 / 17:05), Day (Quiet / Normal / Long) and Primary order (D23 alert first vs pass 1's replies first). All content is made-up sample data (Sam, example.com, Co. A/B, Northwind Store).

Sources read:
- `notes/OVERNIGHT-BRIEF.md`, `projects/callsheet/README.md`, **`FLOW.md`**, `screens/INDEX.md`, and ten screenshots (briefing day 1440, briefing night 390, replies panel, agenda, setup home, setup Your day 390, one at a time 390, and others).
- `BIBLE.md` 0.5, all of `CHANGES.md` (A, B, D1–D52) and the end of `decisions.md`.
- Every `notes/pass1-*.md`.
- The pass-1 Callsheet mockup and `_hifi-base.css` (rocker).

## What changed since pass 1

FLOW.md changed the design more than any visual note. Pass 1 was built around a glance. Pass 2 is built around what FLOW says Isaac actually does:
- He opens the brief from the 06:30 push and reads it on his phone first.
- He acts on three things: the summary, the next reply with its draft, and the agenda.
- He barely touches Setup but finds it the densest part.
- His top Replies complaint is items that "shouldn't show up in replies, but continue to".

Changes by pass-1 audit number:

| Pass 1 # | Was | Now |
|---|---|---|
| 1 (High) one-sentence content | A layout rule only | A **content contract** printed on the page: the Today sentence is 25 words or fewer and never restates a time the scale shows; each rundown step has one sentence and at most three items; the push is one line. The sample sentences follow it (17, 13 and 5 words). |
| 2 (High) bar group doesn't scale | 7 bars drawn for 7 | **Capped at 10 windows**; above that, a full group plus the number in mono ("19"). The windows are now narrow square-cornered slots, so they no longer read as a row of zeros. |
| 3 (High) security vs orange | Replies kept the orange in the morning | **D23 order:** an open alert takes the Next card and the orange button ("Check the sign-in"); "It was me" quiets it to "Seen 08:15" (D11) and the button moves to Priya's draft. A page toggle shows pass 1's order for Isaac to compare. |
| 4 (Med) clash colour / reason dots | Amber, words | Kept, now in D21 form: amber window + ▲ + "Clash · pick one". "Due today" is a warn tag with ▲. VIP is an ink-outlined word tag. No colour dots. |
| 5 (Med) Colour bars vs orange | Colour bars on Today | **Stripes only** (its burnt orange `#b04a1c` is darker than control orange). It shows **only when calm** (D22), drawn in once: on All clear, on Today once nothing needs you, and on the quiet day. Session blocks (red square) and Colour bars are gone from Callsheet. |
| 6 (Med) empty desktop | 45% empty below three stops | Today is now hero → full-width day band → Next card + rundown list → footer. About 20% is still empty at 1440 × 900 in the alert state; the reply state fills it (audit 7). The rundown step mode centres its content vertically. |
| 7 (Med) band labels repeat the sentence | Sentence named the times | The sentence gives the "so what" ("one clash to settle") and the scale gives the times. Labels that would collide are dropped. |
| 8 (Med) Wheatley only a glance | The order, not the steps | **Rundown step mode:** four steps (Your day → Who needs an answer → Worth knowing → Coming up) plus an end card. A progress bar of four slot windows, ←/→ or swipe, Space to replay from Today, and at most one orange button per step. The push opens straight into step 1. |
| 9 (Med) hidden screens | Stubs; Projects off the tab bar | **No hidden places (D26):** five tabs on both devices (Today, Replies, Agenda, Ask, Projects) and a labelled Setup button in the header. Setup is designed (home, Your day, Advanced, a stub for Connections and AI). Projects is drawn plainly. People, Know me and Full brief are still missing (audit 14). |
| 10 (Low) invites | 2 shown | "Invites to answer · 18", soonest first, with **All 18** expanding in place. |
| 11 (Low) quiet LED | Unlit dot | Unchanged, now with words ("Seen 08:20", "Nothing new"). Still reads a little like a stray dot (audit 10). |
| 12 (Low) "Now" wrapped | 58 px column | "Now 08:15" sits on its own line above the rule. The next event gets "Next · in 1 h 15 min" (for the missed-11:30 story in FLOW §1). |
| 13 (Low) toast / swipe | — | The toast is unchanged. Swipe now also works in the rundown steps. |
| 14 (Low) J/K | Not wired | J/K move the list selection on desktop. The selected row lights a leading-edge slot window (D3 for lists). |

Shared findings adopted from the other apps:
- D21 warn.
- D22 accent only on calm.
- D23 primary order.
- D24 destructive: Start over is a dark-ink button inside a confirm sheet that names what it deletes. Enter never fires it.
- D26 nav.
- D29 jobs in place: Refresh and Ask fill a cream slot along the bottom of their own button, and the hero eyebrow says "Writing the summary · started 08:16".
- D30 13 px labels.
- D43 one popup sheet: a bottom sheet with a grip on the phone, centred on desktop, Close top right, Esc and veil close. It's used for the security alert, Not for me, Note and Start over.
- D6 / D11 / D12 from pass 1.

Two UX-driven reversals of pass 1:
- **Replies on desktop opens as list + detail, not One at a time.** FLOW §2 says the detail panel and its copy button are the most used, and One at a time (0.9.0) the least. One at a time stays a key away, and the Next card on Today already is "one at a time" for the first item.
- **The Next card is the item itself**, workable in place (Copy draft / Done / Open / Later / Note / Not for me), because FLOW §4 wants "the next reply with its draft: copy, open in Gmail, done" one tap from opening. Pass 1's "Start replies" was a step too many.

## Research

Web searches run this pass (WebSearch tool, 9 queries). Results were mostly help-centre pages, reviews and tech press. Items marked *(knowledge)* come from my own knowledge.

| Product | What it does to reduce overwhelm | Lesson for Callsheet |
|---|---|---|
| **Google CC** (Labs, Dec 2025; [SiliconANGLE](https://siliconangle.com/2025/12/16/google-tests-cc-ai-agent-summarize-email-calendars-documents/), [Android Central](https://www.androidcentral.com/apps-software/ai/googles-cc-ai-agent-is-a-morning-brief-for-early-birds-that-taps-into-workspace)) | A single "Your Day Ahead" email each morning from Gmail, Calendar and Drive. You reply to it to add to-dos, notes or preferences, and its replies go only to you. | The closest product to Callsheet. Its whole interface is one message, and corrections are made by talking back to it. That supports Callsheet's Note and "Something missing? Tell Callsheet" as the way to fix the brief, rather than more settings. |
| **Superhuman Split Inbox** ([help](https://help.superhuman.com/hc/en-us/articles/38449611367187-Split-Inbox-Basics)) | Default split Important / Other (people vs automated). You correct the sorting with ⌘K "Move to Other" for a message, sender or domain. Custom splits can also show in Important. | **Not for me** becomes a sorting correction with scope (this message vs this sender), not a dismissal. Needs you / For your info is a split that never hides anything. |
| **Google At a Glance** ([Android Authority](https://www.androidauthority.com/google-at-a-glance-widget-store-3376155/), [9to5Google](https://9to5google.com/2023/10/06/at-a-glance-widget-redesign-pixel/)) | One slot on the home and lock screen shows whichever context matters now (next event, flight, delivery, weather). The user picks the categories. | One slot that changes with the moment is the Next card. Only one thing shows; the rest waits. |
| **Apple Weather alerts** ([Cult of Mac](https://www.cultofmac.com/796318/apple-news-in-weather/), [Tom's Guide](https://www.tomsguide.com/phones/iphones/ios-weather-app-severe-weather-alerts)) | A government severe-weather alert sits at the very top and pushes other modules (News) out of view. | An open alert takes the top slot and the button, and decoration and extras step back (D22, D23). |
| **Arc Search "Browse for me"** ([TechCrunch](https://techcrunch.com/2024/01/28/arcs-new-iphone-browser-wants-to-be-your-search-companion), [Inverse interview](https://www.inverse.com/tech/arc-search-ios-app-interview-lead-designer-engineer)) | A splash says what it's reading ("six pages"), then a generated page of short headed sections with links back to the sources. Reviewers say it is thin beyond a cursory glance. | The Ask "Looking" state names what it searched, and every answer keeps its sources. Short headed steps work for a glance, and Callsheet must keep "All N" one tap away for depth. |
| **Apple Journal** ([MacStories](https://www.macstories.net/reviews/apples-journal-app-journaling-for-all/), [Pratt critique 2026](https://ixd.prattsi.org/2026/02/design-critique-journal-iphone-app/)) | Almost nothing on screen (entries and one New Entry button). Suggestions hide behind "+" and can be skipped; a design critique warns that heavy suggestion erodes agency. | Progressive disclosure: settings rows show one line and open on Change. The AI suggests (drafts) and the owner presses (Copy). Keep drafts-only. |
| **Notion Calendar menu bar** ([Notion help](https://www.notion.com/en-gb/help/notion-calendar-settings), [TechCrunch](https://techcrunch.com/?p=2652678)) | Shows only the next event and when it starts, so you can stay focused. You set how far ahead it previews. | "Next · in 1 h 15 min" on the agenda, and a clash takes the Next card only within the hour (my proposed time scope for D23 warns). |
| **Sunsama** ([help: Daily planning](https://help.sunsama.com/docs/daily-planning), [shutdown changelog](https://roadmap.sunsama.com/changelog/daily-shutdown)) | A morning ritual, then a shutdown you schedule. If you skipped the shutdown, yesterday's leftovers come first. Reviewers note no streaks or badges. | A rundown with a clear end ("That's the rundown") and a calm evening state. Celebrate once, never guilt (Callsheet principle 6). No streak row. |
| **Things 3** ([App Store](https://apps.apple.com/us/app/id904237743), [design study](https://blakecrosley.com/blog/design-study-things)) | Today: calendar events at the top, This Evening at the bottom. It separates "when" from "due". A user asks for an urgent group on top. | The day band sits above the work, and the urgent thing (alert) sits on top. "Later" means a time (back at 12:30), not a due date. |

Common thread: the calm products show **one thing at a time in a fixed slot** (At a Glance, Notion's menu bar, Weather's top module). They **separate sorting from hiding** (Superhuman). They **end the session clearly** (Sunsama). And they **make correction cheap** (CC replies, Superhuman ⌘K). That gives Callsheet four patterns: the Next card, Needs you / For your info, the rundown's end card and All clear, and Not for me / Note.

## Design

**The flow first.** The page opens with a flow player rather than screens. The seven flows come straight from FLOW §1, §3, §4 and §6:

| Flow | Steps | What it proves |
|---|---|---|
| A · Morning, from the push | lock screen → rundown 1–4 → end → Today | the rundown is the front door (approved Wheatley direction) |
| B · Clear the alert, then replies | Today (alert Next) → alert sheet → It was me → Copy → Done → All clear → calm Today | the moving primary (D23), seen alerts (D11), jobs with Undo, the accent only on calm (D22) |
| C · Wrong item: Not for me | Replies list+detail on Northwind Store → Not for me sheet → moved out | the fix for "notes about emails that shouldn't show up" |
| D · Check the day | Today band → Agenda → All 18 invites → Tomorrow | agenda one tap away, "Next · in …" for the missed 11:30 |
| E · Find or ask | ⌘K palette → Looking (steps + Stop) → answer with sources | read-only search, jobs in place |
| F · Refresh | idle → slot filling on the Refresh button → toast with what changed | D29 |
| G · Setup, less dense | home → Your day (Change open) → Advanced (Start over) → confirm sheet | the most-complained-about screen, D24 |

**Today (desktop).** It reads top to bottom:
1. Eyebrow + greeting + **one sentence** (the content contract).
2. **The day band**, a black ribbed tuning scale (07–21). Events are slot windows; past events are unlit. A clash shows as **two stacked amber windows** on two lanes with "▲ Clash · pick one". The needle marks now. The band header carries "6 events · ▲ 1 clash · Agenda A". The whole band is a button.
3. **The Next card** (left, wide). Exactly one thing, chosen in D23 order:
   1. open security alert;
   2. a clash starting within the hour;
   3. the first reply, with its editable draft and Copy draft (orange, C), Done (D), Open in Gmail (O), Later (L), Note (N), Not for me (X);
   4. calm: "Nobody is waiting on you" + See tomorrow.
4. **The rundown** (right): rows 2–4 numbered to match the steps, each with its indicator (count bar group, alert LED + word or "Seen 08:20", nothing for Coming up). "Play the rundown" (Space).
5. Footer: what the brief was written from, and "Nothing was sent. Drafts wait for you."

**Today (phone).** The same order, stacked: hero, compact band (no labels, odd-hour ticks), Next card (draft clamped to two lines), then the rundown rows. The first screen always shows the Next card's buttons.

**Rundown step mode.** No header or tabs, just a walnut trim, a progress row (the step name + four slot windows lit up to the current step) and Close.
- **Steps:**
  1. Your day: sentence + band.
  2. Who needs an answer: the three that matter most with their reason tag, a bar group and "All 7".
  3. Worth knowing: security heads-ups first, then what changed. Only three items; "All 5 security heads-ups" in the long day.
  4. Coming up: three date tiles.
- **End card:** "That's the rundown", the promise, "Something missing? Tell Callsheet" (a Note sheet: "The callsheet briefs are missing a lot of things" gets a direct place), and the next thing as the one orange button.
- **Navigation:** Back / Next are quiet keys with ← → keycaps. On the phone, swipe works too.

**Replies.**
- Desktop is **list + detail**.
  - The list splits into **Needs you · 6** and **For your info · 1** ("sorted, never hidden"). Each row has a leading-edge slot window (lit cream when selected), who, a one-line why, age and the first tag. J/K move.
  - The detail is the reply card with "exact details" fact chips ("Deadline: Fri 6 Nov", "Amount: €48,500", "Quoted from the message"), the draft, and the actions.
  - When there's no draft (For your info), the card's orange button is **Not for me** instead of Copy draft.
  - One at a time is the second key: the card plus a dimmed "Up next" peek.
- Phone: the list first, a tap opens the card, swipe right = done, left = later.
- **Not for me sheet:** "Take Northwind Store out of Replies?"
  - Four reason keys with square windows: promo / just for my info / already handled / something else.
  - A rocker for "Same for everything from Northwind Store", saved as a rule in Setup › Your day.
  - **Move out of Replies** (orange), with Undo in the toast.
- **All clear:** the Stripes accent draws in once, then a green LED + "7 of 7 done today", "All clear.", "Nobody is waiting on you.", Back to Today.

**Agenda.**
- Free gaps collapse to "Free · 1 h 15 min".
- "Now 08:15" sits on its own line, and "Next · in 1 h 15 min" goes on the next event.
- The clash is an amber-outlined group with its related Slack message inside it. A past clash quiets to a hairline and "Clashed".
- Invites: soonest first with All 18 in place. Today / Tomorrow keys.

**Ask.**
- A header line: "reads your mail, chat, calendar and notes · never sends".
- The question, then the "Looking" state: a lit slot, each step as it happens, and Stop.
- The answer with source chips and Copy answer, then suggestions.
- The Ask button shows its own progress slot.

**Setup (the densest screen today).**
- Desktop: four places on the left, each with an LED and its current value in one line:
  - Connections "4 Google · Slack · Signal off";
  - Your day "Briefs 06:30 · 12:30 · 17:00";
  - AI "Swift writes · careful at every brief";
  - Advanced "10 rare settings, all closed".
- Home says "Callsheet works without touching any of this." and has Find a setting.
- **Your day** is two cards of one-line rows:
  - **Briefs:** a rocker and "06:30 · Every day · Careful" each, with **Change** opening time, day keys and writer in place.
  - **Quiet hours** (rocker).
  - People who always count, Never needs a reply (the rules Not for me writes), You, Look and sound.
  - Changes save at once, so there's no Save button and no orange primary on the screen.
- **Advanced** is ten closed drawers. Start over says what it deletes, then a confirm sheet:
  - "Keep everything" (secondary);
  - **Start over** (dark ink, never orange or red);
  - no Enter shortcut.

**Look.** Simplified Braun Hi-Fi as in CHANGES A1–A10:
- Jam Theme surfaces (day `#e3e1dc` / `#f1efeb`, night `#1c1c1b` / `#2a2a28`).
- Jost and IBM Plex Mono.
- Ribs only on the day band.
- Flat windows that are always a dark recess.
- Orange only on the one primary per screen or sheet and on rocker paddles.

Measured contrast:

| Text | On | Ratio |
|---|---|---|
| dim `#615e57` | card / ground | 5.63 / 4.95 |
| warn-ink `#7f5a00` | card | 5.43 |
| alert-ink `#b3261b` | card | 5.70 |
| night dim | card | 5.70 |
| band-dim | band | 6.93 |
| ink | orange, day / night | 6.06 / 6.79 |

Labels are 13 px uppercase, body 15+, keycaps 12 px (desktop only), and phone targets 44 px or more.

**Keys (desktop):**
- Enter = the orange button; Space = play the rundown.
- ← → = steps; 1–5 = tabs; A = agenda.
- / or ⌘K = Find or ask.
- C D L O N X = reply actions; J/K = list.
- Esc = close or back.

## Audit

I checked with Playwright (Chromium, `chromium.launch()` with no options):
- page widths 1500 (light scheme) and 390 (dark scheme);
- every step of all seven flows in Day and Night;
- the time and load variants, and the long-day midday state;
- all 18 gallery frames;
- a keyboard run (Enter, Esc, Space, →, 2, J, J, K, C, D, 3, 5, 1, /, Esc).

Results: **no JS errors, no horizontal page scroll at 390, no text under 12 px** inside the app frames, and nothing measured outside its frame.

The fix pass corrected these:
- the count windows reading as "0000000" (now narrow square slots);
- the needle crossing the "Drop-off" label;
- the phone band header wrapping into four lines;
- the step-mode content sitting at the top of an empty 900 px (now centred and larger);
- "Next, in 1 h 15 min" wrapping inside the event name on the phone;
- the evening's "1 change since last night" for "Nothing new";
- the All clear promise inheriting 20 px;
- a thin, invisible selected-row window;
- "Nothing booked" said three times on the quiet day;
- a truncated Ask placeholder.

| # | Problem | Severity |
|---|---|---|
| 1 | **The alert blocks Copy on Today.** With an alert open, Today's Next card is the alert, so Priya's draft is one more step away (Replies tab, or "It was me" first). This is correct by D23, but on a busy morning Isaac may want both. One option is a quiet "Next reply: Priya N." line under the alert card. | High |
| 2 | **The count is said twice in the long day.** The rundown row says "11 waiting" *and* the capped bar group prints "11". D25 lets a meter carry its own number, but the row text repeats it. Either the row drops the number when the cap shows it, or the cap's number is enough on its own. | Medium |
| 3 | **The "within the hour" warn rule is mine.** D23 says alert → offline → warn → routine, with no time scope. Without one, a clash at 11 would take the button at 08:15, before every reply. Isaac needs to decide on the scope (and what the 60 minutes should be). | Medium |
| 4 | **The "Same for this sender" rocker defaults to on** in Not for me. That's fast, but a broad rule can hide a real reply from that sender later. FLOW §6 says VIPs always show. The sheet should say "Never applies to VIPs or security", and the rules need a review place (Setup › Your day › Never needs a reply is a one-line row only). | Medium |
| 5 | **Setup › Your day shows four orange paddles** (three briefs + quiet hours) and nothing else orange. Each is allowed (paddles count separately, D39), but the screen reads orange-heavy, the same as HA pass 1 #1. | Medium |
| 6 | **Desktop list+detail reverses pass 1's default.** It's backed by FLOW §2, but it's a behaviour change from 0.9.0, where One at a time is the loud button on Replies. Isaac should confirm. | Medium |
| 7 | **The Next card's height changes with its type**: alert about 150 px, reply about 245 px, calm about 145 px. The rundown column stays put, but the footer jumps when the alert clears. At 1440 × 900 about 20% of the screen is empty in the alert and calm states. | Medium |
| 8 | **Wheatley "in the car" means voice.** The rundown is drawn as steps but not as audio. A spoken version (with the same steps, the progress windows as the only visual, and Next by voice or a tap) isn't designed. | Medium |
| 9 | **Only Hi-Fi is drawn.** Callsheet ships Bold, Clean, Easy read and nine Jam looks. Step mode, keycaps, slot windows and the two-lane band need checking in at least Bold and Easy read (larger type will stress the phone band and the Next card). | Medium |
| 10 | **"Seen" is an unlit LED + word.** It's right by the window rule, but at a glance on the rundown row it still reads like a stray black dot (pass 1 #11). | Low |
| 11 | **The phone tab bar's unlit windows** read as a row of black dashes in Day (inherits HA #10). | Low |
| 12 | **Space as a shortcut** plays the rundown on Today, but when a button has keyboard focus, Space presses that button instead. The key sheet ("?") isn't drawn, so the conflict isn't explained. | Low |
| 13 | **Labels on the band are dropped when they'd collide.** In the long day, some events show only as windows. That's fine for a glance, but the dropped ones have no hover or label. | Low |
| 14 | **Not drawn:** Full brief (By area, What changed in full), People (Same person?), Know me, the Weekly review run, Look panel, key sheet, first-run wizard, Connections and AI places (stubs), Projects detail, an offline state (Google not reachable, D27), and a failed refresh. | Medium |
| 15 | The rundown's step 2 picks "the three that matter most" by list order. The real rule (VIP > due today > asked > waiting) has to come from the sorter and be the same in the list. | Low |
| 16 | The mockup loads Jost and Plex Mono from Google Fonts. The product must bundle them (README constraint: offline, OFL). | Low |

## Change suggestions for pass 3
- **Alert + reply together (audit 1):** try the alert Next card with a one-line "Then: Priya N., budget sign-off · Copy draft" row inside it. The button stays on the alert, and Copy is a quiet key. Compare it with today's strict version.
- **Count once (audit 2):** drop "N waiting" from rows where the bar group prints its overflow number, or print the number only (no bars) above 10. Test both at 19.
- **Not for me scope (audit 4):** add "Never applies to VIPs or security" under the rocker, and design the **Never needs a reply** list (rules with sender, reason, when added, and an Undo-style Remove).
- **Voice rundown (audit 8):** design "Read it to me": the same four steps, large type, progress windows, auto-advance with a visible pause, and Next / Back / Stop as big keys. It needs a quiet-hours check, and sound is opt-in.
- **Desktop height (audit 7):** try letting the Next card hold the next two items (the current one, plus a peek of the second) so it keeps a steady height, or fix the split row's height to the tallest state.
- **Looks:** render Today, the rundown and Replies in Bold and Easy read with the same structure.
- **Missing screens:** Full brief as the rundown "expanded" (each step's All N on one page), People with the Same person? card, the Weekly review as a step mode (same component as the rundown), and offline/failed states (D27: "Google not reachable since 06:30 · Try again" as a warn Next card).
- **Setup orange:** try the paddles in a graphite finish with a cream lit window for list rows (HA option b) and count the oranges.
- **Key sheet:** draw "?" and resolve Space (only when nothing is focused, or use R for rundown).

## Bible implications
1. **Moving primary needs a time scope (extends D7/D23):** time-bound warns (clashes, starts soon) take the one orange button only within a set window (proposed 60 min). Before that they ride in the list with their warn mark.
2. **The Next card as a shared component:** a front door shows the next thing *itself*, workable in place, in one fixed slot (LED + word + lab, title, one sentence, one orange button, quiet keys). It's the same grammar as Jam-Dash's trouble card. Propose it as the house "one next action" pattern.
3. **Step mode as a shared pattern:** a sequence of full-screen steps with a progress row of slot windows lit up to the current step. ← → / swipe, at most one orange per step (none when a step has no action), and an end card that hands off to the Next card. Rundown, Weekly review and first-run setup would all use it. It's distinct from carousels (§9), because steps are linear and always end.
4. **Callsheet's accent is Stripes, shown only when calm (applies D22):** Session blocks' red square and Colour bars' light oranges are not used in apps with an orange primary on the same screen (resolves D10 for Callsheet).
5. **Bar group cap (D6), plus "count once":** at most 10 windows, then a full group plus the number. When the cap prints the number, the row text must not repeat it.
6. **Seen alert (D11) as a defined form:** an unlit LED + "Seen hh:mm" in the dim word colour. The item stays listed (never hidden) but loses the red, the alert word and the button.
7. **Sheets (D43) refined:** a form sheet whose changes do not apply live may hold one orange button (Save / Move out). A destructive sheet holds none, and Enter never triggers a destructive button (extends D24).
8. **Selected rows in desktop lists use a leading-edge slot window** (lit cream when selected), the list counterpart of the base window (D3, desk and phone, not just TV).
9. **Two-lane tuning scale (details for D8):** overlapping events stack into two lanes as separate windows, a clash is amber + ▲ + word, past events are unlit, labels that would collide are dropped rather than overlapped, and the needle starts below the label row.
10. **A content contract for AI-written text:** a front door's generated sentence is 25 words or fewer and must not restate a value a meter on the same screen shows. "Never twice" applies to generated text too.
11. **Navigation (D26) as applied to Callsheet:** five tabs on both devices (Today, Replies, Agenda, Ask, Projects), with Setup as a labelled header button, never behind More. "Chat" is called "Ask" (one word for the palette and the tab).
12. **Rocker orange in settings lists:** decide whether paddles in long lists stay orange (bible §4) or become graphite with a lit window. Today a settings screen can show four or more oranges with no primary (links D39 and HA pass 1 #1).
