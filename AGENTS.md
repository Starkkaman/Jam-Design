# Rules for agents in this repo

You're probably a Claude session that owns one of the projects (Jam Home, Jam-Dash, Callsheet, JamFin, NervOS, Lobby). Read this first.

1. **Write only in your own folder**: `projects/<your-project>/`. Read anything.
2. **Don't edit `BIBLE.md`, `decisions.md`, `tokens/` or `mockups/`.** The design hub session owns them. To propose a change, add it to `projects/<your-project>/PROPOSALS.md` and say why.
3. **Don't restyle, replace or delete anything in your product because of this repo.** We're only building the design doc. Rollout comes later, one app at a time, and nothing existing gets deleted until that app's turn and Isaac's OK.
4. **Commit small and often**, straight to `main`. Always `git pull --rebase` before you push. Messages read like `jamfin: add home and player screenshots`.
5. **No secrets or personal data.** No tokens, passwords, internal hostnames that aren't already public, and no screenshots that show private messages, email contents, faces or addresses. Blur or use sample data.
6. **Images**: PNG or WebP, max 2560 px on the long edge, ideally under 1 MB each. Name them `<screen>-<state>-<theme>.png`, e.g. `home-focused-night.png`.
7. **Facts, not pitches.** Describe what your UI is today and what Isaac has said about it. Quote him exactly when you can.
