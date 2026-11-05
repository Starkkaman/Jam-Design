# TV launcher (Lobby) · Pass 2

Mockup: `mockups/pass2/tv-launcher.html`. Pass 1 (`mockups/pass1/tv-launcher.html`) is unchanged.

The mockup is interactive. Click the TV, then use:
- the arrow keys, Enter (OK) and Esc or Backspace (Back);
- H (Home), G or Q (Guide, which opens the TV menu), M (≡ options) and I (inputs);
- the remote buttons, including **Hold OK**.

Page controls:
- **Lighting:** Night / Day.
- **Motion:** Full / Calm.
- **Switch 2:** On / Asleep. Asleep shows the no-signal path.
- **Jump to:** Home / Picture + TV menu / No signal / All apps / Settings.

A status line counts presses since Home. It also reports how long the last title card held compared with its load time.

Sources read:
- `notes/OVERNIGHT-BRIEF.md`, `CHANGES.md` (A, B, D1–D52), `BIBLE.md` 0.5 and the end of `decisions.md`.
- All six `notes/pass1-*.md`.
- `projects/lobby/README.md` and `PROPOSALS.md`, and the Lobby screenshots (Calder Play, Homage Listen and Picture chooser, Kinetic Sound chooser, Calder no-signal).
- The pass-1 TV, NervOS and JamFin mockups, and `_hifi-base.css`.

All titles, art, app banners and glyphs are made up. Film names reuse JamFin's demo names; the game reuses a NervOS fixture name. App *names* are the household's real ones from the Lobby README (Jamfin, YouTube, Netflix…), but every banner is a neutral flat field with a generic glyph. There are no logos and no brand colours. The house name "Bungalo", the 9 picture modes, the 8 sound modes, Sound out, the Switch 2 on HDMI 2, the empty HDMI 1/3 and the front door come from the Lobby README and screenshots.

## What changed since pass 1

**Every pass-1 High item is fixed:**

| Pass-1 audit | Pass 2 |
|---|---|
| 1 Inputs row cut off | Continue, Apps and Inputs all fit inside the safe area at once. Measured at 1080p: rows run from y 311 to 1009, with the safe line at 1026. To make room, the sign's action moved onto its one line, app banners got a slim plinth, and Inputs became 74 px keys. |
| 2 Stripes over the top bar | The accent sits in its own clear zone: x 1420–1920, y 124–308. That's below the band, right of the sign (whose text ends at x ≈ 1000) and above the rows. It hides while a toast or the TV menu is up (the clear zone holds one thing at a time). |
| 3 Progress vs selector bars | Cards are art + plinth (D13). Progress runs on the art's bottom edge, full width. The selector window sits on the plinth's bottom edge, half width. The plinth line says "Ends 9:13 PM", not minutes left (D15). |
| 4 Labels under 22 px | Nothing on the TV is under 22 px. Labels and hints are 23–24 px, body text is 26 px. Checked by walking every visible text node in Playwright on every state. |

**Medium and Low items:**

| Pass-1 audit | Pass 2 |
|---|---|
| 5 Monogram tiles | Android-TV-style 16:9 banners, made up and neutral. |
| 6 "Top bar" hero copy | The sign now names the destination ("Inputs", "TV menu", "Settings"). |
| 7 Two focus grammars | One grammar (D3). Tiles, cards and keys light a base window; lists and choosers light the same window on their leading edge. |
| 8 Current input too quiet | The band has a recessed **source window**, like a receiver's display: a lit slot, the input's name and the port in mono. The Inputs row presses the current input in. |
| 9 Empty Settings detail | Every section shows its rows with current values inline, plus faders, toggles and choosers. |
| 10 No live preview | The TV menu's Picture chooser previews the mode on the picture behind it, with no veil over the picture. |

