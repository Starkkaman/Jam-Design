# Callsheet · Pass 1

Mockup: `mockups/pass1/callsheet.html` (interactive). It has a flow diagram, Today on desktop (1440 × 900) and phone (390 × 844), and these follow-on states: Replies one at a time (desktop and phone), All clear, Agenda, Ask, the Find or ask palette (⌘K) and Worth knowing. Page controls switch Day/Night and the time of day (Morning 08:15 / Midday 12:40 / Evening 17:05). All content is made-up sample data in the style of Callsheet's own `sample_brief.json` (Sam, Priya N., Co. A/B, example suppliers).

Sources read: `projects/callsheet/README.md`, `FLOW.md`, `screens/INDEX.md` plus the briefing, agenda and one-at-a-time screenshots, `BIBLE.md` 0.5, `CHANGES.md` A–D, the end of `decisions.md`, mockup 13 and `notes/pass1-tv-launcher.md`.

## Research
I ran three web searches. Most results were third-party reviews and app-store pages, not vendor docs. The other items below come from my own knowledge and are marked that way.

- **Sunsama** (web): each day starts with one planning question ("what do you want to get done?"), carryover gets reviewed, and Focus Mode then shows only the current task. *Lesson:* a short ritual at open, then one thing at a time. ([Sunsama blog](https://www.sunsama.com/blog/how-to-increase-work-efficiency), [Asian Efficiency review](https://www.asianefficiency.com/schedule-management/sunsama-review/))
- **Superhuman** (web): built for the keyboard, with a command bar for anything that has no shortcut, Split Inbox for VIPs and people, and a full-screen reward at Inbox Zero. *Lesson:* every triage action has a key, ⌘K covers the rest, and finishing feels like an event. ([Superhuman blog](https://blog.superhuman.com/inbox-zero-in-7-steps/), [Medium review](https://medium.com/swlh/superhumans-superpowers-a-product-review-6f21535b9a45))
- **Things 3** (web): Today puts calendar events at the top and to-dos below, with a separate This Evening group at the bottom. One reviewer wants an "urgent" group above it. *Lesson:* split the day by time, and keep what matters above the fold. ([App Store](https://apps.apple.com/us/app/id904237743))
- **Fantastical DayTicker** (knowledge): a horizontal strip of the day's events above the list. It's the closest software relative of the day band here.
- **Braun / 70s radio tuning scales** (knowledge): a black window with a printed linear scale and a needle. This is where the "Your day" band came from: read-only, linear (not a dial), so it fits BIBLE §4.
- **Command palettes** (Raycast, Linear; knowledge): search, jump and ask in one box, with the top row as the default action. Callsheet's Find or ask already works this way, so I kept it and made Ask the top row.

## Design (what and why)
**UX first.** I wrote the flow before drawing any screen. The flow is the SVG plus the table at the top of the mockup. Isaac opens Callsheet from the 06:30 push on his phone, then from a desk tab at the 12:30 and 17:00 check-ins (FLOW §1). FLOW §4 lists what must be one tap from open: the rundown, the next reply with its draft, today's schedule and invites, Refresh, Find or ask, and Note. Everything else can wait.

**Today (the front door)** follows the approved Wheatley order (your day, who needs an answer, what to know, what's coming):
1. A greeting and **one sentence** about the day.
2. **Your day**: a black ribbed band drawn as a tuning scale from 07 to 21. A needle marks now, events are lit cream windows, past events are dark recesses, and a clash lights amber. Click it, or press A, to open the Agenda.
3. **Three stops**: Replies (a bar group that empties as you work), Worth knowing (a red LED plus the word "Alert" for security), and Coming up. On the phone, the stop holding the orange button is a card and the other two are rows.
4. One quiet "Also" line: Full brief, What changed, Projects. On desktop the line ends with the fixed promise, "Nothing was sent. Drafts wait for you."

**The orange button moves to the next thing.** In the morning it's Start replies. At midday it's Start replies for what's left. Once replies are clear, it moves to the security check if an alert is still open, otherwise to See tomorrow. There is still only one loud button per screen, but it also tells you what's next. That covers "less daunting" without adding words.

**Replies open one at a time by default**, with List one key away. Each card shows who, why, tags as words (no colour dots), and the editable draft. Copy draft is the primary (C), Done is secondary (D), and Later (L), Open (O), Note (N) and Not for me (X) are quiet text. Every state change shows a toast with Undo. On desktop, an "Up next" column lists the next three. On the phone you swipe right for done and left for later. The last Done leads to **All clear**, the one place the Session blocks accent drops in, once.

**Agenda** collapses empty hours into "Free · 1 h 15 min" lines instead of drawing a 7 am–10 pm grid. The clash is one amber-outlined group marked "Clash · pick one", and the related Slack message sits inside it ("Dev T. asked to move the review to 11:30", which opens that reply). Invites have their own card, and each one opens "Answer in Calendar" (read-only).

**Ask / Find or ask:** ⌘K, Ctrl+K or / opens the palette from anywhere, with Ask as the top row, then people and threads, then settings. The Ask page shows the answer with source chips, "Copy answer", and suggestions. The header line reads "reads your mail, chat, calendar and notes, never sends".

**Look:** simplified Braun Hi-Fi as in CHANGES A1–A10. Flat cards with soft corners, Jost for words and Plex Mono for times and counts. The only ribs are on the day band. Indicator windows are always a dark recess and light with flat colour. Orange appears once per screen. The **Colour bars** accent sits on Today, entering from the right edge in the hero's clear zone, away from the header and the content. **Session blocks** appear only on All clear. Phone tabs drop from 5 to 4 (Today, Replies, Agenda, Ask). Each has a small base window that lights cream when selected, the same window grammar as the TV selector (D3).

**Keyboard (desktop):** Enter = the orange button, A = agenda, 1–4 = tabs, ⌘K / Ctrl+K / / = find or ask, Esc = back to Today. In Replies: C, D, L, O, N, X. The key hint is printed on each button as a small keycap.

## Audit
Checked with Playwright (Chromium) at page widths 1500 and 390, light and dark page themes, Day and Night frames, all three times of day, and a keyboard run through Enter → C → D×7 → All clear → Esc → A → ⌘K → Enter. There were no JS errors, no horizontal page scroll at 390, and no text under 12 px inside the app frames. The fix pass corrected: the page's segmented-control style leaking into the app, the needle running through event labels, past clashes staying amber, the count bars reading as "0"s, the All clear promise inheriting 20 px, and a truncated Ask placeholder.

| # | Problem | Severity |
|---|---|---|
| 1 | **The one-sentence summary is a content rule, not just a layout rule.** FLOW §5 says the brief is "a 3–6 sentence summary" today. At that length the phone hero pushes the stops below the fold and the calm is gone. The writer (Swift/Claude) has to produce one sentence, with the long version behind Full brief. | High |
| 2 | **The count bar group doesn't scale.** It's drawn with 7 bars, but the logs show 14–19 needs-a-reply a day before AI sorting. Twenty bars would be noise. It needs a cap (for example 10 bars, then a full group plus "14"). | High |
| 3 | **Security vs. the orange button.** In the morning the open security alert gets a red LED and the word, but Start replies keeps the orange button. The alert only takes the button after replies are clear. FLOW §6 says security always shows; whether it should also *come first* is Isaac's call. | High |
| 4 | **Clash colour and reason dots.** Callsheet 0.9 draws clashes in red and uses a red VIP dot (`--r-vip #d23a2a`), which breaks colour discipline (red = alerts only). Here clashes are amber and reasons are written as words. That drops the five reason colours, which Isaac may miss. | Medium |
| 5 | **The Colour bars accent and the orange button share a hue range.** The lighter bars (`#d68a2c`, `#e3b24a`) sit close to the control orange `#ec7c22`, especially at night on desktop, where they're about 600 px from Start replies. The bible's "decorative oranges stay darker than control orange" isn't met by the top of this palette. | Medium |
| 6 | **The desktop 1440 × 900 Today is about 45% empty below the stops.** That's calm on purpose, but it may read as unfinished. Options: centre vertically, scale the type up, or let the day band grow taller. One-at-a-time has the same issue. | Medium |
| 7 | **Partial repeat.** The day band's labels ("Stand-up", "Clash: roadmap + supplier call") repeat what the sentence says on the same screen. That isn't a control/indicator mirror, but it bends "say it once". The phone band drops the labels, which avoids it. | Medium |
| 8 | **Wheatley is only a glance here.** The approved direction is a *step-by-step* rundown "like I'm in the car with my assistant". This pass gives the order (day → replies → know → coming) but not a step-through or audio mode. | Medium |
| 9 | **Hidden screens aren't designed yet.** Full brief, What changed (shown only as Worth knowing), Projects, Weekly review, Setup, Know me, People and Notes are stubs or missing. Projects leaves the phone tab bar, which needs Isaac's OK. FLOW lists People as growing. | Medium |
| 10 | **Invites:** about 18 come in over 60 days, and two are shown. The card needs "All 18" and an order rule (soonest first). | Low |
| 11 | In Worth knowing, a quiet state shows an unlit LED with nothing to say. That's correct per the window rule, but it reads as a stray dot on the phone rows. | Low |
| 12 | The agenda's "Now 08:15" wraps to two lines in the 58 px time column. | Low |
| 13 | On the phone, the toast sits above the tab bar and covers the bottom row of content for about 4 s. Swipe has no affordance beyond the hint line. | Low |
| 14 | Key hints: 1–4, A and Enter are new keys. The J/K row movement from 0.9 isn't wired into the List view yet. | Low |

## Change suggestions for the next pass
- Write a **brief content contract**: one sentence of 25 words or fewer for Today, and the rundown steps for Full brief. Show a "long day" stress case (19 replies, 7 events, 5 security heads-ups) to test the calm.
- Count indicator: cap at 10 bars, then show the number. Try it with 19.
- Try two orderings for the moving orange button (security first vs replies first) and ask Isaac.
- Swap Today's accent to Stripes, or move Colour bars to a screen with no orange primary nearby. Check the night contrast between the accent and the button.
- Desktop 1440: try a taller day band (two lanes so a clash shows as two windows) and vertical centring. Try "Up next" as a peek of the next card instead of a list.
- Design the Wheatley step-through: the same stops as full-screen steps with Next (Space / →), and a spoken version later.
- Design Full brief, People (the Same person? card), Projects and Setup home in the same quiet structure, aiming for 1 heading + 1 sentence + controls (README principle 2).
- Agenda: put the time and "Now" on one line, show invites as "All 18", and fold "messages about that time" into each event the way the clash group does.

## Bible implications
1. **Clashes are warn, not alert.** Colour discipline needs an explicit line: calendar clashes, overdue items and "due today" use warn (amber) + shape + word, and red stays for security and real faults. Category or priority dots may not use red (this hits Callsheet's `--r-vip`).
2. **Bar group cap.** §3 "Bar group = a count" needs a maximum (about 10) and an overflow form (full group + number).
3. **The moving primary.** §4 / Words could add: "The one orange action sits on the next thing, and may move between cards as the state changes. It never splits into two." It also needs an order when two things compete (security alert vs. work queue).
4. **A new read-only meter: the tuning scale.** A linear scale on a ribbed black band with a needle at now and lit event windows. It's read-only, so it's allowed under §4, and it belongs in the §5 Meters table. Past items go to an unlit window, not grey text on a lit one.
5. **Keycap hints** as a shared desktop component: 12 px Plex Mono in a recessed chip, printed on the button they trigger. Hidden on touch.
6. **Accent palettes vs. control orange.** §2 Accents says decorative oranges stay darker than the control orange, but Colour bars' `#d68a2c` / `#e3b24a` / `#efd58a` are lighter. Either reword the rule as "never within N px of an orange primary" or retune the palette's top bars away from orange.
7. **Acknowledged alerts.** Security heads-ups "always show" (Callsheet FLOW §6), but after they're seen they need a quieter form than **alert**. Proposal: an unlit LED + the word "Seen 08:20". Should this become a state-word variant, or stay app-specific?
8. **Phone tab bars use the base-window selector** (a small slot above the icon), extending D3 "one focus grammar per device" to phone navigation in every app.
