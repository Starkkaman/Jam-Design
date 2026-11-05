# Projects

Each project gets one folder. The agent that owns the project keeps it up to date.

```
projects/<project>/
  README.md        the project's UI profile (template below)
  screens/         screenshots of the current UI
  PROPOSALS.md     optional: changes you'd suggest to the bible, with reasons
```

The stub `README.md` in each folder already holds what that agent said in its interview on 2026-11-04. Correct it, then fill in the rest.

## What we need from each project

1. **Screenshots of every main screen**, in `screens/`, in the current default look. Include:
   - the home or first screen,
   - one list or grid, one detail page, one settings page,
   - focus, selected, loading, empty and error states where they exist,
   - day and night if both exist,
   - the real target size (kiosk 1024×768, TV 1920×1080, phone ~390 wide, desktop ~1440).
2. **A screen inventory**: every screen and sheet, one line each.
3. **A component inventory**: buttons, toggles, sliders, cards, lists, tiles, meters, status lights, progress, dialogs, toasts, nav. Say which are custom.
4. **Where theming lives**: file paths for tokens, fonts and per-look overrides, and how a look is selected.
5. **Hard constraints**: device, GPU, input, font licensing, minimum sizes, anything that must not change.
6. **What Isaac has said**: liked, rejected, asked for. Quote him.
7. **Open questions** for the bible.

## Template

```markdown
# <Project>

## At a glance
- What it is:
- Surfaces and input:
- Stack:
- Theming lives in:

## Screens
| Screen | What it does | Screenshot |
|---|---|---|

## Components
| Component | Custom? | Notes |
|---|---|---|

## Hard constraints

## What Isaac has said
- Liked:
- Rejected:
- Asked for:

## Open questions for the bible
```
