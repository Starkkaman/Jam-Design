# Callsheet · Pass 4: the day as a sheet you read

Mockup: `mockups/pass4/callsheet.html`. Passes 1–3 are unchanged.

The page has four parts:
1. **A flow player** with ten flows (A–J). Each drives a live desktop frame (1440 or 1280 × 900) and a live phone frame (390 × 844).
2. **Day and night**: 2 desktop frames (1280) and 14 phone frames.
3. **New elements**, described.
4. **Rules this pass broke**, in short.

Page controls: Lighting (Day / Night), Day (Normal / Quiet) and Desktop width (1440 / 1280). All content is made-up sample data (Sam, Co. A/B, Priya N., Northwind Store, a school office).

Sources read:
- `notes/OVERNIGHT-BRIEF.md`, including the Direction update, and the last entry of `decisions.md`.
- `notes/REVIEW.md`, and CHANGES.md §A–§D (D1–D179).
- `projects/callsheet/README.md` and `FLOW.md`.
- `notes/pass3-callsheet.md`. Its functional decisions are kept unless listed below.
- The pass-3 mockups of Callsheet, Jam-Dash and HA, rendered only to check that this one doesn't look like them.

## What changed and why (vs pass 3)

Isaac's direction: "same design language, not necessarily the same design … each interface design is bespoke to its purpose". Pass 3 was the same kit as Jam-Dash and HA: alu ground, raised flat cards, a black ribbed band holding the day scale, and a Next card. Callsheet's purpose is different from a dashboard. It's something you **read** in a minute and act on in a few taps, so this pass turns it into a reading surface.

