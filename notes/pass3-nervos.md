# NervOS · Pass 3 (final)

Mockup: `mockups/pass3/nervos.html`. Passes 1 and 2 are unchanged.

**Tour.** Press **▶ Tour** above the TV. It steps through 26 key states, about 2.8 s each, and names each one under the TV. Any key on the TV, or any Jump button, stops it.

**Keys** (click the TV first):

| Key | Does |
|---|---|
| Arrow keys | Move |
| Enter | A / OK. A tap and a 1 s hold are different. |
| Esc or Backspace | B / Back |
| G | Guide |
| M | ≡ Menu: options on a card, Power on the top band |
| V | Hold ⧉ + ≡ (the Steam fallback) |
| [ and ] | L1 / R1 |
| Letters and digits on the keyboard screen | Type straight in |

The pad buttons do the same, and a small key legend sits under the TV.

**Page controls:**
- Lighting, Motion and Covers.
- **Hints for:** Gamepad (A / B) or Remote (OK / Back).
- **Guide in Steam games:** Steam keeps it, or NervOS gets it.
- A dashed box labelled "Alternative for Isaac to judge · section names" switches between the approved names and plain words.
- Jump buttons to 13 states.

Everything shown is made up: games, covers, films, computers, room codes and player names (Sam, Riley, Jo, Ana).

## What changed since pass 2

**The four asks for this pass:**

| Pass 2 item | Pass 3 |
|---|---|
| Audit 2: the slot shelf covered **51%** of the paused picture (Medium) | **The chooser now sits inside the band.**<ul><li>Save and Load (↑ from the tray), and Chapters in a film, swap the band's key row for a row of four picture cards (421 × 100, picture 156 × 88).</li><li>The band stays **230 px, which covers 21.3%** of the screen (measured), so 79% of the paused picture stays visible.</li><li>The band's header line names the job: "Save to a slot · The paused picture above is what gets saved".</li><li>Replacing a filled slot reads "Replace slot 1? · Press A again".</li></ul> |
| Audit 3: Home had no accent with Full colour covers (Medium) | **The accent has a fixed place.**<ul><li>Colour bars sit in a strip right of the sign and below the band: x ≥ 1344, y 150–234 at 1080p. That strip is never art and never navigation.</li><li>The sign is capped at 1100 px wide so it can't reach the strip.</li><li>The bars show with Toned covers and with Full colour (at 82% opacity, one step quieter).</li><li>Only a toast replaces them: toasts now live in that strip, and it holds one thing at a time (D62).</li><li>No accent on running content, the Guide band or the player. The title card's Stripes are its accent.</li></ul> |
| Audit 4: the Guide band in Steam games may not be buildable (Medium) | **Steam-safe fallback.**<ul><li>A page switch says who gets the Guide button.</li><li>**Steam keeps it** (the likely case under gamescope): Guide opens Steam's own menu, drawn as a labelled stand-in, because NervOS can't draw there. The house band opens from a **1 s hold of ⧉ + ≡** (View + Menu), from Guide on the HA remote, or from the keyboard. Exit game in Steam's menu returns through the normal return card.</li><li>The game page, the launch card's sub-line ("Starting Steam · hold ⧉ + ≡ for the house menu") and the first toast in the game all say so.</li><li>**NervOS gets it:** the same band as pass 2.</li></ul> |
| TV launcher alignment (new) | One grammar with the TV launcher, pass 2. See "One TV grammar" below. |

**The other pass 2 audit items:**

