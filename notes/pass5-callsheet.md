# Callsheet · Pass 5: the whole app on one sheet

Mockup: `mockups/pass5/callsheet.html`. Passes 1–4 are unchanged.

The page has four parts:
1. **A flow player** with 16 flows (A–P). Each drives a live desktop frame (1440 or 1280 × 900) and a live phone frame (390 × 844). Seven flows are new this pass: H (voice, redrawn), K Ask, L People, M Know me, N Projects, O Setup, P First run.
2. **Day and night**: 8 desktop frames (1280 × 800) and 16 phone frames, covering every place in both lightings.
3. **New and redrawn elements**, described.
4. **Rules assumed or broken**, in short.

Page controls: Lighting (Day / Night), Day (Normal / Quiet), Desktop width (1440 / 1280). You can type in Ask and in Setup's call times. All content is made-up sample data: Sam, Co. A/B, `example` domains, and Ofcom's drama range for phone numbers (07700 900xxx).

Sources read:
- `decisions.md` (last entry);
- `notes/OVERNIGHT-BRIEF.md`, including the Direction update;
- `notes/RULES-TIERS.md` in full: the language, tiers, conflicts 1–12, holes H1–H18 and "What each app owns";
- `notes/pass4-callsheet.md` and `mockups/pass4/callsheet.html`, which this pass builds on;
- `notes/pass3-callsheet.md`, for the Setup, People and Know me content;
- `projects/callsheet/README.md` and `FLOW.md`.

Research: no new web research this pass. The call-sheet and flight-plan sources from pass 4 still apply. The rest comes from the repo (README's screen list, FLOW's usage facts, Isaac's quotes) and from general knowledge of printed forms and transcripts. I've marked it as such where it matters.

## What changed since pass 4

### Pass 4 audit fixes

| Pass 4 audit | Severity | Pass 5 |
|---|---|---|
| 1 Lit cream is 1.1:1 on the Day sheet; lit vs unlit is a rim-weight difference | High | **Settled per conflict 3 (form B on light grounds), plus two more cues.** Day unlit = a 1 px groove (outline) drawn at the bezel's outer edge. Day lit = flat cream inside a 3 px dark bezel. Measured: bezel to sheet 16.6:1 and cream to bezel 14.9:1. Blurred (mean luminance over the window's 24 × 12 box), lit is 0.30 and unlit 0.78, a 2.3:1 difference: **lit reads as a dark spot with light in it, unlit as almost nothing**. Two more channels: the word beside a lit window is ink (unlit: dim), and chosen options also press in (shade fill + 2 px inner top line, CT3). Both forms have the same outer footprint, so a window never "grows" when it lights (IN2). |
| — (new, found in this pass) Night unlit recess is 1.1:1 on the navy sheet | Medium | Night unlit windows get a 1 px inner rim, `#5c6273`, 3.0:1. Pass 4 had the same flaw. |
| 2 Gap cue's "about 6 min" needs an estimate the product doesn't have (H17) | Medium | **Dropped.** The gap prints only the calendar's fact ("Free until 09:30 · 2 h 56") plus "A free stretch for replies." and Work through them. There's no count and no minutes. If an estimate ever comes back, it must print "est." and say what it's based on (H17). |
| 3 The summary repeats what a cue shows | Medium | **Rule written and applied: "Said once, live wins"** (below). Shown in flows C and D. |
| 4 Roster rows 4–5 below the fold at 1440 × 900 | Medium | **Fixed.** Headline and summary share one band (5/12 + 7/12), and desktop roster rows are two lines (name · area · reason on one, the ask on the next). Measured bottom of row 05 at 1440 × 900 and 1280 × 900, Day and Night: reply cue 708 px, clash cue 783 px, alert cue 819 px ("2 more in Replies" ends at 863). |
| 5 Setup, Know me, People, Projects detail not redrawn; Ask a sketch | Medium | **All redrawn**, plus Ask, voice and a first run (flows H, K–P). |
| 6 "Sent 0" may read as a joke | Low–Med | **Gone.** The tally is Answered and For tomorrow. Then the walnut rule, then "Nothing was sent. The drafts you copied are yours." in words. The footer drops its own copy of the promise on that screen, so it's said once. |
| 7 Voice timing is a fixed 5 s fill | Low | Still a stand-in. The product uses the real audio length. |
| 8 Day strip has two labels | Low | Capacity stated (H16): next event + first clash. The clash label steps aside while the cue says the same thing; the amber underline stays. |
| 10 Footnotes not interactive on the phone | Low | Tap a number to open its source in place under the summary (44 px hit area), with Close. |
| 12 Two display lines at 17:40 | Low | The headline becomes "That's the day, Sam." and the sign-off has no second display line. |

