# Jam Home switches + the channel-reveal switch · Pass 7

Mockups:
- `mockups/pass7/home-assistant.html`: round 6 with only the switches changed.
- `mockups/pass7/switch-study.html`: the small switch as a shared component, and how it sits in the other apps.

Earlier rounds are unchanged. Nothing here changes Home Assistant or any other app.

## Isaac's note (after round 6, verbatim)

> "The only real issues I have are in Home Assistant it's confusing if a switch is on or off, and the same switch is everywhere. It makes sense for lights to have a switch like that, but the others could be smaller switches that have an accent color in the channel that is reveled when it's on. Could be an interesting subtle accent in other designs as well."

He raised no other issues with round 6, so everything else is kept as it was: the minimal kiosks, the remote, the media cards, the popups, the air purifier, the palette and type, and the one-orange rule.

## What I did

| Isaac | Round 7 |
|---|---|
| "it's confusing if a switch is on or off" | **On is now a solid block. Off is flat.** In round 6, the "pressed" half was a slightly deeper fill with an ink edge, and both states looked like something was pressed. Now, when a light is on, its ON half is filled solid and the paddle's rim takes the same colour. By day the fill is navy ink, with the ON legend and an 8 px band (kiosk; 5 px phone) in the lamp's colour. By night the fill is the lamp's own colour, with a navy legend. When a light is off, the whole paddle is the plain card colour, OFF is in ink and ON is dim, and nothing looks pressed. Squint test (screenshots shrunk to ¼ and blurred): Day on = a dark block, Night on = a bright block, off = nothing, in every case. |
| "It makes sense for lights to have a switch like that" | **Lights keep the paddle**, with their faders. The light-group members in the light popup keep the mini paddle, with the same treatment. |
| "the others could be smaller switches that have an accent color in the channel that is reveled when it's on" | **Everything else that is plainly on/off is now a small switch:** the Tree plug, Fan / blanket, the air purifier and dehumidifier power (they replace the round power key), speaker Group or split (phone popup and kiosk Music sheet), and a new **Automations** block in the phone light popup ("On at sunset", "Off when everyone's out"). Off, the switch is a plain dark recess channel. On, the thumb slides right and the channel reveals a flat accent behind it. |
| "Could be an interesting subtle accent in other designs as well" | `switch-study.html` shows the same switch in Callsheet Setup, JamFin Settings › Appearance (TV), Jam-Dash app settings and Lobby Settings (TV), each with an accent from its own palette. |

**Additions beyond a straight swap:**
- **Automations.** Round 6 had none, and Isaac's list implies them, so I added a two-row Automations block. It's on phone light popups only, to keep the kiosk light popup as it was.
- **Two page controls,** at the top of the page:
  - *Switch accent* (A/B/C), which applies a rule to the whole page;
  - *Motion* (Full/Calm).
- **Section 2a,** which compares the accent rules.
- **Two library entries:** Small switch · states, and Automations.

## Accent options and the recommendation

All the accents share one lightness. They differ only in hue. They're fitted so that the channel stays at least 3:1 against both the off channel and the thumb, in both lightings. That only works in a narrow lightness band: relative luminance 0.15–0.28 by day and 0.11–0.23 by night. The page compares the three rules side by side in **section 2a**.

| Rule | Day / Night | What it says | Problem |
|---|---|---|---|
| **A · One house accent (recommended, the default everywhere)** | Callsheet blue `#6780b4` / `#5971a4`: Callsheet's navy ink's hue (264°) lifted | "On." Nothing else. | It's near Isaac's person tag blue `#3f6fb5` (OKLab Δ 0.04–0.07). The tag is a 20 px letter square in the house strip; the switch is never next to it. |
| B · Colour by device kind | Plugs/power blue (as A); air and climate teal `#43899a`/`#337b8c`; automations violet `#8f72c0`/`#8063b1`; settings steel `#71819c`/`#64738d` | The kind of device | It's a legend to learn. Teal is the nearest of the set to the ok green (Δ 0.14–0.15). Five colours on one Lights sheet is busier than Isaac wants the kiosk. |
| C · The device's own colour | A lamp's automations take the lamp's colour, fitted. The Tree is pine. The rest fall back to A. | Which lamp | Cozy white fits to `#a07a3a`, Δ 0.13 from the control orange, which breaks the 0.15 guard. The pine Tree is Δ 0.07 from the ok green. It fails the "not orange, not status" rule on real data. |

