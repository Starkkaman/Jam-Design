# Jam Design handoff: the starting place (2026-11-06)

Isaac, 2026-11-06: *"Alright I think we have our starting place for this global look and design drafts that can be passed on to the other agents to incorporate."*

This file is what each project agent needs to begin. It sits above `BIBLE.md` (draft 0.5), which still describes the older Hi-Fi look in detail. **Where they disagree, this file wins** until the bible is rewritten.

All mockups in one place: https://claude.ai/artifact/U8RhAU69YzB7et7r7mmcfX (private to Isaac). The files are in `mockups/`.

## Ground rules (unchanged, from AGENTS.md)
- **Nothing is replaced or deleted without Isaac's OK.** Rollout goes one app or service at a time. Existing looks stay available until that app's turn.
- These are **design drafts, not specs to copy pixel for pixel.** Bring the language into your app with your app's real data and constraints, and tell Isaac where reality disagrees.
- Write back in `projects/<your-app>/PROPOSALS.md` in this repo. Don't edit BIBLE.md, decisions.md, tokens/ or mockups/.
- No secrets, private hostnames or personal data in the repo.

## The global look: calm instruments, bespoke per app
One shared **language**, each app a **design of its own** (Isaac: "Everything should feel like it has the same design language, not necessarily the same design").

1. **Calm first.** The calm of *Braun Instrument* and *Flight Instrument* (`mockups/01-directions.html`, panels B and D): ordered, quiet surfaces, generous space, few things per screen. "All fine" looks like nothing.
2. **Less realism.** Don't draw real-world objects as UI: no racks, cables, cabinets, furniture, marquees, plates, grain, glow or brushed metal. Each app is bespoke through its layout, type, palette and one or two signature shapes.
3. **Palette: Callsheet's.** Isaac's favourite. Base tokens (from Callsheet rounds 5 and 6):

   | Role | Day | Night |
   |---|---|---|
   | Ground | `#ece7dd` | `#10141d` (navy) |
   | Panel | `#f7f4ee` | `#161c28` |
   | Ink | `#19202e` | `#ece5d3` |
   | Orange (the one action) | `#ec7c22` | `#f08a2c` |
   | Walnut (house wood, rules and edges) | `#6b4428` | `#6b4428` |
   | ok / warn / alert | `#7bd651` / `#f2c14e` / `#ff5a48` | same |

   Exact values are in `mockups/pass6/callsheet.html` `:root`. Apps may shift these slightly to suit their purpose (JamFin uses the navy night as its base).
