# Callsheet: rollout plan for the handoff look (plan only)

From the Callsheet session, 2026-11-06. Answers HANDOFF.md (2026-11-06) with `mockups/pass6/callsheet.html` and
`notes/pass6-callsheet.md` as the starting draft. **Nothing in Callsheet is restyled, replaced or removed until Isaac
OKs Callsheet's turn.** Facts about today's app are from the code at version 0.10.1.

## Where Callsheet is today

- **Stack:** an HA add-on page (Ingress). Plain JS (`app.js`, ~6,700 lines) and CSS (`app.css`, ~2,500 lines), no
  framework.
- **Looks:** each look is a CSS token block per look × mode (`data-look`, `data-mode` Auto/Light/Dark). Structure
  keys on `data-base` = `bold | clean | easy`.
- **Twelve looks:**
  - Callsheet's own: Bold (default), Clean, Easy read;
  - JamDash's nine: Depth, Braun, NERV, LCARS, Olympia, Transit, Grid, New Wave, Pulsar.
- **Fonts and requests:**
  - All fonts are bundled. Jost and IBM Plex Mono (400) are already in. The page makes no outside requests.
  - Text is rendered with textContent only, and URLs are relative.
- **Tabs:** Briefing, Replies, Agenda, Chat, Projects, Setup. People and Know me sit under Chat and Setup.
- **Setup** has four places (Connections, Your day, AI, Advanced).
- **Existing pieces the draft can reuse:**
  - Chat already keeps conversations (a list, retention, Delete all);
  - drafts already have Copy / Done / Open;
  - Undo exists for every state change.