**Why A.**
- Isaac said "an accent color", singular.
- The calm we're after (Braun / Flight Instrument) is one accent.
- It's the only rule that can't collide with orange, warn, alert or ok.
- The lamp's own colour already lives in the paddle and fader, so the small switch doesn't need to repeat it.

**The other apps (each in its own palette, all the same lightness):**

| App | Accent | Day / Night |
|---|---|---|
| Callsheet | Callsheet blue (the source of A) | `#6780b4` / `#5971a4` |
| JamFin | plum, from the title shapes | `#ac6b97` / `#9d5d88` |
| Jam-Dash | steel, from its key-line grey, kept low because its green, amber and red are service status | `#71819c` / `#64738d` |
| Lobby | teal, from its deep teal art tones | `#43899a` / `#337b8c` |

## Component spec: the channel-reveal switch

**Parts.**
- **Channel:** a pill, dark recess.
- **Reveal:** the accent, a flat fill under the channel, clipped.
- **Thumb:** a flat disc, inset by the gap. Left = off, right = on.

**Colours (shared by every app; only the accent changes).**

| Token | Day | Night |
|---|---|---|
| Channel, off | `#1c2331` | `#05070b`, plus a 1 px `#2a3244` hairline so it reads on the navy card |
| Thumb | `#fbf9f4` | `#ece5d3` |
| Accent | per app, above | per app, above |

**Sizes** (CSS px; TV in 1080p px).

| Use | Channel | Thumb | Gap | Hit area |
|---|---|---|---|---|
| Phone | 46 × 28 | 22 | 3 | 62 × 44 |
| Kiosk | 66 × 40 | 32 | 4 | 78 × 56 |
| Desktop | 36 × 22 | 16 | 3 | 48 × 38 (pointer) |
| TV | 76 × 44 | 34 | 5 | the whole row (D-pad) |

Width ≈ 1.65 × height, and the radius is always full. The label is on the left and the switch at the end of the row.

**Motion.**
- The thumb moves with `transform: translateX(w − h)`.
- The reveal is `clip-path: inset(0 100% 0 0)` → `inset(0)`, so the colour opens from the left edge and appears to come out from behind the thumb.
- Both take **180 ms** on the house settle curve `cubic-bezier(.16,1,.3,1)`.
- No fade, glow, bounce or colour transition.
- **Calm and `prefers-reduced-motion` make it instant.**
- In the mockup, the switch flips in place and the page re-renders after the reveal, so the motion is visible.

**States.**
- **Off:** plain dark channel.
- **On:** the accent is revealed and the thumb is on the right.
- **Pressed:** the thumb scales to 86 % in place.
- **Disabled:** a hollow channel (1.5 px rule) and a grey thumb, with the reason given nearby.
- **Unavailable / offline:** a dashed outline, no thumb, a centred dash; the row's word says "Offline". It isn't clickable.
- **Focus (keyboard):** a 2 px ink ring, offset 3 px.
- **Focus (TV D-pad):** the whole row takes the app's focus treatment (a Lobby row fills with the focus colour; JamFin draws its ring round the switch). On a filled row, the channel gets a 2 px rim in the row's ink, so the dark channel never melts into a navy (Day) focus row.

**Semantics.** A `<button role="switch" aria-checked>` with the setting's name as its label. It is never used as a status indicator.

## Where it applies

- **Jam Home:**
  - Tree and other plugs (jam-tile `switch.*`);
  - Fan / blanket;
  - air purifier and dehumidifier power (jam-fan);
  - speaker group/split;
  - automations;
  - future yes/no settings in popups.
  - **Lights keep the paddle.**
