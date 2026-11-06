# Design Bible — running decision log

## Roadmap
1. Discovery: agent interviews (Callsheet, HA Mr Manager, JamFin, NervOS, Jam-Dash, Control Freak/lobby) + user interview
2. Direction (Rounds 1–2): mood + hybrid  <- here
3. Foundations: colour roles, type scale, spacing/grid, radius, motion curves, sound(?)
4. Surface profiles ("volumes"): Desk (Jam-Dash, Callsheet) · Touch (HA iPad, JamFin mobile) · Lounge 10-ft (TV launcher, JamFin TV, NervOS)
5. Components: tile, list row, lamp, readout, button, focus ring, hero, rail, toast
6. Token pipeline: one tokens.json -> CSS vars / HA theme YAML / Godot Theme / JamFin
7. Alt themes for other household users (swap tokens, keep roles)

## Decided (2026-11-04)
- R1: Liked A's colours + subtle glow; B's readability + accent colours; D as overall hybrid. C rejected (too much contrast, no focal point). D issues: overlapping text, faint right-side labels.
- Retro dose varies by device: quiet on work tools, louder on play surfaces.
- Light/dark follows the device; TV always dark.
- Motion: fluid or cinematic, varies by device (never snappy/mechanical-only).

## Draft tokens ("Telemetry", R2)
- Amber = readouts (look), orange = actions (touch), green/amber/red = lamp state only.
- Body: Schibsted Grotesk; data/labels: IBM Plex Mono.
- Desk motion 240ms cubic-bezier(.22,1,.36,1); Lounge 420ms cubic-bezier(.16,1,.3,1).

## R2 feedback
- Amber (readouts) / orange (actions) split: kept, pending user confirming.
- TV had too much text. Lounge rule: one title + one short detail line max; no part numbers, kickers or status sentences; tiles = one word; only the focused tile is bright.

## Interview: JamFin (received 2026-11-04)
Full answers: NAS ~/project/jamfin/docs/design-bible-answers.md. Rules file: docs/experience-system.md.
- Stack: Kotlin/Compose (tv-material), tokens in ui-common/.../theme/Palette.kt (roles: ground, onGround, mutedOnGround, slab, rule, accents), MotionTokens.kt, Look.kt.
- 8 looks. User LIKED: Unigrid, Olympia, New Wave ("most polished"), Cel'88 parallax city, Unigrid/Olympia/Kinetic animations, popovers above/below timeline "everywhere". Aim: "fun without sacrificing clarity".
- DISLIKED: smash cuts / selector flash, wasted space, Swiss "too dense, too bright, cold and harsh", bright whites, "amateur, lacking polish", wants "less contrasty, more texture, a bit of grit", looks should differ more; hitching animations should mask loading.
- Shared rules already in place: no pure white; Night ground ~#161412, text ~#E8E2D6; secondary text >= 4.5:1; true black only behind video; text never textured/rotated.
- Motion today: focus <=150ms, screen <=350ms, Back 240/150, signature 600/300, menus 200/150. Easings Leave(.4,0,1,1) Settle(.3,1.3,.5,1) Glide(.2,.8,.2,1). Calm setting + per-look UI sounds.
- HARD (TV MT9690/Mali-G57, 1080p, 960x540dp): GPU-bound on full redraws -> grain only as static tiles, NO blur, animate only transform+alpha (=> glow must be a pre-rendered layer faded by alpha, not animated box-shadow), focused items on own layers. 4-5 cards/row.
- Fonts: bundled OFL only (Archivo, Barlow, Bungee, Dela Gothic One, Jost, Karla, Londrina, Saira, Schibsted Grotesk, Sofia Sans XCond, Syne, Zen Kaku). Schibsted OK; IBM Plex Mono is OFL but would need bundling.
- Must not change: focus graph, fixed zones (title+Play upper-left, progress on card bottom edge, timeline bottom), plain button wording, resume <=3 presses, no long/double press.

### Implications for bible
- TENSION: R2 TV focus at 420ms vs JamFin focus <=150ms. Proposal: focus = fast (~150-180ms Glide), cinematic only for screen/hero transitions (350-600ms). Raise with user.
- Add "grit": static grain tile + slightly lower contrast grounds. Keep "volumes" but allow per-look character (user wants looks to differ more) -> bible = shared roles/zones/motion grammar, looks vary skin.

