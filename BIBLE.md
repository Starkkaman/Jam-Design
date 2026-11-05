# Jam Design Bible — working draft 0.3

> **Status: draft. Nothing here is approved for shipping.** The base look is still being designed with Isaac. Source of every decision: [`decisions.md`](decisions.md). Visual reference: [`mockups/`](mockups/), latest first.

## 1. The brief

**Clarity without ever sacrificing fun.** Isaac has given this brief, in some form, to every project.

Inspiration: 70s NASA, Dieter Rams, TNG/Voyager interiors, Ralph McQuarrie and Syd Mead, Cowboy Bebop, Evangelion, Miyazaki and Satoshi Kon, mid-century modern furniture, the Atari 2600, Fallout. *"A retro design lover, but also a lover of clean, effective design."*

Three people live in the house. The default look has to feel friendly to all of them, not like a cockpit.

## 2. The base look: Hi-Fi

The house as a piece of 1970s hi-fi equipment: brushed aluminium, a black ribbed band, walnut trim, orange controls, lit indicator windows. Flattened to "a touch + depth", not full skeuomorphism.

**Rejected on the way:** Telemetry ("feels like every other good responsive UI"), Mission Control (too nerdy for the household), Starliner ("first draft AI design"), Postcard, serif display type.

### Materials

| Role | Day | Night | Use |
|---|---|---|---|
| `alu` | `#dcd9d3` | `#232220` | Base surface |
| `card` | `#eceae6` | `#2c2b28` | Raised cards, list cards |
| `rule` | `#c4c0b7` | `#3a3935` | Dividers, switch track (day) |
| `ink` / `dim` | `#1d1c1a` / `#5f5c55` | `#eeeae2` / `#aaa69c` | Text |
| `band` | `#1d1c1a` | `#121110` | The black ribbed band (continue watching, dock, fixed TV panels). Also the TV ground colour, flat. |
| `walnut` | `#5b3a22` | same | 8 px trim line at the top. Colour only, no woodgrain. |
| `orange` | `#e8641c` | `#f07432` | **Controls only**: the thing you press, the "on" paddle |

- Texture: ribs on the band, 1 px line every 10 px at about 7% white. They must read as lines from normal viewing distance.
- **On TV, ribs only on fixed surfaces** that don't scroll (menu band, player band, title card), drawn once into a cached bitmap per size and never animated. Grounds behind scrolling rows are flat. (A full-screen texture costs 3–9 ms a frame on the Hisense.)
- Depth: three layers. Aluminium base, then floating cards, then the band on top casting an upward shadow. Buttons are bevelled and press down 2 px. Switch tracks and meter faces are recessed.
- Light and dark follow the device. **TV defaults to dark**, with a mid-light Day option (never paper-white) in every TV app.

### Type
- **Jost** for everything you read as words. Uppercase labels at 12 px with 0.16em tracking.
- **IBM Plex Mono** for numbers in lists and labels; **seven-segment** for big live readouts.
- No serifs.

## 3. Light

Light is the signature of this look. The rules:

1. **Lights are for indicators, never controls.** Status lights, meters and progress glow. Switches and buttons use colour and position only. They never glow.
2. **The one exception is a slider.** It reveals light up to where you set it, because the light *is* its reading.
3. **Every light sits behind a window you can always see.** Unlit, the window is a visible recess. Lighting it only changes what's inside.
4. **A window never changes size and never extends past the edge of its object.** Selecting something lights its window; nothing grows.
5. **Nothing is more realistic than its neighbours.** Lights match the depth of the surface around them.
6. **Light colours:** ok `#7be04f`, active `#ff7a2e`, warn `#ffc23d`, alert `#ff4b3a`, info `#fff1dc`. Indicators aren't only green and aren't only round.

### Indicator shapes

| Shape | Means | Example |
|---|---|---|
| Round LED | One thing's status | Door locked, device online |
| Square | A mode that's selected | Movie scene, Away |
| Slot | Something running | Music playing, syncing |
| Bar group | A count | 3 of 5 lights on |

### Signature move: light reveal
When something becomes active, its light is revealed: a shutter slides back, or a glow warms in (about 400 ms in, 180 ms out). Nothing flashes on. Implemented with transform and opacity only, so it's cheap on the TV boxes.

- **Every glow and soft shadow is a pre-rendered sprite** (nine-patch or cached bitmap) on its own layer. Lighting up = that sprite's opacity going 0 → 1. No runtime blur on TV. Hard drawn shadows are fine.
- **On TV, the slow reveal is for signature moments only** (Play, film page reveal, milestones; ≤ 600 ms in / 300 ms out). Anything tied to focus lights within 150 ms.

