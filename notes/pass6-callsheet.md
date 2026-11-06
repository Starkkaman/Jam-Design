# Callsheet · Round 6 (pass 6): calm groups, a proper chat

Mockup: `mockups/pass6/callsheet.html`. Earlier rounds are unchanged.

The page has three parts:
1. **A flow player** with 15 flows (A–O). Each step sets a live desktop frame (1440 or 1280 × 900) and a live phone frame (390 × 844).
2. **Day and night**: 16 desktop frames (1280 × 800) and 18 phone frames, covering every place at both lightings.
3. **What's new or redrawn**, described.

Page controls: Lighting (Day / Night), Desktop width (1440 / 1280), Page (Auto / Light / Dark). You can type in Ask (Enter sends; a sample answer comes back) and in Setup's call times. All content is made-up sample data: Sam, Co. A/B, `example` domains, 07700 900xxx numbers.

Sources read: the last entry of `decisions.md`; `notes/OVERNIGHT-BRIEF.md` (incl. Round 6 direction); `mockups/01-directions.html` panels B and D; `mockups/pass5/callsheet.html` (tokens, all flows) and `mockups/pass3/callsheet.html` (the cards); `notes/pass5-callsheet.md`, `notes/pass3-callsheet.md`; `notes/RULES-TIERS.md` §1; `projects/callsheet/README.md` and `FLOW.md`. No web research this round.

## How I read Isaac's notes

| Isaac said | What I did |
|---|---|
| "I love the colors, font choice, and overall vibe of Callsheet round 5" | Round 5's tokens are kept exactly: sheet `#f6f3ec`-family warm by day, navy `#10141d` by night, ink `#19202e` / `#ece5d3`, dim, orange `#ec7c22` / `#f08a2c`, red alert key, warn amber, walnut `#6b4428`, Jost + IBM Plex Mono, mono labels at 13 px with wide tracking. Night's page ground **is** round 5's navy sheet. I added only one surface step per lighting (see Design) so groups can sit on the ground. |
| "but the cards of round 3 were less overwhelming. I think dense information benefits from being visually broken up and made to look calmer" | The continuous sheet with ink rules is gone. Every screen is now a few **quiet groups**: one idea per panel, a hairline edge, 16 px corners, a mono label, 22–26 px padding, 20 px between panels. Today has five (First reply, Also waiting, Your day, Worth knowing, Coming up). Replies is split by why they wait. The reply itself is two panels (what they want / your draft). Round 3 used shadows and an alu ground; I used a hairline and the round 5 palette instead, closer to Braun Instrument (B) and Flight Instrument (D). |
| "The Ask page should look like a proper chat" | Ask is a conversation: your questions in bubbles on the right, Callsheet's answers in panels on the left, newest at the bottom next to a docked composer, earlier conversations in a list (a sidebar panel on desktop, "Earlier" on the phone), and an empty "New question" state with four suggestions. |
| "I truly love how smart it looks in Round 6 [= round 5]" | Kept every part that made it smart: numbered sources as sidenotes beside each answer (hover a number to light its source), "Read 1 calendar and 1 thread", "How I found it" (now three short steps folded into the answer), Copy, Remember this? saved only when you press Save, the mono time tags, "Reads only · nothing leaves this box", the Reading state with Stop, and an answer that says plainly what isn't true yet. |
| "and should like to see such refinement everywhere else" | Every place was redrawn at the same level: Today, Replies (+ One at a time, Not for me), Agenda, People, Know me, Projects, Setup, Read it to me, Find or ask, the end of the day, an alert, the clash, offline. Same panel, same label, same spacing rhythm, same quiet keys. |
| Direction (all apps): "scrap almost all the lights … (honestly all menus)" | Removed: the lit slot under the current tab and sub-tab (now a 2 px ink rule), unlit windows on rows, "Copied" as a window (now words), Always counts / tick-box windows (now a flat tick box), project status windows (now words), the Setup index slot, the voice rail's lit slot (now an ink edge). Kept, because they carry real status: the red alert light on an alert, the amber light on a clash or a slipped project's header, and one slot in Ask while it's reading. List rows carry no lights at all (Slipped and To check use ▲ + amber word). |
| Direction: "back off realism" | Callsheet drew no objects in round 5 except the printed-sheet metaphor; that metaphor's furniture (ID boxes, numbered sections 01–04, the lettered form A–D in body text) is toned down. The groups are plain panels, not paper. |