## Interview: Home Assistant Mr Manager (received 2026-11-04)
Full: ~/project/home-assistant/docs/design-bible-interview-2026-11-04.md. Morning notes: https://claude.ai/artifact/VJjYvBZudQPs1RgCHyrEg8
- Jam Cards (36 custom cards, repo Starkkaman/jam-cards). Tokens jam-cards/tokens/looks/<id>.mjs -> tools/themes.mjs -> jam-theme YAML (--jam-* vars). Look pack src/looks/<id>.js. Per-user look via jam-looks.
- State contract already exists: data-state on|off|offline|action + data-alert. (Bible should adopt this grammar everywhere.)
- Surfaces: Echo Show 8 1024x768, iPad 961x601 (offline), phone 390, desktop 1280. Kiosk + phone matter most; kiosk read from ~3 m.
- Default JamBoard (Saul Bass): bg #141210, slab #1f1c19, fg #ece2c9, dim #9a8f7c, ochre #e5a31b; room colours teal/blue/pink/violet/green; Londrina + Jost; radius 0.
- User quotes: "Braun is kinda boring... incorporate a little more color"; "cards have lost a lot of readability"; "kiosk music is ugly"; "Tv card looks way better"; "emphasize clarity without ever sacrificing fun... dramatic changes fine". Said NO to NERV and LCARS.
- Standing rules: mockups + OK before shipping; each look has distinctive design + signature motion; text >= 15/13/12px; everything at a glance.
- Pain: idle controls wearing accent (open), top 40% kiosk empty, unlocked door quieter than locked, phone fits 3/5 tabs.
- HARD: kiosk no scroll, no continuous animation, 44px targets, >=4.5:1, 12px min; theme can't read state (logic in cards); fonts OFL self-hosted; original dashboards never edited; any HA change needs Isaac's OK.

### Implications
- Room colours = a third colour role (identity), separate from readout/action/state. Supports "more colour than Braun".
- R2 rule "orange only for things you press" also fixes the open "idle controls wear accent" issue: idle = neutral, active = state colour.
- Two agents now independently say: recurring complaint is READABILITY lost in stylised looks. Bible's core: legibility floor is non-negotiable; personality lives in motion, texture, colour, motifs.

