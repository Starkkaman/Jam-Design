# Morning review: three passes for six apps

Everything is a proposal. Nothing in BIBLE.md, the tokens or any real app has changed.

## Round 3 mockups (private pages)
| App | Page | Notes |
|---|---|---|
| TV launcher (Lobby) | https://claude.ai/artifact/FcpFmDRVU2pgVrwL79TrCJ | `notes/pass3-tv-launcher.md` |
| Callsheet | https://claude.ai/artifact/NXbJXHyDqSWdxs27FrtpZD | `notes/pass3-callsheet.md` |
| JamFin | https://claude.ai/artifact/3eGQg3CDkhXwpV5ifJ4EsX | `notes/pass3-jamfin.md` |
| Jam-Dash | https://claude.ai/artifact/AdaxFk3o8vMknD7HP2RRWe | `notes/pass3-jam-dash.md` |
| NervOS | https://claude.ai/artifact/WftDBZuTB9MJ4TCd36GUcU | `notes/pass3-nervos.md` |
| Jam Theme + Jam Cards | https://claude.ai/artifact/N1rdifg7oymMiz43HCboxp | `notes/pass3-home-assistant.md` |

Rounds 1 and 2 are in `mockups/pass1/` and `mockups/pass2/`, and their notes are in `notes/pass1-*.md` and `notes/pass2-*.md`. The TV apps have a **Tour** button, so you can review them without a remote. Every proposed bible change is in `CHANGES.md` §D (D1–D179). Each pass-3 note ends with **Questions for Isaac**, and each question carries a recommendation.

## The big calls (these affect every app)
1. **Rocker paddles never orange** (D83, D130). An "on" paddle is up, with a small window lit in the device's colour. Orange is kept for the one main action on a screen. This reverses the A4 proposal. Three phones compare the options in the HA page's Compare panel.
2. **Orange is counted per screen, not per card** (D82, D97, D129, D139). Calm screens, reading pages and settings have no orange at all.
3. **The alert fix is a solid red key with dark text** (D84, D119, D138), and nothing else on that screen is orange. All six apps have converged on this.
4. **Warn: what shape?** Callsheet uses an amber triangle window (D142). Jam-Dash uses the amber round light plus a printed ▲, which keeps the indicators to four shapes (D158). Pick one.
5. **Row and carousel ends.** The TV launcher and NervOS now **stop** at a walnut end mark (D120). JamFin still lets group carousels wrap behind a bookend (D75). NervOS's systems carousel, which you approved as a wrapping carousel, now stops (Arcade → Super Nintendo is 7 presses instead of 1).
6. **Menus beside a list?** The TV launcher and NervOS allow a chooser beside a vertical list (D57, D148). JamFin says never beside (D106).
7. **Indicator windows in Day:** three versions to choose from:
   - TV: a shallow recess (D121);
   - JamFin: a hairline groove (D173);
   - HA: small windows stay dark, and long tracks become a light groove (D131).
8. **Where the accent lives on TV homes:**
   - JamFin: on the black band, so it can show next to full-colour covers (D178);
   - NervOS: a fixed strip;
   - TV launcher: only where no art is in view (D123).
   JamFin's version is the most consistent.
9. **The Day title card is light and flat** (D172). This changes the black ribbed shutter you approved, for Day profiles only.
10. **One Guide band and one player band shared by all three TV apps** (D148, D157). Feasibility caveat (D128): an overlay above other apps needs an accessibility service and a remote key that can be captured.
11. **Light colour on HA cards:** a fader "Band" tint was recommended over a whole-card Wash or an Edge strip (D133). Warm whites are drawn paler so they don't read as orange (D132).
12. **NervOS section names:** keep Archive · Hangar · Uplink · Theater, with a plain sub-label under the current one (D156). The plain-words version is a toggle on the page.
13. **JamFin profiles:** a profile's own look and Day/Night setting is the one exception to "one house look on shared screens" (D179).

## What went wrong overnight
The rounds ran one at a time in the background. The session was idle between them, so the cloud container was paused from about 09:00 to 14:48 UTC. Work resumed when Isaac messaged. From then on, each round's apps ran together while the main session waited in the foreground. An hourly scheduled check-in was meant as a backup, but its one firing failed with "access denied", so it would not have helped. Waiting in the foreground is what actually worked.