| Pass 2 audit | Pass 3 |
|---|---|
| 1 Approved names vs friendliness (Medium) | Archive · Hangar · Uplink · Theater stay. The **current** section now shows a 22 px plain sub-label under its name ("Retro games", "Steam games", "Streams and netplay", "Films"). The sign explains the section when the top band has focus. The plain-words switch remains a labelled alternative, and with plain words the sub-label is dropped. |
| 5 Quit for Steam / Disconnect for streams | Unchanged in the design. Still an engineering question (see Audit 7). |
| 6 The bookend relies on key repeat being flagged | **Gone.** The carousel now stops at the ends like every row, so no repeat flag is needed. |
| 7 Press-twice for everyone | Kept for Reset, Quit, Stop, Disconnect, Restart, Shut down and Desktop mode. Replacing a slot is press-twice only. |
| 8 Unlit windows read as a row of black dashes | An unlit window is now a quiet recess, one step darker than its face, with no rim. A lit window is cream with a 2 px dark rim (launcher pass 2 suggestion, D17). Tab windows show only when lit (D91). |
| 10 Empty lower left on the game page | It now holds one line on what Guide does in this game ("Guide pauses it and opens the menu to save, load or quit. B does nothing in a game…"). For Steam games, it gives the fallback instead. |
| 12 Missing screens | All drawn (see Design): the Theater player band, a netplay room, Signal lost, Settings, Power, the on-screen keyboard, boot, and the return / cancel. **Not drawn:** attract and first run. |
| 9, 11, 13 | No eyebrow on Home, double titles on some covers, GPU not measured: accepted as they are, see Audit. |

**One TV grammar with the TV launcher (pass 2).** Where the two apps differed, I picked one:

| Point | NervOS pass 2 | Launcher pass 2 | Pass 3 (both) | Why |
|---|---|---|---|---|
| Guide band | 236 px; 45% veil when paused, 20% when running | 230 px, no veil | **230 px, opaque, no veil.** Paused vs running is shown only by the slot light and its word. | A veil going on and off is two large luminance changes. It also falsifies the Picture-filter preview, which the launcher already found with picture modes. |
| Value keys in the band | One line, "Picture Sharp" | Two lines, label over value | **Value keys are two lines; action keys one line** | Long values (Subtitles · English) fit, and the key says what it is. |
| A chooser's key | The value is hidden | Shows ▲ | **▲** | It says which key the open list belongs to, and keeps the value once (D56). |
| Picture choosers | Popped above the band (51%) | — | **Inside the band, in place of the key row** | It keeps the paused picture visible. |
| Ends of rows | The group carousel wraps behind a bookend | Rows stop at a walnut mark | **Everything stops** at the walnut mark, with a nudge and "n of N" on the focused row only. The carousel shows a "Start" or "End" mark in its peek slot. | One rule is easier to learn than two. It also removes the key-repeat special case. With 8 systems, the far end is at most 7 presses away. |
| Preview rest | 450 ms | 500 ms | **500 ms** | One number; the launcher's is the measured one. |
| Focus edges | Tabs and band keys on the bottom; lists and action keys on the leading edge | Tiles and keys on the bottom; lists on the leading edge | **Row things light the bottom edge; column things light the leading edge.** Holds fill the top edge. | The same split, now stated as one rule. |
| ≡ / Menu | Power (README: "B/Menu for power") | Options for the focused tile | **≡ = options for the focused thing.** On the top band, ≡ or B opens Power. | One meaning per button across the two TV apps. B at the top still reaches Power, as NervOS does today. |
| Button names | A / B | OK / Back | **The hints follow the last-used input**, and so does "Press A again" vs "Press OK again". | The HA remote can drive NervOS; a guest with the remote shouldn't read "A". |
| Error screen | RETRY / back | Try again + Home | **Try again + Home** (D63) | House words. |
| Toasts | Top right, below the band | The accent's clear zone | **The accent's clear zone**; the accent steps aside (D62) | It removes the toast-over-accent clash. |
| System opens | The shutter for everything | System apps may skip it | Settings and Power open with the screen fade, not the shutter. | Shutters are for content. |

## Research
I ran four web searches (standard mode) to fill gaps only. Lines marked *(knowledge)* come from my own knowledge.