### Also changed

- **The sign-off says "All answered · 17:40"**, not "Wrap · 17:40". Isaac: "lets get rid of the cheeky production nods", and the README rule says "no film-production jargon". The *drawing* stays a call sheet; the *words* on screen are plain. "Running order", "roster" and "wrap" are element names in these notes only, never UI text.
- **Undo happens where the change is (LY16).** Pass 4 used toasts for Copy, Done, Later, Not for me and Seen, but each of those changes is visible in place. Now:
  - Done, later and moved rows stay as one struck-through line with Undo. The line strikes once, in 250 ms; Calm turns that off.
  - Copy shows "Copied 06:41" with Undo beside it.
  - "It was me" shows "Seen 06:41 · Undo".
  - "Got it" puts "got it 10:06 · Undo" on the clash bracket (desktop) or under the day strip (phone).
  - Merges, forgotten facts and saved memories do the same.
  - `U` is the desktop key. The struck line goes when you leave the place or make the next change.
- **"Copied" is now a quiet past form**: an unlit round window + word (IN13). Pass 4 drew it as a lit slot, which (conflict 6) means "current".
- **Mockup notes** (dashed, labelled MOCKUP) stand in for things that happen outside the app, like opening Gmail. They are not product UI.
- **Phone overlays are bottom sheets** (CT12). Not for me, Find or ask and Start over use them. Desktop keeps them centred.
- **Labels are 13 px with 0.16em tracking** everywhere (TY3). Pass 4 mixed 0.08 and 0.12.
- **Projects status uses round windows** (unlit = fine, amber + ▲ + word = slipped, dashed = suggested, not confirmed). Pass 4 used slots for status.

### "Said once, live wins" (the summary rule)

The summary is a snapshot written at sheet time. The cue, the roster and Worth knowing are live.
1. Each summary sentence carries the fact it states (an event, a reply, an alert).
2. While a cue or a note **on the same screen** states that fact, the sentence is left out of the printed summary, and its footnote number moves onto the cue's label (the source stays pinned).
3. When nothing live says it any more, the sentence comes back (flow D step 4: after Got it, "two of them land at 11:00¹" returns).
4. Drawings of time (running order, day strip) don't count as a repeat (H7). Words do: the strip's clash label also steps aside while the clash cue shows.
5. Voice and the push read the whole summary, because nothing else is on screen there.
6. Related: at 10:05 the free gap before the clash drops its "55 min", because the cue already says "in 55 min".

This replaces CW4's "a snapshot sentence **dims**": dimmed text is still AA-readable, so dimming is still saying it twice.

## Design

### Today (kept from pass 4, tightened)
- **Desktop:** the masthead; a dateline with Read it to me; then one band with the headline (46 px) on the left and the summary (21 px, footnoted) on the right; then a 2 px ink rule and two columns.
  - **01 Your day** is the running order.
  - **02 Who needs you** holds the cue (if any) and five roster rows. Under them sit **03 Worth knowing**, **04 Coming up** and the footer.
  - Running-order rows are now targets: they open Agenda.
- **Phone:** unchanged in order: dateline, headline, summary, cue, day strip, roster of 4, 03, 04, footer.

### Read it to me: the reading rail (redrawn)
- **Desktop:**
  - A 330 px rail on the left prints the sheet's own sections (01 Your day … 04 Coming up), with one tick per spoken line, labelled by its gist ("Priya: budget sign-off").
  - The line being read has the lit slot (current, per conflict 6). Past lines are dim. Click a line to jump to it.
  - On the right: "02 Who needs you · line 3 of 7", the previous line dimmed, the current line at 38 px, and a line fill that runs once.
  - Heard commands are confirmed under the line ("Heard 'later'. Priya N. waits for your desk at 12:30.").
- **Phone:** the rail folds into a **line strip**: one segment per line, grouped by section with 01–04 under it. This is the same fold as running order → day strip.
- Keys: Back / Pause (orange) / Next at 60 px. At the end there's no orange. No band, no waveform, nothing loops.

