# TV launcher (Lobby) · Pass 6: the clean-up

Mockup: `mockups/pass6/tv-launcher.html`. Earlier passes are unchanged.

This round is **only a clean-up**. Isaac paused Lobby ("I hate how it looks, but I don't know what I want"), but he also gave clean-up notes. So this is a calm starting point for when he's ready, not a new concept.

**How to review it:** press **▶ Tour** (20 steps, about 4 s each, with captions) or **Next step ›**. Click the TV and use the keys: arrows move, Enter is OK (it acts on release), Esc or Backspace is Back, H is Home, S is Settings. The buttons under the TV do the same on a phone. Page controls: Home layout A/B, TV lighting Night/Day, Motion Full/Calm, Front door Locked/Unlocked/Not shown, Switch 2 On/Asleep, page theme. Under the TV, **the two layouts are shown side by side** at rest. They follow the controls.

All titles, art and times are made up. The house name "Bungalo", the app list, the Switch 2 on HDMI 2, the antenna, the front door and "paused by Isaac" come from the Lobby README.

## How I read Isaac's notes

| Isaac said | What I did |
|---|---|
| "The design is very fun… but I don't think I like it. Once again I think too much reality is poking through." | Removed the whole room: sky window, sill and frames, lowboard, three-band dial and needle, socket panel, wall plates, blind and drawer. Nothing on screen is a drawn object. Bespoke now comes from layout, type and palette. |
| "I don't need home assistant on there, except maybe the door being locked… that is kind of nice…" | Lamps, mood lighting and the dimmer plate are gone. The front door is **one line of text**: a small lock outline and "Front door locked", in dim ink. When it's unlocked, it turns amber ("▲ Front door unlocked") and a **Lock** key appears beside it. The TV can lock the door but **never unlocks it** (decided: it removes the hold-to-unlock flow and the guest risk). Settings › Front door on Home can hide the line. |
| "I don't need audio settings up top." | Picture mode, sound mode and sound out are gone from Home. They live in **Settings**, the one quiet place for the TV: one word in A's top line, or the last entry of B's index. |
| "I think this is trying to be too many things and be too silly at the same time." | Four jobs only: Continue, Apps, Inputs, Settings. No idle face, no CEC prompt, no update light, no arrange mode, no rename keyboard, no day strip. Text is plain; there are no jokes or room metaphors. |
| "Clean up the design." | Callsheet round 5's night navy and type, few things per screen, big words, generous space. |
| (all apps) "The lights just look dumb and cheesy on the TV menu (honestly all menus)." | **No indicator lights at all** on Home or in Settings. Focus is a flat cream fill (keys, words, rows) or a cream ring (covers), plus a small lift. The only square left marks the current option inside a chooser. |
| (all apps) "Looking back at flight instrument and Braun instrument… we need to bring their calmness back in." | B's calm surfaces and order, D's mono labels on graphite (here navy). The big light clock in layout B is the most "instrument" moment. |
| (JamFin) "I miss the split shutter animation." | Launch uses the house **split shutter**, flat: the top half slides in from the left and the bottom half from the right, the title sits on the seam, and the slatted bar shows the real wait (hold = max(load, 600 ms)). Then the halves leave the other way. It has no texture or grain. The Stripes accent stays in the top half's corner, as recorded for the title card. Calm is a 140 ms fade. |
| (Lobby/NervOS) "I hate how it looks, but I don't know what I want." | **Two Home layouts** to react to, plus questions below to help him decide. |

## What changed since pass 5

