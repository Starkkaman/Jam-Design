# Callsheet screens (0.9.0, Bold look)

All screenshots use made-up sample data (the app's `sample_brief.json` plus synthetic projects, accounts at example.com and a scripted chat). No real mail, names or calendar items.

- Look: Bold (`data-look=bold`, `data-base=bold`), set through `PATCH api/settings` before each run.
- `day` = light mode, `night` = dark mode. `1440` = desktop (viewport 1440 x 900), `390` = phone (390 x 844; under the 700 px breakpoint, bottom tab bar).
- Full-page captures, cut at 3000 px height. Panels, menus, the palette and the loading state are viewport captures (Chat too on phones, where the column fills the screen).
- Clock fixed at Wednesday 4 Nov 2026, 08:15 UTC. Captured with Playwright (Chromium) through an Ingress-style prefix proxy; no outside requests, no page errors.
- Name pattern: `<screen>-<state>-<day|night>-<1440|390>.png`.

| Screen-state | What it shows | day 1440 | night 1440 | day 390 | night 390 |
|---|---|---|---|---|---|
| `briefing-default` | Briefing with the Start your day card on top (first visit of the day), summary, Weekly review card, Top of the day, Security heads-ups, By area, What changed, Coming up, At a glance. | [png](briefing-default-day-1440.png) | [png](briefing-default-night-1440.png) | [png](briefing-default-day-390.png) | [png](briefing-default-night-390.png) |
| `briefing-nostartcard` | Briefing after Not now: the same page without the Start your day card. | [png](briefing-nostartcard-day-1440.png) | [png](briefing-nostartcard-night-1440.png) | [png](briefing-nostartcard-day-390.png) | [png](briefing-nostartcard-night-390.png) |
| `replies-default` | Replies list: Needs a reply header with the done meter, One at a time (the loud button), Compact/Comfortable segments, area chips, rows. | [png](replies-default-day-1440.png) | [png](replies-default-night-1440.png) | [png](replies-default-day-390.png) | [png](replies-default-night-390.png) |
| `replies-panel` | Replies with the detail panel open on the first row (phone: full-screen panel). | [png](replies-panel-day-1440.png) | [png](replies-panel-night-1440.png) | [png](replies-panel-day-390.png) | [png](replies-panel-night-390.png) |
| `replies-notepadmenu` | Replies with a row's notepad menu open (Note for Callsheet, Doesn't need a reply). | [png](replies-notepadmenu-day-1440.png) | [png](replies-notepadmenu-night-1440.png) | [png](replies-notepadmenu-day-390.png) | [png](replies-notepadmenu-night-390.png) |
| `oneatatime-default` | One at a time: one reply per card with the draft, Copy draft and Done. | [png](oneatatime-default-day-1440.png) | [png](oneatatime-default-night-1440.png) | [png](oneatatime-default-day-390.png) | [png](oneatatime-default-night-390.png) |
| `agenda-default` | Agenda: today's timeline, messages column and an invite to answer. | [png](agenda-default-day-1440.png) | [png](agenda-default-night-1440.png) | [png](agenda-default-day-390.png) | [png](agenda-default-night-390.png) |
| `chat-conversation` | Chat with a short sample conversation, source chips and steps. | [png](chat-conversation-day-1440.png) | [png](chat-conversation-night-1440.png) | [png](chat-conversation-day-390.png) | [png](chat-conversation-night-390.png) |
| `projects-default` | Projects list: slipped line, tools, active projects with status dots and due dates. | [png](projects-default-day-1440.png) | [png](projects-default-night-1440.png) | [png](projects-default-day-390.png) | [png](projects-default-night-390.png) |
| `setup-home` | Setup home: Find a setting and the four place cards (Connections, Your day, AI, Advanced). | [png](setup-home-day-1440.png) | [png](setup-home-night-1440.png) | [png](setup-home-day-390.png) | [png](setup-home-night-390.png) |
| `setup-connections` | Setup, Connections place (areas, sample Google accounts, Slack, Signal, notes and code). | [png](setup-connections-day-1440.png) | [png](setup-connections-night-1440.png) | [png](setup-connections-day-390.png) | [png](setup-connections-night-390.png) |
| `setup-day` | Setup, Your day place (name and time zone, brief times, phones, VIPs, rules, look and sound). | [png](setup-day-day-1440.png) | [png](setup-day-night-1440.png) | [png](setup-day-day-390.png) | [png](setup-day-night-390.png) |
| `setup-ai` | Setup, AI place (who writes, chat, memory, writing style, sorting, what it learned). | [png](setup-ai-day-1440.png) | [png](setup-ai-night-1440.png) | [png](setup-ai-day-390.png) | [png](setup-ai-night-390.png) |
| `setup-advanced` | Setup, Advanced place: every part in a closed drawer. | [png](setup-advanced-day-1440.png) | [png](setup-advanced-night-1440.png) | [png](setup-advanced-day-390.png) | [png](setup-advanced-night-390.png) |
| `findorask-open` | Find or ask (Ctrl/Cmd+K, or Find in the header) with "budget" typed: people and threads, settings, ask Chat. | [png](findorask-open-day-1440.png) | [png](findorask-open-night-1440.png) | [png](findorask-open-day-390.png) | [png](findorask-open-night-390.png) |
| `replies-allclear` | All clear moment: last reply done, the stamp and shapes land once a day (captured after the motion). | [png](replies-allclear-day-1440.png) | [png](replies-allclear-night-1440.png) | [png](replies-allclear-day-390.png) | [png](replies-allclear-night-390.png) |
| `replies-empty` | EMPTY: no replies and nothing done today (the still All clear). | [png](replies-empty-day-1440.png) | [png](replies-empty-night-1440.png) | [png](replies-empty-day-390.png) | [png](replies-empty-night-390.png) |
| `agenda-empty` | EMPTY: nothing on the calendar today. | [png](agenda-empty-day-1440.png) | [png](agenda-empty-night-1440.png) | [png](agenda-empty-day-390.png) | [png](agenda-empty-night-390.png) |
| `briefing-empty` | EMPTY: a quiet day on Briefing (no events, no replies, no sections). | [png](briefing-empty-day-1440.png) | [png](briefing-empty-night-1440.png) | [png](briefing-empty-day-390.png) | [png](briefing-empty-night-390.png) |
| `chat-empty` | EMPTY: Chat with no conversation yet (intro, suggestions, question box). | [png](chat-empty-day-1440.png) | [png](chat-empty-night-1440.png) | [png](chat-empty-day-390.png) | [png](chat-empty-night-390.png) |
| `projects-empty` | EMPTY: no projects yet. | [png](projects-empty-day-1440.png) | [png](projects-empty-night-1440.png) | [png](projects-empty-day-390.png) | [png](projects-empty-night-390.png) |
| `briefing-loading` | LOADING: first load before api/brief answers ("Loading…"). | [png](briefing-loading-day-1440.png) | [png](briefing-loading-night-1440.png) | [png](briefing-loading-day-390.png) | [png](briefing-loading-night-390.png) |
| `briefing-writing` | LOADING: the rules brief is shown while the AI writes ("Writing the summary… Started 08:14."). | [png](briefing-writing-day-1440.png) | [png](briefing-writing-night-1440.png) | [png](briefing-writing-day-390.png) | [png](briefing-writing-night-390.png) |
| `chat-thinking` | LOADING: Chat thinking on a question, with the steps so far and Stop. | [png](chat-thinking-day-1440.png) | [png](chat-thinking-night-1440.png) | [png](chat-thinking-day-390.png) | [png](chat-thinking-night-390.png) |

96 files.
