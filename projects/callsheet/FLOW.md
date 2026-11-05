# Callsheet: experience flow (answers for the design hub)

From the Callsheet session, 2026-11-05. Facts only. Callsheet keeps no usage analytics, so the answers on what
Isaac does come from what he has told me and from server log counts, not from tracking.

## 1. A normal day

- **06:30 morning brief.** Since 0.6.1, Swift writes it before Isaac wakes (about 3–5 min). He reads it on his
  phone first. A push notification says the brief is ready, and he opens the Briefing from it.
- **12:30 and 17:00 check-ins.** Isaac has set Careful (Swift) for all three times. The new default for other people
  is Careful in the morning and Fast at other times.
- **What he opens and acts on:**
  - the Briefing summary;
  - Replies, with the draft to copy;
  - the Agenda, which is how he noticed a missed 11:30 meeting.
- **What he ignores:** most of Setup. Areas (before Chat replaced it) and the long Delivery step were never used day
  to day. That is why Setup became four places plus Advanced.
- **What frustrates him:** emails his notes say need no reply still showing up in Replies (fixed in 0.9.1, not yet
  live).

## 2. Most and least used

- **Most:** Briefing, Replies (with the detail panel and the copy-draft button), Agenda.
- **Growing:** Chat (from 0.6), Know me (scan and profile done), People (he confirmed merges right after 0.8.2).
- **Least, or too new to say:** One at a time (0.9.0), Projects (0.7), Setup.

## 3. What he has called daunting (quotes)

- "There's way too much text on screen."
- "I like it, it's looking a bit dense and I know we aren't done adding things."
- "The menus are getting a bit dense and I want this to be fun to use."
- On redesign: "emphasize clarity without sacrificing fun."
- On missed items: "The callsheet briefs are missing a lot of things."
- On notes: "I keep writing notes about emails that shouldn't show up in replies, but continue to."
- Most complaints: Setup (density), then Replies (wrong items).

## 4. One tap from opening

- Today's rundown (Briefing / Wheatley).
- The next reply with its draft: copy, open in Gmail, done.
- Today's schedule and invites to answer.
- Refresh.
- Find or ask (⌘K, "/") and Chat.
- A note for Callsheet on any item.

## 5. A typical day's data (live log counts, 2026-11-02 to 11-04)

| What | Typical count |
|---|---|
| Accounts | 4 Google, 8 calendars, 1 Slack workspace (Signal linking optional) |
| Mail threads read per sync | 70–94 |
| Needs a reply | 14–19 before AI sorting; expected fewer after 0.9.1 |
| Events on today's schedule | 2–7 |
| Invites to answer (60 days) | about 18 |
| Security heads-ups | 3–5 |
| Brief | a 3–6 sentence summary plus up to 8 drafted replies |
| Sorter | about 260 items in the first run |
| Projects | few so far (new in 0.7) |

## 6. What has to stay

- **Read-only and drafts-only.** Nothing is ever sent, accepted or deleted. "Nothing was sent" is a promise in the UI.
- **Keyboard:**
  - ⌘K / Ctrl+K / "/" for Find or ask;
  - J and K to move through rows;
  - D, C, O and N for done, copy, open and note;
  - "?" for the key sheet.
- **Phone:**
  - swipes in One at a time;
  - bottom tabs;
  - 44 px targets.
- **Never hidden:** security alerts, invites and VIPs always show. AI sorting can group and rank but never hide.
- **Undo:** every action that changes state can be undone.
- **Looks:**
  - Bold, Clean and Easy read, plus the nine Jam looks under JamDash's ids;
  - WCAG AA contrast;
  - works fully offline (bundled fonts, relative URLs).
- **Sources and safety:**
  - every AI sentence pinned to its source;
  - links built by Callsheet only;
  - message text is always untrusted data.

## Direction already approved (for context)

Isaac approved "Wheatley" on 2026-11-04: the brief becomes a step-by-step rundown, "like I'm in the car with my
assistant Wheatley": your day → who needs an answer and why → what you should know → coming up. It comes with
connectors (YouTube, news) and adapts to each person. Design: `~/project/daily-brief/wheatley/design.md` and the
summary https://claude.ai/artifact/2ZGsn344qfQDcQUbg9jPnx (private to Isaac). A redesign "less daunting when opened
up" should build on this flow: the rundown is the front door, and lists and settings are one tap behind it.