| Pass 5 | Pass 6 |
|---|---|
| Sky window following HA sun times, with a darker sky in bright picture modes | A flat navy ground (`#10141d`). The TV Day option is mid-light warm grey (`#cdc8bd`) with navy ink, never paper-white. |
| Walnut sill with picture frames (Continue) | Plain covers: art, a 6 px cream progress line on the bottom edge, and a title underneath. |
| Three-band receiver dial with a needle, 18 slots, All apps A to Z, Arrange | **A:** six apps as words plus All apps (A to Z). **B:** all twelve apps in a 4 × 3 grid. No arranging is drawn this round. |
| Socket panel with five ports and LEDs | Two input keys, "Switch 2 / HDMI 2" and "Live TV / Antenna". Empty ports are hidden (Settings › Empty inputs). |
| House plate: three lamps with dimmers and the door swing | One line for the front door, and Lock when it's needed. |
| TV readout "TV Theater night · Optical" at the top, and a drawer with Picture, Sound, Sound out, Sleep, Front door and Settings | Settings: Picture mode, Sound mode, Sound out, Home layout, Front door on Home, Empty inputs, Sleep timer, About. OK opens a small centred chooser (5 rows at most); Back keeps the current value. |
| Blind with slats as the title card | The flat split shutter (above). |
| Warn by day / red after sunset for the door | Amber warn only, because the TV never unlocks it and offers Lock in one press. No red on Home. |
| Idle face, Power drawer, Restart, CEC prompt, update light | Not drawn. Parked, not rejected. |

## Design

**Palette and type (from Callsheet round 5, night):** ground `#10141d`, cards `#1a2130`, rule `#2a3244`, ink `#ece5d3`, second ink `#d2cbb9`, dim `#a29d8e`, cream `#f3e6c8` (focus and progress), orange `#f08a2c` (only Try again on a failure). Jost for words, IBM Plex Mono for the house name, group labels, ports and the shutter eyebrow.

**A · Shelf (everything on one page).**
- **Top line:** BUNGALO on the left. On the right: the door line, a hairline, the time, "Thursday, November 5 · 57° cloudy", and **Settings**.
- **Hero:** the focused thing in one title (76 px), one detail line, and the OK action ("OK Resume").
- **Continue:** five covers with a 25 px peek of the sixth, and "n of 6" beside the label. The row stops at its ends with a nudge.
- **Apps and Inputs:** one row of words underneath. Jamfin, YouTube, Netflix, Prime Video, Dropout, Moonlight and All apps, then the Switch 2 and Live TV.

**B · Panel (one group at a time).**
- **Left column:** BUNGALO, a big light clock (132 px Jost 300), the date and weather, then an index of four words (Continue, Apps, Inputs, Settings) and the door line at the bottom.
- **Right side:** the chosen group only. Continue is 3 × 2 covers, Apps is 4 × 3 words, Inputs is two big keys, and Settings is the rows.
- **Moving around:** → goes into the group, and ← from its left edge (or Back) returns to the index. While focus is on the index, the right side's heading describes the group ("Six things you started, newest first", "→ Go in"), so the word isn't said twice. The current group keeps a small cream dot beside its name.

**Shared:**
- Focus is a cream fill or ring plus a 3–6 px lift, ≤ 150 ms. The colour snaps, and only transform moves.
- OK acts on release.
- Changing groups in B swaps the panel and fades it up in 160 ms (opacity only).
- **Failure:** if the Switch 2 is asleep, the shutter stays closed. The bar stops and dims at about 30%, the screen says "No picture on HDMI 2. Turn on the Switch 2, then try again.", and it offers **Try again** (orange) and **Home**.

## Audit

Checked with Playwright (Chromium, `chromium.launch()` with no options): all 20 tour states at 1500 px wide × 1.31 DPR (TV ≈ 1920 px), plus a real-keyboard run (Down, Right × 6 to All apps, OK, Back; Up to Settings, Home layout → Panel, Back), mid-shutter and no-signal shots, 390 px light and dark. Screenshots are in the scratch dir.

