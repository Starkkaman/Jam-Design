# Pass 5 · Cross-app journeys

Mockup: `mockups/pass5/journeys.html`. Nothing else changed.

Isaac's goal (decisions.md, 2026-11-05): *"The purpose of this exercise is to create a design system where each interface design is bespoke to it's purpose, but moving between them feels natural."*

Passes 1–4 tested each app on its own. This pass tests the second half of that sentence: six real household journeys that cross apps, played step by step, with each app's pass-4 frame at its real device size and the **handoff** between each pair drawn as its own step.

**How to use it:** pick a journey, then use **→ / ←** (or Next / Back, or 1–6 to jump between journeys). Striped steps are handoffs: both screens side by side, a table of what carries across, what changes on purpose, and links to the seams that jar there. The chips at the top ("Outline what carries") draw blue review dashes around that thread in every frame on the stage. Page theme (Auto / Light / Dark) and Motion (Full / Calm) as in the other mockups. A step can be linked as `#j2-7`.

**Sources read:** the last entry of `decisions.md`, the Direction update in `notes/OVERNIGHT-BRIEF.md`, `notes/RULES-TIERS.md`, all six `notes/pass4-*.md`, the six `mockups/pass4/*.html` (rendered and read for tokens and CSS), and the Lobby, NervOS and Jam Home READMEs (for what's plugged into the TV).

**Method.** Each frame copies its app's pass-4 tokens and CSS fragments and redraws the screen in fewer parts: recognisable, not complete. Nothing was unified, so the seams show. TV frames are authored at 1920 × 1080, kiosks at 1024 × 768 and 961 × 601, phones at 390 × 844, desk at 1440 × 900, all scaled to fit. People are the household's first names as already used in the repo (Isaac, Amber, Marissa); titles, times, hosts and events are samples. The Jam Home plan is a placeholder, as in pass 4.

---

## The six threads

From the 15-item language in `RULES-TIERS.md`, these are the six you can actually see survive a move between two screens. Every handoff rates each one: carries / partly / breaks / not in play.

| Thread | Language item |
|---|---|
| Cream focus light | #4, #8: the thing you're on is lit cream with a small lift; its shape is the app's |
| Orange: one thing to do | #7 (and #6: red replaces it while an alert shows) |
| State words | #5, CW2: shared words, short words, quiet past forms |
| Slatted load bar | MO9, TV4 |
| Walnut | #10, SM8 |
| Jost + Plex Mono | #1, TY1 |

What **changes** on purpose at every handoff: the ground, the objects and the layout. That's the bespoke half, and it held up. None of the changes below is listed as a seam.

---

## The journeys

### 1. Movie night (Jam Home → Lobby → JamFin → Jam Home) · 14 steps
Amber taps **Movie** on the living-room kiosk (scene presses in, lamps fade, TV turns on) → **Lobby** wakes, the house plate already shows the scene, the needle remembered Jamfin → Lobby's **blind** (12 slats) → JamFin **tickets** → JamFin **marquee** → JamFin **house lights + colour-block title card** (16 slats) → the **kiosk** during the film (Pause is the room's one orange) → the **intermission** card → the **Goodnight round** on the kiosk → "Goodnight · done".

- **Same family:** the type pair on every screen; cream for lit and here all evening (lamp windows, needle, plaque slots, ticket window, slats); orange stays rare and moves (none, none, none, Pause, Resume, Goodnight); On / Off / Locked / Playing / Paused carry; walnut everywhere in a different shape; both covers show a real load.
- **Where it jars:** two launch covers in three minutes that look nothing alike (S1), with slats drawn two ways (S2), and the first cover is arguably wasted (S3); "Jamfin" vs "JamFin" (S4); JamFin's warm baked spill vs Lobby's flat focus (S6); the same lamps drawn as a dimmer column and a wall paddle, "20" vs "On · 20%" (S15); "house lights" means the screen in JamFin and the lamps in Jam Home (S19); while paused, the TV says Resume and the kiosk has no rule (S20); Amber is green on her ticket and teal on her key tag (S21); the door is a swing on the kiosk and a thumb-turn on the TV (S14).

### 2. "Jellyfin is down" (JamFin → phone → Callsheet → Jam-Dash → JamFin) · 10 steps
Marissa's JamFin shows the **offline marquee** (broken ring, "Not answering", orange Try again) → a **push** on Isaac's phone (drawn as Jam-Dash, because nobody owns it) → or Callsheet's **red alert cue** whose key opens Jam-Dash → **Jam-Dash phone**: dashed "Not answering" legend, offline tag, orange "Try nas again" → **Jam-Dash desk**: ghost modules and five dashed amber cords → **fixed**: dark board, grey "nas · Fixed 21:58" → back to JamFin, which simply works again.

