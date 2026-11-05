# TV launcher (Lobby) · Pass 3 of 3

Mockup: `mockups/pass3/tv-launcher.html`. The pass-1 and pass-2 mockups are unchanged.

**How to review it without a remote:** press **▶ Tour** above the TV. It steps through 21 states, about 4 s each, with a caption for each one. **Next step ›** moves one state at a time. Clicking the TV or pressing a key stops the tour and hands you the keyboard.

**Keys** (also printed in a legend on the page):
- Arrow keys move. Enter is OK: it acts on release, and holding it opens options or unlocks.
- Esc or Backspace is Back, and H is Home.
- G or Q opens the TV menu (Guide), I opens inputs, and M is ≡ options.

**Page controls:**
- Lighting: Night / Day. Motion: Full / Calm.
- App banners: Stand-in / Brand-strength, toned / Brand-strength, untoned.
- Home: Lived-in / First run. Switch 2: On / Asleep (switching it On from Asleep shows the device prompt).
- Netflix: Opens / Won't open. Lobby update: Up to date / 1.4 ready.
- Jump to: eight states.

Sources read:
- `notes/OVERNIGHT-BRIEF.md`, all of `CHANGES.md` (A, B, D1–D91), `BIBLE.md` §2–§9;
- `projects/lobby/README.md` and `PROPOSALS.md`;
- `notes/pass1-` and `pass2-tv-launcher.md`, `pass2-nervos.md`, `pass1-jamfin.md` (JamFin's pass 2 wasn't committed when I started), and the pass-2 Callsheet, Jam-Dash and HA notes for shared rules;
- `mockups/pass2/tv-launcher.html`, which this pass builds on.

All titles, art and banners are made up. The household's app names, lamps, front door, Switch 2 on HDMI 2 and the house name "Bungalo" come from the Lobby README.

## What changed since pass 2

**The pass-2 audit, item by item:**

| Pass-2 audit | Pass 3 |
|---|---|
| 1 Two ways to switch inputs on Home | **One way in on Home: the Inputs keys** in the bottom row. The band's Input key and source window are gone from Home. Over a picture, the TV menu's Input key is the way in, and that's the only place that marks a current input. |
| 2 "Current input" is fuzzy | **Defined honestly.** The TV is always on exactly one source. Lobby and every app share the TV's own source, which Lobby calls **Apps** ("Lobby and apps"). On Home, Apps is what's on screen, so no HDMI key presses in, and the Switch 2 key just says "HDMI 2 · Signal". The TV menu's header names what's underneath ("over The Copper City · Jamfin", "over Switch 2 · HDMI 2", "over Home"). Its Input chooser marks Apps, HDMI 2 or Antenna with the square. |
| 3 "Never twice" on Home (window + pressed key) | Gone with the window. |
| 4 Day windows read as black dashes | **An unlit window in Day is a shallow recess**: 14% black over its own surface, measured at 1.36:1 against the plinth. **A lit one is cream inside a 2 px dark rim** (D17): cream vs rim 13.8:1, rim vs plinth 11.0:1. Windows on black bands, sheets and the title card keep the night recess. The marks are still there (the window is always visible), but they no longer read as dashes. |
| 5 Live preview latency | Unchanged, and still unmeasured on the TV (audit 10). The mockup now filters only the picture layer, not Lobby's own UI. |
| 6 TV menu covers 21% | Unchanged (Low). |
| 7 Banner colours invented | Banners sit in a **6 px card-coloured surround**. At night they're **toned by a colour filter** (`saturate(.62) brightness(.74)`), never a blended rectangle. The new **Brand-strength** switch fills banners with made-up saturated fields (pure red, white, black, bright blue, yellow, green) to test the worst case. Measurements are in the Audit. |
| 8 Stripes too heavy next to art | **Stripes show only where no cover art is in view**: on the title card, on the first-run Home, and with Continue turned off. They're also hidden on failure screens (D22) and while a toast, prompt or menu needs the clear zone (D62). |
| 9 Hold OK changes OK's timing in All apps | **OK acts on release everywhere on the TV**, as Android's own views do. A short press means the same thing on every screen, and a hold never changes it. |
| 10 The move ring is new vocabulary | The ring is gone. A moving tile lifts higher between two arrows, and the hints name it ("Move YouTube"). |
| 11 Shutter for Android settings | **System screens** (Android settings, App info) **open with a plain 140 ms cut**, with no title card. |
| 12 Music in Continue opens a title card | **Music plays and pauses in place.** The card's slot lights, its line reads "House music · playing", and a toast confirms it, because the speakers are in another room. |
| 13 Missing states | Added: **first run**, **an app that won't open**, **update ready** (plus updating), and **a device turned on** (HDMI-CEC prompt). Lobby's **House group** is back (Floor lamp 40%, Table lamp, Mood lighting, Front door). **TV Day** is in the tour. Still not drawn: see audit 15. |
| 14 Real data | Still sample data (audit 16). |