### Ask: a transcript with sidenotes
- **The page, top to bottom:**
  - the sub-row Ask · People · Know me (pass 3's decision, so five tabs stay);
  - "Reads only · nothing leaves this box";
  - "Earlier · Yesterday · 2 questions ›" folded to one line;
  - each exchange.
- **Each exchange:**
  - a mono time tag ("Q · 07:02"), then the question at 21 px;
  - the answer at 19 px with footnote numbers;
  - its sources in the right margin on desktop (sidenotes), or under the answer on the phone;
  - "Read 1 calendar and 1 thread · How I found it · Copy" on one quiet line.
- **Remember this?** is a ruled block that offers to save a fact to Know me. It's saved only when you press Save (the product's owner-pressed rule).
- **The compose line** is a 2 px rule with an input. Ask turns orange only when there's text (orange = the one thing to do now; an empty box has nothing to do).
- **Reading** shows a lit slot + "Reading Gmail · Personal" + Stop (plain key).
- **The sample answer** says plainly what isn't true yet: "Nothing is booked yet … your draft says Wednesday, but it hasn't been sent."

### People: the match gutter
- **Same person? (1 of 3)** sits under a 2 px rule: two records field by field (Name, Mail, Phone, Chat), with a narrow gutter marking each field: `=` same, `≈` close, `≠` different, `·` one side has none. A one-line legend sits under the grid, then the reason in one line ("Same phone number, and the names agree.").
- **The three answers are neutral keys**, with no orange. A merge is a judgement Callsheet can't make for you, and orange on "Same person" would lean on the answer. Each answer is confirmed in place with Undo, and the next pair follows.
- **You hear from most:** name, where seen, last heard, and "Always counts" with a lit square.
- **A person** (beside the list on desktop, full screen on the phone) is printed as a definition list:
  - Always counts (tick box);
  - Where;
  - Last heard;
  - Waiting on you (opens the reply);
  - Note for Callsheet.
- No faces and no location (H15).

### Know me: the fact list
- **The intro:** one sentence ("Forgetting a fact doesn't touch your mail").
- **Three steps as rows with ID boxes:**
  1. Read your history: done, with real counts, and Read again.
  2. Check what it wrote: "Check 2 things" is the one orange.
  3. A few questions: waits for step 2.
- **What it knows:** numbered facts, each with its source (a sidenote on desktop, under the fact on the phone) and Forget. Facts it wants checked carry "● ▲ To check" (warn = needs a look, not urgent).
- **Check mode** is the one-at-a-time pattern: ID-box progress, the fact at 30 px, "From …", then Right / Not quite / Forget this as neutral keys. Not quite opens a box, and Save and next becomes the orange. The end has "Answer 4 questions" (the orange moves on).
- **Questions:** square-window choices; the chosen row presses in.

### Projects: the slip track
- **The list:** a round window per project, the name, one line, and the status in words. A suggested project ("School trip forms?") has a dashed window and dashed rule, because it's unconfirmed, plus Add project.
- **The detail** (Kitchen refit):
  - an amber cue rule: "▲ Slipped a week. The fitter moved the fitting from 14 to 21 November¹."
  - the **slip track**: five weeks as a strip, milestone ticks (done ones dim), a dashed tick at the old date with an amber arrow to the new one, and today's needle with a lit cap (the day strip's needle);
  - tasks as tick boxes (done = lit square + struck);
  - the source footnote quoting the fitter's mail.
- No orange: nothing is urgent.

### Setup: the form at the back of the sheet
- **The index:** lettered sections A Connections, B Your day, C AI, D Advanced (letters, so they don't clash with the sheet's 01–04). Each has a one-line status. On desktop the index sits beside the open section with a lit slot; on the phone it's a list with ›.
- **Fields:** a mono label, the value, and a quiet Change. On/off and choices are **tick-box windows that apply at once** (no Save, CT12).
- **Call times** are drawn as a short running order: a time column, a rail, a tick per sheet, and "Careful · Every day". Editing a time:
  - checks it as you type (try "6:45" or "25:00");
  - shows Careful / Fast;
  - says what it costs: "Careful: about 3–5 min, from the last 7 sheets" (CT10, H17: a claim pinned to data).
- **Connections:**
  - each account has an On window, or a dashed "Offline · last read 06:30";
  - a broken account gets a dashed row with **Try again (orange)**, the only orange Setup ever shows (CW7);
  - the first Try again fails and says what to check.