| Pass 3 | Pass 4 | Why |
|---|---|---|
| Alu ground + flat cards (Next card, rundown card) | **One printed sheet, no cards.** A warm sheet `#f6f3ec` with navy ink `#19202e` by day; a deep navy sheet `#10141d` with cream ink by night (from the saved Mission palette). Hierarchy comes from type, a heavy rule and a time column. | A brief is read top to bottom. Cards made it look like a dashboard of separate things. |
| Black ribbed band with the day scale (tuning needle) | **Running order** on desktop (the day down a time column with a NOW rule). On the phone the running order folds into a one-line **day strip**. | Time-first, like a call sheet or a flight plan. The band was the heaviest thing on a page meant to be calm. |
| Next card (fixed slot, 300 px min) + Then line | **Roster row 01 opens out** with its draft and keys. When an alert or clash takes the cue (a ruled block above the roster), row 01 shrinks and is labelled **THEN**. | Same cue order. Priya is printed once instead of twice (card + Then line + rundown row). |
| Rundown card with a bar group "count" | **The roster's own numbering is the count.** "2 more in Replies" is the only number printed. | Count once, with no extra meter. |
| Separate Full brief page | **The sheet is the full brief.** Worth knowing, Coming up and the summary's sources sit under the roster. On the phone the lists fold; on desktop it's all printed. | "The rundown is the front door, lists one tap behind" (FLOW). A second page was a second version of the same facts. |
| Stripes accent on calm screens (D67) | **No accent.** Calm and done are marked by the **Wrap**: a typographic sign-off with a walnut double rule that draws in once. | Pass 3 audit #7: principle 6 ("make the end feel good") rested on a decoration. Now the end itself is designed. |
| Reason dots in the product | **Reason in words** ("Always counts · Due today"). | No colour to learn; colour stays for state. |
| Warn = triangle window (D142) | **Round amber light + printed ▲ + word** (Jam-Dash's D158), plus a **clash bracket** in the rail. | Gives up Callsheet's fifth indicator shape so the language keeps four. The bracket is drawing, not an indicator. |

Kept from pass 3:
- the cue order: alert → offline → clash within 60 min → reply → calm (wrap);
- the red alert key, with no orange on that screen (D84/D138);
- one orange per screen, and a sheet or palette veils the page's orange (D82/D97);
- "Just this one" as the default for Not for me, with the sender rule locked for people who always count (D146);
- Undo on every change;
- Read it to me (Wheatley) with Pause as the one orange;
- the offline dashed bar over cached content (D143);
- single-letter keys and `?` (D147), five places (D73), list + detail on desktop Replies;
- "Seen 06:20" as the word plus an unlit window.

## Research

**Method:** WebSearch, three queries this pass (film call sheets, Apollo flight plans, strip boards; the strip-board query returned nothing useful). Items marked *(knowledge)* are from memory.

| Source | What it says | Used for |
|---|---|---|
| **Film call sheets** ([StudioBinder template](https://www.studiobinder.com/film-call-sheet-template), [Assemble](https://www.onassemble.com/blog/how-to-make-a-call-sheet), [Prodigium](https://www.prodigium-pictures.com/blog/call-sheet)) | One page. Day-specific facts (date, crew call, weather) at the top. A numbered cast list. The day's schedule. An **advance schedule** for the next day at the foot. "Fit all sections on one page so it's easy to scan." | A dateline at the top ("Thursday 5 November · sheet 06:30"). A numbered roster with ID boxes. Coming up as the advance schedule. One sheet, not pages. |
| **Apollo flight plans** ([National Archives, Apollo 11](https://www.archives.gov/exhibits/featured-documents/apollo-11-flight-plan/flight-plan.html), [NASA a11 flight plan](https://www.nasa.gov/history/alsj/a11/a11-fltplan.htm)) | A time column (GET, with local time in parentheses). Each page covers one or two hours. Activities are printed beside the time in columns. Hand annotations were added in flight. | The running order: a mono time column, a hairline rail with a tick per event, entries beside it. The day reads top to bottom, and NOW is a rule across the page. |
| **Production strip boards** *(knowledge)* | Each scene is a thin strip. Colour codes day/night and interior/exterior. The board is the day's order at a glance. | The phone's day strip: events as ink strips, a clash as two half-height strips with an amber edge. No colour codes, so colour stays for state. |
| **Swiss editorial grids, Braun manuals** *(knowledge)* | Flush-left, ragged-right text. A strong grid. Numbered sections and callouts. One accent colour. Rules separate; space groups. | Numbered sections (01 Your day · 02 Who needs you · 03 Worth knowing · 04 Coming up). One heavy 2 px rule under the summary. Footnote numbers for sources. |

## Purpose

A daily brief that must not be daunting. Isaac reads it on his phone at about 06:30 from a push, then at 12:30 and 17:00. In those moments he wants three things:
- what the day holds;
- who needs him, with a draft to copy;
- what's coming.

He has said "way too much text on screen" and "emphasize clarity without sacrificing fun". So the sheet does three things:
- puts one thing to do in reach (the cue);
- prints the day once, in time order;
- **ends**. The Wrap is a reason to put it down.

## Design

**Desktop Today (1440 × 900):**
- **Masthead:** walnut trim, the wordmark, five places as words (the current one has a lit slot under it, D91), and Find / Refresh / Setup.
- **Dateline** (mono) with Read it to me (R).
- **Headline** "Good morning, Sam." at 46 px.
- **Summary:** three short sentences at 23 px with footnote numbers.
- A 2 px ink rule, then two columns:
  - **01 Your day** (5/12): the running order. Finished events fold into "Done: Stand-up". The NOW rule has a lit cream slot. Free gaps show as a dashed rail. A clash is bracketed. "End of day · clear from 19:00" closes it.
  - **02 Who needs you** (7/12): any cue block, then the roster (5 rows), then "2 more in Replies". Under that, **03 Worth knowing** | **04 Coming up**, then sources and the promise ("Nothing was sent. Drafts wait for you.").

**Phone Today (390):** dateline, headline (31 px), summary (18 px), cue block, 01 day strip, 02 roster (4 rows), 03, 04, sources and the promise. Bottom tabs are text, with the lit slot on the current one. The first screen at 06:34 holds the headline, summary, strip and the whole of row 01 with Copy draft.

**Cue order** (unchanged; the forms are new):
1. **Alert:** a red 2 px rule, a ringed red light, "Alert · 06:12", one sentence, the red key "Check the sign-in" and a quiet "It was me". Nothing on the screen is orange.
2. **Offline:** a dashed bar above the page. Try again is the orange; Copy stays as a plain key.
3. **Clash within 60 min:** an amber rule, the round amber light, "▲ Clash · 11:00 · in 55 min". See the clash (orange) opens Agenda; Got it hands back.
4. **Reply:** roster row 01 opens out with the draft. Copy draft (orange) → "Copied 06:41" with a lit slot, and Done becomes the orange. The orange moves to the next step instead of disappearing.
5. **Wrap:** no orange.

**Other screens:**
- **Agenda:** the full running order (past events dimmed, "ON NOW" with a lit slot) and Invites to answer, each with "Answer in Google Calendar". No orange.
- **Replies:** the full roster plus Done today. On desktop it's list + slip.
- **The slip:** what they want, their words, the editable draft, Copy / Done / Open, then Later / Note / Not for me. For a shop mailing there's no draft and no Copy key.
- **One at a time:** one person per screen. The roster's ID boxes across the top are the progress: heavy = current, struck = done, dashed = later. Swipe hint on the phone. Ends in the Wrap.
- **Read it to me:** the sheet read aloud. The section numbers 01–04 match the sheet. The current line is large and the previous one dimmed. A line fill runs once per line. Back / Pause (orange) / Next sit at 60 px. The end has no orange.
- **Find or ask:** a palette. The page behind loses its orange.
- **Key sheet:** opened with `?`.
- **Not for me:** a sheet with square windows for "Just this one" / "Everything from…". The second is locked for Priya, with the reason.
- **Ask, Projects:** sketched in the new type only. Setup is not redrawn.

### New elements
1. **Running order.** The day down a mono time column with a hairline rail and a tick per event. A NOW rule (a lit slot and a full-width ink line) cuts across. Past events fold into one line.
2. **Gap cues.** Free time is printed as a dashed stretch of rail ("Free until 11:00 · 55 min"). The first gap says how many replies fit ("Room for the first 3 on the roster, about 6 min") and links to Work through them. This puts replies into the day instead of a pile.
3. **The roster.** Who needs you as a call sheet's numbered cast list. Each row has an ID box, name, area, one line for what they want, the reason in mono words, and the age. The numbering is the count.
4. **THEN row.** When something else takes the cue, row 01 is labelled THEN and keeps a quiet Copy draft. This is pass 3's Then line at zero extra cost.
5. **Clash bracket.** Two overlapping events share one time cell and an amber bracket in the rail, headed "● ▲ Clash · pick one".
6. **Day strip** (phone). The running order folded to one line: ink strips, the clash as two half-height strips with an amber underline, a needle with a lit cap. It labels only the next event and the clash. A tap unfolds it in Agenda, so the strip and the order never share a screen.
7. **Source footnotes.** Each sentence of the summary carries a superscript number, explained at the foot ("¹ Calendars · Co. A and Co. B"). This shows "every AI sentence pinned to its source" in a form you read.
8. **Wrap.** The sign-off. It shows:
   - "Wrap · 17:40" and "That's the day.";
   - three light 44 px figures: Answered, Tomorrow, Sent (always 0);
   - a walnut double rule that draws in once (350 ms, off under reduced motion);
   - tomorrow's first thing (taken out of Coming up so it's said once);
   - two quiet keys.

## Language check

What ties this to the family, and what someone arriving from Jam-Dash, HA or the TV would recognise within a second:
- **Jost for words, IBM Plex Mono for times, labels and numbers.** This is the strongest tie, and Callsheet leans on it hardest.
- **Indicator windows.** The lit cream slot (NOW, Copied, current tab), the round LED (ringed red alert; amber warn with ▲), square windows for a chosen option. Same shapes and meanings, and only four shapes.
- **State words and their quiet past forms:** "Seen 06:20", "ON NOW", "done", "Offline". These are D159's quiet forms.
- **One orange per screen, and it moves** (Copy → Done). Red key for alerts. No orange on calm, reading or done states.
- **The walnut trim** at the top. Walnut is also the Wrap rule, so the house trim colour gets a second, meaningful job.
- **Motion character:** short and causal. A rule draws in once, a fill runs once, nothing loops.
- **The honest calm:** plain words, "Nothing was sent", no badges.

What's deliberately not shared: the ground, the ink tint, cards, the black band, the accent. Someone coming from HA sees a different room in the same building.

## Rules I broke

| # | Rule (where) | What I did instead | Why Callsheet needed it | Verdict |
|---|---|---|---|---|
| 1 | BIBLE §2 Materials: alu ground, raised `card` surfaces, three depth layers | A flat sheet ground (warm white / deep navy) with no cards and no shadows; navy-tinted ink | A reading surface. Cards split one story into tiles, and depth adds nothing to text. | **App-local.** Grounds and surfaces belong to each app. Global: only the ink/dim contrast floors and the state colours. |
| 2 | BIBLE §2 Black ribbed band (and D99/D162 night bands) | No band anywhere, voice mode included | The band was the heaviest object on a calm page, and its job (holding the day scale) moved into type | **Device family:** TV and kiosk (fixed, glanceable surfaces). Not language-wide. |
| 3 | BIBLE §2 Accents (one per screen) and D67 (Callsheet = Stripes when calm) | No accent. The reward is the Wrap's walnut rule. | Decoration on a reading page competes with the text, and the end deserved to be designed itself | **App-local, optional.** "At most one accent per screen" can stay global; "every app has one" should not. |
| 4 | D65 / D137 Next card as a shared card component with a fixed min height | The cue is a ruled block or roster row 01; no card, no fixed slot | The card repeated the person printed again in the rundown. The ordering was the valuable part. | **Split:** the **cue order** is language-wide; the **card form** is dropped as a rule. |
| 5 | D6 / D68 / D141 Bar group for counts (10-segment recess) | The roster's ID numbers are the count, plus "2 more in Replies" | A numbered list already counts. A bar group would print the same number twice. | **Device family** (dashboards, kiosks), not for lists that number themselves. |
| 6 | D8 Tuning scale (day timeline with needle on a band) | Running order (desktop) and day strip (phone) | Time-first reading needs titles beside times, not labels above a scale | **App-local.** |
| 7 | D142 Warn = triangle window (my own pass-3 rule) | D158: amber round light + printed ▲ + word, plus a clash bracket in the rail | Keeps the language at four indicator shapes. The bracket shows *which* two things clash, which a light can't. | **Language-wide (D158 wins).** The bracket is app-local drawing. |
| 8 | Callsheet principle 5 "Three sizes a screen" | Four: headline 46, summary 23, body 15–18, mono labels 13 | A reading page needs a lede size between the headline and the body | **App-local:** reading surfaces get a lede. Keep three elsewhere. |
| 9 | D145 "A reading page is the steps expanded" (a separate Full brief) | The front door *is* the full brief; the phone folds lists, desktop prints all | Two versions of one brief is a "say it once" problem | **Drop** the separate page for Callsheet; the reading-page *rules* (no orange, sources) stay. |
| 10 | Product reason dots (`--r-vip` etc.) | Reason in mono words | Five colours to learn, and colour is reserved for state | **Drop** (affects the product at rollout). |
| 11 | BIBLE §3 "unlit window = visible dark recess" in Day | In Day on the light sheet: unlit = hairline groove, lit = cream inside a 2–3 px dark rim (as JamFin D173) | Dark unlit squares on a light sheet read as *checked*, and cream lit ones as *empty*. I found this in screenshots (the Not for me sheet read backwards). | **Language-wide, made precise:** windows by lighting, D173's form. Needs one decision across D121/D131/D173. |
| 12 | D9 key hints printed on buttons, everywhere on desktop | Kept, but quiet keys show them in a 12 px mono box at 70% opacity | Hints on every key turned the reading page into a keyboard diagram | **Device family (desktop)**, with a "hints only on keys and the primary" refinement. |

## Audit

Checked with Playwright (Chromium, `chromium.launch()` with no options):
- page width 1500 (light scheme): every step of all ten flows in Day, nine steps in Night, both widths and the Quiet day;
- page width 390 (dark scheme): seven flow steps and the full page;
- a keyboard run: c, Enter, ?, Esc, /, Enter, Esc, r, →, Esc, 3, 1, j, k, x, Esc, w, d, Esc, 2, l;
- real clicks on the phone (Copy, Done).

Results: **no JS errors, no horizontal page scroll at 390, nothing outside its frame, no text under 12 px** (the only 12 px text is keycaps, hour labels and footnote numbers; uppercase labels are 13 px per D30).

Contrast was computed for the new tokens:

| Pair | Day | Night |
|---|---|---|
| ink on sheet | 14.7 | 14.7 |
| dim on sheet | 5.7 | 6.6 |
| warn ink | 6.2 | 11.0 |
| alert ink | 5.9 | 8.0 |
| text on orange | 6.6 | 7.4 |
| text on red key | 6.3 | — |

The fix pass corrected:
- secondary keys had lost their outline (a specificity bug);
- the gap cue said "Room for the first 7" (now at most 3);
- gap rows printed their start time twice;
- the Wrap repeated the name and the last event;
- Tomorrow appeared in both the Wrap and Coming up;
- the phone tally wrapped to two lines;
- strip labels clipped and collided with the needle;
- a shop mailing showed a fake draft and a Copy key;
- Day windows read backwards (rule 11);
- the day clash bracket was 1.5:1 against the sheet (now `#a87a12`, 3.5:1).

Screenshots are in the scratch dir `p4cs/shots/` (flows day/night, 1280, quiet, 390 frames, gallery).

| # | Problem | Severity |
|---|---|---|
| 1 | **The lit cream window is 1.1:1 against the Day sheet.** It reads only through its dark rim. The Not for me squares and the NOW slot work, but "lit vs unlit" in Day is a rim-weight difference, not a light. Every light-ground app has this problem. | High (language) |
| 2 | **Gap cues need numbers the product doesn't have.** "About 6 min" assumes a per-reply time estimate. Callsheet would have to guess one from draft length, and a wrong guess makes the cue nag. | Medium |
| 3 | **The 11:00 clash is said twice at 10:05**: in the summary (written at 06:30) and in the cue. Similarly, "Two replies are due today" in the summary sits next to roster rows marked "Due today". The summary is a snapshot, the cue is live. A rule is needed: summary sentences about something a cue now shows should dim or drop. | Medium |
| 4 | **Desktop at 1440 × 900:** roster rows 4–5 and Worth knowing sit below the fold, and the page scrolls as one sheet with the running order. That's fine for reading, but the right column ends far below the left. | Medium |
| 5 | **Setup, Know me, People and Projects detail are not redrawn** in the sheet language. Ask and Projects are sketches. The first-run wizard and Look panel are still missing (since pass 3). | Medium |
| 6 | **"Sent 0" as a figure** is the promise made visible, but it could read as a joke, and Isaac's voice rules say no jokes about failures. | Low–Medium |
| 7 | **Voice line timing** is a fixed 5 s fill standing in for TTS length. Pass 3's feasibility note still applies: a locked phone needs the Companion app. | Low |
| 8 | **The day strip allows only two labels** (next and clash). A day with two clashes would label only the first. | Low |
| 9 | **The navy ink tint** (`#19202e`) is a Callsheet-only colour. If Callsheet keeps Bold/Clean/Easy read and the Jam looks, the sheet layout must survive those looks' tokens. Only the Hi-Fi-derived sheet is drawn. | Low |
| 10 | **Footnote numbers are not interactive.** On the phone, tapping ¹ could show its source inline; today you scroll to the foot. | Low |
| 11 | **Desktop One at a time** is a 700 px column in a 1440 frame, about 60% empty. Calm, but it may feel unfinished. | Low |
| 12 | **The Wrap headline sits under "Evening, Sam."**: two display lines on one screen at 17:40. | Low |
| 13 | **Gallery frames are scaled to about 55%**, so their text is physically small (the CSS sizes are all ≥ 12). Mockup only. | Low |

## Questions for Isaac

1. **Is Callsheet allowed its own ground and ink (a warm sheet by day, a deep navy sheet by night, no cards)?** *Recommend yes.* It's the clearest "bespoke to its purpose" move, and the type, windows and orange keep it in the family.
2. **Front door = the whole brief (no separate Full brief page)?** *Recommend yes.* Desktop prints all of it, and the phone folds lists one tap away.
3. **Replace the Next card with "roster row 01 opens out", with the THEN label when an alert or clash takes the cue?** *Recommend yes.* Same order, one fewer copy of each name.
4. **Gap cues ("Free until 11:00 · room for the first 3, about 6 min"): helpful, or a nudge you'd rather not have?** *Recommend* keeping them on the first free gap only, and hiding the minutes until the estimate is proven.
5. **The Wrap: keep "Sent 0" as a figure, or say it in words ("Nothing was sent") only?** *Recommend words only* if the figure reads as cheeky to you. Everything else in the Wrap stays.
6. **Reason dots → reason words in Replies (and later in the product)?** *Recommend yes.* Colour stays for state.
7. **Warn shape: Callsheet now uses Jam-Dash's round amber light + ▲ (D158) instead of its own triangle window.** *Recommend D158 for every app*, which closes REVIEW big call #4.
8. **Windows on light grounds:** unlit = hairline groove, lit = cream inside a heavy dark rim (D173)? *Recommend yes, language-wide.* It's the only form that read correctly on the sheet.
9. **No accent on Callsheet at all?** *Recommend yes.* The Wrap's walnut rule is the reward, and accents become optional per app.
