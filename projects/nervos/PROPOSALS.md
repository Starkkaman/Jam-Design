# NervOS: proposals for the bible

Checked against BIBLE.md draft 0.3 for the two NervOS hard limits: the GPU budget (a GTX 1060 Mobile shared with
games) and SAFE motion. Most of Hi-Fi fits. The points below conflict, or would need a rule to fit.

## P1. Say what Calm/SAFE means, not only that it exists
§9 asks for "a Calm/SAFE setting everywhere" but doesn't define it. NervOS SAFE today:
- no continuous motion (ticker, attract pulse and idle loops stop; grain is static);
- no shake or flash;
- every transition becomes a short fade;
- the boot is shortened (6.5 s → 1.8 s).

**Proposal:** adopt that as the shared definition. For the light reveal (§3) in SAFE: the glow appears at once, or with a
fade of ≤ 180 ms, with no travelling shutter.

**Why:** each app currently decides on its own, and a household setting should mean the same thing on every screen.

## P2. Light spill must be one-shot, not a live effect (settled in 0.3)
§7 W1 lights the window, gives the label "an uneven warm glow" and lets the spill light "the panel's rib texture".

**Proposal:** state that the glow and spill are pre-drawn textures faded with opacity when focus arrives, with no live blur
or per-frame light pass, and nothing animating once focus has landed.

**Why:** the GPU is shared with the running emulators, and the frontend stays up behind the game. Draft 0.3 now says this: glows are pre-rendered sprites faded by opacity, and the spill is one bitmap per tile width. Nothing more is needed. NervOS can afford
opacity and transform changes on focus, but not a continuous lighting shader. This matches the bible's own "transform
+ opacity only" rule. It just says so for the selector.

## P3. Allow stepped motion as an alternative to the settle curve
NervOS decoration moves on twos (12 fps, stepped), which also makes it cheaper: it only redraws 12 times a second.
Focus moves take 140 ms, and the bible's 150 ms is close enough.

**Proposal:** let a look declare "stepped" as a fifth curve beside glide, decelerate, settle and leave (§8), for decoration only. Focus keeps glide within 150 ms. Floors stay the same.

## P4. Carousels for groups on TV
§9 forbids carousels for groups. Isaac asked for two of them in NervOS:
- the VHS consoles: "make the consoles free floating on the left, and as you go down the line they carosel vertically";
- CHOOSE YOUR HERO: "only want to see one on screen at a time", then "Needs to be clearer that there's other options".

Both were approved on 2026-11-03.

**Proposal:** allow a group carousel in alternate looks when the neighbours are always named or visible at the edges and
the position is shown ("3 of 8").

## P5. Full-screen film layer (scanlines, grain, fringe) per look
§9's TV floor ("no blur") doesn't mention a post layer.

**Proposal:** allow it as part of a look, chosen by the user, never drawn over real art or video, static in SAFE, and off
in Hi-Fi.

**Why:** NervOS already works this way (`ui/art_mask.gd`), and the cost is one full-screen pass that turns off when the
look is "clean".

## P6. Token shape for Godot
§10 lists Godot `theme.json` as a pipeline target. NervOS themes override tokens with a `tokens` block shaped like its
`design/tokens.json`. It uses dotted roles such as `color.bg.void`, `color.bg.panel`, `color.ink.primary`, `color.ink.secondary`,
`color.signal.amber`, `typography.scale.body.size` and `motion.duration.focus`.

**Proposal:** emit that block. The Hi-Fi roles map as `alu` → `bg.void`, `card` → `bg.panel`, `ink`/`dim` → `ink.primary`/`ink.secondary`,
`orange` → `signal.amber`, and the light colours → `signal.*`.

Two things don't map. The band and walnut trim need a NervOS layout, which is code, not tokens. The seven-segment readouts
need an OFL font: DSEG is OFL 1.1.