- **Same family:** offline is a broken form wherever it's drawn (ring, dashed legend, dashed stub, dashed cords); every failure ends in Try again + a way out; one loud thing per screen; the type pair.
- **Where it jars:** one outage is orange-offline on the TV and in Jam-Dash but red-alert in Callsheet (S7); nobody owns the urgent push (S8); Marissa can't tell anyone knows (S9); the fix is invisible on the TV (S10); Callsheet's red key only opens another app (S11); 9:46 PM on the TV, 21:46 on the phone (S5).

### 3. Game night (Lobby → NervOS → Lobby) · 12 steps
Lobby's dial on the PLAY band (Moonlight, Steam Link) → the **patch bay** with NervOS on HDMI 1 (assumed, see S18) → Lobby's blind for the input → NervOS **console** (Continue orange and focused) → **Pick up a controller** → **the cartridge goes in** (16 slats) → NervOS's **Guide band** → someone presses the TV remote's menu key: **Lobby's drawer over NervOS** → **return card** → Lobby home, whose shelf doesn't know what was just played.

- **Same family:** cream focus all the way (socket ring, base window, lit port, band slot); orange on every NervOS screen and none on Lobby's home; walnut as furniture in both; ribs only on dark surfaces; both covers fill slats with the real load and let Back cancel.
- **Where it jars:** Lobby and Jam Home disagree about what's on HDMI 1 (S18); 7:41 PM then 19:41 on the same TV (S5); two more covers (S1) and 12 slats then 16 (S2); two system menus on one screen from two controllers (S16); Lobby's Continue doesn't show the game (S17).

### 4. Morning and a parcel (Callsheet → Jam Home → Callsheet) · 10 steps
06:34 **lock-screen push** → Callsheet's **day sheet** (Copy draft orange) → 10:05 **Agenda**: the parcel row "needs a signature" with a plain link key → Jam Home phone **House tab** → the door's **bottom sheet** (Unlock orange) → **unlocked: the phone turns red** → locked again (no past form) → back in Callsheet, the parcel row hasn't moved.

- **Same family:** light, calm, warm grounds with one ink; the type pair; orange is the one thing and moves on (Copy draft, then Unlock); walnut trim and key rail; pressed-in for chosen.
- **Where it jars:** a house action has no cue slot in Callsheet (S24) and the link key has no defined form (S11); unlit windows are hollow on Callsheet's light sheet and dark dots on Jam Home's light plates (S22); a deliberate daytime unlock turns the phone red (S12); no past form for the door anywhere (S25); Callsheet doesn't hear that the parcel came (S23).

### 5. The front door at night (Lobby · Jam Home Echo · Callsheet) · 5 steps
One state on three screens at once: Lobby's thumb-turn becomes the **red key** with the sign "The front door is unlocked"; the kitchen Echo's **door swing opens in red** with a red Lock key; Callsheet's **red alert cue** with "Lock it in Jam Home". Then a three-up comparison, then the three-up after locking from the kitchen.

- **Same family:** the red key is the same idea on all three (solid red, dark text, nothing else orange). This is the strongest shared thing in the family. A round LED for status on all three. The type pair and walnut on every screen. Each draws the door its own way and is still readable as "the door, open" in a second.
- **Where it jars:** three words, three sentences and three action labels for one state (S13); the door drawn as a thumb-turn and a swing (S14); Callsheet's red key only opens Jam Home (S11); 10:48 PM vs 22:48 (S5); only Callsheet keeps a past form after the fix (S25).

| | TV · Lobby | Kitchen kiosk · Jam Home | Phone · Callsheet |
|---|---|---|---|
| Object | Thumb-turn, bar upright | Door swing, open in red | Ringed red LED and a red rule |
| Word | Unlocked · OK locks | Unlocked | Alert |
| Sentence | Unlocked at 10:48 PM at the door | — | Unlocked for 4 minutes |
| Key | Red unit + sign "Lock it" | Red "Lock" | Red "Lock it in Jam Home" (opens the app) |
| Time | 10:48 PM | — | 22:48 |

### 6. Overnight, in the past tense (phone → Jam-Dash → Callsheet) · 5 steps
01:50 push → Jam-Dash's **red key** "Restart Crafty" → grey **"Crafty · Fixed 01:53"** → the 06:35 sheet's **Worth knowing**: "Crafty stopped answering at 01:49 and you restarted it at 01:53. Nothing was lost.³"