**Shared rules that conflicted, and the one chosen for the TV:**

| Conflict | Chosen for the TV | Why |
|---|---|---|
| **The alert fix:** solid red key (D84, HA) vs alert ring + LED (pass-2 TV, D11-style) | **Solid red key with dark text (D84).** Focused, it takes D18's cue: a black label, a deeper under-edge and a lit window. | One form in every room means the family learns it once: kiosk, phone and TV draw the same thing. At 3 m a 4 px ring is a thin line, while a solid key is unmistakable. The red area is about 1% of the screen, far under the 25% saturated-red clause. Dark text measures 6.0:1, and 6.8:1 when focused. |
| **Carousel ends:** stop with an end mark (D59) vs wrap behind a "Start" bookend (D75) | **Stop, on every row on the TV** (Lobby, and JamFin on the same set). | Lobby's focus engine already stops (`lobby:edge`). The opening state (first Continue card) stays a landmark. A held key at 20/s can't whip round. A stop doesn't depend on key repeats being flagged, and NervOS's own audit 6 shows they often aren't. Both use the same walnut mark, so the vocabulary is still shared. I recommend D59 house-wide, with NervOS's systems carousel as the only wrap if Isaac wants one. |
| **Unlit windows:** "a window you can always see" (§3 rule 3) vs "tab bars draw only the lit window" (D91) | **TV cards and keys keep the window, toned per lighting.** D91 stays for phone and kiosk tab bars. | On a TV card the window is the selector's place, and keeping it there avoids layout jumps. Toning fixes the Day noise that D91 was solving. |
| **Non-hold path:** ≡ key (D58) vs the remote | **Press twice is the on-screen path.** ≡ stays as a shortcut where a remote has it. | The Lobby README lists the Hisense remote as D-pad only (arrows, OK, Back). A ≡ key can't be the only path (audit 3). |

## Research
I used WebSearch for 3 searches. Fetching full pages wasn't needed. Lines marked *(knowledge)* come from my own knowledge.

- **Android TV banners** (developer.android.com, "TV app icon design guidelines"): a banner is 16:9 and comes at five densities from 160×90 to 640×360, with 320×180 at xhdpi. The app's name text is part of the image, the logo stays inside a safe area, and borders are discouraged because they get cropped. So **Lobby's frame has to add the surround**, because a real banner can't be trusted to have one. The text is part of the banner, which is why the stand-ins print names.
- **Remote buttons on Google TV** (Android Central on Button Mapper; tvQuickActions; MX3 Button Mapper on F-Droid):
  - Google TV has no built-in way to remap buttons. Remappers catch keys through an **Accessibility Service**.
  - Button Mapper reports some functions not working on Google TV, and the YouTube button on Chromecast's remote can't be disabled.
  - **What this means for Lobby:** the TV menu over a film (D54) needs Lobby to run an accessibility service, and also an overlay permission to draw over another app *(knowledge: `SYSTEM_ALERT_WINDOW` / `TYPE_APPLICATION_OVERLAY`)*. A plain launcher only draws when it's in front.
- **The Hisense remote's own keys:** the search found only non-Google-TV Hisense manuals and a low-quality guide saying Hisense remotes generally have an Input (or Source) key. **The exact key set of Phoster's remote is unconfirmed.** The Lobby README says "D-pad only (arrows, OK, Back)", so the design can't rely on Guide or ≡.
- *(knowledge)* Android views perform a click on **key up** for DPAD_CENTER/ENTER, which is the basis for "OK acts on release".
- *(knowledge)* HDMI-CEC "One Touch Play" lets a device that wakes ask the TV to switch to it. Most TVs offer it as an on/off setting, which is where Lobby's Ask / Switch / Stay setting comes from.

## Design (what and why)