- **Advanced:** ten closed drawers.
  - Google sign-in key says "A key is saved … It's never shown again" (CT10).
  - Start over opens a **confirm sheet** that names what goes ("the local index (2,412 threads), your profile and its 6 facts, the three call times and 1 rule … Your mail, calendars and chats aren't touched").
  - In that sheet, Keep everything comes first, and the destructive key is dark (never orange or red). Enter never fires it (CT7).
- **Setup has no orange at rest.** Refresh now is a plain key.

### First run (new, missing since pass 3)
- **The steps:** three ID boxes with labels (Connect · Call times · Know me), one orange per step.
  1. Connect Google account. Once connected, the orange moves to Next.
  2. Use these times (the call-times drawing).
  3. Read my history, with Not now as the alternative.
- **The end is the blank sheet:** "You're set up. Your first sheet prints tomorrow at 06:30." The four numbered sections are printed as empty grooves (ST3: a visible recess, one line), with one plain key, "Write today's sheet now". No orange.

### New elements this pass
1. **Day bezel:** the light-ground window form, with an equal footprint for lit and unlit.
2. **Struck line:** in-place done / later / moved with Undo.
3. **The form:** Setup as a lettered form with tick-box windows.
4. **Call times:** a running order for settings.
5. **Transcript with sidenotes:** Ask.
6. **Match gutter:** People.
7. **Fact list:** Know me.
8. **Slip track:** Projects.
9. **Reading rail and line strip:** voice.
10. **The blank sheet:** first-run end.

Capacities (H16):
- **Roster:** 5 rows on desktop and 4 on the phone, then "n more in Replies".
- **Day strip:** 2 labels.
- **Reading rail:** about 15 lines at 900 px tall, then it scrolls. A brief is 3–6 sentences plus up to 8 replies, so the rail needs a fold for long briefs (audit 7).
- **Slip track:** 5 weeks and about 5 milestones.
- **Call times:** 4.
- **You hear from most:** 10, then "All people ›".
- **Fact list:** 8 per section, then "More".
- **Transcript:** the current day; earlier days fold.

## Language check (the 15 items)

| # | Item | Held / adjusted | How |
|---|---|---|---|
| 1 | Two typefaces | Held | Jost + IBM Plex Mono only (Google Fonts in the mockup). Every label, time and count is mono. |
| 2 | Indicator windows | **Adjusted (Day)** | Always visible. Day unlit is now a groove at the bezel's edge instead of a recess (conflict 3 B); Night unlit has a 1 px rim so the recess shows. Lit is flat, never glows, and never changes footprint. |
| 3 | Window shapes | **Adjusted** | Round = status (projects, connections, Copied, Seen), square = chosen (tick boxes, options), slot = current (NOW, nav, voice line, Reading). Pass 4's lit slot for "Copied" became a round past form; pass 4's project slots became round. No fifth shape: the match gutter's marks and ID boxes are type, not windows. |
| 4 | Cream is the house light | Held | NOW, current place, voice line, chosen squares, On. |
| 5 | State = colour + shape + word | Held | ▲ + amber + word for warn (clash, slipped, To check); dashed for offline/unconfirmed; past forms "Seen 06:41", "Copied 06:41", "got it 10:06". |
| 6 | Red means alert | Held | One red key, "Check the sign-in"; nothing orange on that screen (checked by script in every flow step). |
| 7 | Orange is the one thing to do now | Held | At most one per frame across all 16 flows and 24 gallery frames (scripted count). It moves: Copy → Done, Connect → Next, Not quite → Save and next, step 2 → step 3. Calm, reading, Agenda, People, Projects and Setup have none. Ask is orange only with text. |
| 8 | Focus = a light at the thing | Held | Lit slot under the current place (nav, sub-row, Setup index). Rows show a 2 px focus outline. |
| 9 | Chosen things press in | Held, extended | Chosen option rows press in (shade + inner top line) as well as lighting their square. |
| 10 | Walnut | Held | The top trim, the sheet's top edge, and the sign-off's double rule that draws in once. |
| 11 | Things end visibly | Held | "End of day · clear from 19:00", "n more in Replies", "line 7 of 7", "Same person? · all checked", the blank sheet, and the sign-off. |
| 12 | Calm is the resting state | Held | The sign-off, Setup, Agenda and the blank sheet have no orange, nothing moving and nothing looping. |
| 13 | Motion: short, causal, once | Held | Strike 250 ms, walnut rule 350 ms, key press 2 px. The voice fill runs once per line. All off under reduced motion. |
| 14 | Say it once | **Adjusted** | New summary rule (live wins). The footer promise drops on the sign-off. "55 min" no longer prints twice. The evening summary no longer repeats the strip's swimming label. Gallery Undo is inline, not a toast. |
| 15 | Honest objects, drawn flat | Held | The printed sheet everywhere: the form, transcript, slip track and blank sheet are all paper things. No texture, no shadows except overlays. |

