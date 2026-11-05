# Jam-Dash · Pass 3 (final)

Mockup: `mockups/pass3/jam-dash.html` (interactive). Passes 1 and 2 are unchanged.

What the page draws:
- **Home** at desktop 1440 × 900, desktop 1280 × 800 and phone 390 × 844.
- **Busy day** at 1440 and 1280 (fixed frames).
- **Settled parts**, side by side: night band, warn mark and alert key.
- **App detail** (Crafty, alert).
- **Full log** (desktop and phone).
- **Edit setup** (desktop Crafty, phone Nginx Proxy Manager).
- **History** (desktop and phone).
- **First run** (desktop and phone).
- **Settings › Servers** (1280).
- **Store** (desktop and phone).
- The final **state-words table**.

Page controls:
- **Lighting:** Day / Night.
- **Situation:** Trouble / All good / nas offline / Only warns / Busy day.
- **Home density:** Auto / Rows.
- **Motion:** Full / Calm.

Every Home caption measures itself: the ladder step reached, how far it runs over, whether every faceplate is on the first screen, and on the phone where the apps start.

All data is made-up sample data. The only host names are "home-server" and "nas". The one-time codes ("R4TN-2WQH") and the secret (shown as dots) are fake.

Sources read:
- `notes/OVERNIGHT-BRIEF.md`, all of `CHANGES.md` (A, B, D1–D103), the end of `decisions.md`, and `BIBLE.md` 0.5.
- `projects/jam-dash/README.md` (there is still no PROPOSALS.md).
- `notes/pass1-jam-dash.md` and `notes/pass2-jam-dash.md`.
- The pass-2 notes for Callsheet (Next card, D65) and HA (D82 orange budget per screen, D83 quiet paddles, D84 alert key).
- `mockups/pass2/jam-dash.html`, which this file is built from.

## What changed since pass 2
Pass 2's audit and change suggestions were the to-do list.

| Pass-2 item | Sev. | Pass 3 | Measured |
|---|---|---|---|
| #1 Busy day doesn't fit (262 px over at 1440, 362 px at 1280) | High | **Decided: Home may scroll, but only below the faceplates.** The first screen always holds the hero, every trouble card (up to 3, then "N more"), "To look at" and every server's faceplate. **Ladder step 5 = Rows:** the faceplates sit side by side under the trouble zone, and each server's apps become 36 px one-line rows (name · LED + word · Open), 5 columns at 1440 and 4 at 1280. Rows can also be chosen by hand (Settings › Home › Density, per device). | Busy day (42 containers, 3 alerts): **1440 fits** at step 5. **1280 is 164 px over**, but both faceplates are on the first screen. Trouble: 1440 fits at step 1; 1280 fits at step 5. |
| #2 Night faceplates 1.15:1 | Med | Band `#070706`, a rib every **5 px** at 14% white (was every 7 px at 9%), edge `#4a4944`, highlight `#ffffff2e`. Pass 2 and pass 3 are side by side in section 4. | Band vs ground 1.18 (was 1.15). Rib vs band 1.40 (was 1.21). Rib lines are now *lighter* than the ground (1.19), so the band reads as a striped field. Edge 1.89 (was 1.70). |
| #3 Phone: nas 1.6 screens down | Med | The **strip is now the server picker**: tap a row and its square window lights (square = selected); the grid shows that server's apps. After the first trouble card, warns fold into one "To look at · 2" row that opens in place. | Trouble: apps start at **607 px** of a 695 px first screen (was 1,145 px for nas), and the page is 1,146 px (was 1,463). nas's apps are one tap away and start at the same place. Calm: 260 px. Offline: 476 px. Busy day: 668 px (the heading sits at the fold). |
| #4 Calm Home has no orange | Med | Kept. It's a question for Isaac (Q4). | |
| #5 Warn line holding the orange | Med | When nothing is down, **the first warn becomes the trouble card** (amber ring, LED + ▲) and takes the orange. The other warns stay in the line. See "Only warns". | |
| #6 Two card layouts | Low | **One shape at every count:** LED + lab, title, one sentence, actions underneath. It's the same grammar as Callsheet's Next card (D65). | |
| #7 Triangle window = a fifth shape | Med | **Folded.** Warn is the round status LED lit amber, plus a printed ▲ in warn ink (a symbol, not a light). Indicator columns in lists are 24 px so the pair fits. | Amber vs green LED is 1.08:1 by luminance, so the ▲ is what separates them for red-green colour blindness. |
| #9 "Nginx Proxy Manager" truncates | Low | **Names wrap to two lines on tiles** and never get an ellipsis. Rows use **"Name on Home"**, a new field in Edit setup ("Proxy Manager"). | No tile name truncated at 1440, 1280 or 390, in any situation (checked by script). |
| #10 Store heading over a failed update | Low | "Updates · 2 ready · 1 didn't take", and "Updates · 1 didn't take" once the rest are done. | |
| #14 Not drawn | Med | Drawn: **first run + Add a server**, **Full log**, **Edit setup** (ports, folders, environment, restart policy, memory limit), **History**, **Settings › Servers**. Backups: the README doesn't describe a backups feature (Kopia and Duplicati are just sample apps), so there's no screen. | |
| HA D84 (alert key) | — | **Adopted.** An alert's fix is the solid red key with dark text (5.52:1). Only the newest alert gets it; the other cards get plain keys. While it shows, nothing on the screen is orange. | |