- **Same family:** red alert then a quiet grey past form that stays put; both 24-hour (the one pair of apps that agree on the clock); the morning sheet quotes the owner with a footnote instead of re-grading it. This is the model for how state should travel.
- **Where it jars:** who sends the push (S8); "Fixed 01:53" on a tag and prose in the sheet, with no shared vocabulary (S25).

---

## What carries, in short

- **Holds everywhere:** the type pair (one exception: the product names themselves drift, S4); the red alert key; "one orange per screen, none at rest"; walnut as one colour in many shapes; offline as a broken form. Grounds, objects and layout change at every handoff and **never** jarred on their own. The bespoke half works.
- **Holds, but drawn differently enough to notice:** cream focus (plaque slot, needle, socket ring, window under art with a spill, base window); the slatted bar (12 recessed / 16 faint / 16 recessed).
- **Breaks:** **state words and severity across apps** (S7, S13, S25), **the clock** (S5), and **anything that has to cross a device boundary**: pushes, "seen", "fixed", Continue lists, the parcel, the inventory. The language is defined per screen; nothing yet says who owns a fact when two screens show it.

---

## Seams to fix

Severity is what it costs someone moving between screens. Tier per `RULES-TIERS.md`.

| # | Seam | Apps | Journeys | Severity | Proposed fix | Rule / tier |
|---|---|---|---|---|---|---|
| S1 | Launch covers differ in one evening (blind, house lights + colour block, media drop) | L, JF, NV | 1, 3 | Medium | Keep each cover (conflict 4 B); make everything around it identical: opaque layer, max(load, floor), B cancels, Calm fade, the same bar (S2) | TV4 → Device: TV (form App-local) |
| S2 | Slatted bar drawn three ways (12 recessed; 16 faint + "LOADING"; 16 recessed, centred) | L, JF, NV | 1, 3 | Medium | One component: 16 slats, each an indicator window, left-aligned under the title, "Loading → Ready" in Plex Mono at its end; also for Jam-Dash's bench download | MO9 → Language (component) |
| S3 | Two covers back to back (Lobby's blind with a 600 ms floor, then JamFin's card) | L, JF | 1 | Low | When the target app has its own cover, Lobby's blind holds only to the app's first frame | TV4 → Device: TV |
| S4 | Names drift: Jamfin / JamFin; Nerv//OS / NerveOS / NervOS | L, JF, HA, NV | 1, 3 | Low | Glossary entry per product, spelled as it spells itself | H18 → Language |
| S5 | Clock format: 12-hour (L, JF, HA) vs 24-hour (NV, CS, JD), even on one TV | All | 2, 3, 5 | Medium | One household clock setting; logs, tapes and 7-segment may stay 24-hour | New → Language (CW) |
| S6 | JamFin's baked warm spill under focus; others flat | JF | 1 | Low | Drop the spill (IN3), or name it JamFin's one exception | IN3, TV1 → Language |
| S7 | One outage, three severities: offline (JF), alert (CS), offline + warn (JD) | JF, CS, JD | 2 | **High** | The owning app sets state, word and severity; others quote it and draw the same form. Callsheet uses its offline cue for an offline server | CW2, CL6 → Language (new: one owner per state) |
| S8 | No app owns urgent pushes | JD, CS | 2, 6 | Medium | The owner app pushes once, with the state word as the title; Callsheet mentions it next sheet, past tense, footnoted | LY16 → Language |
| S9 | A housemate can't see that anyone knows | JF, JD, CS | 2 | Medium | "Seen 21:49 · Isaac" travels to every app showing the state | IN13 → Language |
| S10 | Recovery is silent on the TV | JF | 2 | Low | "Back since 21:58" in the marquee eyebrow once | App-local (JF) |
| S11 | Red keys that only open another app; no form for a cross-app link | CS | 2, 4, 5 | Medium | Link key names the app and ends in ↗; red only if one press lands on the fix, else neutral with the red on the cue | CL6 amended → Language |
| S12 | A deliberate daytime unlock turns the phone red | HA, L | 4, 5 | Medium | Conflict 12 B: warn by day, alert after sunset or nobody home, never alert for 10 min after an unlock from a family device | CW8 → Language (Isaac's call) |
| S13 | The unlocked door worded three ways | L, HA, CS | 5 | Medium | Jam Home owns the three lengths ("Unlocked" / "Unlocked at 10:48 PM at the front door" / "Lock"); others quote them | CW2 → Language |
| S14 | Door drawn twice (thumb-turn vs swing) | L, HA | 1, 5 | Medium | Conflict 9 B: Jam Home owns the drawings of house objects | Conflict 9 → Language |
| S15 | Lamps drawn twice, "20" vs "On · 20%" | L, HA | 1 | Medium | As S14, plus one level form "On · 20%" | Conflict 9, CT4 → Language |
| S16 | Two system menus on one screen (Lobby's drawer over NervOS's band) | L, NV | 3 | Medium | One owner per key row: Lobby's drawer over an input shows only TV keys and names what's under it; NervOS's band only game keys | TV5 → Device: TV |
| S17 | Lobby's Continue doesn't know NervOS's game | L, NV, JF | 3 | Medium | Each app publishes its in-progress item; Lobby shows it as a frame that switches input and lands on Continue | New → Device: TV |
| S18 | What's on HDMI 1 is disputed (Lobby: empty; Jam Home: "Nerv//OS") | L, HA, NV | 3 | **High** | One inventory from Home Assistant (via Control Freak) for every app | H17 → Language |
| S19 | "House lights" = the screen (JF) and the lamps (HA) | JF, HA | 1 | Low | Rename in the glossary, or make Play dim the real room (Q6) | H18 → Language |
| S20 | No agreed orange in the room while the film is paused | JF, HA | 1 | Low | Paused counts as playing on the kiosk; Goodnight takes the orange only once the TV is off | CL5 → App-local (HA) |
| S21 | People's colours differ (HA key tags vs JF tickets) | HA, JF | 1 | Low | One printed colour per person, owned by HA's key tags | CL13, H15 → Language |
| S22 | Unlit windows on light grounds: hollow (CS) vs dark dot (HA) | CS, HA | 4 | Medium | Settle conflict 3 by ground, as recommended in RULES-TIERS | Conflict 3 → Language |
| S23 | Callsheet doesn't hear the house (the parcel) | CS, HA | 4 | Low | Callsheet reads HA's door log for rows it printed and gives them a past form | App-local (CS) |
| S24 | House actions have no cue slot in Callsheet | CS | 4 | Low | A row with a link key, never a cue, never orange in Callsheet | LY7 → Language |
| S25 | Past forms differ or are missing (Fixed tags, Seen, prose, none) | All | 2, 4, 5, 6 | Medium | One vocabulary (Seen / Fixed / Locked / Back + time + who), shown by the owner ≥ 10 min and quoted by any app that showed the state | IN13, CW2 → Language |
| S26 | Key shapes change at every handoff; only the orange fill is constant | All | all | Low | **Accept** (CT2). Listed so nobody "fixes" it | CT2 → App-local |

Two High, fourteen Medium, ten Low. Both Highs are about facts, not looks.

---

## Bible implications

1. **Add a "Handoffs" section.** The six threads (cream focus, one orange, state words, slatted bar, walnut, type pair) must survive every move between apps. Grounds, objects and layout may change, and are expected to.
2. **Every state has one owner app.** Servers: Jam-Dash. House (doors, lamps, people, inputs): Jam Home. Media progress: JamFin. Games: NervOS. The TV itself: Lobby. The day: Callsheet. The owner sets the word, the form and the severity; other apps quote them and never re-grade (S7, S13).
3. **Past forms travel.** One vocabulary (Seen / Fixed / Locked / Back + time + who), shown by the owner and quoted by every app that showed the state (S9, S10, S25). IN13 moves from per-app to cross-app.
4. **Notices have one sender:** the owner, once. Callsheet reports, it doesn't re-push (S8).
5. **A cross-app link key** names the destination app and ends in ↗. It may be red only if one press lands on the fix; otherwise it's neutral (S11). CL6 gets this amendment.
6. **The slatted bar becomes one component** (16 recessed slats, placement, Loading → Ready), not just "a slatted bar". The covers around it stay app-local (S1, S2). Conflict 4 → option B.
7. **Shared house objects are drawn by Jam Home** and reused by Lobby (door, lamps), with one level form "On · 20%" (S14, S15). Conflict 9 → option B.
8. **One household clock format** on every screen (S5).
9. **One inventory.** Inputs, devices and people come from Home Assistant; a drawing that states a fact about the house must use it (S18, S21). H17 becomes Language.
10. **One orange per room, not just per screen:** screens facing the same people never ask for two different next actions at once (S20).
11. **On the TV, one owner per key row:** the TV remote's menu is the TV's; the gamepad's Guide is the app's (S16). Conflict 10 → option B.
12. **A Continue contract on the TV:** each app publishes its in-progress item and Lobby's shelf shows it (S17).
13. **Glossary:** product names as spelled by each product; "house lights", "offline / not answering / down", "Lock" (S4, S19).
14. **Key shapes stay app-local** (S26). The orange fill, press-in and one-per-screen are what carry.

---

## Questions for Isaac

1. **Is NervOS (the Aero) on the living-room TV, and on which HDMI port?** Jam Home lists "Nerv//OS" as an input; Lobby's README and pass 4 show HDMI 1 and 3 empty.
   *Recommendation:* tell us the port. Then make Home Assistant's input list the one source that Lobby's patch bay draws from.
2. **12-hour or 24-hour, one setting for the whole house?** Today the TV shows 7:41 PM in Lobby and 19:41 in NervOS a minute later.
   *Recommendation:* one household setting. Default to 12-hour (what the TV and kiosks already use), with 24-hour kept in logs and tapes.
3. **When a server goes offline, is it an alert on your phone, or offline everywhere?**
   *Recommendation:* offline everywhere (dashed form, orange "Try again" or "Open Jam-Dash ↗"). Red only when data is at risk or something is down that won't come back by itself, as with Crafty.
4. **Should the TV tell a housemate that you've seen an outage?** ("Seen 21:49 · Isaac" on JamFin's marquee.)
   *Recommendation:* yes: name and time, once, and "Back since 21:58" when it's fixed.