What someone arriving from another app recognises within a second: the type pair, the cream slot under the current place, the one orange key, the red alert key, the ▲ amber light, and walnut. What's deliberately Callsheet's own: the warm and navy sheets with no cards, the time column, numbered sections, footnotes and the sign-off.

## Conflicts assumed (all "assumed, pending Isaac")

| # | Conflict | Assumed | Where it shows |
|---|---|---|---|
| 1 | Warn shape | **B**: round amber light + ▲ + word | Clash cue, clash bracket, Slipped, To check. |
| 2 | Row ends: wrap or stop | **A**, stop at a visible end | Every list ends ("End of day", "n more", "all checked"). No carousels. |
| 3 | Windows in Day | **B on the light sheet** (groove / cream in a dark bezel, equal footprint, plus word and press); **C** at night (dark recess, now rimmed). Drop A. | Every window. |
| 4 | Title / launch card | Not applicable (no TV). | — |
| 5 | Day title card | Not applicable. | — |
| 6 | Round = status; slot = current | **B** | Copied moved to a round past form; projects use round; slots only for NOW, the current place, the voice line and Reading. ID boxes stay typographic, not windows. |
| 7 | Ribs | **B**, but Callsheet uses none | — |
| 8 | Accents optional | **B**: Callsheet has none | — |
| 9 | Shared house objects | **B**, but Callsheet draws none | — |
| 10 | Guide band | Not applicable. | — |
| 11 | Menus beside a list | **B** | "More" opens below the row; sheets are centred (desktop) or bottom (phone). |
| 12 | Unlocked door | Not applicable. | — |

## Holes applied

| Hole | Applied here |
|---|---|
| H2 Objects as UI | The printed sheet, including the form, transcript and slip track. Never a real product's look. |
| H6 Reading surfaces | No cards, a lede size, sources as footnotes/sidenotes, numbered sections, a sign-off. **Amended**: Today is a reading surface *and* a front door, so its cue carries one orange (rule 2 below). |
| H7 Timelines | Running order, day strip, slip track, reading rail. The past dims or folds; hit areas ≥ 24 px on desktop and 44 px on touch. **Amended**: NOW is an ink rule + lit slot in Day (a cream rule would be 1.1:1) and a cream rule at night. |
| H9 Shadows | One kind (soft), only under overlays. None on text. |
| H12 Signature moments | The walnut rule draws in (350 ms) and the strike (250 ms); both off under reduced motion; never on focus. |
| H15 People | Name + where seen; no faces, no location. No colour tag (rule 7 below). |
| H16 Capacity | Stated for every element (above). |
| H17 Claims about the real world | Gap cue minutes dropped. Writer time is pinned to "the last 7 sheets". Slip dates are footnoted to the mail they came from. The Ask answer says what isn't true yet. Scan counts are real counts. |
| H18 Glossary | Callsheet keeps "running order" (RULES-TIERS suggests JamFin renames its own to "episode list"). Pass 4's internal "slip" (the reply detail) is renamed **reply page**, because "slipped" is a Projects word and the slip track uses it. "Wrap" is no longer screen text. "Day strip" is distinct from HA's "room strip" and "power strip". |
| H1, H3–H5, H8, H10, H11, H13, H14 | Not applicable to Callsheet. |

## Rules I broke