## 4. Controls

- **Rocker switch:** up = on. The paddle turns orange when on. No glow. The state is also written in text. Night: a light graphite paddle in a near-black slot.
- **Buttons:** orange primary, raised and bevelled, press down 2 px. Secondary buttons are aluminium.
- **Slider (fader):** a lit strip revealed up to an aluminium cap. Never bright white.
- **No knobs, dials or curved controls for input.** Arcs and dials are read-only.

## 5. Meters (read-only)

| Meter | Use | Readout |
|---|---|---|
| **Quiet face** | A level with a needle (power, temperature) | Dark rectangular window under the needle, orange mono digits. Needle casts a soft shadow from a fixed top-left light. |
| **Lit scale** | A level as an arc of LEDs | Seven-segment screen whose bottom sits on the arc's baseline, unit on black punch-label tape below it (never over the screen). |
| **Ladder** | Volume and quick levels in a list row | None |

The lit scale and ladder use one LED per notch, with a little bleed. The top notches are red.

## 6. Progress

**Shutter and hot spot.** A lit orange strip under a dark shutter with a faint filament texture, and a warm hot spot at the leading edge. Shutters slide on the decelerate curve. (Slatted is parked for a future look.)

- Progress bars on cards are **drawn at their value, static**. The shutter animates once, only on the focused item, the player timeline or a signature moment. At most one thing moves besides the focused item.

## 7. TV selector

**Base window (W1).** A window cut into the base of each tile, flush with its bottom edge, always visible. When focused:
- the tile lifts (150 ms) but doesn't change colour. **The lift is drawn inside the tile's own layer and never moves its focus rectangle** (a moved hit box makes D-pad search walk the wrong way),
- the window lights within 150 ms, and snaps under a held key (≤ 80 ms or instant), brightest on the front and falling off as it wraps under the edge,
- the label switches to a warm cream (snap or ≤ 150 ms colour step), never a glow on the glyphs, and stays ≥ 4.5:1 throughout,
- the spill below lights the panel's rib texture: **one pre-drawn bitmap per tile width, faded by opacity**, not a runtime mask.

Brightness: window about 85%, spill about 65% of full. The selector never animates like the progress bar.

## 8. Motion curves

One table, and the names mean the same thing in every project.

| Name | Curve | Use |
|---|---|---|
| `glide` | `cubic-bezier(.2,.8,.2,1)` | Focus, hover, small moves |
| `decelerate` | `cubic-bezier(.16,1,.3,1)` | Shutters, reveals, things arriving |
| `settle` | `cubic-bezier(.3,1.3,.5,1)` | Rocker paddle, things landing with a small bounce. **Overshoot is capped at 1.3** (spring damping ≥ 0.7). |
| `leave` | `cubic-bezier(.4,0,1,1)` | Things exiting |

## 9. Floors (every look, every app)

| Rule | Desk & phone | Kiosk (~3 m) | TV (~3 m, night) |
|---|---|---|---|
| Text | Body 15, labels 13, min 12 px | Body 18+, min 12 px | Body 26, min 22 px at 1080p |
| Contrast | WCAG AA, including secondary text | same | same; focused labels never fade below AA |
| Targets | 44 px touch | 44 px, no scrolling | Focus visible from the sofa |
| Motion | Desk gets more motion than phone | One-shot only, nothing continuous | Transform + opacity only; no blur; glows are sprites; focus ≤ 150 ms (≤ 80 ms or snap under key repeat); scenes 350–600 ms |
| Flashing | At most 2 big luminance changes per second; a Calm/SAFE setting everywhere | | |
| State | Never colour alone: shape + word | | |
| Fonts | OFL, bundled, no CDNs | | |
| Words | Plain, complete button wording ("Resume from 1:12:04"); no jokes in the interface | | One title + one line on **home screens, launchers and focused cards**. Detail pages and buttons keep complete wording. |
| Carousels | — | — | Allowed for cover and screenshot rows. The next item peeks. Never for groups, controls or settings. |

## 10. Still open

- The project-by-project check: every project documents its current UI in `projects/` first.
- TV title card in Hi-Fi (mockup 09: Shutter, Tape counter or Tuning dial), interface sounds, Callsheet's and HA's current Saul Bass defaults, LCARS II.
- The look shelf: which alternates survive and get rebuilt on these roles.
- Token pipeline: one token file converted to CSS variables, HA `--jam-*` YAML, Compose `Palette.kt` and Godot `theme.json`.