Checks on every state:
- every visible TV text ≥ 22 px at 1080p;
- all text inside the 96/54 px safe area (except the cover peeking past the row's edge);
- no clipped text;
- no JS or console errors;
- `scrollWidth` 390 at 390 px.

**All passed after the fix pass.**

Glare at rest (share of a 960×540 downsample above relative luminance 0.5; cap 10%):

| State | Glare | Saturated red (cap 25%) |
|---|---|---|
| A Home, night | 1.1% | 0% |
| A Settings with chooser | 2.3% | 0% |
| B Home, night | 1.4% | 0% |
| B Apps | 1.0% | 0% |
| No signal | 0.6% | 0.5% (the stripe) |

**Fixed in the fix pass:**
- B's index and the panel heading shared a class name, so "Go in" sat inline with the title.
- Changing Home layout from inside Settings left the old layout under it, and a JS error followed on Back.
- A 3 px sliver of the sixth cover's title showed at the safe edge. Covers are now 316 px with a deliberate 25 px art peek, and titles of covers out of view are hidden.
- The "Back" hint badge was too narrow for its word.
- B's house name sat 4 px above the safe line.
- The tour counted presses and landed on Live TV instead of the Switch 2. It now focuses by key.

**Fresh-eyes pass** ("is this calm? would Isaac call any part cheesy?"):
- Nothing on Home glows, blinks or pretends to be an object.
- The one thing that could still read as decoration is the Stripes accent on the shutter. I kept it because it is the approved house title card and it's only on screen for about a second.
- In B, a heading that repeated the index word ("Continue" twice) was replaced by the group's description.

| # | Problem | Severity |
|---|---|---|
| 1 | **A still has three things competing:** the hero, the covers, and the apps and inputs row. It's calmer than pass 5, but it's still "everything at once". That is the main trade-off against B. | Medium |
| 2 | **B hides two of the three groups** behind one press. Isaac called hidden navigation "atrocious" on Jam-Dash, but he also asked for fewer things. Only his reaction can settle it. | Medium |
| 3 | **The hero repeats the focused cover's title** (the hero and the label under the art). This is Lobby's long-standing stage pattern, but it is a "say it once" bend. Dropping the labels under the covers is the next simplification to try. | Low |
| 4 | **A's empty right half of the hero band.** It's intentional space, but someone may want something there (cover art, the clock). Leave it empty unless Isaac asks. | Low |
| 5 | **Apps are words only, with no logos or marks.** Guests looking for "the red N" still have to read. Pass 5's decision stands. | Low |
| 6 | **Door status depends on HA via Control Freak.** If HA is unreachable, the line should say "Front door: no data" (dashed). Not drawn. | Low |
| 7 | **Not drawn this round:** All apps arranging, renaming inputs, sleep/power, idle face, CEC prompt, updates, Lobby crashing. All parked until Isaac picks a direction. | Low |
| 8 | **Nothing is measured on Phoster:** focus legibility at 3 m, the shutter's cost in the WebView. | Medium |
| 9 | **TV menu over an app** (pass 3–5 risk) is dropped from this round. Settings is reachable only from Home. That's simpler, but it means two presses (Home, then Settings) to change picture mode during a film. | Low |

## Questions for Isaac

These are meant to help find out what you want Lobby to be, more than to approve this round.

1. **When you press Home, what do you want first: the thing you were watching, or the choice of what to do?**
   *Recommendation:* the thing you were watching (both layouts open on it). If you'd rather see the choices first, B's index is the start of that.
2. **Everything at once (A) or one group at a time (B)?** A shows it all with no presses; B is quieter, but the other groups are one press away.
   *Recommendation:* try B on the real TV for a week. You said this one is "trying to be too many things", and B is the version with fewest things per screen.
3. **Should Home show pictures (covers) at all, or only words?** A words-only Home would be the calmest version possible, and the covers would appear only in the hero.
   *Recommendation:* keep covers for Continue only. They are the fastest way to recognise what you were watching.
4. **Is the front-door line worth its place, and should the TV only ever lock (never unlock)?**
   *Recommendation:* keep the line and lock-only. It's the one Home Assistant thing you called "kind of nice", and lock-only removes the risk of a guest unlocking the door.
5. **Which existing screen do you like living with most** (a streaming app, Google TV's home, NervOS's original, Callsheet)? Naming one gives the next round something real to aim at.
   *Recommendation:* point at Callsheet's night sheet. This round already leans on its palette, so the next round could also borrow its grouping and rhythm.
6. **Is there anything about the TV you'd want Lobby to show that isn't here** (the time a film ends, what's playing in the house, the weather in more detail)? Or is "less" the point?
   *Recommendation:* less. Add one thing only when you miss it.
