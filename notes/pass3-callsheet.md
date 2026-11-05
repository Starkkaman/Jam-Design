# Callsheet · Pass 3 (of 3)

Mockup: `mockups/pass3/callsheet.html`. Passes 1 and 2 are unchanged.

The page has four parts:
1. **A flow player** with nine flows (A–I). Each drives a live desktop frame (1440 × 900) and a live phone frame (390 × 844).
2. **The rules this pass settles**, plus an orange-budget table.
3. **A day/night gallery**: 6 desktop frames and 12 phone frames.
4. **Stress and empty cases**: the long day, the quiet day, and a 120% "Large text" zoom standing in for Easy read.

Page controls switch Lighting, Time (08:15 / **10:05** / 12:40 / 17:05), Day (Quiet / Normal / Long), **Connection** (OK / Google offline / Box unreachable) and **Alert card** (With Then line / Strict). Every Today frame has a live count of "things in view" on its caption. All content is made-up sample data (Sam, example.com, Co. A/B, Northwind Store, +44 7700 900xxx).

Sources read:
- `notes/OVERNIGHT-BRIEF.md` and `projects/callsheet/README.md` + `FLOW.md`.
- All of `CHANGES.md` (A, B, D1–D103) and the end of `decisions.md`.
- `notes/pass1-callsheet.md` and `notes/pass2-callsheet.md`. Their audits and change suggestions were my to-do list.
- The pass-2 notes for Jam-Dash and HA, for the trouble card, D82 per-screen orange, D83 quiet paddles, D84 alert key, D92 warn triangle, D95 calm overview and D97 page behind a sheet.
- `mockups/pass2/callsheet.html`, which this pass is built from.

## What changed since pass 2

| Pass 2 # | Was | Now |
|---|---|---|
| 1 (High) alert blocks Priya's draft | With an alert open, Copy was a step away | **The Then line.** Any Next card that isn't a reply (alert, offline, clash) ends with a hairline and "Then · Priya N. · the Q4 budget sign-off · Copy draft (C)". Copy is a quiet key. The alert's own key is the **red alert key** (D84), so a busy morning shows no orange at all. The "Alert card" control switches to pass 2's strict card for comparison. |
| 2 (Med) count said twice | "11 waiting" text + capped bar group "11" | **Counted once.** The rundown row never prints the count. Instead it names who comes next ("Then School office, Landlord…"). Nav badges are gone everywhere, since they repeated the Today meter. Rundown step 2 says the number in words and links "See them all", not "All 7". The bar group prints its number only above 10. The bar group is now drawn as **one dark recess with segments**, so it stops reading as "0000000". |
| 3 (Med) time scope of warns | The 60 min rule was mine | **Settled as a rule and shown in a flow (D).** At 08:15 the 11:00 clash rides the scale and the reply keeps the card. At 10:05 the clash is within 60 minutes, so it takes the card (triangle window, "Clash · 11:00 · in 55 min", orange See the clash), and Priya waits on the Then line. Got it hands the card back. Non-time-bound warns (a slipped project) never take Today's card. |
| 4 (Med) "same for this sender" default on | Rocker defaulted on | **Default "Just this one".** "Everything from Northwind Store" is a second key you have to press. For people who always count, that key is locked with the reason ("Priya N. always counts, so only this message moves"). Sender rules never apply to invites or security heads-ups. The **Never needs a reply** list shows sender, reason, date added and how many it caught, with Remove + Undo. |
| 5 (Med) four orange paddles in Your day | 4 orange, no primary | **Quiet paddles (D83):** up + a cream window on the paddle. Your day has **0** orange, and so does Setup as a whole. |
| 6 (Med) desktop list+detail | Reversal of 0.9.0 | Kept. Still a question for Isaac (below). |
| 7 (Med) Next card height jumps | 150 / 245 / 145 px | Desktop Next card has a 300 px minimum. Alert, clash, offline and reply all sit in the same slot, and the footer no longer jumps. |
| 8 (Med) Wheatley = voice | Not designed | **Read it to me** (flow G), described below. |
| 9 (Med) only Hi-Fi | — | Not solved. A "Large text" (120%) stress frame on desktop and phone found one bug: phone buttons clipped "Check the sign-in". Fixed by letting buttons wrap. |
| 10 (Low) "Seen" reads as a stray dot | Unlit LED + word | On the rundown row, Seen is **the word only** ("Seen 08:20"). Unlit windows stay only where windows line up in a column (step 3 list). |
| 11 (Low) tab bar dashes | Unlit windows under every tab | **Only the lit window is drawn (D91).** |
| 12 (Low) Space conflict | Space played the rundown | **R plays the rundown**, B opens the full brief, and `?` opens a key sheet. Space is left to the browser (it presses the focused button). Inside voice mode, Space is Pause/Play. |
| 13 (Low) dropped band labels | Some events had no label | The desktop band now names only **the next event and any clash**. Everything else is a window, and the Agenda (A) has the full list. That is a deliberate cut, not a collision fallback. |
| 14 (Med) missing screens | Full brief, People, Know me, offline… | Drawn: **Full brief, People (Same person?), Know me (status, check, questions), Read it to me, Google offline, box unreachable, failed refresh, the Never needs a reply list, the key sheet, the More sheet.** Still not drawn: the Weekly review run, the first-run wizard, the Look panel, Projects detail. |
| 15 (Low) "three that matter most" | List order | Written down as the sorter's order, used in the list, the rundown and the full brief: people who always count → due today → asked you → waiting. |
| 16 (Low) Google Fonts | — | Unchanged (mockup only; the product bundles them). |