**Home (night):**
- **Band:** the house name, **TV menu** and **Settings**, then the clock, date and weather. There's no input window.
- **Sign:** an eyebrow, the title, one line, and the OK action on the same line.
- **Rows:**
  - **Continue:** art + plinth. Progress runs on the art's edge, the window sits on the plinth (D13).
  - **Apps:** banners in a 6 px surround.
  - **Inputs · House:** one row of 74 px keys in two labelled groups. **Inputs** has Switch 2 ("HDMI 2 · Signal" with an LED) and Live TV ("41 channels"). Empty ports are hidden by default; Settings › Inputs › Show empty inputs brings them back. **House** has Floor lamp 40%, Table lamp Off and Mood lighting On, each with a slot window filled in the lamp's own colour (D45), plus Front door (LED + Locked).
- **Everything fits in the safe area at once.** The House row is 89 of the 90 cqw available.
- **Focus:** the focused group's header shows "n of N", and the row stops at a walnut end mark (D59).
- **Lamps toggle in place with OK.** There's no toast, because the change is visible.
- **Front door:**
  - Hold OK for 1 s (the fill runs on the top edge, the window stays on the bottom, D31), or press twice within 3 s ("Press OK again").
  - **Unlocked** turns it into the solid red key with dark text. The sign reads "The front door is unlocked · Unlocked at 8:24 PM from this TV · OK Lock it", and one press locks it.
  - The same key is in the TV menu.
- **No accent on a Home with covers.**

**The TV menu (Guide) over anything:**
- The header shows a lit slot, "TV menu", **what's underneath**, hints and the clock.
- The keys are **Input** (the real source: Apps / Switch 2 / Live TV), Picture, Sound, Sound out, Sleep, Front door and Settings.
- The Input chooser lists **Apps · Lobby and apps**, Switch 2 · HDMI 2, HDMI 1, HDMI 3 and Live TV · Antenna, with LEDs and the square on the real source. OK on Apps from an HDMI input goes Home.
- Choosers anchor to the menu's resting height, so they never start below the safe line mid-slide (fixed this pass).
- The Picture preview waits 500 ms after you stop (D55).

**Launching:**
- **Films, shows, games, apps and inputs:** the flat shutter holds for max(load, 600 ms), then opens in 300 ms (D60).
- **System screens:** a 140 ms cut. **Music:** in place.
- **Calm:** a 140 ms fade.

**Failure layers all end the same way**: what happened, what to do, **Try again** (the one orange, with D18's focus) and **Home**. The slatted bar stops, and the Stripes step back.
- **No signal:** "No signal on HDMI 2. Turn on the Switch 2, then try again." An empty port says "Nothing is plugged into HDMI 1…".
- **An app that won't open:** the bar stops at about a third and dims. "Netflix didn't open. It stopped while starting. Try again. If it keeps happening, restart the TV from Settings › Sleep & power." Sleep & power gained **Restart the TV**, a press-twice row that is never orange (D24).

**A device turned on (HDMI-CEC):**
- When the Switch 2 wakes while Home is showing, one ribbed card drops into the clear zone: "HDMI 2 · just now", "● Switch 2 turned on", then **Switch to it** (orange) and **Stay on Home**.
- It takes focus. ←/→ choose, OK acts, and Back stays. It leaves on its own after 15 s and never repeats.
- Settings › Inputs › **When a device turns on: Ask / Switch to it / Stay here** (default Ask).
- If anything else is open, it becomes a toast instead.

**Update ready:**
- A **cream LED on the Settings key** in the band, and nothing pops up.
- Focused, the sign says "Lobby 1.4 is ready. It installs tonight, or now from About."
- **Settings › About** shows the LED and "Update ready" in the list. Its detail has the Lobby version ("1.3 · 1.4 is ready"), What's new, **Install Lobby updates overnight** (On), the TV, and **Update now** (the screen's one orange).
- Updating runs the same title card ("Lobby · 1.4", "Updating Lobby", "Installing. Home comes back on its own."). Home returns with the toast "Lobby is up to date · 1.4".
- Apps update themselves through the Play Store, and the About line says so.

**First run:**
- The sign: "Welcome · Hello. This is Lobby. Your apps, your inputs and the lamps, and nothing else. Start by choosing what's on Home."
- Continue is a **recess** with "Nothing to continue yet. Films, shows, games and music you start will wait here." and the one orange **Arrange Home**, which opens All apps. Focus starts on that key.
- Apps shows six defaults plus All apps. Inputs and House are as usual.
- **Stripes show**, because there's no art.

