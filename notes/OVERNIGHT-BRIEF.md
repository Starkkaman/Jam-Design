# Overnight brief (for every round)

Isaac asked (2026-11-05, before bed): mockups for every interface, three passes each, saving every mockup and every round of notes. Order: TV launcher, Callsheet, JamFin, Jam-Dash, NervOS, Home Assistant (Jam Theme + Jam Cards together). He reviews in the morning. Nothing here changes any real app.

## Read first
- `CHANGES.md` (especially section A: the course correction) and `decisions.md` (the last ~60 lines)
- `BIBLE.md` (draft 0.5): floors, state words, TV rules, motion, carousels
- `projects/<app>/README.md` (+ PROPOSALS.md, FLOW.md if present) and a few screenshots in `projects/<app>/screens/`
- `notes/pass*-*.md` from earlier rounds, **especially the same app's previous pass**
- Reference implementation of the current look: `mockups/13-jam-home-braun-hifi.html` (style block also in `mockups/_hifi-base.css`) and the TV mockup `mockups/pass1/tv-launcher.html`

## The look: simplified Braun Hi-Fi (current direction)
- Calm, flat cards with soft corners (Jam Braun is the reference Isaac likes); Jost for words, IBM Plex Mono for small labels/numbers.
- **No grain, no paper texture, no brushed metal, no glow/halo.** Ribs (fine horizontal lines) only on black bands.
- Indicator lights: small windows that are always a dark recess; lit = solid flat colour. Shapes: round LED (status), square (selected mode), slot (running), bar group (count).
- Colours: day alu `#e3e1dc`, card `#f1efeb`; night `#1c1c1b`, card `#2a2a28`; band `#1d1c1a`/`#121211`; walnut rule `#6b4428`; cream light `#f3e6c8`; ok `#7bd651`; warn `#f2c14e`; alert `#ff5a48`; orange `#ec7c22` (night `#f08a2c`).
- **Orange is rare**: rocker paddles (on) and the ONE primary action per card/screen. Sliders reveal cream (or the thing's own colour). Chosen keys press in.
- Rocker switches (up = on). Faders reveal light. No knobs/curved input controls. Never show the same value twice on one panel.
- Seven-segment digits only on appliance-style cards (and maybe the TV title card).
- Accents (one per screen, in a clear zone away from content AND navigation): Stripes, Session blocks, Colour bars (palettes in BIBLE §2).
- TV: dark, safe area 5% sides / 5% top-bottom, text ≥ 22 px at 1080p (≈1.15cqw), transform/opacity motion only, focus ≤150 ms, flat base-window selector, flash/glare floors, carousels allowed with neighbours visible and position shown.
- Shared state words: on / off / offline / action / alert.

## Each round
1. **Research**: summarise what you learn (WebSearch/web pages if your tools allow, otherwise from knowledge, and say which). Cite products, not marketing copy.
2. **Design**: one self-contained HTML mockup at `mockups/pass<N>/<app>.html`. Interactive where it helps (focus/keyboard for TV, clicks elsewhere). Realistic sample content (no real private data). Real target sizes (TV 1920×1080 via cqw, phone 390, desktop 1280–1440, kiosk 1024×768 / 961×601). The page must work at phone width and in light and dark page themes (follow the existing mockups' page chrome).
   - Only external resources allowed: Google Fonts and scripts from cdnjs/jsdelivr/unpkg pinned versions. Inline everything else.
3. **Check**: render it with Playwright (`require('playwright')`, chromium needs no options), screenshot key states, fix what's broken (overflow, overlaps, text under minimums, JS errors). One fix pass, then move on.
4. **Audit + notes**: `notes/pass<N>-<app>.md` with sections: Research, Design (what and why), Audit (numbered table: problem + severity), Change suggestions for the next pass, **Bible implications** (numbered, things BIBLE.md would need to change). Be honest and specific.
5. **Commit** only your files: `git pull --rebase` then commit and push to main. Message like `pass2: jamfin mockup and notes`. End commit messages with:
   `Co-Authored-By: Claude Opus 5.5 <noreply@anthropic.com>` and `Claude-Session: https://claude.ai/code/session_01Hpx2S4wpnTRdWt2FDhhdQm`

## Don't
- Don't edit BIBLE.md, decisions.md, CHANGES.md, tokens/, projects/ or other apps' files.
- Don't message other sessions or change any real app or server.
- Don't use logos or recreate a real product's look; references inform, they aren't copied.