**Shared parts adopted from other apps:**
- D82: one orange per screen, and a sheet is its own screen.
- D83: quiet paddles.
- D84: red alert key, with no orange on that screen.
- D92: warn = amber triangle window + word, so the "▲" glyph is gone from words that sit next to a window. Alert = round, red, ringed LED.
- D95: a calm screen has no orange.
- D97: the page behind a sheet or palette loses its orange.
- D99: night bands get a hairline and stronger ribs.
- D27/D101: offline is dashed, with "last read" said once, and Try again can fail and must say what to check.

**First-screen count.** One count per separately readable thing: a word label, a heading, a sentence, a button or link, a tag, a tab, a band label, and a meter (the day scale and the bar group count once each). Icons, chevrons and a window next to its word don't count. Pass 2 was measured with the same rule by script (selectors mapped to pass 2's markup), in the same state (08:15, normal day):

| State | Desktop pass 2 → 3 | Phone pass 2 → 3 |
|---|---|---|
| Alert open | 44 → **36** | 35 → **30** |
| Next = reply | 51 → **37** | 35 → **30** |
| Calm | 41 → **32** | 33 → **27** |

**What was cut:**
- nav badges (×2 on desktop, ×1 on phone);
- the hero eyebrow (it returns only while the summary is being written);
- the band's "1 · Your day · now 08:15" and its "6 events · ▲ 1 clash" summary;
- labels for past and later events;
- the reply's second tag;
- "06:30" next to Refresh (the footer says it once);
- three quiet links on Today's Next card: Later, Note and Not for me move behind **More** (their keys still work, and Replies keeps them all visible);
- the two footer lines, merged into one;
- step numbers on the rundown rows;
- on the phone: the header date, the band label and the Full brief link.

## Research

**Method:** WebSearch, 4 queries, this pass. Items marked *(knowledge)* are from memory.