- **Callsheet Setup:** the checkboxes that apply at once: "Tell me when it's ready" (Sam's phone, Kitchen tablet), "Ask on this device", and a person's "Always counts". Lighting (three choices) stays a segmented key, and Start over stays a key with a confirm.
- **JamFin Settings › Appearance:** Animate Back, and Covers read as "Toned covers" on/off. Lighting, Title shapes and Motion keep their choice keys.
- **Jam-Dash app page:** a Behaviour card (Restart if it stops, Update by itself, Show on Home, Tell me when it's unhealthy). Stop, Restart and Update stay keys.
- **Lobby Settings:** "Front door on Home" and "Show empty inputs" (both two-way choices today). Rows with more options still open the chooser.

**Where it should not be used:**
- **Lights:** they keep the paddle.
- **Anything destructive** (Start over, Remove account, Delete, Forget): use a key with a confirm.
- **Anything that isn't instant or can fail** (Lock, TV on, Wake, Start/Restart a service, link Signal): use a key that says "Locking…" and then the result.
- **Choices with three or more options.**
- **Status display.**

## Audit

Checked with Playwright: Chromium, `chromium.launch()` with no options, screenshots in the session scratch dir.
- **Viewports:** 1440 (light scheme) and 390 (dark scheme), for both pages.
- **Jam Home, every kiosk screen:** each of the four kiosks (iPad and Echo, Day and Night) opened at home and in every sheet and popup: Lights, TV, Music, Remote, Light, All off.
- **Accent rules:** all three applied page-wide.

**Results:**
- **No JS errors.** The only external requests were Google Fonts.
- **No horizontal overflow** at 1440 or 390, on either page.
- **Kiosks:** no element outside the screen, and nothing scrolls in any home, sheet or popup.
- **Text floors:**
  - kiosk homes ≥ 18 px;
  - kiosk sheets and popups ≥ 15 px (the remote's 12 px engraving is excepted, as in rounds 4–6);
  - everything else ≥ 12 px;
  - TV frames in the study ≥ 22 px at 1080p.
- **Switch contrast,** computed from rendered colours for every live switch (59–61 per Jam Home state, under all three rules; 46 on the study page): channel-on vs channel-off and thumb vs channel are all ≥ 3:1 in both lightings, with 0 failures. Worst case is 3.74:1 (thumb vs on, Day). The off channel vs the thumb is 15.0 (Day) and 16.1 (Night).
- **Motion:** the thumb was caught mid-travel 60 ms after a click (translateX 2.6 px). The transition is 180 ms; with Calm it is 0 s.
- **TV:** D-pad focus and Enter toggled "Show empty inputs" in the Lobby Day frame.

**The fix pass corrected:**
- the paddle's lamp colour resolving to cream (the custom property was set on the theme root, not the paddle);
- state labels overlapping in the study's state grid;
- a class clash between JamFin's row label and the Lobby frame;
- a Callsheet Night frame titled "Setup · Day".

| # | Finding | Severity |
|---|---|---|
| 1 | **By day, "on" is a dark block.** The navy ON block reads at once from 3 m (squint test), but "lit = dark" is a reversal of Night's bright block. The lamp-colour legend and band carry the link to the lamp. Check that it reads naturally on the real iPad. | Medium |
| 2 | **The accent band is narrow.** With a near-black channel and a pale thumb, every accent must sit at luminance ≈ 0.17–0.22, so all app accents are mid-tones of equal weight. That's fine for "subtle", but there's no room for a bright accent without changing the thumb or the channel. | Medium |
| 3 | **Rule C fails the colour rules on real data.** Cozy white → `#a07a3a`, Δ 0.13 from the control orange (guard 0.15). The pine Tree is Δ 0.07 from the ok green. Shown in the compare panel; not recommended. | Medium (only if C is chosen) |
| 4 | **The house blue is near Isaac's person tag** (Δ 0.04–0.07). They never sit next to each other, but someone could read it as "Isaac's". | Low |
| 5 | **The purifier lost its round power key with the green-lit symbol,** which round 6 kept as part of its appliance character. The brief and Isaac's note put purifier power on the small switch. The seven-segment readout still carries "running". | Low |
| 6 | **The Tree card on the kiosk Lights sheet is mostly empty space** (a name and a switch at the foot, the same height as the paddle cards). It's calm, but a reader may expect more in it. | Low |
| 7 | **Rollout:** the switch is card code (jam-tile, jam-fan, the speaker card, the light popup), not a theme key, and the new automation rows need `automation.*` entities wired in. In Callsheet, JamFin, Jam-Dash and Lobby it replaces existing checkboxes and two-way choices, on each app's own turn. | Low |

## Questions for Isaac

1. **Day paddle: is a dark ON block right for "lit"?** The alternative is the lamp's colour as the block by day too, but warm whites almost vanish on the paper (1.03–1.35:1), which is the confusion you described.
   *Recommendation:* keep the dark block by day. It's the only version that passes the squint test.
2. **Accent rule: one house blue (A), colour by kind (B), or the device's own colour (C)?**
   *Recommendation:* A. It's what you described ("an accent color"), and B and C either add a legend or collide with orange and the status colours.
3. **Should the other apps use their own hue (plum, steel, teal) or all use the same house blue?**
   *Recommendation:* their own hue, at the same lightness. It's the same part with the app's own accent, which fits "a shared language, not a shared template".