- **Who gets Guide under gamescope.**
  - A Bazzite user reports that in Gaming Mode, Guide and Ctrl-1/Ctrl-2 opened nothing while a game ran, while Desktop Mode's overlay worked ([Universal Blue forum](https://universal-blue.discourse.group/t/any-way-to-get-the-overlay-in-gaming-mode-while-in-game-ctrl-1-ctrl-2-or-guide-button-not-working/1018)).
  - Valve issue #8513: non-Steam games don't take focus in a gamescope session ([GitHub](https://github.com/ValveSoftware/steam-for-linux/issues/8513)).
  - A 2016 Steam thread: Guide switches focus to Steam, and holding it opens Big Picture ([Steam Community](https://steamcommunity.com/discussions/forum/10/412446292772822343)).
  - *Lesson:* NervOS can't count on the Guide press. The house band needs a second door that Steam doesn't own, and the screen must say where that door is.
- **Steam Deck on-screen keyboard.**
  - 2022 updates added dual-trackpad typing, moved input to click-down for accuracy, and added layouts ([GamingOnLinux](https://www.gamingonlinux.com/2022/04/steam-deck-gets-a-bunch-more-keyboard-tweaks), [GamingOnLinux](https://gamingonlinux.com/2022/09/valve-finally-fixes-up-the-steam-deck-on-screen-keyboard-some-more)).
  - Users found switching between trackpads and face buttons for delete and space awkward, and asked to remap them ([Steam Community](https://steamcommunity.com/app/1675200/discussions/2/3395175706741961527)).
  - *(knowledge)* Xbox's and Steam Big Picture's pad keyboards map X to delete and Y to space.
  - *Lesson:* print X / Y / ≡ in the hints, keep the grid fixed, and jump focus to Done when the entry is full.
- **Moonlight.** The release notes list fixes for an "immediate connection termination" over some connections and better reliability through short network drops. They recommend Ethernet to the host and 5 GHz to the client ([F-Droid](https://f-droid.org/packages/com.limelight/)).
  - *Lesson:* a lost stream is common and usually a sleeping host or a network blip. Signal lost says which it probably is, and what to do.
- **Jellyfin on TV.** A forum feature request says the TV app can't turn subtitles off until playback starts. The v0.19 release brought a new player UI ([Jellyfin forum](https://forum.jellyfin.org/t-is-there-an-android-tv-player-that-just-works), [release notes](https://newreleases.io/project/github/jellyfin/jellyfin-androidtv/release/v0.19.0)).
  - *Lesson:* Subtitles and Audio get a default in Settings › Films, plus value keys in the player band.
- *(knowledge)* Console power menus (PS5, Xbox) are short lists with no primary. On Switch you hold the power button to get the full power options.
  - *Lesson:* a power list with no orange, focus on the safe choice, and a hold for the destructive ones.

## Design (what and why)
All sizes are at 1080p. Text is 22 px at the smallest (labels 22–24, body 26–28, titles 46–92). The safe area is 96 / 54 px.

**Home.**
- The band is 132 px. The current section shows its sub-label under its name. On the right are the controller LED with "Controller 72%" and the clock.
- The sign is a title + one line, up to 1100 px wide. The accent sits in its fixed strip to the right.
- Rows are 318 px apart (Continue, Collections, Systems), about 2.5 rows at rest, as in pass 2.
- Ordinary rows end with a walnut mark. The systems carousel shows "Start" or "End" marks in its peek slot.
- **≡ on a game card** pops the shared dark sheet below the card, or above it near the bottom: "Continue from Tuesday 21:40" (orange, D18), Favourite (square + On), and "Go to Super Nintendo".

**Shelf and game page.** These are as in pass 2, with three changes:
- The preview waits 500 ms.
- The hints include ≡ Options.
- The game page has a guest line about Guide (or the Steam fallback).

**Launch, cancel and return.**
- **Launch:** the title card holds max(load, 600 ms), then opens in 300 ms.
- **Cancel:** **B during the card** sends the halves back the way they came, with "Cancelled" and a toast "Didn't start Glass Dragon".
- **Return:** quitting closes the shutter over the last frame. It reads "Back from · GLASS DRAGON · Played 42 min · resume point saved", holds for about 1 s, then opens on the page you launched from.
- Films say "Stopped · At 1:12:04 · it resumes from here". Streams say "Disconnected".

**Guide band (230 px, one shape).**
- **Header line:** a state slot (unlit + "Paused", or lit + "Running" / "Streaming"), the title, the context, zone hints and the clock.
- **Retro keys:** Resume (orange) · [Save · Load · Slot 2] tray · Picture / Sharp pixels · Reset · Quit game.
- **Steam keys:** Resume · Steam menu · Quit game.
- **Stream keys:** Resume · Stream menu · Disconnect.
- Holds are 1 s, or press twice within 3 s. The fill runs along the top edge, and the armed label reads "Press A again to quit".

**Theater player** (the band in a film):
- A or Guide pauses the film and opens the band.
- The band's **top edge is the timeline**: 10 px, cream for what's played and walnut for the rest. The header shows "1:12:04 · Ends at 21:58" (the position is the bar's own readout, D25; the end time is a different value, D15).
- **Keys:** Play (orange) · Back 10 s · Forward 30 s · Subtitles / English · Audio / English 5.1 · Chapters · Stop film.
- Subtitles and Audio pop text lists above their keys.
- Chapters is a picture chooser inside the band: eight chapters, four visible, "3 of 8", with a lit square on the current chapter.

**Netplay room** (Uplink › Netplay rooms › a room, or "Join with a code"):
- **Left:** the eyebrow, the game, facts (system · players · "Hosted by Sam"), then **seats as slot lights** ("Player 1 · Sam (host)", "Player 2 · Free seat" as an empty recess), then a state line with an LED and word.
- **Keys:** Take seat 2 (orange) · Watch only · Leave room. Then I'm ready (orange) · Leave room. Then "Waiting for Sam to start" (amber) with Not ready yet · Leave room.
- The host starts the game, and the title card reads "Netplay · with Sam".
- **Right:** the cover, a mono "ROOM MOON42" chip, "Connection good · 18 ms", and one plain line about how netplay waits instead of skipping.

**On-screen keyboard.**
- The header: "Room code" with one line of instruction.
- A recessed field shows the text in mono capitals, a steady caret (no blink: continuous motion is out) and "4 of 6".
- A 12-unit grid of 84 px keys: digits + Delete, letters + . / @ : - , ? _, Shift (pressed in = capitals), and Clear · Space · Cancel · **Done** (the one orange).
- When the sixth character goes in, focus jumps to Done. A physical keyboard types straight in.
- The hints print A Type · X Delete · Y Space · ≡ Done · B Cancel.

**Signal lost.**
- An opaque full-bleed screen (floor 7).
- **Text:** an offline LED + "Offline" · "Uplink · Study PC", then "Lost the picture from Study PC", then "It stopped answering 8 seconds ago. It may have gone to sleep or dropped off the network.", then in bold "Wake it from Jam Home, then try again."
- **Keys:** Try again (orange) · Home, with a small mono code at the bottom ("NV-204 · stream timed out").
- An offline host reached from Home gets "Can't reach Laptop".

**Settings.**
- A slim band, then a rail of six pages, each with its value under its name: Display, Library, Steam, Streaming, Films, Netplay.
- The pane has a heading, a lead line and rows (label + help line, value at the right).
- **Display** rows:
  - Look (Braun Hi-Fi / NERVOS / Cut-out / Choose your hero / VHS).
  - Lighting, with a 500 ms preview on the real TV; Back reverts in one change.
  - Covers.
  - Calm motion (square window + On/Off).
  - Button hints.
  - Film layer, dim and "Off": "Only in NERVOS, Cut-out, Hero and VHS".
  - Picture output.
- **Steam** holds "Guide button in Steam games", which drives the same switch as the page control.
- Choosers pop beside the list, over the rail.

**Power.**
- B or ≡ on the top band pops the dark sheet below the band, top right.
- **Rows:** Sleep · Restart · Shut down · Desktop mode · Settings · Cancel. Each has a one-line consequence ("Turns the computer off. The TV stays on.").
- **Focus starts on Cancel.** Nothing is orange. Restart, Shut down and Desktop mode take a hold or two presses; Sleep is one press, and any button wakes it.

**Boot.**
- 1.6 s, or 0.8 s in Calm, dark throughout.
- A walnut rule draws across (transform), "NervOS" fades in, then "Controller 72% · ready" with a green LED. Then the fade to Home.
- Any button skips.
- This is the Hi-Fi boot only. The approved looks keep their own (the NERVOS POST, the VHS tape).

## Audit
Checked with Playwright (Chromium, `chromium.launch()` with no options) at 1500 px wide and deviceScaleFactor 1.308, so the TV renders at about 1920 px. The script:
- ran all 26 Tour states (screenshots t01–t26) and a keyboard run (carousel end, Uplink, typing a code, joining a room, playing, holding Quit, the return);
- checked Day Home, the Day game page, the Day room, plain words and a 4-seat room;
- checked the page at 390 px in the dark scheme.

Screenshots are in the session scratch folder `p3nervos/shots/`, not in the repo.

**Results:**
- no JS errors and no console errors;
- **no visible TV text under 22 px** in any state;
- **no text outside the 96 / 54 safe area**, apart from cards peeking off an edge and the Steam stand-in;
- the Guide band covers **21.3%** of the screen in every state, choosers included;
- at 390 px, `scrollWidth` is 390.

**The fix pass corrected:**
- Subtitles and Audio reading "undefined" in the film band;
- the films' "Ends at" disagreeing between the card and the band (it's now computed from the position);
- "Press A again to replace" truncated on a slot card (it's now "Replace slot 1?" / "Press A again");
- seat labels wrapping in a 4-seat room (mono capitals became Jost);
- room codes showing lowercase keys (Shift now starts pressed in);
- focus not reaching Done after a full code;
- the outro's and launch's timers surviving a Tour jump;
- the Display page's eighth row (sounds, which aren't decided) colliding with the hints.

| # | Problem | Severity |
|---|---|---|
| 1 | **The Steam fallback chord is unverified.** Under gamescope, Steam Input may virtualise the pad, and NervOS may not see ⧉ + ≡ while a Steam game has focus. If so, the only ways back to the house band in a Steam game are the HA remote, the keyboard and Steam's own Exit game. It has to be tested on the Aero before rollout. | High |
| 2 | **A stopping carousel loses some of the carousel feel** Isaac approved (P4). Arcade → Super Nintendo is now 7 presses instead of 1. It's the right call for one grammar, but it's a change to an approved behaviour. | Medium |
| 3 | **Slot pictures are small** (156 × 88) at 3 m. The paused frame above the band is what you judge before saving; the slot pictures are only reminders for Load. A bigger picture would need a taller band. | Medium |
| 4 | **The accent next to full-colour covers** is still three colour sources near each other (bars, row 1 covers, orange). It's quieter at 82%, but the clash D19 describes isn't gone, only placed. | Medium |
| 5 | **≡ changes meaning for NervOS users**: Menu used to open Power; now it opens options on a card. B at the top band still opens Power, but muscle memory breaks once. | Medium |
| 6 | **Two player bands in the house.** NervOS's Theater band (mpv) and JamFin's player on the TV launcher draw the same shape with the same keys, but they're two implementations. They'll drift unless the bible names one component. | Medium |
| 7 | **Quit, Disconnect and Steam's Exit game** still assume NervOS can close the content cleanly. There's no "Closing…" state, and no fallback if a Steam game ignores the request (pass 2 #5, unchanged). | Medium |
| 8 | **Hints that follow the last input** need NervOS to know which device sent the last press (SDL3 pad vs MQTT remote vs keyboard). It's possible, but it's new plumbing, and the hint flips the moment someone touches the other device. | Low |
| 9 | **The return card adds about 1 s to every quit.** It masks the hand-back to the frontend like the title card does, but quitting to go to bed is now slower. | Low |
| 10 | **The 10 px timeline on the band's top edge** is thin at 3 m. The time in the header carries the exact value; the bar is for a glance. | Low |
| 11 | **The OSK is for short entries only**: no word prediction, no paste, no accented letters. That's fine for codes, PINs and names, but too weak for a Wi-Fi password, which belongs on the desktop. | Low |
| 12 | **Netplay shows other households' display names.** They're names people chose, not personal data, but they appear on our screen without moderation. Watch only isn't drawn. | Low |
| 13 | **Error codes (NV-201, NV-204) are invented.** NervOS has its own; the screen keeps one small mono line for them. | Low |
| 14 | **The Film layer row is listed but dead** in Hi-Fi. It's honest (it says why), but it's a focusable row that does nothing. | Low |
| 15 | **Not drawn:** attract (45 s idle), first run / pairing, Watch only, Library › Hidden games, and the Steam menu itself (a stand-in only). | Low |
| 16 | **GPU cost still not measured.** Nothing animates at rest except the clock; the band, choosers and accent are static. The return card adds one shutter pass per quit. | Low |

## Questions for Isaac
1. **Section names.** Keep Archive · Hangar · Uplink · Theater, with a plain sub-label under the current section? Or switch the band to Retro · Steam · Streaming · Films?
   *Recommendation:* keep the approved names with the sub-label. It costs one 22 px line, and guests learn the words in a day.
2. **Ends of rows and carousels.** Stop at a walnut mark everywhere, including the systems carousel (pass 3), or keep pass 2's wrap behind a "Start" bookend for group carousels only?
   *Recommendation:* stop everywhere. It's one rule shared with the TV launcher, and it removes the key-repeat special case.
3. **The ≡ / Menu button.** Make it "options for what's focused" (as on the TV launcher), with Power on B or ≡ from the top band?
   *Recommendation:* yes. It's one meaning per button on both TV apps.
4. **The Steam fallback.** Is holding ⧉ + ≡ for a second an acceptable way back to the house band when Steam keeps Guide? If testing shows Steam swallows it, accept "Guide on the HA remote, or Exit game in Steam's menu" as the only ways back?
   *Recommendation:* test on the Aero first, ship the chord if it works, and print the way back on the launch card either way.
5. **The Home accent with full-colour covers.** Always show it in the fixed strip (one step quieter, as drawn), or hide it whenever the covers are full colour?
   *Recommendation:* always show it. The fixed strip keeps it clear of art and navigation, and "one accent per screen" holds without an exception.
6. **One player band.** Should NervOS's Theater band and JamFin's TV player be one bible component (same keys, same timeline edge)?
   *Recommendation:* yes. Name it in the bible now; build it once at rollout.
7. **Boot length in Hi-Fi.** 1.6 s calm boot for Braun Hi-Fi only, with NERVOS, VHS, Hero and Cut-out keeping their approved boots?
   *Recommendation:* yes.
8. **The return card.** About 1 s of "Back from <game> · played 42 min" on every quit?
   *Recommendation:* keep it (it hides the hand-back flicker), but make it a fade with no hold in Calm.

## Bible implications (final form)
1. **One Guide band for every TV app.** Guide opens a 230 px bottom band at 1080p: opaque, ribbed, with a walnut top edge and **no veil** over the picture. Its header line holds a state slot + word (unlit "Paused", lit "Running"), the title, context, hints and the clock. Its keys are 100 px tall. It has at most one orange key (Resume / Play), or none when changes apply live. The launcher's TV menu and every in-content menu use this shape. (Settles D54/D35; replaces D77's veil.)
2. **Choosers by kind.** A text chooser pops above a bottom-band key, below a top band, or beside a vertical list (D57). A **picture chooser** (save slots, chapters) replaces the band's key row, and the band never grows.
3. **Focus edges.** Things laid out in a row light their bottom edge (base window). Things in a column light their leading edge. Hold-to-confirm fills the top edge.
4. **Unlit windows are quiet.** An unlit selector window is a recess one step darker than its face, with no rim. A lit window is flat cream with a dark rim. Tab bars draw only the lit window. (Refines §7, D17, D91.)
5. **Rows and carousels stop.** Every row and every carousel, groups included, stops at a walnut end mark. An extra press nudges (not in Calm), and "n of N" shows on the focused row only. Nothing wraps. (Confirms D59; replaces D75 and answers D32.)
6. **One preview rest: 500 ms.** Any full-screen or large preview waits until focus has rested 500 ms, and Back reverts it in one change. (D55; NervOS's 450 ms is retired.)
7. **A chooser's key shows ▲ while its chooser is open.** The chooser's lit square carries the value. Two keys that act on one value share a tray that names it once. (D56 + D76.)
8. **≡ means "options for what's focused".** On a top band, ≡ (and B) opens Power. Hold OK/A for 600 ms is an optional shortcut, never the only path. (D58.)
9. **Hints name the last-used input's buttons** (A / B on a gamepad, OK / Back on a remote), and armed labels follow ("Press OK again to quit").
10. **A second door to the house band.** When a third-party app owns Guide (Steam under gamescope), the band must still open another way: a 1 s chord (⧉ + ≡), the HA remote's Guide, or the keyboard. The launch card and the first toast in the app say how.
11. **The accent's fixed place on TV homes.** A strip right of the sign and below the band (x ≥ 1344, y 150–234 at 1080p), never art or navigation. It shows with full-colour covers one step quieter. Only a toast displaces it, and toasts live in that strip. No accent on running content, the Guide band or the player; the title card's Stripes are its accent. (Settles D19 / D22 / D62.)
12. **Error screens.** An offline LED + word, a title saying what happened, one line why, one bold line saying what to do, **Try again** (orange) + **Home**, and a small mono code at the bottom. (Extends D63.)
13. **Power on TV.** A sheet below the top band. Focus starts on Cancel, and nothing is orange. Each row has a one-line consequence. Restart, Shut down and Desktop take a 1 s hold or two presses; Sleep is one press. (D24 / D70.)
14. **TV keyboard.** A 12-unit grid of 84 px keys with **Done** as the one orange. X Delete, Y Space and ≡ Done are printed in the hints. The caret is steady, never blinking. Focus jumps to Done when a fixed-length entry is full. A physical keyboard types directly.
15. **Boot and return.** A boot is at most 1.6 s (0.8 s in Calm), dark throughout, and any button skips it. The return reuses the shutter ("Back from <title>" + time played, about 1 s) and opens where you launched from. B during a title card cancels the launch. System screens (Settings, Power) open with the screen fade, not the shutter. (Extends D60.)
16. **Settings rows on TV.** Each row has a label + one help line and the value at the right. On/off shows as a square window + word. Choosers pop beside the list. A row that doesn't apply to this look stays listed, dimmed, and says why.
17. **An app's own vocabulary.** An app may keep its approved section names on a shared screen when they're set in house type and the **current** section carries a plain 22 px sub-label. (D78, final form; Isaac decides between this and plain words.)
18. **One TV player band.** Films on any TV app use one band: Play (orange), Back 10 s, Forward 30 s, Subtitles, Audio, Chapters (a picture chooser) and Stop. The timeline is the band's top edge, and the header gives the position and "Ends at" (D15, D25).