| Source | What it says | Used for |
|---|---|---|
| **Apple CarPlay HIG** ([interaction](https://developer-mdn.apple.com/design/human-interface-guidelines/technologies/carplay/interaction), [overview](https://developer.apple.com/design/human-interface-guidelines/carplay.md)) | Minimise touchscreen use while moving, and need as few manual steps as possible. Messaging must work by voice alone. Avoid starting playback automatically unless resuming. | Voice mode starts only from an explicit tap (push action or rundown button), never on its own. It has three big keys, and voice commands cover every step. |
| **Gemini Live captions** ([Android Authority](https://www.androidauthority.com/gemini-live-live-captions-rollout-3564739/), [PhoneArena](https://www.phonearena.com/news/gemini-live-just-added-a-key-feature-for-talking-quietly-with-your-android-phone_id171696)) | Captions show **only the current response**, centred. They're offered automatically when volume is at its lowest. | Read it to me shows the current line large and the previous line dimmed, nothing more. Sound off / quiet hours = "captions only". |
| **Google Contacts Merge & fix** ([Google help](https://support.google.com/contacts/answer/7078226)) | Suggests likely duplicate pairs from matching names, phones and emails. You merge or dismiss each pair. It can't merge across accounts. | The **Same person?** card: one pair at a time, the reason in one line, and Same person / Not the same / Not sure. Not the same is remembered ("won't ask about this pair again"). |
| **ChatGPT memory** ([OpenAI help](https://help.openai.com/en/articles/8590148-memory-in-chatgpt)) | A list of remembered items you can delete one by one. Deleting a memory doesn't delete the chats it came from. Turning memory off doesn't delete what's saved. | Know me lists each fact with its source and a **Forget** link, and says plainly that forgetting doesn't touch your mail. |
| **Gmail "Filter messages like these" / Superhuman "Move to Other"** *(knowledge)* | Both make the scope explicit (this message vs this sender) before saving a rule. | Not for me defaults to Just this one, and the sender is a second, deliberate choice. |
| **Slack / Gmail offline banners** *(knowledge)* | A thin persistent bar ("Trying to reconnect…") while cached content stays readable. | Box unreachable: a dashed bar above everything, the last brief stays readable, Copy still works, and one Try again. |

## Design

**Today (desktop).** It reads top to bottom:
1. Greeting + one sentence.
2. The day band: label "Your day", Agenda (A), the scale, and labels for only the next event and the clash.
3. The **Next card** (left) beside the **rundown card** (right).
   - The rundown card's header holds Play the rundown (R) and Full brief (B).
   - Its rows: Who needs an answer (next names + bar group), Worth knowing (changes + "Seen 08:20"), Coming up.
4. One footer line.

The Next card takes, in order:
1. an open alert (red key);
2. offline (dashed card, Try again);
3. a clash within 60 minutes;
4. the next reply (Copy draft, Done, Open, More);
5. calm (no orange; See tomorrow is a quiet key).

Cards 1–3 end with the **Then** line.

**Today (phone).** The same order, stacked. The first screen holds the greeting, the sentence, the band, the whole Next card with its Then line, and the top of the rundown card. Open in Gmail moves into More.

**Read it to me (voice, "Wheatley").** It's reached from the push ("Read it to me"), from the rundown's speaker button, and works on desktop too.
- **Layout:** the walnut trim; a lab ("Read it to me · Wheatley"; just "Wheatley" on the phone); Sound on/off; Close; four progress windows plus the step name; the current line at 40/29 px with the previous one dimmed; a slot that fills linearly while the line is read (one fill per line, no loop, no waveform, no glow).
- **The black ribbed band** at the bottom holds what you can say ("next", "back", "later", "repeat", "stop") and three 76–80 px keys: Back, **Pause** (the one orange, playing > idle) and Next.
- **"Later"** is confirmed in words: "Heard 'later'. Priya N. waits for your desk at 12:30."
- **Sound off** or quiet hours = captions only.
- **The end** has no orange: Back, Play again, Close.
- Lines follow the content contract: one or two sentences, the same facts as the step.

**Full brief.** A reading page. It has a sticky section list on desktop (slot window lit for the chosen section) and five sections:
1. Your day: the sentence plus every event, with clash triangles.
2. Who needs an answer: everyone, in sorter order. Each row opens that reply. The For your info names are listed too.
3. Worth knowing: all security heads-ups plus everything that changed.
4. Coming up: the next two weeks as date tiles, then the next two months.
5. By area: one line each for Co. A, Co. B and Personal.

It ends with "Something missing? Tell Callsheet" and the promise. There is **no orange**: nothing on it needs doing.

**People** (Ask › People). Ask, People and Know me are three views of what Callsheet has read, in one sub-row under the Ask tab, so D73's five tabs stay.
- The **Same person?** card leads ("1 of 3"): two identity blocks, "=?", the reason, and Same person (orange) / Not the same / Not sure. Merge has Undo.
- Below it: the list of people you hear from most, with an "Always counts" tag.
- The detail shows:
  - an Always counts quiet rocker;
  - where Callsheet sees them (mail address, Slack, Signal);
  - when they were last heard from;
  - what's waiting on you (opens that reply);
  - Note for Callsheet about them.
- Setup › Your day › "People who always count" now links here instead of keeping its own list ("each setting in one place").

**Know me** (Ask › Know me). One sentence ("uses this to sort replies and write drafts… stays on this box"), then:
- **Three steps as one-line rows** with slot windows:
  1. Read your history: done, with counts, Read again.
  2. Check what it wrote: "Check 2 things", the screen's one orange.
  3. A few questions: Answer, quiet until step 2 is done.
- **What it knows about you**: each fact with its source and Forget.
- **Check mode** is the shared step pattern: progress windows, one fact at 34 px, Right / Not quite / Forget this. Not quite opens a text box.
- **Questions**: square-window choice keys and Save and next.

**Offline and errors.**
- **Google offline:**
  - a dashed Next card: "Offline · Google · last read 06:30" / "Google isn't answering" / "This brief came from Slack and Signal only…" / Try again.
  - The calendar windows on the scale go dashed and the band says "Your day · not updated". The footer names the sources actually used.
  - The first Try again fails and says when it tried and what to check, and adds a Connections key. The second succeeds and says what changed.
- **Box unreachable** (phone away from home):
  - a dashed bar above the page: "Can't reach Callsheet · Showing the brief from 06:30. Copy still works; the rest waits until it's back." with Try again (orange);
  - Refresh and Find dim, and the page's own orange drops to a quiet key.
- **Failed refresh:** a warn toast with the triangle ("Refresh didn't finish: Google didn't answer. The 06:30 brief stays.").

**Not for me + rules.** Covered in the table above. The rules list lives at Setup › Your day › Never needs a reply. Removing a rule says what happens next ("Northwind Store's next mail comes back to Replies") and offers Undo.

**Setup.** As pass 2, but with quiet paddles and zero orange. Quiet hours now says "voice starts muted". Connections shows Google as "Offline · last read 06:30" when it is.

**Keys (desktop):**
- Enter = the loud key (alert, orange or Try again).
- R = rundown; B = full brief; A = agenda; 1–5 = tabs.
- / or ⌘K = Find or ask (Enter opens the top person).
- C D L O N X = reply actions. C also works from the Then line.
- J/K = list (Replies and People).
- ← → = steps; Space = Pause/Play in voice mode.
- ? = key sheet; Esc = back.

## Audit

Checked with Playwright (Chromium, `chromium.launch()` with no options):
- page width 1500 (light scheme, every step of all nine flows in Day, eight steps in Night, every section) and 390 (dark scheme, every flow);
- a keyboard run: c, Enter, Esc, r, →, →, Esc, b, 1, ?, Esc, 2, j, k, x, Esc, 4, /, Esc.

Results: **no JS errors, no horizontal page scroll at 390, no element outside its app frame, no text under 12 px** (keycaps are the 12 px floor).

The fix pass corrected:
- the copy icon rendering as a filled black square on keys;
- "Copy draft" wrapping on the Then line;
- the bar group reading as zeros (now one segmented recess);
- the voice band not spanning the desktop width;
- the phone Setup rows collapsing to one word per line;
- the phone offline bar squeezing its text;
- "Check the sign-in" clipped at Large text.

Screenshots: scratch dir `shots/` (flows A1–I4 day, eight night steps, every section at 1500, the page at 390).

| # | Problem | Severity |
|---|---|---|
| 1 | **Voice on a locked phone may not be buildable as drawn.** Callsheet is an HA Ingress web page. A web page can't keep speaking with the screen locked, take a push action straight into audio, or listen for "next" in the background. Read it to me probably needs the HA Companion app (TTS to the phone or a media player) or a small native wrapper. The design holds; where it runs is the open part. | High |
| 2 | **The phone first screen is still about 30 things.** The cuts saved 5. The rest is the Next card (9 with the Then line) plus header and tabs (8). Going further would mean dropping the sentence when the Next card already says it, or hiding the rundown card behind Play. Both lose something FLOW §4 wants one tap away. | Medium |
| 3 | **Three reds in one alert card** (ringed LED, ALERT word, red key). That follows D84, but on a 390 phone it's the loudest thing in the whole app for what is often "it was me". | Medium |
| 4 | **People and Know me under Ask** is my call, to keep D73's five tabs. Know me is easy to miss there, and "Ask" doesn't say "who you know". | Medium |
| 5 | **The 60-minute warn window** is a guess. If Isaac is in the 10:00 stand-up, the clash card appears while he's in a meeting. 30 min would be too late to rearrange. | Medium |
| 6 | **Box unreachable needs an offline cache** (a service worker or a cached JSON of the last brief). Ingress URLs carry a session token that can expire, so "showing the 06:30 brief" isn't free. | Medium |
| 7 | **Calm has no orange**, so All clear's Back to Today is quiet. That matches D95, but principle 6 ("make the end feel good") now rests on the Stripes accent alone. | Low |
| 8 | **Quiet paddles:** on vs off is mostly paddle position. The cream window is small (12 × 3 lit), the same as HA pass 2 #3. In Setup the row text ("Off") carries it. | Low |
| 9 | **The disabled "Everything from Priya N." key** is drawn at 45% opacity. Disabled text is exempt from AA, but it's hard to read. The line under it explains. | Low |
| 10 | **The segmented bar group** (one recess, cream segments) differs from Jam-Dash/HA bar groups drawn as separate windows. It reads better at 5 px widths; the bible should pick one. | Low |
| 11 | **More** hides Later / Note / Not for me on Today. The keys still work and Replies shows them, but a mouse user on Today needs one more click for Later. | Low |
| 12 | **The count rule is mine**, and it counts what's in view, so a taller phone scores higher. It's good for comparing passes, not as an absolute target. | Low |
| 13 | **Only the Hi-Fi look is drawn.** The 120% zoom is a stand-in for Easy read, not Bold or the Jam looks. | Low |
| 14 | **Still not drawn:** the Weekly review run (step pattern), the first-run wizard, the Look panel, Projects detail. | Low |
| 15 | Desktop Today at 1440 × 900 is still about 20% empty below the footer in every state. That's calm, but noticeable. | Low |

## Questions for Isaac

1. **Busy morning: should the alert card carry a "Then" line with Priya's Copy draft?** *Recommend yes.* It answers "I want both" without breaking alert-first, and it costs one row. (Compare with the Alert card → Strict control.)
2. **How early should a clash take the Next card?** *Recommend 60 minutes before it starts*, with Got it to hand the card back. Before that, the clash shows on the scale and in the agenda.
3. **Not for me: should "Just this one" be the default, with the sender rule a second press and never for people who always count?** *Recommend yes.* A broad rule hiding a real reply later is worse than one extra tap.
4. **Setup paddles: quiet (up + cream window, never orange) as in HA pass 2?** *Recommend yes.* Your day goes from four oranges to none.
5. **Calm screens (calm Today, All clear) with no orange at all?** *Recommend yes* (D95). The Stripes accent is the reward. Say if All clear should keep one orange Back to Today as the "peak".
6. **Where do People and Know me live: under Ask (Ask · People · Know me) or as a sixth desktop place?** *Recommend under Ask*: five phone tabs stay, and all three read the same local index.
7. **Read it to me: is "Wheatley" a name shown in the app, or only the voice's name?** *Recommend* showing it only in the voice screen's label ("Read it to me · Wheatley"), never in navigation, keeping plain words elsewhere.
8. **Voice where: phone speaker via the HA Companion app, a car/home speaker, or only while the page is open?** *Recommend* the Companion app's TTS on the phone first. It's the only route that works with the screen locked; confirm before building.
9. **Today's quiet links: Later, Note and Not for me behind "More" on Today (still visible in Replies, keys unchanged)?** *Recommend yes.* It's the biggest single cut on the Next card.
10. **Replies on desktop opening as list + detail rather than One at a time** (carried over from pass 2). *Recommend list + detail*, per FLOW §2.

## Bible implications (final form)

1. **The Next card (shared "one next action").** A front door shows one next thing, workable in place, in a fixed slot of fixed minimum height. It is chosen in this order: alert → offline → time-bound warn within 60 min → routine → calm. Any card that isn't routine ends with a **Then line** naming the next routine item with one quiet key. (D7, D23, D64, D65, D95.)
2. **Warn time scope.** A time-bound warn (clash, starts soon) takes the Next card only within 60 minutes of its start. Warns without a time never take a front door's card; they stay on their own screen.
3. **Alert key, one form.** The control that fixes or checks an alert is a solid alert-red key with ink text. While it shows, nothing on that screen is orange. The alert LED is round and ringed. (Confirms D84/D92.)
4. **Orange budget per screen, and calm has none.** One orange per screen; a sheet or palette is its own screen, and the page behind loses its orange. Calm screens (nothing to do) have no orange. Reading pages (full brief) have none. (D82, D95, D97.)
5. **Quiet paddles everywhere.** Rocker paddles are never orange: on = up + a lit cream window (or the device's colour) on the paddle. Settings screens carry no orange. (D83, closes D74.)
6. **Count once (never twice, applied to counts).** A count appears once per screen. Nav badges don't repeat a meter on the same screen. A bar group prints its number only above 10. Text near a bar group names things instead of counting them. (D25, D68.)
7. **Bar group drawing.** A bar group is one dark recess holding up to 10 segments (lit = cream), with the overflow number printed inside the recess. Pick this or separate windows for all apps.
8. **Warn shape.** Warn = amber triangle window + word, and the "▲" glyph is dropped from words that already sit next to a triangle window. Tags without a window keep "▲". (D92.)
9. **Seen alert, final.** On summary rows a seen alert is the word only ("Seen 08:20"). In aligned lists it's an unlit window + word. No red and no button. (D11, D69.)
10. **Scoped corrections.** Any "hide this kind of thing" control defaults to the single item. The broader scope (sender, type) is a second deliberate choice, is locked for people who always count, never applies to security or invites, and its rules live in one visible list with Remove + Undo.
11. **Offline, final.** A source that stops answering becomes a dashed Next card with one Try again, its data goes dashed where it's drawn, and "last read" is said once. If the whole service is unreachable, a dashed bar sits above the page, cached content stays readable, read-only actions (Copy) still work, and everything else dims. The first failure says what to check. (D27, D101.)
12. **Voice mode (new shared pattern).** It plays the same steps as step mode, starts only from a tap, shows only the current line (previous dimmed), uses a linear per-line fill slot (no waveform, no loop) and three large keys on a black ribbed band (Back / Pause-Play / Next), with Pause-Play as the one orange. Heard commands are confirmed in words. Quiet hours = captions only. Voice can never send, accept or delete.
13. **Step mode extended (D66).** The same component runs the rundown, Know me's checks and questions, and (later) the Weekly review and first run.
14. **Reading pages.** A long generated page (full brief) is the step content expanded, with a sticky section list using slot windows, every item linking to where it's acted on, and no orange.
15. **Same-person pattern.** Merging identities is one pair at a time: two identity blocks, a one-line reason, Same / Not the same / Not sure. Not the same is remembered, and merges have Undo.
16. **Keys.** Single-letter shortcuts only; Space is never an app shortcut outside voice mode. `?` always opens the key sheet.
17. **Callsheet navigation (D73, final).** Five tabs: Today, Replies, Agenda, Ask, Projects. Ask holds Ask · People · Know me as a sub-row. Setup is a labelled header button. There are no nav badges.