**Adopted from other apps:**
- **D13** split progress/selector.
- **D14/D36** the title card holds only as long as the load, with a 600 ms floor.
- **D16** pop above or below: choosers pop *above* a bottom-band key and *below* the top band, and app options pop above or below the tile. A chooser from a vertical Settings list pops *beside* it.
- **D18** an orange primary has its own focus cue: a black label, a deeper under-edge and a lit leading window.
- **D31** holds: the fill runs on the edge opposite the focus window, and every hold has a non-hold path.
- **D32** carousel end rule: rows stop at the ends, with a walnut end mark, a small bump, and "2 of 6" in the row header.
- **D33** "never twice" while a chooser is open: the key's value turns into ▲ while its chooser shows the value.
- **D35** Guide opens one house menu everywhere.
- **D42** alert outranks primary on the front-door key.
- **D22** accents step back.

## Research
I ran 12 web searches. Fetching full pages was blocked by this session's network allowlist (maketecheasier, 9to5google, macstories, aftvnews and lon.tv failed to resolve), so the facts below come from search-result summaries of vendor help pages, reviews and forums. Lines marked *(knowledge)* come from my own knowledge.

| Product | Launch apps | Change inputs | Picture and sound | Full Android / system settings |
|---|---|---|---|---|
| **Apple tvOS 17/18** | Top row of apps, with Top Shelf above it showing the focused app's content (the TV app can show Up Next instead of featured previews). Users report Top Shelf losing Up Next after tvOS 18 updates. | n/a (no inputs) | **Control Center** opens with a press and hold of the TV button. It holds users, music, sleep and the **Sleep Timer** (15 / 30 min, 1 / 2 h). Audio output (AirPods, AirPlay speakers) sits in Control Center tabs. Accessibility shortcuts are system-wide, not per user. *(knowledge)* It's a side panel over whatever's playing. | Settings app |
| **Google TV** | "For you" rows of recommendations and ads *(knowledge)*. An "Apps only" mode exists *(knowledge)*. | Philips Google TV: **Source** opens the input list; some sets show Inputs in the quick bar. | Quick settings via the Settings icon top-right, or **long-press Home**. Picture is a quick link. The 2023 redesign is a 2×2 tile grid; the Home panel (smart home) opens as a feed on the **right side**. | The gear opens the side panel, then the full Settings. Menu names vary by brand (TCL: Channels & Inputs, Display & Sound). |
| **Projectivy** (ad-free, the closest relative) | Freely arranged apps and grid modes; rename apps, change icons, icon packs; program cards are customisable. | Shortcuts to **HDMI 1/2/3/AV**; it can auto-start straight into an input or app. | Shortcut to the TV's on-screen menu popup. | Status-bar toggles (clock, settings icon); submenus need the tvQuickActions companion. **Themes** are a Premium feature and mostly cover card corners, size, transparency, glow and wallpaper. Users praise the "clean look" from rounding and card size. |
| **FLauncher** (open source) | Categories with manual reorder inside each; row or grid per category. | n/a | n/a | Settings icon top-right. A fork (LTvLauncher) replaced "finicky gestures" for reordering categories with **Left/Right arrow keys**, a lesson for D-pad reorder. |
| **ATV Launcher Pro** | Folders (hidden and password-protected), 12 row styles. | Not confirmed | n/a | Reviewers say "the sheer number of features and settings might be too much". |
| **Fire TV (2026 redesign)** | Up to **20 pinned favourites**. Reorder by holding the circle button and using the arrows, or Options → **Move**; long-press Select for move/uninstall. | **Inputs button in the menu bar**, between profile and Home. A reviewer wants inputs on the top row and can't customise it. | **Hold Home** opens a quick panel (audio, display, cameras, smart home). | Gear at the end of the menu bar. |
| **Roku TV** | Grid of channel tiles; ✱ hides or moves tiles. | **Input tiles on Home**, each with Options → **Rename input** (name + icon, or a custom name) and Remove. Forum users complain when inputs get nested or tiles go missing. | **✱ during playback** opens an overlay with Sleep timer first (30 min to 3 h), Picture mode, brightness and sound. In some channels ✱ is taken by the app and doesn't open it (a "two menus on one button" problem). | Settings → TV inputs, System, etc. |
| **LG webOS 22–24** | Home with apps below. | **Home Hub** shows inputs *above* the apps. Sources disagree on webOS 24's Input button; later versions fold inputs into Home Hub. | webOS 23 added a **customisable Quick Menu** (gear icon; you choose the tiles). | Full settings from the Quick Menu. |

