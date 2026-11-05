# Home Assistant (Jam Theme + Jam Cards) · Pass 4

Mockup: `mockups/pass4/home-assistant.html` (new; passes 1–3 unchanged).

Pass 4 follows Isaac's direction after passes 1–3: "Everything should feel like it has the same design language, not necessarily the same design. … I don't really want to see identical cards and backgrounds across designs unless there's a clear reason. … New elements will need to be designed, be creative, that's part of the ask."

Jam Braun is the look Isaac actually uses on Jam Home and likes, so in this pass "bespoke" does not mean leaving Braun's calm. It means pushing what only a **home** dashboard has: rooms, lamps, a front door, the people who live there, the time of day.

## What changed and why (vs pass 3)

| Pass 3 | Pass 4 | Why |
|---|---|---|
| Kiosk home = Jam Braun's clock + weather + a dock of three blocks (Lights / TV / Music) | **Lit plan** of the house + **day arc** + a "by the door" plate + the sideboard + one bottom key | From across a room, the question is "what's on, where, and is the door locked". A plan answers it in one look; a dock of words doesn't. |
| Weather as text ("64° cloudy · sunny at 3 · high 70°") | **Day arc**: sunrise to sunset, the sun where it is, forecast marks on the arc at their hour | One calm element instead of three lines. The clock keeps the time, so the arc never prints it. |
| Light card: name row + corner rocker with an 18 × 7 paddle window + horizontal fader with a 30 % band | **Dimmer plate**: a big paddle (top pressed = on) and a slide dimmer beside it. The lamp glyph's shade is the indicator window. No band. | A light card that looks like what's on the wall beside the door. It also answers pass 3 audit #8 (three "on" cues): now the lamp window, the fader fill and the word. |
| Switched devices: a light-style card with a rocker | **Outlet plate** (one smart-plug module with a lit power symbol) and a **power strip** of every plug on the House page | The Tree and the fan really are smart plugs. They now look different from lights, which also explains why "Lights · N on" doesn't count them (D90). |
| TV card, PC row and speaker card stacked | **Sideboard**: TV, speaker and PC standing on one walnut-topped cabinet. Each opens its own popup; the cabinet holds the one control for what's playing | That's how they sit in the living room. One card instead of three, and the "which is playing" question has one place. |
| House strip on a black ribbed band with people chips | **Key rail** (who's home) + **door swing** (lock state) in a plate | Keys on hooks is a domestic, private way to say "home/away" (no location). The door swing is the plan's own symbol, so the lock reads the same on the plan and the plate. |
| HA tabs: Living / Kitchen / Master / Music | **Room strip**: House · Living · Kitchen · Master · Marissa, each tab a small window lit in that room's lamp colour | The tab bar becomes the house at a glance on a phone. Music is no longer a tab: media lives on the sideboard and kitchen radio, and Play is primary in their popups. |
| (none) | **Goodnight round**: one sheet that lists what's still on and open, previews the dark plan, then does it | The evening routine is the one moment three people act on the whole house. |
| Day ground: shared aluminium `#e3e1dc`; cards `#f1efeb` | Jam Braun's own page `#e7e3da` and plate `#f2efe8`; anthracite `#1c1c1a` / `#2a2a27` at night | HA is the app closest to Jam Braun. The other apps' passes share the alu, so HA no longer does. |
| One orange per screen, playing → on → idle (idle Play could be orange) | Home screens: orange **only** for something playing (Pause) or bedtime with nothing playing (Goodnight). At rest: zero | "Not too much orange". A house at rest has nothing to press. Popups that are media homes still make Play orange (D129). |

**Kept from pass 3, unchanged:**
- the air purifier ("came out great") and dehumidifier, the only seven-segment displays;
- the remote: soft plastic, red IR flash at the top, lit power symbols;
- the TV source tile grid with printed colour tabs, and "On now";
- the speaker's Group or split;
- five whites that show their colours, colour picks that recolour the lamp window and fader, and the orange guard (pass 3's display colours);
- a popup on every light and media card;
- kiosk sheets at kiosk size, with nothing scrolling;
- the solid red key for the unlocked door, and no other orange while it shows;
- no brushed metal, glow, grain or paper.

## Purpose
- A house dashboard for three people (Isaac, Amber, Marissa) on phones, the living-room iPad (1024 × 768) and the kitchen Echo Show (961 × 601).
- **Glanceable from across a room:** which rooms are lit, is the door locked, what's playing, who's home, what the day is doing.
- **Quick to act, never fiddly:**
  - big plates, not small rows;
  - one tap per room on the kiosk;
  - one control on the sideboard;
  - one key for bedtime.
- **The house's state at a glance** is the home screen itself, not a summary strip above a list.

## Research
Brief. I used **WebSearch** (3 searches) and otherwise my own knowledge (marked).
- **Floor plans for smart homes** (WebSearch):
  - Apple's Home app has no built-in floor plan. Third-party HomeKit apps do: *Controller for HomeKit* (v7, 2024) scans with LiDAR or takes a drawn plan, and *Homerise* has a plan dashboard.
  - On these plans, a tap on a device toggles it and a tap on a room opens its overview.
  - *Lesson:* plans work best as a room picker plus status. Putting every device on the plan as a target is what makes them fiddly.
  - So the lit plan shows rooms and a bar group per room; devices live in the room sheet.
- **Braun clocks** (WebSearch): the AB 1 / travel alarm line is credited to Dietrich Lubs (with Rams).
  - *Knowledge:* Braun clocks use one yellow accent hand on a neutral face.
  - I used that yellow (`#e8b12a`, already a Jam Braun pack constant) for the sun on the day arc, and nothing else.
- **Nothing OS widgets** (WebSearch): dot-matrix clock and weather widgets, praised for showing air quality and humidity at a glance, with a dot animation only on open.
  - *Lesson:* one honest graphic per fact, with motion only on open. The day arc follows that (static; nothing ticks but the clock's minute).
- **Rams' ten principles** *(knowledge)*: useful, understandable, unobtrusive, honest, "as little design as possible". The plates follow "honest" (they look like what they control), and the arc and plan follow "unobtrusive".
- **Wall dimmers** *(knowledge)*: slide dimmers pair a paddle with a small slider beside it. That's the model for the dimmer plate.

Sources:
- [Controller for HomeKit floor plan (MacStories)](https://www.macstories.net/reviews/controller-for-homekits-interactive-floor-plan-is-the-best-way-to-control-your-home-yet/)
- [Controller for HomeKit v7.0 release notes](https://controllerforhomekit.com/release-notes/v7-0)
- [Homerise (App Store)](https://apps.apple.com/bb/app/homerise/id1439944386)
- [Braun travel alarm, 1975 (Irish Times)](https://www.irishtimes.com/life-and-style/homes-and-property/interiors/design-moment-braun-travel-alarm-1975-1.3472681)
- [Nothing OS 3 hands-on (Android Authority)](https://www.androidauthority.com/nothing-os-3-hands-on-3488739/)
- [Nothing launcher widgets (Inverse)](https://www.inverse.com/input/tech/nothing-android-launcher-beta-widgets-design-phone-1-test-pixel-6)

## Design

### New elements (all drawn and interactive in the mockup)
1. **Lit plan** (kiosk home, phone House tab, Goodnight preview)
   - **What it is:** a flat floor plan, with architect's wall lines, door gaps, double-line windows and the front door's swing.
   - **Lit rooms:** a room fills with the display colour of its brightest lamp while any lamp is on, like a house seen at dusk. By day it's a pale tint; at night it's a luminous fill.
   - **Labels:** name, a bar group (one segment per lamp, lit in that lamp's colour, dashed if offline), the room temperature where there's a sensor, and a slot when media plays in a room the screen doesn't already show.
   - **Openings:** an open window is an amber bar in the wall, with one line under the plan: "Kitchen window open · 25 min".
   - **You are here:** the kiosks mark their own room with a walnut "Here" pin.
   - **Interaction:** tap a room to open its kiosk sheet, or the room view on a phone.
2. **Day arc** (kiosk top, phone header)
   - Sunrise to sunset as one arc over a horizon line: solid for the part of the day that's gone, dotted for what's left. The sun is a Braun-yellow disc where it is.
   - The forecast sits **on the arc at its hour** ("sunny" at 3, "70° high"), and the temperature and condition sit under the arc.
   - At night the same arc runs sunset to sunrise, with the moon, the kiosks' **screen-off** time (23:00, a real HA automation) and the overnight low.
   - It never prints the current time; the clock does that.
3. **Dimmer plate** (every light)
   - **Paddle:** a big rocker. On = top half pressed in; Off = bottom half pressed in.
   - **Slide dimmer:** sits beside the paddle. It reveals the lamp's display colour up to the cap, and the number shows on the cap while dragging (phone). Kiosks print it on the cap always (D86) and say "Off" at 0.
   - **Lamp glyph:** floor, table, strip, pendant, bulb, string or lantern. Its shade *is* the indicator window: dark when off, flat colour when on.
   - **Popup:** tap the name (›).
   - **Offline:** dashed plate with a dashed paddle and track. The kiosk version is a narrow column with "Can't be reached since…" and a Details key.
4. **Outlet plate and power strip** (switched devices)
   - **Outlet plate:** a smart-plug module on a wall plate, with a round key whose power symbol lights green (the lit-glyph rule). The name and glyph dim when off.
   - **Power strip:** the House tab gathers every plug onto one strip with a cord and one "Free" socket.
5. **Sideboard** (living-room media)
   - **The objects:** a TV, a speaker and a PC on a cabinet with a walnut top and tapered legs.
     - The TV screen is the only ribbed surface on any HA screen. It shows the state word, the title and "ends 11:02", plus a lit power symbol.
     - The speaker's grille lights one cream dot while playing (D50).
     - The PC is a small box with a slot window ("Zz" when asleep).
   - **Interaction:** each object opens its own popup (TV, speaker, PC).
   - **The cabinet:** holds one control for what's playing (Pause, orange) or, when nothing plays, Remote and Source.
   - **On the iPad:** the sideboard is a silhouette with no small print. A tap opens a full **Sideboard sheet** with TV, speaker and PC columns.
6. **Kitchen radio**: the kitchen speaker as a countertop radio (grille, what's on, one key). On the Echo it sits in the right column.
7. **Key rail** (who's home)
   - A walnut rail with three hooks.
   - **Home:** your key hangs there with a printed colour tag and your initial.
   - **Away:** the hook holds a dashed outline of the key, with "Away", plus "since 8:40" on phones.
   - Words only: no map and no location.
8. **Door swing** (lock state)
   - Locked: the door sits in its wall gap, with a faint swing arc and a hinge dot.
   - Unlocked: the leaf swings open in red with a red dashed arc, a red LED and the solid red **Lock** key.
   - It's the same symbol on the plan, the door plate and the doors list.
9. **Room strip** (phone navigation)
   - Five tabs; each room tab carries a small two-pane window lit in that room's lamp colour, and House shows a tiny plan.
   - The current tab presses in (it doesn't light, because the windows already mean "lit room").
   - It sticks to the top while the room scrolls.
10. **Goodnight round** (House tab and kiosks at night)
    - **Rows:**
      - the door ("Locked", or "Unlocked: will lock");
      - the open window, as a reminder only ("close it by hand");
      - each room with lamps on, with Turn off / Leave on;
      - the purifier's night speed.
    - **Defaults:** shared rooms off, bedrooms left on.
    - **Preview:** a live plan of the house after Goodnight.
    - **Run:** "Goodnight" does it; rooms fade out on the plan (opacity, one-shot) and the key goes quiet ("Goodnight · done").

### Screens in the mockup
- **Phones (390 × 844), all four interactive:**
  - Living · Day (0 orange);
  - House · Day (0);
  - Living · Night (1: the sideboard's Pause while the film plays);
  - House · Night (0, because the film is playing, so Goodnight waits).
  - Every room is one tap away on the strip.
- **iPad (1024 × 768):**
  - Day (0 orange; the bottom key is a plain "All lights off…") and Night (1: Pause).
  - Sheets:
    - four room sheets (scenes, outlet and purifier on the left; plates as tall columns);
    - the Sideboard sheet;
    - the TV popup with the source grid;
    - the remote;
    - the PC popup;
    - the speaker popup with Group or split;
    - the light popup (two columns);
    - the offline popup;
    - Goodnight (plan preview + checklist).
- **Echo (961 × 601):**
  - Day (1: the kitchen radio's Pause) and Night (1: Goodnight, since nothing plays in the kitchen).
  - The same sheets, sized down.
- **Library:** every card in Day and Night, with its popups at phone size.
- **Theme:** a short sheet with colours, type, display whites and indicators.

### Orange (measured)
| Screen | Orange marks | What |
|---|---|---|
| Phone Living · Day | 0 | Nothing playing |
| Phone House · Day | 0 | — |
| Phone Living · Night | 1 | Pause (TV) |
| Phone House · Night | 0 | Film playing, so Goodnight isn't orange |
| iPad · Day | 0 | — |
| iPad · Night | 1 | Pause (TV) |
| Echo · Day | 1 | Pause (kitchen radio) |
| Echo · Night | 1 | Goodnight |
| Any home screen, door unlocked | 0 | The red Lock key takes over |
| After Goodnight has run | 0 | "Goodnight · done" is plain |

## Language check
**What ties it to the family:**
- **The state words**, under every name: On / Off / Offline / Locked / Unlocked / Playing / Idle.
- **Indicator windows:** dark recess when off, flat colour when on, never a glow. Round LED for the doors and the window, square for a chosen scene or speed, slot for playing, bar group for a room's lamps.
- **Type:** Jost for words, IBM Plex Mono for small numbers.
- **One orange per screen at most;** the solid red key for the one alert.
- **Lit power symbols** on plugs, appliances and the remote.
- **Pressed-in keys** for chosen things.
- **Walnut** as trim.
- **Seven-segment** only on appliances.
- **The motion character:** short settles, fades for sheets, nothing continuous on kiosks.

**What someone coming from another app recognises within a second:**
- the dark windows that light flat;
- the type pair;
- one orange key (or none);
- "On · group" written under a name.

The remote, purifier and source grid are the same objects as in the other HA passes.

**What's Jam Home's own:**
- the plan, the arc, the plates, the sideboard, the key rail, the door swing and the room strip;
- Jam Braun's warm white and anthracite instead of the shared aluminium;
- no black ribbed band on home screens;
- no accent (Stripes / Session blocks / Colour bars): the house's lamps are the colour.

## Rules I broke
| # | Rule (source) | What I did instead | Why Jam Home needed it | Verdict |
|---|---|---|---|---|
| 1 | Shared `alu`/`card` surfaces (BIBLE §2 Materials; every app's pass 3) | Jam Braun's page/plate (`#e7e3da`/`#f2efe8`, `#1c1c1a`/`#2a2a27`) | HA is the app Isaac uses in Braun; the direction asks for no identical backgrounds without a reason | **App-local** (surfaces per app; language keeps "warm neutral ground + one raised tone") |
| 2 | Black ribbed band as the signature surface (BIBLE §2; D47/D87 dock; pass 3 house strip) | No band on any HA screen; ribs only inside the TV's screen | The house state is the plan, not a band; ribs belong to screens and TV chrome | **Device family** (TV) / app-local elsewhere |
| 3 | Paddle window 18 × 7 lit in the device colour (D130, BIBLE §4) | The dimmer plate's paddle has no window; the lamp glyph's shade is the window | One colour cue per light (pass 3 audit #8 had three) | **App-local** |
| 4 | Four indicator shapes only (BIBLE §3; D158) | Two object-shaped windows: the lamp shade and the door swing | In a house, the object identifies itself faster than a generic dot | **Language-wide, amended:** keep the four generic shapes, and allow object-shaped windows that behave exactly like windows (dark off, flat fill on, never grow) |
| 5 | Orange order playing → on → idle; idle can be orange (D129, D82) | Home screens: orange only for playing media or bedtime; at rest zero. Media popups keep idle Play orange | "Too much orange"; calm overviews have nothing to press (agrees with D95/D139) | **Language-wide** (merge D95 + D129: overviews at rest have no orange; media homes keep Play) |
| 6 | Tab bars draw only the current tab's lit window (D12, D46, D91) | Every room tab has a window lit with its lamps; the current tab presses in | The tab bar doubles as the house at a glance | **App-local** (D91 stays for tab bars without state) |
| 7 | Lights are for indicators; controls don't glow, except lit power glyphs (BIBLE §3.1 + the lit-glyph rule) | Navigation tabs carry state windows; plugs' power keys light | A control may show its target's state if it's a window, not a glow | **Language-wide** (extend the lit-glyph rule to "a control may carry its target's state window") |
| 8 | Kiosk home = clock + facts + dock (D47, D87; Jam Braun's jam-kiosk) | Plan + arc + door/keys + sideboard + one key | Rooms are the way in; a dock of words is a template, not a house | **Drop** as a rule (kiosk layout is app-local) |
| 9 | Light colour never fills a whole card (B1, D45, D133 Band) | The plan fills whole *rooms* with lamp colour; plates have no Band, only the fader fill | A map of light is the honest place for colour; on cards it stays in the window and fader | **App-local** (plan only); **drop D133** (Band) for HA |
| 10 | One accent per screen in a clear zone (BIBLE §2 Accents) | No accent anywhere in HA | The lamps and the sun are the colour; an accent would compete | **Device family** (TV homes) / optional elsewhere: "at most one", not "one" |
| 11 | Room colours retired (B1); colour discipline (BIBLE §3) | People get printed colour tags on their keys | Identification, not state; printed, never lit (D89) | **Language-wide** (D89 extends to people) |
| 12 | Walnut = top trim line (BIBLE §2) | Walnut is the house's wood: key rail, cabinet top, room rules, "Here" pin | Trim placement is layout; the colour is the language | **Language-wide** colour, **app-local** placement |
| 13 | Kiosk clock 168 / 124 px (D51) | Echo clock 116 px | Needed the height for the arc row | **App-local** (sizes per device, floor stays 18 px) |
| 14 | Music tab as Play's home (D129, pass 3) | No Music tab; media lives on the sideboard and kitchen radio, and Play is primary in their popups | Rooms are the tabs; media belongs to the room it's in | **App-local** |

Rules I kept on purpose:
- never the same value twice (the kiosk plan hides the media slot for its own room, because the sideboard or radio already says it);
- kiosk no-scroll and the 18 px kiosk-home floor;
- state never by colour alone;
- the alert key;
- one popup sheet pattern (D43);
- seven-segment on appliances only;
- light display colours with the orange guard.

## Audit
Checked with Playwright (Chromium, `chromium.launch()` with no options). Screenshots are in the session scratch directory.
- **Viewports:** 1440 (light) and 390 (dark scheme).
- **States opened:** on each kiosk, every room sheet, the light popup, the offline popup and the bottom key; on the iPads, the Sideboard sheet, TV/source, remote, PC, and speaker plus Group or split; on the Echos, the kitchen speaker plus Group. That's 44 kiosk layer states, plus 8 kiosk home states (locked and unlocked).
- **Phone popups:** light, TV, speaker, PC, remote, Goodnight, offline.
- **Interactions:** a fader drag; Goodnight run on the night iPad.

Results:
- **No JS errors.** No horizontal page scroll at 1440 or 390, and none inside the phones or sheets.
- **Kiosks:** no element is clipped or outside the screen (0 of 52 states).
- **Text floors:** nothing under 18 px on the visible kiosk home (key-tag initials excepted, see #7), nothing under 15 px in kiosk sheets (remote engraving and appliance units excepted), and nothing under 12 px anywhere on the page.
- **Orange counts:** as in the table above.

**The fix pass corrected:**
- a muddy night plan (it averaged colours; now it uses the brightest lamp at a luminous opacity);
- a closed door that read as a dash (it now shows a faint arc and a hinge dot);
- the iPad sideboard overflowing at night with 11–12 px labels (it's now a silhouette plus an 18 px line);
- the Echo's key rail getting the phone variant, which pushed the bottom key 7 px off screen;
- kiosk state words at 14 px (now 16);
- "Radio" shown twice on the Echo;
- Goodnight staying orange after it had run;
- the sticky bar taking 160 px on phones.

| # | Problem | Severity |
|---|---|---|
| 1 | **The plan is invented.** I don't know the bungalow's real layout. A plan that's wrong is worse than no plan: people will look for the kitchen where it isn't. It needs a rough sketch from Isaac (room names and positions only, no address or dimensions). | High |
| 2 | **New HA work, not a theme.** The plan, arc, plates, sideboard, key rail, room strip and Goodnight are new custom cards (or big changes to jam-light, jam-tile, jam-media, jam-house, jam-kiosk, jam-tabs), and Goodnight needs an HA script. The room strip replacing HA's header tabs brings back a custom tab card (jam-tabs was dropped on 2026-10-27). | Medium |
| 3 | **The phone slide dimmer is 36 px wide** (under the 44 px target). The hit area has to be padded to 44 in the build, or the plate's fader needs widening, which squeezes the paddle. | Medium |
| 4 | **The House tab shows "which rooms are lit" twice:** in the strip's windows and on the plan. It's state, not a value, so "never twice" isn't strictly broken, but it's the same fact in two places on one screen. Option: unlight the strip windows while House is open. | Medium |
| 5 | **The Car port is a kitchen light** (inventory), so at night it lights the kitchen on the plan in "Clean" white. Outdoor lights need an "outside" zone drawn beyond the walls. | Medium |
| 6 | **Room fill = the brightest lamp only.** Marissa's room at night is "Neutral" cream though the pink fairy lights are on (the pink shows in the bar group). Low-level lamps read brownish at night (Master at 30 %). | Medium |
| 7 | **Key-tag initials are 9–11 px** on the kiosk. They're identification, with the name printed under them at 19 px, but they're text under the 18 px floor. | Low |
| 8 | **The sun is Braun yellow `#e8b12a`**, close to warn amber `#f2c14e`. Context (a disc on an arc) separates them, but a colour-blind viewer might not. The moon is cream. | Low |
| 9 | **The paddle's "top pressed = on"** is real-world rocker logic but has no window. A light that's on but dim relies on the word, the lamp window and the fader fill. Needs a hallway test with the family. | Medium |
| 10 | **Goodnight defaults are my guesses** (bedrooms left on, purifier to 25 %, the door always locks). Goodnight only takes the orange when nothing plays, so on a film night the iPad's orange stays on Pause until the film ends. | Medium |
| 11 | **The Echo's night radio label wraps** ("Kitchen · Idle" over two lines in 18 px caps). | Low |
| 12 | **The plan's labels are 18–22 px,** far under the ~65 px "read at all from 3 m" size. From across the room the plan reads by colour and shape. Fine for "which room is lit"; the names are for when you walk up. | Low |
| 13 | **Echo cost:** the plan is ~40 SVG elements with non-scaling strokes and one opacity fade. Probably fine on WebView 139, but unmeasured. | Low |
| 14 | **The phone header's door plate has dead space** next to the key rail. | Low |
| 15 | **Library popups are phone-size only;** kiosk popups are seen from the dashboards. | Low |

## Change suggestions for the next pass
- Draw the plan from Isaac's sketch. Add an outside strip (porch, car port, yard) so outdoor lights land outside the walls.
- Widen the phone slide dimmer's hit area to 44 px. Try a version where the whole plate is the slider and the paddle is a tap zone (fewer parts).
- Fill rooms with a two-stop split when two lamp colours are on (left/right halves, still flat).
- Let the House tab unlight the strip windows while it's open (audit #4).
- A screensaver variant: the night plan alone, dimmed, with the arc. That could replace the Clock/Photos screensaver at night.

## Bible implications
1. **Surfaces are per app.** Each app's page and raised-surface tones are app-local. The language only fixes "a warm neutral ground, one raised tone, soft shadow or hairline, no texture".
2. **Object-shaped windows.** Besides the four generic indicator shapes, an app may use object-shaped windows (a lamp shade, a door swing) if they behave exactly like windows: dark recess when off, flat fill when on, never growing, never glowing.
3. **Orange at rest is zero on overview screens.** Orange appears only for something happening (playing → Pause), a time-scoped routine (bedtime → Goodnight, only when nothing plays and only until it has run), or inside a media home (Play). This merges D82, D95, D129 and D139.
4. **A control may carry its target's state window** (extends the lit-power-glyph rule): a navigation tab's window lit in its room's colour, a plug key's power symbol.
5. **Kiosk layout is app-local.** The dock (D47, D87) stops being a rule. Kiosk floors (18 px home, no scroll, 44 px targets, one-shot motion) stay.
6. **Accents: at most one per screen, optional.** HA uses none.
7. **Walnut is a colour role, not a placement:** trim, wood fixtures, "here" markers.
8. **Printed colour codes may identify people** (key tags), never lit and never a state (extends D89).
9. **The ribbed band is TV-family chrome.** Outside TV apps it appears only where a screen is drawn (the TV inside the sideboard).
10. **D133 (fader Band) is dropped** for HA. A lamp's colour lives in its lamp window, fader fill and the plan.

## Questions for Isaac
1. **Can I draw the plan from the real house?** A rough sketch of room positions is enough, with no address or dimensions.
   *Recommendation:* yes. It's the single thing that makes the kiosk home work. Until then, the mockup's plan is a placeholder.
2. **Kiosk home: lit plan + day arc instead of the clock-and-dock?**
   *Recommendation:* yes on both kiosks, keeping the big clock top left. Rooms are 100+ px targets, and the plan answers "what's on where" from the sofa.
3. **Light cards as dimmer plates** (paddle + slide dimmer, lamp-shade window), replacing pass 3's card with a corner rocker and fader band?
   *Recommendation:* yes, with the dimmer's hit area widened (audit #3).
4. **Phone tabs become a room strip with lit windows, starting with House?**
   *Recommendation:* yes. Each person's phone opens on their usual room (HA's per-user default view).
5. **Who's home as keys on a rail** ("Away since 8:40", no location)?
   *Recommendation:* yes. It's friendly, and it says only what HA already knows (home/away).
6. **Do you want a Goodnight round?** If so, what should it leave on: bedrooms, the purifier, the porch light?
   *Recommendation:* yes, with bedrooms left on by default, the door always locking, and the window as a reminder only. Orange only when nothing is playing.
7. **No orange at all on a calm home screen** (daytime, nothing playing)?
   *Recommendation:* yes. Pass 3 had about one per screen; this makes orange mean "something is happening".
8. **TV, speaker and PC as one sideboard card**, and the Music tab gone?
   *Recommendation:* yes for the living room. The kitchen keeps its own radio, and Play stays primary inside each media popup.
9. **The forecast on the day arc** (marks at their hour), instead of a "sunny at 3 · high 70°" line?
   *Recommendation:* yes. One element instead of three lines, and it never repeats the clock.