5. **The front door unlocked on purpose by day: red, or amber?**
   *Recommendation:* amber "Unlocked ▲" by day, red after sunset or when nobody's home, and never red for the first 10 minutes after you unlock it from a family device (conflict 12 B).
6. **Should JamFin's Play also dim the real living-room lamps?**
   *Recommendation:* yes, as a per-profile setting that's off by default. It runs only when no scene is already on, and it uses the Movie scene, so the TV and kiosk agree on what "house lights" means.
7. **Should Lobby's shelf show the game in NervOS's console?**
   *Recommendation:* yes, as a frame ("Glass Dragon · NervOS · HDMI 1"). OK switches input and lands on Continue.
8. **Different launch covers per app (blind, house lights, media drop), with one shared slatted bar?**
   *Recommendation:* yes. Each app gets its moment, and the bar (same slats, same place, same words) is the family's. Lobby's blind should skip its 600 ms floor when the app it opens has its own cover.
9. **Who sends urgent pushes?**
   *Recommendation:* the app that owns the state (Jam-Dash for servers, Jam Home for the house), once, with the state word as the title. Callsheet reports it in the next sheet instead of re-pushing.

---

## Audit

Checked with Playwright (Chromium, `chromium.launch()` with no options) at 1500 × 1000 (light) over every step of all six journeys (56 steps, calm motion), and at 390 × 844 in the dark and light schemes.
- **No JS or console errors.**
- **Smallest TV text: 22 px** at 1080p scale, across every TV frame on every step.
- **No horizontal page scroll at 390** (scrollWidth 390 in both schemes, checked on four steps). The seams table scrolls inside its own container.
- **Nothing outside its device**, except two intended cases: Lobby's peeking sixth Continue frame, and the kiosk clocks' line box (the glyphs are inside the screen).
- **Only Google Fonts load from outside.**

The fix pass corrected:
- Callsheet's Agenda rows collapsing into the rail column;
- Jam Home's key rail drawn behind its plate;
- dark labels on a dimly lit room;
- JamFin's "LOADING" over the slats;
- clipped spine titles in NervOS;
- the NervOS cartridge sitting too high in the slot;
- the day arc's temperature overlapping the sun;
- the Jam Home phone's door plate clipping its labels.

| # | Problem | Severity |
|---|---|---|
| 1 | Frames are redrawn in fewer parts than pass 4, so small details (hover states, choosers, every row) are missing. A seam that only shows in those details won't appear here. | Medium |
| 2 | HDMI 1 = NervOS is an assumption (Q1). The game-night journey depends on it. | Medium |
| 3 | The Jam Home plan is still a placeholder, as in pass 4. | Low |
| 4 | Pushes are drawn in the phone's own style as a stand-in, not as a design. | Low |
| 5 | The journeys show handoffs at the scale of a screen, not of a room. Glare, brightness jumps between the TV and the kiosk, and sound weren't measured. | Low |