**Lessons for Lobby:**
1. Every product puts **picture, sound and sleep in one overlay over the picture** (Control Center, ✱, long-press Home, Quick Menu). Several put sleep first. That's the TV menu.
2. **Inputs are first-class on the TVs that have them** (Roku tiles, Fire TV menu bar, webOS Home Hub). People notice when inputs are buried or nested. So: a source window in the band plus an Inputs row.
3. **Renaming inputs** with a name and an icon is standard (Roku). Lobby gets "HDMI 2 is called…" in Settings.
4. **Reorder uses Options → Move plus arrows** (Fire TV, FLauncher's fork), not gestures. A long press is the shortcut, never the only way.
5. **Ad-free launchers win on subtraction and get worse with options** (ATV Pro). The family needs the few switches that matter, with Android settings one entry away for the rest.
6. A button that means different things in different apps (Roku ✱ in some channels, NervOS's Steam Guide) is a trap. Lobby's Guide should always open the same menu.

## Design (what and why)

**Home: the input, the thing you were watching, your apps.**
- **Band:** a fixed ribbed band with walnut trim. It holds the house name, then three keys: **Input** [source window: lit slot · *Switch 2* · `HDMI 2`], **TV menu** and **Settings**, then the clock, date and weather. The source window says which input the TV is on. After launching an app it reads *Google TV · Apps*. OK on it drops the Inputs chooser **below** the band (D16).
- **Sign:** an eyebrow, a 64 px title and one line, with the **OK action on the same line** ("OK Resume from 1:12:04"), which keeps Lobby's hero "OK Resume" without adding a third line. It swaps by opacity (50 ms out, 100 ms in).
- **Continue:** 320 × 180 art + plinth. Five cards are fully visible and the sixth peeks in the margin. Each plinth says "Jamfin · Ends 9:13 PM". Music and games have no bar and no fake progress.
- **Apps:** user-ordered banners, with **All apps** last (it shows the count). The plinth only holds the window.
- **Inputs:** keys with a neutral device glyph (gamepad, plug, antenna; D34), the name, and an LED + word ("HDMI 2 · Signal", "Nothing plugged in", "Antenna · 41 channels"). Empty ports are quiet. The current input presses in.
- Rows stop at their ends: a walnut end mark, a small bump, and "n of N" in the focused row's header (D32).
- **The opening state is Lobby's:** focus on the first Continue card, and Back from anywhere on Home returns there.

**Launch: the title card.**
- The flat shutter halves slide in (460 ms, decelerate) with ribs and Stripes down the right side, lined up across the seam and clear of the centred title.
- The eyebrow says what's happening ("Jamfin · Resume from 1:12:04"), and the slatted bar shows the real load.
- The card **holds only as long as the load, with a 600 ms floor** (D14/D36). Measured in the mockup: a 0.70 s load held 0.84 s, and a 1.10 s load held 1.24 s.
- The picture is composed behind the opaque card first, then the halves leave (300 ms). Back during the card cancels it.
- Calm makes it a 140 ms fade.

**Switching inputs.**
- Inputs use the same card with "Input · HDMI 2" and "Waiting for a picture" (an HDMI handshake takes 1–3 s).
- No signal: the bar stays unlit and the line says what to do, in Lobby's own wording: "No signal on HDMI 2. Turn on the Switch 2, then try again."
- It offers **Try again** (the screen's one orange key, with the D18 focus cue) and **Home**.
- An empty port says "Nothing is plugged into HDMI 1. Plug a device in, then try again." The layer is opaque and full-bleed (Lobby floor 7).

**TV menu (Guide): one house menu (D35).**
- G (Guide), Q, the band key, or I (opens straight on Inputs) raise one ribbed band from the bottom over Home, an app or an input.
- Its first line has a slot, "TV menu · over The Copper City", hints that change with the zone, and the clock.
- Its keys: **Inputs · Picture · Sound · Sound out · Sleep · Front door · Settings**.
- **Choosers pop above their key** (D16), anchored over the band so they never cover its header. They use Lobby's own chooser words: "OK Use Filmmaker mode" / "Back keeps Theater night".
- **The key's value becomes ▲ while its chooser is open**, so the current value shows once, as the square window in the list (D33).
- **Live preview:** there's no veil above the band, so moving through Picture modes changes the picture behind, but **only 500 ms after you stop**. A held ↓ through nine modes can't make more than 2 big luminance changes a second (Lobby flash floor 1). Back reverts in one change.
- **Sound out** is one press (Stereo ↔ TV speakers), as in Lobby.
- **Sleep** shows "Off at 9:24 PM", a time rather than a countdown.
- **Front door:** "Locked" with a green LED. **Hold OK for 1 s** to unlock, with the fill on the key's **top** edge while the window is on the bottom edge (D31). **Or press OK twice** within 3 s ("Press OK again" shows on the key): the non-hold path for remotes that can't hold.
- Unlocked, the key turns alert (a red ring, a red LED and the word). One press locks it, and that key is drawn alert rather than orange (D42).
- There's no orange in the TV menu: every change applies live.

**All apps (reorder).**
- A slim band ("All apps · Back Home"), then two groups: **On Home · in this order** and **Not on Home**, at 7 per row. Every installed app is visible at once, with no scrolling.
- **OK opens. Hold OK (600 ms) or ≡ opens Options**, popping below the tile (or above it, near the bottom): **Open YouTube** (orange, D18), **Move**, **Remove from Home** / **Add to Home**, and **App info** (Android's page).
- **Move:** the tile lifts with a cream ring and side arrows. The arrows move it through the grid live, **OK puts it here** ("YouTube is number 4 on Home"), and **Back puts it back** where it started.
- Home's Apps row follows the order immediately.

**Settings.**
- A slim band, a list on the left (leading window) with each section's value inline, and a detail pane: a heading, one lead line, then rows.
- **Picture:** Picture mode, a Brightness fader (cream reveal, with the number on the cap, D40), Motion smoothing, and "More picture settings › Android settings".
- **Sound:** Sound mode, Sound out, Dialogue boost (square window + On/Off), Lip sync.
- **Inputs:** "HDMI 2 is called" (renames the input everywhere), "Switch when a device turns on", and "Show empty inputs on Home" (live: HDMI 1 and 3 leave the row).
- **Home screen:** apps and order (→ All apps), Continue row, Accent (Stripes / Off), Lighting (Night / Day / Auto), Calm.
- **Sleep & power**, Network, Remote & accessories, Accessibility, About.
- **Android settings:** a lead line plus **Open Android settings**, the screen's one orange key. It opens through the title card into a plain stand-in, and **Back returns to the same Settings row**.
- Choosers from these rows pop *beside* the list.

**Look and floors.**
- Simplified Braun Hi-Fi: flat, with ribs only on fixed bands (home band, slim bands, TV menu, title card). Flat grounds behind rows.
- Windows are always a dark recess; lit means flat cream (or green / red for LEDs).
- Jost for words, Plex Mono for ports, counts and the eyebrow.
- Focus colour snaps, and only transforms animate (lift ≤ 10 px inside the card; the hit box never moves).
- TV Day: ground `#bdb9b1`, black bands.
- Calm: fades of 140 ms or less, no bumps, no lifts.

## Audit
Checked with Playwright (Chromium, no launch options):
- Page width 1500 at deviceScaleFactor 1.31, so the TV renders at about 1920 px. Also checked at 390 px wide in the dark scheme.
- The keyboard run: Home → band → Inputs chooser below the band → apps row end (bump) → Inputs row → Continue OK → title card → playing → Guide → Picture chooser with preview → OK → front door hold → Home (focus restored) → All apps → ≡ options → Move ×2 → OK → hold-OK options → Settings → Picture → Brightness fader → Picture chooser beside the list → Android settings → stand-in → Back → no-signal jump → Day → Calm.
- 30 screenshots, kept in the scratch dir, not the repo.

Results after the fix pass: **no JS errors**, **no TV text under 22 px** in any state, **no text outside the safe area** apart from peeking cards, and **no horizontal scroll at 390**.

The fix pass corrected:
- the slim bands' text sitting 6 px above the 54 px safe line (the band grew to 125 px);
- the TV menu's chooser covering the band's own header line;
- "Optical (stereo)" truncating on its key (now "Stereo");
- the chooser footer repeating the same value ("Keep X / Back keeps X");
- the Android stand-in's caption clashing with the page's `.note` style and sitting under the live hints.

| # | Problem | Severity |
|---|---|---|
| 1 | **Two ways to switch inputs on Home.** The band's source window opens an Inputs chooser, and the Inputs row switches directly. Both are cheap, but a family member may not know they're the same thing. The research (Roku tiles, Fire TV menu bar, webOS Home Hub) splits the same way, and none does both. | Medium |
| 2 | **"Current input" is fuzzy on Google TV.** When Lobby is showing, the TV is technically on its own Google TV source. The window shows the *last* input ("Switch 2") until an app launches, then "Google TV · Apps". That's honest but abstract. The sign helps ("Its picture is waiting. OK goes back to it."). It needs a check with the family. | Medium |
| 3 | **"Never twice" on Home.** The source window names Switch 2 and the Inputs row presses Switch 2 in, on one screen. One is a word and the other a shape in a different panel, but it bends the rule (D41: is a panel a card or a view?). | Medium |
| 4 | **Day selector windows read as black dashes.** Every unlit base window on a light plinth or key is a 9 px black bar, so the Day home shows about 20 of them. The lit one reads, but the rest is noise (the same as HA pass-1 #10). | Medium |
| 5 | **Live preview is a CSS filter on the whole content layer.** On the TV, picture mode is a panel setting that Lobby asks Control Freak to change over MQTT. The preview latency is unknown (MQTT plus the panel's own transition), and it may already exceed the 500 ms debounce. Real flash behaviour must be measured on the Hisense. | Medium |
| 6 | **The TV menu covers 21% of the picture** (a 230 px band). That's fine for picture modes (you judge the top four-fifths), but a chooser over a film's subtitles hides them. | Low |
| 7 | **Banner colours are invented.** They're toned and in the lightness band, but a family member looking for "the red one" (YouTube) finds a brick-red field and a screen glyph. The real build will show each app's own Android TV banner, which brings back brand colours and logos. It needs the toning rule from Lobby floor 3 (brand colours pulled into the lightness band) as a colour filter, not a blended rect. | Medium |
| 8 | **The Stripes accent is heavy** next to six art covers and eight colour banners: three colour sources on one screen (D19). It hides for toasts and the TV menu, but not when covers are busy. | Medium |
| 9 | **Hold OK in All apps changes OK's timing.** Open fires on key-*up* there (so a hold can become Options), while everywhere else OK fires on key-down. The difference is about 100 ms, but it's two behaviours on one key. Lobby's engine already emits press-start and press-end, so it's buildable. | Low |
| 10 | **The move ring** (a 4 px cream outline) is a second focus mark next to the base window. It reads clearly, but it's new vocabulary. | Low |
| 11 | **The title card for a 0.7 s Android settings open** still runs the full shutter. Opening settings may not deserve a signature moment; a plain cut could be better for system apps. | Low |
| 12 | **The Continue row mixes kinds** (films, a streamed game, house music). They share one 16:9 shape, and music shows a slot instead of a bar. It works, but "Late Set · House music" opening a title card is odd for audio that just resumes. | Low |
| 13 | **Not drawn:** Lobby's Watch / Play / Listen / Home groups (lamps), screensaver/ambient, first run, profiles, the HDMI-CEC "device turned on, switch?" prompt, the input rename sheet, and Android permission dialogs. | Medium |
| 14 | **Real data:** the clock is fixed at 8:24 PM, Continue isn't fed from Jellyfin/Moonlight, and nothing is measured on the TV's WebView (Chromium 156). | Low |

## Change suggestions for pass 3
- **Inputs:** pick one. (a) Keep the row and make the band window read-only (it shows, but doesn't open). Or (b) drop the row and make the window the way in, as Fire TV and Google TV do. Try (b) with the freed 118 px given to a second Continue line or to Lobby's Home group (lamps, front door).
- **The source window when an app is up:** try "Watching Jamfin" with the app's name instead of "Google TV · Apps".
- **Day windows:** try an unlit window in the plinth colour one step darker, with a dark rim only when lit (inverting the D17 rim rule), and count the marks per screen.
- **Accent with art:** step back when Continue is full of covers (D19). Try the Stripes only on the title card and the empty Home, and Colour bars on Settings.
- **Real banners:** design the frame for real 320 × 180 Android TV banners: a 6 px card-coloured surround, and a toning filter at night (Lobby floor 3). Show the YouTube and Netflix cases and measure the saturated-red clause along the row.
- **The CEC prompt:** when the Switch 2 wakes, a toast-sized card says "Switch 2 turned on · OK to switch". Its OK is the one orange.
- **Bring back Lobby's Home group:** Floor lamp 40%, Table lamp, Mood lighting, Front door. Lamps toggle in place with a slot light, and the front door hold moves here from the TV menu (or stays in both?).
- **System opens** (Android settings, App info): try a plain 140 ms cut instead of the shutter.
- **Test on the Hisense:** the preview latency over Control Freak, the flash check with `tools/shoot.js --check`, and the focus read at 3 m.

## Bible implications
1. **§7 TV selector + D13:** cards are art + plinth everywhere on TV. On a banner with no progress, the plinth may shrink to a strip that only holds the window.
2. **TV menu (D35, made concrete):** on a launcher, Guide (or the launcher's menu key) always opens one bottom band with Inputs, Picture, Sound, Sound out, Sleep, a house control, and Settings, over whatever is playing. Apps never take over that button.
3. **Live preview floor:** a chooser that previews a full-screen change (picture mode, Day/Night) applies the preview only after focus rests for ≥ 500 ms, and Back reverts in one change. This extends Lobby flash floor 1 to previews.
4. **D33 settled:** while a chooser is open, its key shows ▲ instead of the value; the chooser's square window carries the value.
5. **D16 extended:** a chooser from a top band pops below it, from a bottom band above it, and from a vertical list beside it. All three share one dark sheet with a leading-window focus and a square for the current value.
6. **D31 concrete:** holds are 600 ms for options and 1 s for anything that unlocks or deletes. The non-hold path is the ≡ key for options and "press OK again within 3 s" for confirms, and the key says so while it's armed.
7. **D32 settled for launcher rows:** stop at the ends (no wrap), show a walnut end mark after the last item, nudge on an extra press (not in Calm), and show "n of N" only on the focused row.
8. **D14/D36:** one rule for every launch: hold = max(load, 600 ms), then 300 ms to open. System apps (settings, app info) may skip the shutter (pending pass 3).
9. **New: the source window.** A TV's current input is shown as a recessed display window on the fixed band (lit slot, name, port in mono): an indicator, not a control colour. It's a candidate shared component for Jam Home's TV card too.
10. **Accent clear zone holds one thing:** when a toast or a menu needs the space, the accent hides by opacity, and it comes back when they leave. This extends D2/D22.
11. **Destructive and alert keys on TV (D42):** a key whose press fixes an open alert (lock the door) is drawn with an alert ring + LED + word, never orange. Orange stays for the one primary, which a live-applying menu doesn't have.
12. **Inputs vocabulary:** "Signal / No signal / Nothing plugged in", with an LED for the first two and none for empty, and the no-signal layer always ends with Try again + Home. Add it to the state-word table as Lobby's display words for on / off / offline.