| # | Rule (where) | What I did instead | Why Callsheet needed it | Verdict |
|---|---|---|---|---|
| 1 | IN2 / conflict 3 "unlit = visible dark recess" | Day: unlit is a 1 px groove at the window's outer edge; lit is cream in a 3 px dark bezel. Night: recess + 1 px rim. | A dark recess on a light sheet reads as "checked", and a cream fill on it is 1.1:1. The bezel makes lit a dark mass with light in it; the groove keeps the footprint equal. | **Language-wide** (as conflict 3's rule for light grounds), with "equal footprint" added to IN2. |
| 2 | H6 "reading surfaces: no orange" | Today keeps one orange on its cue; its reading parts (summary, 03, 04, footer) have none | Today is a front door as well as a reading surface. FLOW: "the next reply with its draft" must be one tap from opening. | **Language-wide amendment to H6**: "no orange in the reading part; a front door's cue may carry the one orange." |
| 3 | H7 "NOW is a cream rule" | Ink rule + lit slot in Day; cream rule at night | Cream on the warm sheet is 1.1:1 | **Language-wide amendment**: the NOW rule is the ground's highest-contrast ink; the cream is in the slot. |
| 4 | CW4 "a snapshot sentence dims" | It leaves the printed summary while a live cue or note says it; its footnote moves to the cue | Dimmed text still passes AA, so it's still said twice | **Language-wide** (replace "dims" with "steps aside"). |
| 5 | CL5 "no orange on settings screens" | Setup has none, except Try again on a broken connection | CW7 says every failure ends in an orange Try again; the two rules collide in Setup | **Language-wide refinement**: settings have no orange unless something there is broken. |
| 6 | CT1 / D83 quiet paddles in Setup (pass 3) | Tick-box windows (square = chosen) on a printed form | A paddle is a device object; on a paper form a tick box is the honest object, and it uses the language's square window | **App-local.** Paddles stay the language for device-like switches (HA, Lobby). |
| 7 | H15 "a printed colour tag + name" | Names in type only, no colour tag | Colour on the sheet is kept for state. Callsheet never shows people side by side on a shared surface, where tags help. | **App-local exception**; H15's tag is right for shared surfaces (HA key rail). |
| 8 | LY8 "at most one orange per step", applied as "every step has one" | Judgement steps (Same person?, Right / Not quite) have none | Orange on one answer leans on the answer | **Language-wide addition**: when the step asks for a judgement, no answer is orange. |
| 9 | LY16 "no pop-ups" (broken in pass 4 by toasts) | Undo in place (struck line, inline Undo) | Pass 4 broke it; this pass complies | **Language-wide** (kept; the struck line is app-local drawing). |
| 10 | Callsheet principle 5 "Three sizes a screen" | Four on Today (headline, lede, body, mono); three elsewhere | Same as pass 4 | **App-local** (TY7). |

## Audit

Checked with Playwright (Chromium, `chromium.launch()` with no options):
- page 1500 wide: every step of all 16 flows in Day and in Night (50 steps × 2), plus the 24 gallery frames;
- a scripted check per frame: at most one orange, no orange with a red key, no horizontal overflow inside the page, no text under 12 px;
- fold measurements at 1440 × 900 and 1280 × 900 in four states and both lightings;
- a keyboard run: c, u, c, d, u, ?, Esc, /, Enter, Esc, r, →, Esc, 4, 2, j, x, Esc, w, d, Esc, 3, 1;
- typing in Ask: Ask turns orange, Enter → reading → answer;
- typing in a call time: "25:00" → "Write it as 06:30."; "6:45" → "Next sheet at 06:45 tomorrow.";
- page 390 wide: `scrollWidth` 390, full-page screenshot;
- page 1500 in the dark scheme.

Results: **no JS errors; 0 frames with more than one orange; 0 with orange beside red; no overflow at 390; no text under 12 px.** The 12 px text is keycaps, strip hours, week labels and footnote numbers; uppercase labels are 13 px.

The fix pass corrected:
- the gallery's voice frames still rendered the sheet underneath, which counted as two oranges;
- the phone slip track's "1 Dec" label overflowed by 2 px;
- the reading rail's current line inherited the 38 px voice style;
- a too-specific button reset removed padding from every list row;
- the Measure label collided with today's needle;
- the destructive key turned cream at night (now a dark key with a cream outline);
- the clash row nested a button inside a button, which blanked the desktop right column after Got it;
- "55 min" printed twice at 10:05;
- the evening summary repeated the strip label;
- the night unlit recess was 1.1:1.

Contrast (WCAG):

| Pair | Day | Night |
|---|---|---|
| ink on sheet | 14.7 | 14.7 |
| dim on sheet | 5.7 | 6.6 |
| dim on pressed row (shade) | 5.1 | 5.9 |
| lit cream on sheet | 1.1 (why the bezel exists) | 14.9 |
| bezel on sheet / cream on bezel | 16.6 / 14.9 | — |
| unlit groove / rim on sheet | 5.7 | 3.0 |
| warn ink / warn line | 6.2 / 3.5 | 11.0 |
| alert ink | 5.9 | 8.0 |
| text on orange / on red | 6.6 / 6.3 | 7.4 / — |

