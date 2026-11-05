# TV launcher (Lobby) · Pass 1

Mockup: `mockups/pass1/tv-launcher.html` (interactive: arrow keys, Enter, Esc, Q quick settings, I inputs).

## Research (from knowledge, no live browsing this pass)
- **Apple tvOS**: the top shelf turns the focused item into a big hero; a quiet grid of apps; Control Center slides in from the side; restraint, almost no chrome; focus = lift + parallax.
- **Google TV**: a profile and settings top-right; Inputs live in the top bar; "For you" rows full of recommendations and ads (the thing to remove); quick settings panel from the side.
- **Projectivy Launcher** and its themes: ad-free; wallpaper + one or two app rows; a top bar with clock and shortcuts (inputs, settings, Android settings); user-ordered apps; channels optional; themes are mostly wallpaper, card shape and focus style.
- **Takeaway**: an ad-free launcher is mostly *subtraction*: your continue-watching, your apps, your inputs, and settings one press away.

## Design (pass 1)
- Top bar: clock, Inputs (with the current input), Quick settings, Settings.
- Hero (tvOS top shelf): the focused thing's title + one line.
- Rows: Continue (covers with progress), Apps (user ordered + All apps), Inputs.
- Panels: Inputs and Quick settings slide in from the right; All apps grid; Settings list + detail with an Android settings entry.
- Launch: flat Shutter title card with the slatted bar.
- Look: simplified Braun Hi-Fi (CHANGES.md A1–A10): flat, ribs only on panels and the title card, flat base-window selector (cream), Stripes accent.

## Audit
| # | Problem | Severity |
|---|---|---|
| 1 | The Inputs row is cut off at the bottom: three rows plus the hero don't fit 1080 inside the safe area. Breaks "everything visible at once". | High |
| 2 | The Stripes accent runs into the top bar pills ("Quick settings" sits on it). The clear zone must exclude the top bar. | High |
| 3 | On a focused cover, the progress bar and the base-window selector are two cream bars a few pixels apart. Reads as two progress bars. | High |
| 4 | Panel sub-labels and hints are 1.05–1.1cqw (20–21 px at 1080p), under the 22 px TV floor. | High |
| 5 | Monogram app tiles ("Ja", "Yo") look like placeholders. Real launchers show the app's own icon or banner; brand colours need pulling into the lightness band (glare rule). | Medium |
| 6 | Hero copy when the top bar is focused says "Top bar". It should describe the destination, not the place. | Low |
| 7 | List focus (a cream bar on the left edge) differs from tile focus (base window). Two focus grammars on one device. | Medium |
| 8 | What's on the TV right now is only a tiny pill in the top bar. The current input deserves a stronger place. | Medium |
| 9 | Settings detail pane is nearly empty; Picture/Sound should show their current values inline. | Low |
| 10 | Quick settings uses segmented windows (good) but no live preview: changing picture mode should be visible behind the panel (dim the veil less). | Low |

## Change suggestions
For the next TV pass:
- Fit three rows: shrink the hero to two lines, make Inputs a compact row, or move Inputs into the top bar only.
- Clear zone for accents: below the top bar and right of the hero text, never touching interactive chrome.
- Selector vs progress: progress rides on the cover's *top* edge, or the selector window moves to a side; never two bars at the bottom.
- Bring every TV label to 22 px+ (1.15cqw); hints 24 px.
- Use real app banners (Android TV banners are 320×180) inside a frame with a flat neutral surround.
- One focus grammar: the base window for tiles AND a matching window on the leading edge of list rows (same cream, same size logic).

**Bible implications** (added to CHANGES.md §D):
- D1. A component can't show two same-coloured bars at one edge (progress + selector): define where progress lives on focusable cards.
- D2. Accent clear zones exclude navigation and chrome, not just titles and buttons.
- D3. One focus grammar per device: tiles and list rows use the same window logic.
- D4. TV minimum applies to hints and sub-labels too (22 px), with hints 24 px.