## Interview: Callsheet (from transcript; file ~/project/daily-brief/for-design-unification-callsheet.md)
- HA add-on (Ingress). Briefing, Replies, Agenda, Chat, Projects, Setup. Desktop (keyboard: Cmd-K, J/K) + phone (700px bp, 44px). No TV.
- Plain JS/CSS; tokens at top of app.css per data-look x data-mode, data-base = bold|clean|easy. Source ~/project/daily-brief/harmony/themes-harmony.css + gen.py (contrast report).
- Looks: Bold (Londrina+Jost, cream #e3d8bd), Clean (Plex Sans, blue #2457d6), Easy read (Atkinson Hyperlegible) + JamDash's 9 look ids. Motion 150/250/350, nothing loops.
- Quotes: "3 looks definitely work!"; "red could be darker"; "get rid of the cheeky production nods"; "way too much text on screen"; "menus getting dense, want it fun"; wants Callsheet<->JamDash "fluid".
- HARD: offline, bundled OFL fonts, WCAG AA (+ deeper step for text on colour), 44px, plain words, look ids shared with JamDash.

## Interview: Jam-Dash (from transcript; reply bounced)
- SvelteKit in Go binary; smol-boi + TrueNAS :8484. Screens: Home (alert hero, app tiles, live previews), Apps, App detail, Store, Files, Shares, System, Settings. Global view via HA add-on.
- Desktop first 1440, phone close second 390.
- Looks: web/src/lib/themes/<id>/<id>.css; guide web/docs/LOOKS.md. Remaining: Depth (default), Depth II, Braun, Braun II, LCARS, LCARS II, NERV, Transit, Olympia, Grid, Pulsar, New Wave, Riso. Removed: Kinetic/Aero/Harper ("no"), six II redesigns ("just not for me").
- Depth: dusk #173A52, ridge #3E5F78, sun #F0B36E, window #F6F8FA, action #2F6FE4, alert #FF8F73; Instrument Sans; radius 14/26/20; ease (.2,.8,.2,1).
- Quotes: "excellent design and cool animations"; "text is too small"; "navigation in depth is atrocious"; liked "Depth II, Braun II, LCARS II - much better!". Must be shareable with others.
- HARD: AA, body >=15 / labels 13 / min 12, 44px, reduced motion, state never colour-only, local fonts, no franchise logos.

## Interview: Lobby / Control Freak = TV launcher (from transcript; file /mnt/ai/projects/lobby/docs/for-design-unification.md)
- Hisense Google TV "Phoster", Android 14, WebView Chromium 156, 1920x1080. D-pad only. ~3 m, often at NIGHT in dark room.
- Text >= 22px, body 26+; safe area 96 sides / 54 top-bottom; focus unmistakable; nothing hidden in carousels; everything visible at once.
- Layout: top line (name, time, date, weather) / hero for focused item / five groups: Continue, Watch, Play, Listen, Home.
- Plain HTML/CSS/JS; tokens in designs/<nn>/style.css. 8 designs (Homage, Dessau, Sea Ranch, Tanaka, Liquid, Kinetic, Dither, Calder), none Rams; user hasn't reviewed. Shortlist Homage/Kinetic/Calder.
- HARD: transform/opacity only; flash rule (<=2/s big luminance changes); night glare (Sea Ranch cut to <8% bright screen area); colour fades must not drop focused label contrast -> snap colour, animate transform.

## Cross-project synthesis (5 of 6 in; NervOS pending)
1. Universal user brief: "clarity without ever sacrificing fun". Recurring complaints: text too small, too much text, too dense, too bright/harsh, hidden navigation, amateur polish.
2. Fonts available everywhere (bundled OFL): Schibsted Grotesk (JamFin list + Lobby), Jost, Archivo, Barlow. Instrument Sans in Jam-Dash. Mono must be bundled (IBM Plex Mono OFL).
3. Shared floors to adopt verbatim: AA contrast; text 15/13/12 desk & touch, 22/26 TV; 44px touch; state never colour-only; transform+opacity only on TV; no blur on TV; flash rule; no continuous kiosk animation; reduced-motion; local fonts.
4. State grammar: HA's data-state on|off|offline|action + alert -> bible-wide.
5. Look systems already exist in all 5 (CSS vars / Compose Palette roles / HA --jam-*). Bible = ONE role vocabulary + a default look ("Telemetry") + rules every look obeys; existing looks become alt themes. Callsheet<->JamDash already share look ids: extend that registry to all.
6. Motion: everyone already ~150 focus / 250 / 350 screen. User wants fluid/cinematic -> keep focus fast, put cinema in screen transitions + one signature motion per look.
7. Lobby's TV layout + JamFin's TV fixed zones are close: reconcile into one Lounge layout.

## Interview: NervOS (received)
- Godot 4.7.2 launcher on Aero 15 (CachyOS), 65" HDR 1080p120, ~3 m, Steam Controller (SDL3), kbd, HA MQTT remote. Sections ARCHIVE / HANGAR / UPLINK / THEATER.
- Tokens design/tokens.json -> core/tokens.gd; themes app/themes/<id>/theme.json + per-theme layouts; motion core/choreo.gd (stepped fps, SAFE mode). Data-only user themes in ~/.local/share/nervos/themes.
- Default NERVOS (anime ops-room): void #0D0B14, panel #1D1829, ink #EFE7D6, amber focus #FFA41B, green #52F28C; Saira + Share Tech Mono; chamfers; stepped 12fps; focus 140 / panel 240 / page 320. Others: CUT-OUT, CHOOSE YOUR HERO, VHS.
- Quotes: VHS "very fun, I love it!"; Hero "I like it a lot!"; "Loved the art... character art"; carousels "from time to time"; CUT-OUT v1 "way too busy"; descriptions "too long now haha".
- Pain: default hub busy; long-title overlap.
- HARD: GTX 1060 shared with games -> cheap idle; flash <=2/s + SAFE mode; OFL bundled; original art only in repo; keep "Signal Deck" + MQTT ids; HDR 200-nit SDR ref.

## NOTE: two 10-ft launchers in the living room
NervOS (Aero 15) and Lobby (Hisense Google TV) overlap (both list Moonlight/RetroArch/Jellyfin). Ask user how they relate.

## Decided (after interviews)
- NervOS and Lobby stay SEPARATE products; share only the bible rules.
- Looks: Telemetry default everywhere + small shared shelf of alternates rebuilt on shared roles, offered in every app; rest retired.
- TV motion: fast focus (~150ms), cinema in scene changes (350-600ms) + one signature move per look.

## Bible 0.1 markup (user)
- TV carousels OK for image-led rows (covers, screenshots): keeps UI calm. Next item peeks; groups/controls/settings never in carousels.
- Desk gets MORE motion than phone (hover, staggers, screen changes). Phone restrained.
- Look shelf: user "coming to my senses" -> rethinking. Wants to pick a NEW BASE LOOK (Telemetry under review). Shelf + base on hold.

## New base look (2026-11-05)
- Telemetry rejected as base: "feels like every other good responsive UI", lacks personality.
- Lives with 2 others: Mission Control "too nerdy" for them; Braun is default-by-default, but explore first.
- Inspirations: 70s NASA, Rams, TNG/Voyager, McQuarrie, Syd Mead, Bebop, Evangelion, Miyazaki, Satoshi Kon, mid-century modern, Atari 2600 industrial design, Fallout. "Retro design lover, but also clean, effective design."
- Round 3 (https://claude.ai/artifact/7aRorPkJqjQPgtxr7dx7XK): A Hi-Fi (Braun+Atari woodgrain, VU needles), B Starliner (painted time-of-day sky, TNG-style colour-coded soft panels), C Session (calm lists + Bebop/Eva serif title cards), D Postcard (illustrated Miyazaki house scene). All original, household-friendly.

## Round 3 feedback -> Round 4 (https://claude.ai/artifact/3ofRwCh9UiaXDkvPagM2Cy)
- A Hi-Fi: LIKES colours, orange button, rocker switch, continue-watching black band. Avoid too much skeuomorphism.
- B Starliner: "too much like a first draft AI design". C Session: "really nice" but dislikes serif fonts. D Postcard: no.
- R4 "Hi-Fi, flattened": aluminium #dcd9d3 / black band #1d1c1a / walnut #5b3a22 line / orange #e8641c; Jost + Plex Mono; C's numbered 3-item list; flat VU dial; Jost-caps title card w/ orange stripe; texture switch Flat / A touch / Full.

## Round 4 feedback
- Texture: "A touch" is right. Ribs too dense (read as flat colour at distance) -> spaced to 1px every 10px.
- Switch: orange-when-down was arbitrary. Rule: rocker UP = on, orange paddle only when on, state also written in text (never colour-only).
- Wants more depth on indicators, buttons, card layers -> added "A touch + depth" (floating list card, band raised over it, lit lens lamps, bevelled press-down buttons, recessed dial/progress). Awaiting verdict.
- Depth "mostly right". Lamps were too realistic -> flat lamp, thin rim, soft glow (match surrounding depth level). Dial inset = same half-disc shape as dial; face contrasts with its panel (dark on day, aluminium on night). Progress = lit orange strip revealed by a sliding shutter, hot spot at edge, unlit filament texture behind.
- Rule candidate: every element sits at the same realism level; nothing more "real" than its neighbours.

## Round 4 v3 feedback -> Round 5
- Lamps brighter. Dark switch blended in; LIKES light switch -> night = light graphite paddle in near-black slot.
- Dial: black face too distracting -> 4 options in R5 (A quiet recess, B lit segments [default], C amber face, D ladder).
- Progress reveal: "very cool, very much the vibe". SIGNATURE MOVE CONFIRMED: "light reveal" — orange light revealed by a shutter (transform) / glow warms in (opacity) when something becomes active. Applied: progress, loading, switch on, level meter, TV focus strip, title-card stripe.

## Round 5 feedback -> Round 6 (https://claude.ai/artifact/2HA6dDsfZiSgXkZHSUmLRm -> round6)
- Progress: R4 version looked better than R5. R6 shows P1 (R4 exact), P2 backlit tube, P3 slatted.
- Switches: NO glow.
- RULE: lights are for INDICATORS, not controls. Controls may contain light only as a slider revealing light.
- RULE: no knobs / curved / dial controls for input (unreliable). Arcs & dials are read-only.
- Meters kept: quiet face, lit scale, ladder (indicators only). Amber face dropped.
- TV selector: likes the indicator strip but NOT the progress-style sweep. R6 shows S1 fade-up strip, S2 centre bloom, S3 lamp, S4 underglow, S5 lit frame.

## Round 6 feedback -> Round 7 (https://claude.ai/artifact/RFBframE5YumEVUBkauNcv -> round7)
- Progress LOCKED: P1 shutter + hot spot. Slatted parked for a future shelf theme.
- Fader cap: less white -> brushed aluminium #cfcbc3 (graphite #8d8981 in dark).
- RULE: indicator lights come in shapes: round LED, square, slot, bar group; colours ok/active/warn/alert/info (not only green).
- RULE: every light sits behind a window that's always visible (unlit = recess).
- Meters: all 3 kept. R7 shows lit scale + ladder as per-notch LED (with bleed) and as shutter-revealed continuous light.
- TV selector: UNDERGLOW chosen, but the window must always be visible; the glow motivates the warm highlighted label. R7: A window inside tile, B window on tile lip.

## Round 7 feedback (v2 published same URL)
- Meters: all look good. LOCKED: lit scale + ladder = one LED per notch (with bleed). Shutter meters dropped.
- Readouts added: quiet face = needle + end labels + dark recessed readout window with orange mono digits; lit scale = big number centred in arc + unit + range at ends; red slot "peak" lamp >= 85%.
- TV selector: window on the LIP chosen, but was too bright -> two dimmer levels shown (lit .75/.55, spill .55/.35), deeper orange, label warmth reduced.
- Slatted replay fixed.
- LOVES quiet face; readout-in-a-window is "a very nice touch" -> RULE: numeric readouts sit in dark recessed windows with orange mono digits.
- Lit scale: centre readout now in a ROUND inset window.
- TV lip: LOCKED at a touch brighter than Softer (lit .85 / spill .65). RULE: indicator windows never grow with their control; selection only illuminates them.
- Readout windows enlarged (round r44 / 28px digits; quiet face 84x29 / 18px).
- Needles cast a subtle shadow; light comes from one fixed direction (top-left), so the shadow doesn't rotate with the needle.
- TV lip slot: moved fully inside the tile's bottom face (no overhang), no outer glow on the window itself; only the underglow spills. Brightness locked.
- RULE: a light's window never extends past its object's edge.
- Quiet face readout: back to 84x24 / 16px (the previous size was right).
- Lit scale readout options shown: 1 half-circle window concentric with LEDs, 2 small circle + black punch-label tape unit, 3 seven-segment display (ghost segments visible).
- TV slot: user wants it at the BOTTOM, as a window in the button's base that wraps around the edge. Options: W1 base window, W2 lit base edge (full width), W3 centre notch.
- Lit scale readout: SEVEN-SEGMENT chosen. Placement A (screen bottom on the old half-circle baseline) vs B (centred where small circle was). Unit on black punch-label tape BELOW the screen, never over it.
- TV selector: W1 base window chosen. Refined: selected button does NOT change colour (only lifts); label gets an uneven warm glow strongest near the window; underglow lights the panel's rib texture (rib-masked glow layer).
- Seven-segment placement A LOCKED (screen bottom on the arc baseline, punch-label unit below).
- Jam Home mockup in Hi-Fi built (kiosk 1024x768 + phone 390): rooms list w/ rockers + bar-group counts, living room faders + scene buttons (square windows) + TV band w/ progress, music w/ ladder + volume fader, power quiet face + 7-seg lit scale, front door LED + Unlock, dock = W1 base-window tiles with rib underglow. Kiosk uses spare height for larger type.

## TV title card (2026-11-05)
- Mockup 09: three Hi-Fi title cards that mask real loading and stay dark (flash-safe): Shutter (band halves close, lit strip = load), Tape counter (faceplate, 7-seg 000-100, punch label LOADING -> READY + LED), Tuning dial (backlit dial, red needle sweeps with load, "Tuned" LED). Min hold ~1.6 s; slow loads hold until ready. Awaiting Isaac's pick.

## Project check 1: JamFin (2026-11-05)
JamFin pushed its profile, 38 screenshots and 10 PROPOSALS against draft 0.2 (TV perf + invariants). Isaac's answers:
- TV grounds behind scrolling rows are FLAT; ribs only on fixed surfaces (menu/player band, title card) as cached bitmaps.
- Selector label: warm cream colour step (<=150 ms), no glyph glow; rib spill = pre-drawn bitmap per tile width faded by opacity.
- Short-text rule (one title + one line) applies to home screens, launchers and focused cards only. Buttons/detail pages keep complete plain wording.
- KEEP a TV Day option (dark default; mid-light, never paper-white) in every TV app.
Adopted without needing a call (no visible change): glows/soft shadows as pre-rendered sprites; focus lights <=150 ms (<=80 ms/snap under repeat), slow reveal only for signature moments; lift drawn inside tile layer (focus rect never moves); card progress bars static, shutter animates once on focused/timeline/signature; one shared curve table with overshoot capped at 1.3; flash limit stays 2/s (JamFin can adopt).
-> BIBLE.md draft 0.3.

## Project check 2: Jam Home
HA pushed profile + 44 screenshots. Correction: kitchen Echo Show 8 is ~961x601 CSS px; living-room iPad is 1024x768 (the interview had them swapped; mockup 08 labels the 1024x768 frame as the kitchen kiosk, which is wrong).

## Process rule (Isaac, 2026-11-05)
- We are only building the design doc. Nothing is replaced or deleted yet.
- Rollout happens later, one app/service at a time. Nothing existing (looks, themes, dashboards) gets deleted until that app's turn, with Isaac's OK.
- Answers to project questions describe the eventual design, not immediate changes.

## Project answers: Jam Home questions (Isaac, 2026-11-05) — design doc only
- Hi-Fi becomes HA's default at HA's rollout turn; existing looks stay until the shelf decision.
- Per-user looks on personal devices; one house look on shared screens (kiosks, TVs). EXCEPTION: JamFin saves each profile's preferred look.
- ADOPTED for every app: HA's state words (on/off/offline/action + alert); colour discipline (colour only for on/selected, idle neutral incl. room accents; red reserved for alerts; kiosk-safe motion tier).
- NOT adopted for now: kiosk glance size (~65 px), attention surfaces rule.

## Project check 3: NervOS
Profile, 26 WebP goldens (original art only), PROPOSALS P1-P6 against 0.3. Adopted without a visible change: P1 shared Calm/SAFE definition; P2 (already in 0.3); P3 "stepped" curve for decoration only; P5 per-look post layer, user-chosen, never over art/video, static in Calm, off in Hi-Fi; P6 Godot token shape + DSEG (OFL) for seven-segment. Open for Isaac: P4 group carousels in alternate looks (VHS consoles, CHOOSE YOUR HERO), which he approved on 2026-11-03.
-> BIBLE.md draft 0.4.
- NervOS P4 (Isaac): group carousels ALLOWED in every look, Hi-Fi included, when neighbours are named/visible at the edges and position is shown ("3 of 8"). Never for controls or settings.

## TV title card (Isaac, 2026-11-05)
- SHUTTER chosen. Isaac wants to see it with the slatted progress bar ("told you it would come back"): mockup 09 now has "Shutter · slatted" (unlit slats stay faintly visible, per the window rule). Pending his verdict on slatted vs the shutter-and-hot-spot strip inside the card.
- Title card: SHUTTER + SLATTED bar chosen ("I really like the shutter with the slatted bar").
- Isaac wants the UI "less cartoony" with more texture. Mockup 09 adds Texture: Current / Subtle / Rich (default Rich): brushed-metal + grain on the shutter halves, embossed ribs, light falloff, a machined lip at the seam, a recessed bezel + glass highlight on the slatted bar, printed (letterpress) title text, moulded tiles with grain, grained walnut trim. Static textures, fixed surfaces only (TV rule): no texture on the ground behind scrolling rows. Awaiting verdict.
- Texture: RICH locked. Asked for coarser grain, paper-like texture on text, and more geometric shaping in the background.
  Mockup 09 now: coarse grain on shutter halves + tiles; paper texture on HEADLINES only (card title, home hero title, clock), small labels stay solid; Geometry switch None / Orbit (concentric arcs + planet, walnut arc) / Panels (equipment-rack insets, walnut side band, screws) / Stripes (70s bent triple stripe in walnut-tan). Geometry = flat static shapes, so it's allowed behind TV rows (texture still isn't); the shutter halves carry the same geometry so it lines up when they close. Awaiting pick.
- Geometry: STRIPES chosen. Richer tones: chocolate #6b3416, burnt orange #b04a1c, gold #d69a2e, with a faint highlight rule on the outside edge. Placement: they come down from the top right, bend, and exit right; never behind buttons, tiles or titles. On the title card the composition shifts right to clear the centred title. Note: the burnt-orange stripe is decoration and stays darker than the control orange (#e8641c) so it never reads as a control.

## Splash of colour (2026-11-05)
- Mockup 10: nine original colour accents from Isaac's influences, each in the clear zone (top right, never behind titles/buttons), flat + static: Stripes (chosen), Horizon (McQuarrie/Mead porthole sunset), Mission patch (70s NASA roundel), Atomic starburst (mid-century), Eames dots, Colour bars (Atari/70s TV), Session blocks (Bebop/Kon), Braun keys (Rams), Launch chevrons (NASA/Eva). No logos or emblems. Decorative oranges stay darker than control orange. Proposal: one splash per screen, different screens/apps may differ. Awaiting picks.
- Isaac's picks: accents STRIPES, SESSION BLOCKS, COLOUR BARS. Saved for later: the HORIZON palette and the MISSION PATCH palette ("could be used later for something").
- Title card recorded as final in the bible: Shutter + slatted bar, Rich texture, paper headlines, Stripes accent.
-> BIBLE.md draft 0.5.

## Project check 4: Lobby
24 screenshots + 7 measured flash/glare proposals. All adopted as TV floors (advice for kiosks), no visible change to Hi-Fi: numeric big-change definition, saturated-red clause, night glare cap (<10% of screen above L 0.5 at rest), snap focus colour / transform-only, fades count as two changes, Calm swaps in one frame without bare frames, opaque full-bleed launch layers.

## Project check 5: Jam-Dash
56 Depth screenshots + profile. Its questions 1, 3, 4, 6 (which originals/II looks stay, Global views per look, picker previews, look bugs) are app-internal and wait for Jam-Dash's rollout turn / the shelf decision. Q2 (Runner direction) and Q5 (phone monitoring rule) go to Isaac.
- Isaac: Runner -> keep as a shelf candidate. Phone monitoring-row rule -> NOT adopted.

## Jam Home v2 mockup (2026-11-05)
- Isaac: look shelf waits until the lookbook is done; no interface sounds yet; token pipeline undecided. Keep defining.
- Mockup 11: Jam Home from HA's real inventory (phone Living view, living-room iPad 1024x768, kitchen Echo Show 961x601) with everything locked: Rich texture (Echo in kiosk-safe tier, no grain overlays), paper clock/room titles, state words on every light (On · 70 / Off / Offline), light colour as a lit swatch window (never a full-card fill; room accent colours retired per colour discipline), readouts in windows, scenes with square windows, P1 progress on the TV band, ladder + volume fader, lock as a round window (green LED locked / red diamond + "Unlocked" + orange Lock button), base-window dock with state lines, HA tabs with base windows. One accent per screen: Session blocks (phone room title), Stripes (iPad), Colour bars (Echo).
- Jam Home v3 feedback (Isaac): air purifier should feel like a tiny appliance; a slider and an indicator showing the same value on one panel is "hilariously obnoxious"; media cards should look and feel like media devices; kiosk button indicator lights should sit elsewhere; make the HA remote popup "100x cooler".
  Done in mockup 11 (v3): air purifier = tiny appliance (grille, 7-seg PM2.5 readout, round power key, speed keys with square windows, feet). Lights say On/Off only (the slider carries the level). Speaker ladder removed (volume shown once, by the fader). TV = deck with a glass screen, 7-seg time left, VCR piano transport; PC = console with a cartridge in a slot (punch-label title), 7-seg play time; speaker = tape deck with a cassette (static reels), 7-seg time, piano transport, volume fader. Kiosk dock state lights moved to each tile's top-right corner. New remote sheet: physical brushed-aluminium remote with a walnut cap and IR window (lights orange on each press = transmit indicator), metal ring d-pad with orange OK, rubber keys (Back/Home/Menu/Setup), piano transport, stereo section with power LED, volume rocker bar, input keys with square windows; Close + keyboard key.
- RULE: never show the same value twice on one panel (a control and an indicator must not mirror each other).
- RULE: media cards are drawn as devices (deck, console, tape deck), still within the Hi-Fi materials.
- Jam Home v4 (Isaac: "kinda love what you've done here"): remote = soft-touch plastic (no brushed metal), IR emitter at the very top edge, flashes RED on each press (IR transmit is a natural red; recorded as the one exception to red = alerts). Power symbols LIGHT UP (green) when the device is on; the lit glyph replaces separate power LEDs. Air purifier = full card width, no feet. Tree = a switched device (rocker + On/Off, no dimmer), like the bedroom fan/blanket.
- RULE: a control may carry a lit glyph that shows its device's power state (power symbol). Otherwise controls still don't glow.
- Next: popups for lights and every media card; a catalogue of the other Jam card types.
- Mockup 12 (Jam Home cards): pop-ups and the other card types, all from the same parts. Pop-ups: Light (big brightness slider, Cozy/Clean white keys, hue slider, "Your colours" swatch windows, group members each with slider + rocker, off-timer keys, lit power symbol); TV Source (inputs/apps as rack switches with punch-label names, no logos; the live one lights its slot + "On now"); Speaker Library (base-window tabs, record shelf, mini tape deck, grouped speakers slot); NerveOS PC (cartridge deck, Sleep/Quit/Mute, volume, small soft-plastic remote). Other cards: switched devices (symbol + name + word + rocker), house strip, weather (flat glyph, paper temp, forecast readouts), history graph as a chart recorder (paper, red grid, solid inside / dashed outside), gauge (quiet face + state word), dehumidifier (appliance sibling), doors & windows list (open = amber, red only for alerts), choice keys, control-room panel (bad value -> red word + readout), automations (slot lights, unreachable count).

## Course correction (Isaac, 2026-11-05) — "too much skeuomorphism again"
- Loves the direction and is excited to continue, BUT: ditch the brushed-metal texture and the glowing; ditch a lot of the seven-segment displays; too much orange. Likes the minimalist simplicity of the CURRENT Jam Home, which runs the **Jam Braun** look (not Poster/JamBoard). Next redesign starts from Jam Braun's simplicity.
- Keep: air purifier card ("came out great").
- Light pop-up: the CCT presets (Cozy 2200K / Clean 4000K) must SHOW their colours. Changing a light's colour should change the colour of its slot/window.
- TV Source: not a list of buttons.
- Speaker pop-up: needs a button to see other speakers, to group or separate them.
- NerveOS card: messy, rework it.
- Requested Jam Braun screenshots + tokens from the HA agent (projects/jam-home/screens/braun/).
- Isaac shared screenshots of the live Jam Home in **Jam Braun** (desktop, dark): calm charcoal cards, soft corners, pill scene chips, HA toggles, 3x2 source tile grid, NerveOS row, speaker card with a Braun dot grille and one orange dot, orange primary actions.
- Isaac: "Lets see it without the grain or the paper. Keep the ribs though."
- Mockup 13 (Jam Home simplified = Hi-Fi on Jam Braun): no grain, no paper, no brushed metal, no glow; ribs only on black bands (house strip, TV screen, NV mark). Indicator windows always a dark recess, lit = flat solid colour. Sliders reveal warm cream (or the light's own colour) instead of orange. Selected scenes/sources press in (no orange). Orange left on: rocker paddles, Turn on, Play, Done. Seven-segment only on the air purifier (cream digits). Light pop-up: five white presets (2200K-5000K) each showing its colour; colour picks recolour the light's slot and sliders. TV sources: tile grid with coloured slots. Speaker: Braun grille card + Speakers button opening a group/split panel with rockers. NerveOS: one clean row.

## Same language, bespoke designs (Isaac, 2026-11-05, after seeing part of passes 1–3)
- Isaac: "Everything should feel like it has the same design language, not necessarily the same design. In fact I don't really want to see identical cards and backgrounds across designs unless there's a clear reason. The purpose of this exercise is to create a design system where each interface design is bespoke to it's purpose, but moving between them feels natural. New elements will need to be designed, be creative, that's part of the ask. A lot of our rules will be broken which means they probably shouldn't be global rules, this is an opportunity to discover holes, and issues. Anyway keep it up!"
- DIRECTION: the bible defines a shared **language** (grammar, vocabulary, behaviour), not a shared **template**. Each app gets its own layout, surfaces, card shapes and signature elements, chosen for its purpose. Identical cards/backgrounds across apps need a stated reason.
- DIRECTION: rules get sorted into tiers (language-wide / device family / app-local / dropped) using the evidence from the passes: a rule an app had to break is a candidate to move down a tier.
- Next: pass 4 for every app with this brief (bespoke design, new elements, a "rules I broke" table), plus a rules-tier audit of BIBLE.md + CHANGES.md.

## Isaac's design notes after round 5 (2026-11-06)
Verbatim:
> CALLSHEET  I love the colors, font choice, and overall vibe of Callsheet round 5, but the cards of round 3 were less overwhelming. I think dense information benefits from being visually broken up and made to look calmer.
> The Ask page should look like a proper chat I truly love how smart it looks in Round 6, and should like to see such refinement everywhere else.
> JAMFIN I think round 5 looks the best, but I honestly don't really like any of ithem very much. The geometric shapes are interesting especially behind the titles. I miss the split shutter animation. The lights just look dumb and cheesy on the TV menu (honestly all menus) think we need to scrap almost all the lights. I like the theater direction, but let's be a little less literal. I just keep thinking about how good the color palette is in the dark version of call sheet version 6.
> JAMDASH I think jam dash V3 is my favorite design, the skumorphism is just too cheesy to work every day. That being said, I do really like seeing how the different containers connect when I drag my mouse over one. Maybe there's an interesting way to do something in between?
> NERVOS Idk I hate everything so of except what I already have. Let's not continue here until I can actually focus on what I want same goes for LOBBY. I hate how it looks, but I don't know what I want.
> HOME ASSISTANT I like the new toggles, but I liked it better with the symbols from version 5. Lets back off on the realism and incorporate the color palette from Callsheet a little bit more. Including the air purifier. It looks a little different from everything else and I think we need to make some sleight changes. I don't like the sideboard at all. It's requires too much imagination to know what to do. I really like the remote Don't need or use layout views in look 5 Don't like the keys The kiosk looks way too busy in look 5. Should be very minimalistic.
> Lobby/TV The design is very fun… but I don't think I like it. Once again I think too much reality is poking through. I don't need home assistant on there, except maybe the door being locked… that is kind of nice… I don't need audio settings up top. I think this is trying to be too many things and be too silly at the same time. Clean up the design.
> Looking back at flight instrument and Braun instrument from the four directions render look very nice and make me feel like we need to bring their calmness back in.

How I read it (Isaac's "round 6" / "version 6" = the newest round, round 5; the library page shows five rounds):
- DIRECTION (all apps): back off realism and skeuomorphism. Bring back the calm of **Braun Instrument (B)** and **Flight Instrument (D)** from `mockups/01-directions.html`. Bespoke per app stays, but by layout, type and palette, not by drawing real-world objects.
- DIRECTION: **Callsheet round 5's colours and type** (especially the dark navy palette) are the strongest; other apps (JamFin, Jam Home) borrow from that palette.
- DIRECTION: **scrap almost all indicator lights in menus** (JamFin especially, "honestly all menus"). Lights only where they carry real status.
- DIRECTION: dense information is broken into calm groups (Callsheet round 3's cards), not one continuous sheet.
- Callsheet: R5 colours/type/vibe + R3's calmer grouping; Ask is a proper chat; refine everything to Ask's level.
- JamFin: start from R5; keep the geometric shapes behind titles; bring back the split shutter; theatre idea less literal; Callsheet's dark palette; no menu lights.
- Jam-Dash: start from R3 (favourite); no skeuomorphism; keep the hover-to-see-connections idea in a lighter form.
- NervOS: PAUSED until Isaac knows what he wants. Lobby: Isaac also said pause, but gave concrete clean-up notes (no HA except maybe the door lock, no audio settings up top, less silly, fewer things); one clean-up round only.
- Jam Home: keep R5 toggles with R5's symbols; less realism; Callsheet palette incl. the air purifier (slight changes so it fits); drop the sideboard, the floor-plan/layout views and the key rail; keep the remote; kiosk very minimal.

## Isaac on Jam Home round 6 switches (2026-11-06)
Verbatim: "The only real issues I have are in Home Assistant it's confusing if a switch is on or off, and the same switch is everywhere. It makes sense for lights to have a switch like that, but the others could be smaller switches that have an accent color in the channel that is reveled when it's on. Could be an interesting subtle accent in other designs as well."
- DIRECTION: the ON/OFF paddle stays for **lights only**, and must read on/off at a glance.
- DIRECTION: every other on/off (plugs, fan, Tree, blanket, purifier power, automations, settings) uses a **small switch whose channel reveals an accent colour when on** (the "channel reveal" switch). Off = plain recess.
- CANDIDATE (language-wide): the channel-reveal switch as a subtle accent in the other apps' settings and toggles.
- Isaac's other round 6 notes: no further issues raised for Callsheet, JamFin, Jam-Dash or Lobby.

## Starting place agreed (Isaac, 2026-11-06)
- Isaac on Jam Home round 7: "This design looks much better! I like the switch color by kind but with the ability to override with a different color if I want."
- DECISION: switch accent = **colour by kind, with a per-device override**.
- Isaac: "The paddle rocker design looks super clean, and it's more obvious when its on, but now the off state isn't as clear. I don't think we need to do another round of designing though. I'll probably just have Mr Manager fix it in the real home assistant design."
- DECISION: no more design rounds for now. The paddle's OFF state is to be fixed in the real HA build.
- Isaac: "Alright I think we have our starting place for this global look and design drafts that can be passed on to the other agents to incorperate."
- DECISION: `HANDOFF.md` is the starting place. Callsheet, JamFin and Jam-Dash start from round 6; Jam Home from round 7 on round 6; Lobby isn't started (round 6 is reference only); NervOS is paused.