Screenshots are in the session scratch dir, `p5cs/shots/` (flows in Day, eight flows in Night, gallery, page at 390, page dark).

| # | Problem | Severity |
|---|---|---|
| 1 | **The Day bezel is Callsheet's answer, but every light-ground app needs the same one.** HA's Braun page and JamFin's Day lightbox have the same 1.1:1 problem. If conflict 3 is decided differently, every window here changes. | High (language, pending Isaac) |
| 2 | **Summary rule needs fact tags from the writer.** "Said once, live wins" works only if the brief writer marks which fact each sentence carries (event id, reply id, alert id). The product's summary is free text today. Without tags, the rule can't run. | Medium (feasibility) |
| 3 | **Phone footnote hit areas overlap.** Two footnote numbers in one sentence sit closer than 44 px, so their hit areas overlap; the later one wins. A tap on the sentence could cycle sources instead. | Medium |
| 4 | **Setup's tick boxes replace pass 3's quiet paddles.** Isaac hasn't seen either in use. Squares for on/off are honest on a form, but "On" with an unlit square still needs the word to read. | Medium |
| 5 | **Slip track labels are hand-placed.** Real projects will have close milestones; it needs a placement rule (alternate above and below, then a "+2" label) before it ships (H16). | Medium |
| 6 | **The struck line's lifetime** ("until the next change or you leave") is untested with people. On the phone a struck row can scroll out of view, leaving Undo out of reach; `U` covers desktop only. | Medium |
| 7 | **The reading rail grows with the brief.** At 8 replies the rail is about 15 lines and scrolls; it needs the running order's fold ("Done: 4 lines"). | Low |
| 8 | **The night rim `#5c6273` and the Day bezel width are raw values**, not tokens. | Low |
| 9 | **Undo on Copy** only unmarks the row; it can't empty the clipboard. The wording may promise more than it does. | Low |
| 10 | **Only one of four Know me questions is drawn,** and the history scan's progress isn't drawn (it would be CT9: progress on the step row). | Low |
| 11 | **Desktop Setup › Your day is a long form** (about 1,100 px), so Look and Lighting sit below the fold. It's fine for settings, but the index could jump within the section. | Low |
| 12 | **Projects' "On track" and "Waiting"** look the same (both unlit); only the word differs. That's honest (neither needs you), but worth confirming. | Low |
| 13 | **Voice line timing** is still a fixed 5 s stand-in, and a locked phone still needs the Companion app (pass 3 note). | Low |
| 14 | **Looks:** only the Hi-Fi-derived sheet is drawn. The sheet layout still has to survive Bold, Clean, Easy read and the Jam looks (pass 4 audit 9, unchanged). | Low |

## Questions for Isaac

1. **Windows on a light background: unlit = a thin outline, lit = cream inside a heavy dark bezel, the same size either way?** *Recommend yes, for every app's light grounds* (conflict 3 B). It's the only form that read correctly on the sheet, and it no longer depends on rim weight alone.
2. **Summary vs live cue: should a summary sentence step aside (not dim) while the cue on the same screen says the same thing?** *Recommend yes.* It keeps the source number, and voice still reads it all.
3. **Gap cues without the minutes ("Free until 09:30 · 2 h 56 · A free stretch for replies"): still useful?** *Recommend keeping them on the first free gap only*, with no time estimates until there's real data.
4. **The end of the day: "Answered / For tomorrow" as figures and "Nothing was sent" in words, labelled "All answered", not "Wrap"?** *Recommend yes*, as it follows "lets get rid of the cheeky production nods".
5. **Setup as a printed form with tick boxes, instead of quiet paddles?** *Recommend yes for Callsheet only*: paddles stay the language for device switches.
6. **Same person? and Know me checks with no orange answer?** *Recommend yes*: orange would push you towards one answer.
7. **Undo in place (a struck-through line) instead of toasts?** *Recommend yes*, language-wide (LY16).
8. **Ask, People and Know me as a sub-row under Ask (five tabs kept)?** *Recommend yes* (unchanged from pass 3; asking again because Know me is now a fuller screen and may want its own place on desktop).