**All apps:** two groups (On Home in order / Not on Home).
- **Options:** Hold OK (600 ms) or ≡ → Open (orange) · Move · Remove / Add · App info.
- **Move:** the tile lifts between two arrows. OK puts it here, and Back puts it back.
- App info opens with the system cut.

**TV Day:**
- A mid-light ground (`#bdb9b1`), cards `#d3cfc7`, and the focused face `#e8e4dc`.
- The bands, sheets, the TV menu and the title card stay black, and keep night windows.
- The red alert key is the same in both lightings.

**Calm:** fades only, with no lifts, bumps, slide-in screens or shutters.

## Audit
Checked with Playwright (Chromium, `chromium.launch()` with no options). The page was 1500 px wide at deviceScaleFactor 1.31, so the TV renders at about 1920 px, and also 390 px wide in the dark scheme. What I ran:
- all 21 tour states, through `LOBBY.runStep`;
- a real-keyboard run:
  - the end of the Continue row (bump), then the end of the Apps row;
  - the Inputs · House row, and an Enter **held for 1.2 s** on the front door (unlock);
  - Enter to lock, then the band and Settings;
  - G for the TV menu over Home, and its Input chooser;
  - OK on the film, then playing, then I for inputs over the film, then H for Home with focus restored;
  - All apps with Enter held for 0.8 s (options), then opening an app and Back;
- the jumps: No signal, App won't open, Device turned on, First run and Settings.

That made 46 screenshots, kept in the scratch dir (not the repo). The tour also ran at 390 px. Script checks on every state:
- every visible TV text node is **≥ 22 px** at 1080p;
- hint text is **≥ 24 px**;
- no text sits outside the 96/54 px safe area, except on cards peeking past a row's edge;
- no JS errors and no console errors;
- `scrollWidth` is 390 at 390.

**All passed after the fix pass.**

Measured at rest, as the share of a 960×540 downsample of the TV:

| State | Glare (> 0.5 relative luminance) | Saturated red (linear R/(R+G+B) ≥ 0.8) |
|---|---|---|
| Home, night, stand-in banners | 1.2% | 0.0% |
| Home, night, brand-strength **toned** | 1.7% | 1.5% |
| Home, night, brand-strength **untoned** | 3.4% | 1.6% |
| First-run Home (Stripes) | 1.0% | 0.5% |
| Home, Day | 15.3% (no cap by day) | 0.0% |

Caps: glare 10% at night; saturated red 25%.

The fix pass corrected:
- a cancelled title card's timer clearing the *next* card, which crashed No signal after a quick retry (the only JS error);
- the Input chooser over a film measuring the TV menu while it was still sliding in, so its footer sat at y 1020–1054, below the safe line;
- "Antenna · 41 chan" clipping on the Live TV key (now "41 channels");
- the device prompt being suppressed by a card that was already gone;
- the picture-mode filter dimming Lobby's own UI;
- Stripes showing on failure screens;
- About saying "1.4 is ready" twice;
- door toasts repeating a change already visible on the key;
- the Netflix test field being too close to the real brand's look (it's now black with white type).