## What changed since round 5

| Round 5 | Round 6 |
|---|---|
| One continuous sheet; 2 px ink rules between sections; numbered sections 01–04 | Quiet panels on a ground, one idea each; numbers dropped from section labels (the voice rail still uses 01–04, since that's its reading order) |
| Running order down the whole left column of Today | **Your day** panel: past events folded into "n done earlier", NOW, the first free stretch only, the clash bracket, "Clear from 19:00". Agenda keeps the full day with every free stretch. |
| Roster of five numbered rows with the first opened inline | **First reply** panel (one person, draft in an inset, the one orange) + **Also waiting** panel (four rows, no ID boxes, "n more in Replies") |
| Ask as a transcript, no bubbles | A chat (above) |
| Lit slot under current tab; unlit windows on rows; tick-box windows | Ink rule; no row lights; flat tick boxes; option rows that press in |
| Replies as one list | Three panels by reason; the reason word is no longer repeated on rows inside its own group |
| People / Know me / Projects / Setup as printed forms | Same content, regrouped into panels: Same person? / You hear from most / the person / their note; Three steps / What it knows; one panel per project + the open project as What happened / Five weeks / Tasks / Source; Setup index + a few panels per section |
| Voice: rail with lit slot, 38 px line | Same, calmer: ink edge on the current line, no lit slot; a paused line shows a part-filled line instead of a full one |
| First run drawn | **Not redrawn** this round (Isaac didn't ask for it; it keeps round 5's flow) |

Kept from round 5 unchanged in behaviour: one orange per screen that moves on (Copy → Done; Check 2 things; Try again); the red alert key with no orange beside it; "Said once, live wins" (a summary sentence steps aside while the cue says it, its footnote moves to the cue label); Undo in place (struck line, "Copied 06:41 · Undo", "Seen 06:41 · Undo", "Got it 10:06 · Undo"); neutral keys for judgements (Same person?, Right / Not quite); Not for me defaulting to Just this one and locked for people who always count; call times that check as you type and say what they cost; the match gutter; the slip track; Setup with no orange at rest except Try again on a broken connection; Start over with Keep everything first and a dark (not red, not orange) destructive key; keys C D L O N X U W R / 1–5 J K Esc.

## Design

### Tokens
Round 5's palette, plus one surface step. Light ground is a touch deeper than round 5's sheet so the panels can be the sheet.

| Token | Day | Night |
|---|---|---|
| ground (page) | `#ece7dd` | `#10141d` (round 5's navy sheet) |
| card (panel) | `#f7f4ee` | `#161c28` |
| inset (draft, how-I-found-it) | `#efeae0` | ground `#10141d` |
| press (selected row, chosen option) | `#e8e2d5` | `#202838` |
| bubble (your question) | `#e6dfd0` | `#232c3e` |
| hair (panel edge, row dividers) | `#e0d9cb` | `#232b3a` |
| kline (key and tick-box edges) | `#8a8477` | `#636e87` |
| ink, ink2, dim, orange, alert, warn, walnut | round 5 | round 5 |

Panel: 1 px hair edge, 16 px radius (14 on phone), padding 22/26 (18 on phone), 20 px gap (12 on phone). Label: Plex Mono 13 px, 0.14em, uppercase, dim, with at most one quiet link at the right. A cue that needs you adds a 3 px inner edge in its state colour (red alert, amber clash/slipped); panels never fill with a state colour. Keys: 10 px radius, 1 px kline edge, 38 px (44 on phone). No shadows except under overlays.

### Today
- **Desktop:** dateline + headline on the left, summary on the right (round 5's band). Then two columns: First reply and Also waiting (7/12); Your day, Worth knowing, Coming up (5/12). Footer line with the promise.
- **First reply** takes, in order: an alert (red edge, red key, Priya on the Then line with a quiet Copy draft), the clash within 60 minutes (amber edge, See the clash orange, Got it), the next reply, or **All answered** (two figures, the walnut rule drawing in once, "Nothing was sent").
- **Phone:** dateline (short form), headline, summary with tappable footnotes, then First reply, Your day, Also waiting (three rows), Worth knowing, Coming up.
- **Footnotes** are small outlined pills, not superscripts, so they read as sources rather than noise.

### Replies, One at a time, Not for me
- Replies: heading "7 people are waiting" (the count is said once; no badges), Work through them as a plain key. Three panels: Due today, Asked you, Waiting a while. Desktop: the selected reply opens beside them as two panels (What they want + their words; Your draft, editable, Copy / Done / Open in Gmail, then Later / Note / Not for me as quiet links).
- One at a time: a single centred panel and a 7-segment bar (segments, not lights). Ends in All answered.
- Not for me: centred sheet on desktop, bottom sheet on phone; option rows press in.

### Ask
- Desktop: sub-row Ask · People · Know me; a 272 px Conversations panel (New question, Today / Yesterday / Mon, and what the answers draw on); the thread column (680 px) with a 250 px source margin; composer docked under the thread.
- Phone: sub-row, the thread, sources folded inside each answer, the composer above the tab bar.
- Turn anatomy: mono meta ("You · 07:02", "Callsheet"); your bubble (20/20/6/20 radius); Callsheet's panel (6/20/20/20 radius) with the answer at 18 px, footnote pills, then one hairline and one quiet line: what it read · How I found it · Copy.
- Reading: a lit slot + "Reading Gmail · Personal" + Stop. Nothing loops.
- Ask turns orange only when the composer has text.

### Agenda, People, Know me, Projects, Setup, voice
- **Agenda:** the whole day in one panel (past dimmed, "on now", every free stretch, the clash bracket with Got it); Invites to answer and From mail, not booked as their own panels. No orange.
- **People:** Same person? (match gutter, reason, three neutral keys) and You hear from most on the left; the person and Note for Callsheet as two panels on the right (full screen on the phone).
- **Know me:** Three steps (one orange: Check 2 things) and What it knows (fact, source, Forget/Undo). Check and question modes are single centred panels with a segment bar. Facts saved from Ask appear here.
- **Projects:** one small panel per project, a dashed panel for the suggestion; the open project as What happened (amber edge), Five weeks (slip track: done milestones filled and unlabelled, dashed old date, amber arrow to the new one, today's ink needle labelled "Today"), Tasks (tick boxes), Source.
- **Setup:** index panel (A–D) + the open section as small panels (Call times, Tell me when it's ready, Quiet hours, Lighting; Google accounts, Chat, Notes; Who writes, Sorting, Ask; Advanced drawers). Phone: index list → section.
- **Read it to me:** header with position, quiet rail (desktop) or segment strip (phone), previous line dimmed, current line 38 / 27 px, one fill line, Back / Pause (orange) / Next.

### Capacities
Also waiting: 4 desktop / 3 phone, then "n more in Replies". Your day on Today: upcoming events + one free stretch; past folds to a count. Replies groups: 3, any length (scrolls). Conversations list: about 8 before it needs "Older". Sources beside an answer: about 4 before the margin outgrows the answer (audit 3). Slip track: 5 weeks, about 4 labelled milestones.

## Audit

Checked with Playwright (Chromium, `chromium.launch()` with no options):
- page at 1500 wide, every step of all 15 flows in Day and Night (both frames), plus all 34 gallery frames;
- per frame, by script: at most one orange, no orange beside a red key, no element outside its frame, no horizontal scroll inside the frame (except the intentional ellipsis on the phone's Then line), no text under 12 px;
- typing in Ask: Ask turns orange, Enter → Reading → the answer;
- a keyboard run: c, u, c, d, u, /, Esc, 2, j, x, Esc, 4, 3, r, →, Esc;
- desktop at 1280; the page at 390 (`scrollWidth` 390); the page in the dark scheme.

Results after the fix pass: **no JS errors; 0 frames with more than one orange; 0 with orange beside red; no overflow; no text under 12 px** (12 px is keycaps, tags and mono meta).

The fix pass corrected:
- the page's own `p{margin:0}` rule leaked into the app and flattened every paragraph's spacing (the ask line, the clash sentence, voice lines);
- footnote pills were invisible on the Day ground (now outlined);
- the phone dateline wrapped (now "Thu 5 Nov");
- the chat thread started at the top, leaving a gap above the composer (now anchored to the bottom, like a chat);
- reply rows repeated their group's name ("Asked you" inside Asked you);
- phone rows squeezed the name beside the reason (reason now goes under);
- the phone draft label collided with its note;
- the match gutter's lines broke between columns;
- "Today" on the slip track collided with "3 Nov";
- the voice line showed full while paused;
- "Expenses tool down until noon" still showed at 17:40;
- key and tick-box edges were 2.5:1 (now 3.4:1 Day, 3.3:1 Night).

Then, looking again at the screenshots for calm and cheese: amber lights on list rows (projects list, Know me facts) were removed in favour of ▲ + amber word; lights stay only on cue panels.

Contrast (WCAG):

| Pair | Day | Night |
|---|---|---|
| ink on panel / on ground | 14.9 / 13.2 | 13.6 / 14.7 |
| dim on panel / on ground / on pressed row | 5.7 / 5.1 / 4.9 | 6.1 / 6.6 / 5.3 |
| ink on your bubble | 12.3 | 11.1 |
| key and tick-box edge on panel | 3.4 | 3.3 |
| warn ink / alert ink on panel | 6.2 / 6.0 | 10.2 / 7.4 |
| text on orange / on red | 6.6 / 6.3 | 7.4 / 6.3 |
| panel against ground | 1.1 (a hairline does the work) | 1.1 (hairline) |

Screenshots are in the session scratch dir `p6cs/shots/` (not in the repo).

| # | Problem | Severity |
|---|---|---|
| 1 | **Panel vs ground is 1.1:1 in both lightings.** The hairline carries the edge. That is the calm Isaac asked for (B and D panels do the same), but on a cheap or very bright screen the panels may merge with the ground. Deepening the Day ground further would drift from round 5's sheet. | Medium |
| 2 | **Today on desktop scrolls**: Worth knowing and Coming up start below 900 px. The first screen holds the headline, summary, First reply, most of Also waiting and all of Your day. More space per group means less per screen. | Medium |
| 3 | **Chat source margin doesn't scale past about four sources.** Longer source lists would overrun the answer; they'd need "+3 more" folding. The product's answers already cite up to 6. | Medium |
| 4 | **"Said once, live wins" still needs fact tags from the brief writer** (round 5 audit 2, unchanged). | Medium (feasibility) |
| 5 | **The phone Then line truncates** ("Needs the Q4 bud…") in the alert and clash panels. The name and Copy draft fit; the ask doesn't. | Low |
| 6 | **Conversations panel on desktop costs 300 px** of width in Ask. A one-question session wastes it. Could fold to a button when there's only one conversation. | Low |
| 7 | **The Reading slot is the only light left outside alert and warn.** It's real status, but it's a light in a chat. If Isaac wants zero, a line of text ("Reading Gmail · Personal…") works. | Low |
| 8 | **First run wasn't redrawn** in the new panels; it still lives in round 5. | Low |
| 9 | **Voice timing** is a fixed 5 s stand-in, and a locked phone still needs the Companion app (rounds 3 and 5). | Low |
| 10 | **Only this look is drawn.** Bold, Clean, Easy read and the Jam looks still need to survive panels (they have their own `--surface` tokens, so this should be easier than the sheet was). | Low |
| 11 | **The new surface tokens are raw values** in the mockup (ground, card, inset, press, bubble, kline). They need to be named in `tokens/` by the hub if adopted. | Low |

## Questions for Isaac

1. **Panels by hairline only (no shadow, 1.1:1 against the ground), as in Braun Instrument and Flight Instrument?** *Recommend yes.* A shadow or a stronger tone would make the screen busier again.
2. **Ask's earlier conversations as a side panel on desktop, or a single "Earlier" line as on the phone?** *Recommend the side panel*: it's where people expect chat history, and it holds the one-line note about what answers draw on.
3. **Keep one light (the slot) while Ask is reading?** *Recommend yes*: it's the only signal that work is happening, and nothing moves.
4. **Today's Your day panel: fold past events to "n done earlier" and show only the first free stretch, with the full day in Agenda?** *Recommend yes*; it's the biggest single cut in density on Today.
5. **Replies grouped by why they wait (Due today / Asked you / Waiting a while), not one sorted list?** *Recommend yes*: the sort order is the same, only broken up.