## Research
I ran 4 WebSearch queries this pass. They only fill gaps for the new screens. Pass 1 and pass 2 covered the products in general.

| Product | What I found | Used for |
|---|---|---|
| **Dozzle** (web: linuxiac, virtualizationhowto, a homelab doc; flagged as secondary) | A live tail with **pause auto-scroll**, search that **highlights matches**, a `/` key to focus search, filters (some sources add level/time), and download. | Full log: Following/Paused, search with cream marks, Problems, time range, Download. |
| **Komodo** (web: komo.do "connect servers", docs.rs `komodo_client`) | Adding a server takes a **one-time onboarding key** made in Core and passed to the agent, then a "connected" check. Its API has alerts with `resolved` and `resolved_ts`, newest first. I didn't find a user-facing doc for an alerts page. | Add a server: a one-time code from the other server, then live checks. History: open vs resolved, with when and how it was resolved. |
| **Portainer Duplicate/Edit** (web: oneuptime blog series, GitHub #2423; secondary) | One pre-filled form for ports, volumes, env, restart policy and limits. Changes **re-create the container**. Named volumes survive. One old report says env edits didn't stick on Synology. | Edit setup: one page, "Save and restart" says the cost, data folders stay, and Save waits on checks. |

Sources: [linuxiac on Dozzle](https://linuxiac.com/dozzle-real-time-docker-logs-viewer/), [virtualizationhowto on Dozzle](https://www.virtualizationhowto.com/2025/05/dozzle-real-time-docker-log-monitoring-made-easy/), [Komodo: connect servers](https://komo.do/docs/setup/connect-servers), [komodo_client alert API](https://docs.rs/crate/komodo_client/2.1.0/source/src/api/read/alert.rs), [Portainer recreate guide](https://oneuptime.com/blog/post/2026-03-20-portainer-recreate-container/view), [Portainer issue 2423](https://www.github.com/portainer/portainer/issues/2423).

## Design (what and why)
**The first-screen promise replaces "every app on one screen".**
- Pass 1 tried to fit every app on one screen, and 40 apps on a 1280 laptop break that.
- What the house checks at a glance is "is it OK?". That answer is in the hero, the trouble cards, "To look at" and the faceplates, so those may never fall below the fold.
- App tiles may scroll.
- Ladder step 5 (Rows) means the scroll is rarely needed. Busy day fits at 1440, and at 1280 it's 164 px.
- Rows keep every app's name, its state word and its Open key, so monitoring still works at a glance. They drop live previews and "· 12 d".

**Loudness, settled.**
- With an alert on screen, the loud thing is the **red key** on the newest alert's card (D84).
- Otherwise there's one orange, in D23 order: offline → warns → the screen's routine action. A calm overview has none.
- Forms and sheets are their own screen (D82). So Edit setup's "Save and restart" may be orange while Crafty alerts elsewhere.
- Disabled Save is plain, so the orange only appears once there's something valid to save.

**Edit setup** (README "Edit setup").
- Five cards: Name on Home, Ports, Folders, Environment, When it restarts (plus the memory limit).
- Every port is checked as you type: "8080 is used by SABnzbd on home-server. Pick another." That's warn, and Save waits.
- Folders show whether they exist, with a read-and-write / read-only key.
- Secrets are dots with **Replace**, and "Set by you on Oct 2". They're never shown back (README hard constraint).
- The save bar is sticky. It counts changes and says what saving does ("restarts Crafty, about 30 s").
- Saving an alerting app runs the restart and lands on the detail page, where the fix plays out.

**Full log.**
- Following/Paused uses the slot window: lit while following.
- While paused, new lines are counted ("3 new lines · Jump to newest") instead of moving the view.
- All lines / Problems · n; 10 min / 1 hour / Since start ("4,812 earlier lines · Load more"); search with cream highlights and a match count; Wrap lines; Download.
- Failing lines carry ▲ as well as colour.
- Phone: the controls wrap above the log, and line numbers hide.

**History.**
- Seven days, both servers, grouped Tonight / Yesterday / date.
- Open items keep a lit LED, the word "Open now" and "Go to it".
- Finished items show an unlit LED and how they ended: "Fixed 01:53 · started by you", "Back at 22:14 by itself", "Back under 90% on Nov 4". That's the same quiet form as Callsheet's seen alert (D69).
- Filters: Everything / Problems / Updates.
- There's no bell and no unread count, because Home is where open things live. History is reached from the hero's sub line.
- Fixes and updates made on the page appear here.

**First run (step mode, D66).**
1. Set a password.
2. This server: what was found, and the promise that "26 came from CasaOS. They keep running as they are. Jam-Dash changes nothing until you ask".
3. Add another server (optional): its address and a one-time code from that server's Settings › Servers › Let another server in. The first code fails ("That code didn't match. Codes last 10 minutes…"), and the second one connects with three checks.
4. Done, showing both faceplates.

Slot windows show progress, there's one orange per step, and Skip and Back are links. Settings › Servers has the same Add a server sheet and its own failure: "That's nas, which is already here. Nothing changed." **Let another server in** shows the code with Copy and says what it allows.

**Phone Home.** Hero → strip (server picker, disk mini-meters) → first trouble card → the next alerts as rows → "To look at · 2" folded → the chosen server's apps in two columns of name tiles, with names up to two lines.

## Audit
Checked with Playwright (Chromium, `chromium.launch()`):
- Widths: 1500 px (light scheme) and 390 px (dark scheme).
- All five situations, Day and Night.
- Flows: Restart Crafty on Home; a port conflict in Edit setup; a log search; first run fail → connect → done; Update all (Immich rolls back); Add a server in Settings; a fix shown in History; phone strip → nas; the phone busy day.

Results:
- **No JS errors.**
- **No horizontal page scroll at 390**, and no horizontal overflow inside any frame body.
- **No text under 12 px.** Inside the frames, the minimum is 13 px except keycaps (12).
- **No phone button or input under 44 × 44**, except checkboxes, whose labels are 44 px tall.
- No tile or row name, state word or strip line truncated. The script flags the ▲ wrapper as a false positive.

Contrast:
- Ink on alert red: 5.52.
- warn-ink on the day card: 5.79. Warn on the night card: 8.57.
- band-dim on the new band: 8.2.
- Search mark on the log: 13.8. Line numbers: 5.3.

The fix pass corrected:
- the warn LED + ▲ pair spilling out of 14 px grid columns (10 px over on phone Home; the pair is now one inline unit, and the columns are 24 px);
- the section-4 faceplate overflowing the page at 390 (it now sits in a container so its meters stack);
- the phone save bar scrolling away (it's now sticky);
- folder paths breaking mid-word (they now break after slashes);
- ports' check column squeezing (the check moved under the row);
- the phone apps starting at 1,088 px (warns now fold into one row: 607 px);
- the contrast figures in section 4, which were recomputed.

| # | Problem | Severity |
|---|---|---|
| 1 | **At 1280, plain Trouble (2 alerts) already reaches Rows.** The ladder is honest, but a small laptop loses tiles, live previews and the stopped chips with only 20 apps. Step 5 might need a floor ("only above ~24 running apps"), with the page scrolling under the promise instead. | Medium |
| 2 | **Busy day at 1280 still scrolls 164 px**, and nas's rows start at the fold. The first-screen promise holds, but you can't see every app at once. | Medium |
| 3 | **The add-a-server flow is my assumption.** The README says Global goes through the HA add-on and doesn't say how servers pair. The one-time code follows Komodo's pattern. Jam-Dash's real mechanism has to be checked before the bible states it. | Medium |
| 4 | **Night bands rely on 1 px ribs.** Band vs ground is still only 1.18:1. On a scaled or low-quality display, 1 px lines every 5 px can alias or shimmer. Day ribs are unchanged from pass 2. | Medium |
| 5 | **A lot of red on the busy day:** three red-ringed cards and one red key, plus three red row marks. "Said once" holds per element, but the screen is loud. | Medium |
| 6 | **Phone busy day:** the apps heading is at 668 px of 695, so the tiles start below the fold. nas is one tap away, but home-server's apps need a scroll. | Medium |
| 7 | **No push.** History is pull-only. A housemate learns Crafty is down only by opening Jam-Dash. The README lists no notifications. | Medium |
| 8 | **Folded warns on the phone** name the items ("Immich, nas's pool") but hide their buttons behind a tap. | Low |
| 9 | **"Name on Home" is a new data field.** Until someone sets it, rows still cut a long name (with the full name as a tooltip). Tiles wrap, so tile rows can differ in height. | Low |
| 10 | Edit setup's orange Save while an alert shows elsewhere reads as a loudness exception, even though it follows D82 (a form is its own screen). | Low |
| 11 | Two warn forms remain on the strip: the disk mini-meter prints "▲ Pool" with an amber bar but no LED (there's no room). | Low |
| 12 | Phone full log: the three control rows take about 170 px before the first line. | Low |
| 13 | **Not drawn:** the Apps table, System, Find ⌘K, Custom app, upload progress, phone Settings, Sign in. Backups have no screen because the README has no such feature. | Medium |
| 14 | The mockup loads Jost and Plex Mono from Google Fonts. The product bundles them. | Low |

## Questions for Isaac
1. **Busy day:** may Home scroll as long as the hero, trouble, "To look at" and every server's faceplate stay on the first screen? *Recommendation: yes.* It's the only rule that holds at 40 apps on a laptop.
2. **Rows:** should it be automatic as the last ladder step, a per-device choice, or both? *Recommendation: both, with Auto as the default.* Consider a floor so a small laptop with 20 apps keeps its tiles (audit 1).
3. **The red alert key (HA D84) in Jam-Dash:** one red key on the newest alert, plain keys on the others, and no orange while it shows? *Recommendation: yes.* It matches HA, and one loud thing per screen survives three alerts.
4. **A calm Home with no orange at all** (from pass 2). *Recommendation: keep it.* Calm should look like nothing to do. Every tile still has Open.
5. **Warn mark:** fold pass 2's triangle window into the round LED plus a printed ▲? *Recommendation: yes.* It keeps the bible at four indicator shapes, and the ▲ is what makes amber readable for colour-blind eyes.
6. **Night bands:** a deeper black with a rib every 5 px. Should the same apply to every night band (HA's night dock, TV bands)? *Recommendation: yes for HA and the phone strip. Check the TV separately*, because of shimmer (audit 4).
7. **Adding a server** with a one-time code shown on the other server? *Recommendation: yes, pending a check of how Jam-Dash pairs today* (audit 3). It's simple and there's nothing to copy by hand except the code.
8. **Notifications:** should Jam-Dash push alerts? *Recommendation: not from Jam-Dash.* Keep History pull-only, and later expose alerts to Home Assistant, which already notifies phones. Make it opt-in, alerts only, never warns.
9. **"Name on Home"** as a per-app short name? *Recommendation: yes, optional.* Tiles wrap anyway, and only rows need it.
10. **Phone warns folded** into one row under the trouble card? *Recommendation: yes.* It's what puts a server's apps on the first screen.

## Bible implications (final form)
1. **State words:** shared hooks on / off / offline / action / alert, plus **warn**. Each comes in three lengths: lab word, short word (≤ 14 characters) and sentence. "Fixed hh:mm" and "Seen hh:mm" are the quiet past forms.
2. **Four indicator shapes only** (round, square, slot, bar group). Warn = the round LED lit amber + a printed ▲ in warn ink. This replaces D92's triangle window.
3. **One loud thing per screen:** an alert's fix is the solid red key (the newest alert only). Otherwise there's one orange in D23 order. Calm overviews have none. A sheet or form is its own screen.
4. **One trouble/Next card component** (LED + lab, title, one sentence, actions underneath) at every count, shared with Callsheet. When nothing is down, the first warn takes the card.
5. **Dashboards: the first-screen promise.** The status summary (headline, trouble, warns, group faceplates) never falls below the fold. Items may scroll after the density ladder has run.
6. **The density ladder ends in Rows** (one-line name · LED + word · Open, at least 250 px wide). It's also a per-device setting.
7. **Phone overviews with groups:** the group strip doubles as the group picker (lit square = shown). Trouble after the first card folds into one row per kind.
8. **Night black bands:** `#070706`, a 1 px rib every 5 px at 14% white, edge `#4a4944`, top highlight `#ffffff2e`. Night ribs may be denser than day ribs.
9. **Names never get an ellipsis on tiles:** they wrap to two lines. Single-line rows use a user-set short name.
10. **History pattern:** a 7-day log of problems and changes. Open items are lit with "Open now"; finished ones are unlit and say how they ended. No bells, no unread counts.
11. **Step mode for setup flows** (D66): every step that can fail says what to do next, and the second try is one press away.
12. **Secrets:** typed only by the person, shown as dots with Replace, never shown back. This is a house rule for every app.
13. **Live text steps, it doesn't stream** (extends D100): a following log appends on change, and when paused it counts new lines instead of moving.
14. **Forms check as you type.** A failing check is warn (amber + ▲ + what to do), and the save button waits. Saving says its cost ("restarts Crafty, about 30 s").