| # | Problem | Severity |
|---|---|---|
| 1 | **The TV menu over an app isn't buildable as a plain launcher.** Lobby only draws while it's in front. Opening the menu over Jamfin or HDMI 2 needs an **accessibility service** to catch a remote key and an **overlay permission** to draw over the app. Remappers do this on Google TV, but with reported gaps (Button Mapper's notes). This is the main risk to D54. | High |
| 2 | **Which key opens it is unknown.** The README says the remote is D-pad only (arrows, OK, Back), and I couldn't confirm Phoster's remote layout. The mockup's G/Q, I and M keys are keyboard stand-ins. Without a mappable key, the TV menu is reachable only from Home. | High |
| 3 | **≡ may not exist on the remote**, so in All apps the only paths to Options are hold OK and… nothing else on screen. D58's non-hold path assumed ≡. All apps needs a press-twice or an on-screen "Arrange" path to meet D31. Not drawn. | Medium |
| 4 | **Unlocking the front door from the sofa.** Anyone holding the remote, including a child or a guest, can unlock it with a 1 s hold. The design is safe against accidents, not against intent. This is Isaac's call (Questions 2–3). | Medium |
| 5 | **"Unlocked" is always an alert here.** At 2 PM with someone in the garden, a solid red key on Home is loud for a calm family screen (B6 is still open). | Medium |
| 6 | **The device prompt takes focus** for up to 15 s. A press meant for the row underneath lands on the prompt instead. Google TV's own dialogs do the same, but it's the one place Lobby moves focus by itself. | Medium |
| 7 | **The House row only fits with empty ports hidden.** With "Show empty inputs" on, the row holds 8 keys and scrolls, and the front door ends up off screen. That breaks "everything visible at once" for anyone who turns the setting on. | Medium |
| 8 | **Toning is for calm, not for the floor.** Even untoned brand fields stay under the glare cap (3.4%) and far under the red clause (1.6%). The colour filter lowers glare but barely changes the saturated-red share, because red stays red. The real reason to tone is three colour sources on one screen. | Low |
| 9 | **Stripes' burnt orange `#b04a1c` counts as saturated red** under Lobby floor 2's formula (linear R share ≈ 0.84). It passes because it's static and tiny (0.5%), but it's a decorative colour that the "red = alerts" rule would call red. | Low |
| 10 | **Picture preview** is still a CSS filter on the picture layer. On the TV, picture mode changes the whole panel (Lobby included) through Control Freak over MQTT, with unmeasured latency (carried from pass 2 #5). | Medium |
| 11 | **"Apps" as the name of the TV's own source** is new vocabulary. It's honest, but nobody in the house has heard it yet, and Hisense's own input list may call it something else (unverified). | Low |
| 12 | **OK on release** delays every action by the length of the press (about 100 ms). A long press on something that can't be held now does nothing until release, which may feel sticky on a slow remote. | Low |
| 13 | **Day still has the marks.** They're quiet (1.36:1), but a Day Home still shows about 20 window recesses. If Isaac prefers D91's "lit only", the TV could follow it. | Low |
| 14 | **The first-run defaults** (Jamfin, YouTube, Netflix, Prime Video, Play Store, Live TV) are invented. The real first run can only read installed apps, not what the family uses. | Low |
| 15 | **Still not drawn:** screensaver/ambient, profiles, the rename-input sheet, Android permission prompts, a Live TV guide, Lobby crashing (Android's fallback to the stock home), Restart confirmation, and the remote-key setup. | Medium |
| 16 | **Nothing is measured on Phoster** (WebView Chromium 156): GPU cost of the filters, focus legibility at 3 m, and the flash check with `tools/shoot.js --check`. | Medium |
| 17 | The TV menu still covers 21% of the picture, including subtitles while a chooser is open (carried). | Low |

## Questions for Isaac
These are the decisions only Isaac can make. Each has my recommendation.

1. **May Lobby run an accessibility service on Phoster, and which remote button becomes "TV menu"?** Without both, the TV menu only exists on Home.
   *Recommendation:* yes. Map the remote's Input or Source key, if Phoster's remote has one, because Lobby shows inputs itself. Leave Home and long-press Home to Google.
2. **May the TV unlock the front door?**
   *Recommendation:* yes, as Lobby already planned: a 1 s hold or press twice. Locking always takes one press. If kids or guests are a worry, make it lock-only on the TV.
3. **When is an unlocked door an alert?**
   *Recommendation:* after sunset or when the house is set to Night, it's alert (the solid red key). In daytime it's warn (amber ▲ + "Unlocked", no red). This also settles B6 for the TV.
4. **Inputs on Home as keys beside the lamps (this pass), or only in the TV menu, as Google TV and Fire TV do?**
   *Recommendation:* keys on Home. The Switch 2 is a destination the family picks as often as an app, and Lobby's own rule is "everything visible at once".
5. **When the Switch 2 turns on, should the TV ask, switch on its own, or stay put?**
   *Recommendation:* Ask, once, in the clear zone. Switching on its own interrupts whoever is watching.
6. **Should app banners be toned at night or shown in full colour?**
   *Recommendation:* toned at night, with Full colour as a Home screen setting. Glare is fine either way, so this is taste.
7. **Should Lobby update itself overnight, or wait to be told?**
   *Recommendation:* overnight (On by default), shown as a cream light on Settings and never as a pop-up.
8. **Are Floor lamp, Table lamp, Mood lighting and Front door the House row?**
   *Recommendation:* yes, fixed at those four for everyone. There's room for exactly four keys next to the two inputs.
9. **Should rows stop at their ends on every TV screen (D59), or may NervOS's systems carousel wrap (D75)?**
   *Recommendation:* stop everywhere. Keep the walnut end mark as the shared sign.

## Bible implications
Final form for the TV (Lobby, and JamFin on the same set).

1. **TV cards are art + plinth.** Progress runs on the art's bottom edge and the selector window sits on the plinth's bottom edge. On banners, the plinth shrinks to a strip that only holds the window (D13, D53).
2. **One TV menu.** Guide (or whatever key the house maps to it) opens one bottom band over Home, an app or an input, with Input · Picture · Sound · Sound out · Sleep · a house control · Settings. Its header names what's underneath. Building it needs a captured key and an overlay; record per device which key that is (D54).
3. **The current source, defined.** A TV is always on exactly one source, and Lobby and every app share one called **Apps**. Home never marks an HDMI input as current. Only the TV menu's header and its Input chooser show the source, with the square. This **replaces D61**: there's no source window on the launcher's Home.
4. **One way in per job, per screen.** A destination appears once on a screen. On Home, inputs are keys in the bottom row. Over content, the Input key in the TV menu is the way in.
5. **The alert fix on TV is D84.** It's a solid red key with dark text at every size and in both lightings. Focused, it takes D18's cue (black label, deeper under-edge, lit window). Nothing else on that screen is orange. There are no alert rings. This replaces pass-2 implication 11.
6. **Rows stop on every TV screen (D59).** A walnut end mark follows the last item, an extra press nudges (not in Calm), and only the focused row shows "n of N". In a row split into groups, the header of the group with focus shows it. D75's wrap is reserved for NervOS's systems carousel if Isaac wants it.
7. **Windows by lighting.** At night an unlit window is a dark recess. In Day it's a shallow recess about 14% darker than its own surface (about 1.3:1). A lit window is a flat colour; in Day it sits in a 2 px dark rim (D17). Windows on black bands, sheets and the title card keep the night form. D91's "lit only" stays for phone and kiosk tab bars.
8. **Real banners get a frame and night toning.** Draw any third-party banner inside a 6 px card-coloured surround. At night, apply a colour filter (`saturate(.62) brightness(.74)` in the mockup), never a blended rectangle. Never brighten a banner on focus: only its window lights.
9. **Accents only where there's no art.** On a launcher, the accent shows only when no cover art is in view: the title card, the first-run Home, and Continue off. It also steps back on failure layers and while a toast, prompt or menu uses the clear zone. This settles D19, D22 and D62 for TV.
10. **Every failure layer ends the same way**: what happened, in plain words; what to do; **Try again** (the one orange) and **Home**. The slatted bar stops, unlit or dimmed. This extends D63 from inputs to apps.
11. **One launch rule (D60, settled).**
    - Films, shows, games, apps and inputs: the title card holds for max(load, 600 ms), then opens in 300 ms.
    - System screens (Android settings, App info): a plain 140 ms cut.
    - Music: plays and pauses in place, with no card.
    - Calm: a 140 ms fade.
12. **OK acts on release on TV.**
    - Holds are 600 ms for options and 1 s to unlock or delete, with the fill on the edge opposite the window.
    - **Every hold has an on-screen non-hold path** (press twice within 3 s, with the key saying "Press OK again").
    - ≡ is a shortcut only where the remote has one. This refines D58.
13. **Notices never pop up.** An update that's ready is a cream LED on the Settings key plus a row in About. A device that wakes gets one prompt in the clear zone, with one orange. It takes focus, leaves after 15 s and never repeats. A setting says Ask / Switch / Stay.
14. **Changes that show in place don't toast.** A lamp or the door changes its own key. Toasts are only for changes that happen somewhere else (house speakers, a setting saved, Home rearranged).
15. **First run and empty Continue.** An empty Continue is a recess with one line saying what will appear there. On first run it holds the one orange, **Arrange Home**. A launcher never fills empty space with suggested content.

Sources:
- [TV app icon design guidelines (Android Developers)](https://developer.android.com/design/ui/tv/guides/system/tv-app-icon-guidelines)
- [How to remap the YouTube and Netflix buttons on Chromecast with Google TV (Android Central)](https://www.androidcentral.com/how-remap-youtube-and-netflix-buttons-chromecast-google-tv)
- [tvQuickActions (AlternativeTo)](https://alternativeto.net/software/tvquickactions/about/)
- [MX3 Button Mapper (F-Droid)](https://f-droid.org/packages/com.odiousapps.mx3buttonmapper/)
- Hisense remote guides found were for non-Google-TV models (e.g. [Hisense 55U6K manual, remote page](https://www.manualslib.com/manual/3078554/Hisense-55u6k.html?page=9)); Phoster's remote layout stays unconfirmed.
