# Lobby: proposals for the bible

Lobby's phased design audit (4 phases, 14 passes) measured these rules. Each one fixed a real bug. They're proposed as
floors for every TV surface, and as advice for kiosks.

1. **Put numbers on "big luminance change" (bible §9 Flashing).**
   - A big change is at least 50 % of a 310×310 px window (at 1080p; about 25 % of the central 10° of vision from
     3 m on a 65" set) changing relative luminance by 0.10 or more in the same direction.
   - At most 2 a second, in normal and Calm mode alike.
   - Measure it with a held key, with alternating presses at 4 a second, and at one press a second.
   - Why: a window-average rule failed big title swaps that don't flash, and missed real flashes that straddled a
     fixed grid. The area rule is still twice as strict as WCAG's.
2. **Add a saturated-red clause.** Red (linear R/(R+G+B) ≥ 0.8) covering 25 % of the screen or more may not switch on
   and off more than twice a second.
   - Why: brand-red apps (YouTube, Netflix, YouTube TV) once turned 95 % of Homage's screen red on every pass along
     the Watch row.
3. **Add a night glare cap for TV.** At rest, under about 10 % of the screen above relative luminance 0.5. No
   full-screen white or yellow floods on open; brand colours are pulled into the look's lightness band.
   - Why: Sea Ranch's white stripe lit 20 % of the screen in a dark room; capping its paints at L 0.78 brought that
     to 2–3 % without losing the look.
4. **Snap focus colour, animate only transform.**
   - The bible says "focused labels never fade below AA". The way this is broken in practice: transitioning a label's
     colour and its background together passes through equal lightness, so the label drops to about 1:1 for around
     200 ms on every move.
   - The old focus has to go off in the same frame the new one lights.
5. **Don't count a fade as one change.**
   - A cross-fade between a light and a dark picture is two changes, because it passes through grey.
   - Opening by zooming a picture sweeps its bright and dark parts through the same area several times. A window
     growing over a still picture changes each area once.
6. **Calm mode swaps in one frame, never through a bare frame.**
   - Decode images (`img.decode()`) before swapping.
   - Never remove the old face before the new one is ready.
   - Why: "snap" is not automatically safe. An instant black-to-white swap is a flash, and a bare frame between two
     pictures counts as two changes.
7. **Launch and open layers are opaque and full-bleed**, so the home screen never shows through, and an input says
   what to do when it has no signal.