4. **Type:** Jost for words, IBM Plex Mono for small labels, times and numbers (uppercase labels about 13 px with wide tracking). No serifs.
5. **Dense information is broken into calm groups:** panels with a hairline edge and soft corners, no shadows, one idea per panel (Callsheet round 6).
6. **Almost no indicator lights in menus.** A light appears only where it carries real status (an alert, offline, something running). Focus is a cream outline or fill plus a small lift, never a lit dot.
7. **Orange is the one thing to do now:** at most one per screen. Calm screens, reading pages and settings have none.
8. **Red means alert.** The fix is a solid red key with dark text, and nothing else on that screen is orange.
9. **State is colour + shape + word,** never colour alone. Shared state words: on, off, offline, action, alert, plus warn (amber + ▲). Quiet past forms: "Seen 06:20", "Fixed 01:53".
10. **Switches:**
    - **Lights:** the ON/OFF paddle, where the pressed half is the state.
    - **Everything else** (plugs, fans, settings, automations, app options): the **channel-reveal switch**. It's small; off is a plain dark channel, and on, the thumb slides and an accent colour is revealed in the channel. It's flat, takes ~180 ms and is instant in Calm.
    - **Accent rule (Isaac's choice): colour by kind, with a per-device override** the user can set. This applies in every app, not just Jam Home. Kind colours start from `mockups/pass7/switch-study.html` / `notes/pass7-switches.md` option B: plugs/power blue, air/climate teal, automations violet, settings steel. Accents never use the control orange or the ok/warn/alert colours.
    - The switch is also a subtle accent in other apps' settings; the switch study shows it in each.
    - It's never used for lights, destructive actions, things that aren't instant, or choices with three or more options.
11. **TV:**
    - The **split shutter** title card is the launch and Play transition: flat halves part, and a slatted bar shows the real load (hold = max(load, 600 ms); Calm = short fade).
    - Floors: 5% safe area, text ≥22 px at 1080p, transform/opacity motion only, focus ≤150 ms, flash and glare floors.
12. **Say it once, in plain words.** No value twice on one screen. Every failure says what happened and ends with Try again and a way home.

Full reasoning and the earlier rule-by-rule sort: `notes/RULES-TIERS.md`. Its language list still holds, except where items 1, 2, 6 and 10 above override it.

## Per app: your starting draft

| App | Start from | Notes | What Isaac said |
|---|---|---|---|
| **Callsheet** | `mockups/pass6/callsheet.html` | `notes/pass6-callsheet.md` | Loves round 5's colours, type and vibe; round 3's grouping was calmer; Ask must be a proper chat. Round 6 does all three. |
| **JamFin** | `mockups/pass6/jamfin.html` | `notes/pass6-jamfin.md` | Geometric shapes behind titles; split shutter back; scrap the lights in menus; theatre feel, less literal; Callsheet's dark palette. |
| **Jam-Dash** | `mockups/pass6/jam-dash.html` | `notes/pass6-jam-dash.md` | Round 3's design was his favourite; no skeuomorphism; keep the "see how containers connect on hover" trace. |
| **Jam Home** (HA: Jam Theme + Jam Cards) | `mockups/pass7/home-assistant.html` (switches) on top of `mockups/pass6/home-assistant.html` | `notes/pass6-home-assistant.md`, `notes/pass7-switches.md` | "This design looks much better!" Switch colour by kind with override. **To fix in the real build:** the paddle's OFF state isn't clear enough now that ON is so strong; give OFF its own clear marking. Very minimal kiosks; keep the remote; no sideboard, plan views or key rail. **Add the Goodnight list back** (see the answers below). |
| **Lobby** (TV launcher) | `mockups/pass6/tv-launcher.html`, for reference only | `notes/pass6-tv-launcher.md` | **Not started.** Isaac doesn't know yet what he wants. Round 6 is only a clean-up: no Home Assistant except maybe the door-lock status, no audio settings up top, less silly. Don't restyle Lobby until he decides. |
| **NervOS** | none | none | **Paused.** Isaac likes what NervOS already has. Don't restyle it until he says so. |

## Answered after handoff (Isaac, 2026-11-06)
1. Switch accent in the other apps: **by kind as well**, the same rule as Jam Home.
2. Air purifier power: **the small switch** for now ("I may change my mind").
3. Lobby and NervOS: Isaac will work with each app's agent directly on how it should feel.

4. Goodnight in Jam Home: **yes, bring it back** ("Yes absolutely I want that"). As a plain list, with no floor plan:
   - one sheet listing everything still on or open;
   - each row has Turn off / Leave on keys;
   - one Goodnight press does it all, and the door always locks;
   - afterwards it shows "Goodnight · done 9:41".

   Defaults:
   - shared rooms and outside: off;
   - bedrooms: left on;
   - TV: left on while it's playing, otherwise off;
   - purifier: night speed 25%;
   - window: a reminder only.

   On a kiosk it fits without scrolling. Goodnight is the screen's one orange, only when nothing is playing and only until it has run. Full spec: `notes/pass5-home-assistant.md` (the Goodnight row), restyled in the round 6/7 look.

## Where to find things
- `decisions.md`: every decision, with Isaac's words.
- `notes/REVIEW.md`: all rounds with links.
- `notes/pass*-*.md`: each round's audit and reasoning.
- `notes/pass5-journeys.md`: the seams between apps. The two that matter most:
  - one app owns each fact and the others quote it;
  - one device inventory, from Home Assistant.
