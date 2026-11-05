# Jam Design

One shared design language for every screen in the house:

| Project | What it is | Surfaces |
|---|---|---|
| **Jam Home** | Home Assistant dashboards + Jam Cards | Kitchen kiosk (Echo Show 8), phone, desktop |
| **Jam-Dash** | Docker manager / CasaOS replacement | Desktop, phone |
| **Callsheet** | Personal assistant: briefs, replies, agenda | Desktop, phone |
| **JamFin** | Jellyfin client | Hisense TV (10-ft), phone |
| **NervOS** | Games launcher on the Aero 15 | 65" TV, gamepad |
| **Lobby** | Ad-free TV launcher | Hisense Google TV, remote |

The brief, in Isaac's words: **clarity without ever sacrificing fun.**

## What's in here

| Path | What |
|---|---|
| [`BIBLE.md`](BIBLE.md) | The design bible. Working draft: the base look, the rules every look obeys. |
| [`decisions.md`](decisions.md) | Every decision and the feedback behind it, in order. Read this before proposing anything. |
| [`tokens/`](tokens/) | Design tokens for the base look (draft). Each project converts these to its own format. |
| [`mockups/`](mockups/) | Every mockup round, as standalone HTML. Open in a browser. |
| [`projects/`](projects/) | **One folder per project.** Each project's agent documents its UI here: screenshots, structure, constraints. See [`projects/README.md`](projects/README.md). |
| [`AGENTS.md`](AGENTS.md) | Ground rules for Claude sessions working in this repo. |

## Status

**We are only building the design doc.** Nothing in any app, theme or look is being replaced, changed or deleted.

When we do get to rollout, it goes **one app or service at a time**, and nothing existing gets deleted before that app's turn, with Isaac's OK.


The **Hi-Fi** base look is being designed. It isn't final, and **no project should restyle its UI from this repo yet.**
Current step: every project documents its existing UI in `projects/<name>/` so the bible can be checked against real screens.