- **New since round 6 was drawn** (the draft doesn't show these):
  - 0.9.1 sorting sections: Needs you / For your info / Sorted for you;
  - 0.10.0 Connectors (YouTube, news) and their Briefing list;
  - 0.10.1 Reports (other agents' digests) and their Briefing list.
- **Coming next is the Wheatley rundown (0.10.3).** It's a narrated, step-by-step Briefing: your day → who needs an
  answer and why → what you should know → coming up. Voice follows in 0.11.

## The approach

Build the handoff look as **one new look with its own structure**: `data-look="jam"` and a new `data-base="panel"`.
It sits beside the existing ones. Panels, labels, keys and state words key on `data-base="panel"`, so Bold, Clean,
Easy read and the nine Jam looks keep working unchanged until Isaac decides their fate.

Once he approves the finished look, it becomes the default. Retiring any old look is a separate OK.

## What changes, in order

Each step ships on its own and keeps every check: WCAG AA, 44 px phone targets, no overflow at 400/1280, offline,
no foreign requests.

1. **Tokens and type.**
   - Add the `jam` look with Day/Night from the pass 6 `:root`: ground, card, inset, press, bubble, hair, kline,
     ink/ink2/dim, orange, walnut, ok/warn/alert.
   - Labels: Plex Mono 13 px uppercase with wide tracking. Body text in Jost.
   - Nothing else moves yet.
2. **Shared parts on `data-base="panel"`:**
   - the panel (hairline, 16/14 px corners, no shadow, 20/12 px gaps), the panel label, keys (38/44 px);
   - footnote pills for sources, flat tick boxes;
   - state as colour + shape + word (▲ warn, red alert key with dark text);
   - "Seen 06:20"-style past forms;
   - a check that allows at most one orange per screen and no orange beside red, added to the existing UI audit;
   - removal of every lit dot or slot that carries no real status.
3. **Briefing → "Today", built as the Wheatley rundown's front door.** Do this together with 0.10.3 so Today isn't
   designed twice.
   - Round 6's panels become the rundown's steps: First reply (alert > clash within 60 min > next reply >
     All answered), Also waiting, Your day (past folded to "n done earlier", the first free stretch only), Worth
     knowing, Coming up.
   - Feeds and reports become one quiet "From your channels, feeds and reports" panel.
   - Each spoken line maps to one panel, which keeps "Said once, live wins" possible. The rundown pins every sentence
     to its source, which gives the fact tags the pass 6 audit (#4) asked for.
4. **Replies, One at a time, Not for me.**
   - Group Needs you by why it waits (Due today / Asked you / Waiting a while). The reason comes from the existing
     sorter and wait times.
   - The selected reply opens as two panels: What they want / Your draft, with Copy as the one orange.
   - For your info and Sorted for you stay as closed panels with counts. Nothing is hidden: the 0.9.1 promise.
   - One at a time gets the segment bar.
5. **Chat → "Ask" as a proper chat.**
   - Bubbles for the owner, answer panels for Callsheet, the composer docked at the bottom.
   - Conversations panel on desktop, "Earlier" on the phone (the conversation store exists).
   - Sources in the margin, folding to "+n more" after 4: real answers cite up to 6 (pass 6 audit #3).
   - Reading state with Stop.
   - Remember this? stays owner-pressed only.
6. **Agenda, People, Know me, Projects** regrouped into panels as drawn: the full day in Agenda, the match gutter,
   Three steps / What it knows, the slip track.
7. **Setup.**
   - An index plus small panels per section.
   - Connectors and Reports get panels in the same rhythm. They aren't in the draft, so I'd follow Setup's pattern
     and send screenshots before building.
   - Setup has no orange at rest except Try again.
   - On/off settings use the channel-reveal switch with the **settings steel** accent (handoff item 10).
   - Choices with three or more options (e.g. Always tell me / If it's important / Only in the list) stay
     segmented keys.
8. **Read it to me** (0.11 voice): rail on desktop, segment strip on phone, Back / Pause / Next. It's built with the
   voice stage, not before.
9. **First run** gets redrawn last. The draft doesn't redraw it (pass 6 audit #8).

## Hard or impossible in the real stack, and what I'd do instead

- **Twelve existing looks × a new structure.** Re-flowing all of them into panels at once is the biggest risk. I'd
  instead ship `jam` + `panel` as an added look and leave the others on their current structure until Isaac decides.
  Testing every look × mode doubles while both exist.
- **Desktop Today scrolls** (pass 6 audit #2) once real data arrives: 70–94 threads per sync, 14–19 needing a reply
  before sorting, 2–7 events. With the rundown as the front door, Today shows one step's panels at a time on the
  phone. On desktop, Worth knowing and Coming up stay below the fold; I wouldn't shrink the panels to avoid that.
- **The one-orange rule with real states.** Several states can want the orange at once: an alert, a clash and a
  reply. I'd use a fixed priority (alert → red key, no orange; clash → See the clash; otherwise the next reply's
  Copy) and enforce it in code and in the UI audit, rather than leave it to each screen.
- **Panel against ground is 1.1:1** (pass 6 audit #1), so the hairline carries the edge. The hairline has to stay at
  least 1 px with no sub-pixel scaling in HA's iOS/Android webviews. I'd test on Isaac's phone before the default
  switch.
- **Plex Mono is bundled at 400 only.** If labels need 500, that's one more OFL file (~25 KB), which is fine.
- **Shortcut keys.** The draft adds X U W R and 1–5 to today's ⌘K / "/", J K D C O N and "?". I'd add those only
  where the draft's screens exist, and keep "?" listing them all.
- **No device switches in Callsheet.** The by-kind accent rule only touches Setup's on/off settings (steel).
  Callsheet has no plugs, lights or fans.

## Questions for Isaac

1. **Old looks.** When the new look is the default, should Bold, Clean, Easy read and the nine Jam looks stay as
   options, be cut to Easy read only (it's the accessibility look), or be retired? *Recommend: keep Easy read, retire
   the rest after a week on the new look.*
2. **Tab names.** Rename Briefing → Today and Chat → Ask, as in the draft? *Recommend yes; one-time notice, old links
   keep working.*
3. **Order against Wheatley.** Build steps 1–2 now, then do Today together with the 0.10.3 rundown (so Today is
   designed once)? *Recommend yes.*
4. **Ask's reading light.** Keep the one slot while Ask is reading, or text only? *Recommend keep* (pass 6 Q3).
5. **Connectors and Reports in Setup** aren't drawn yet. OK to follow Setup's panel pattern and send screenshots
   first?
