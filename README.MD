# Haze — a carbon footprint tracker

**Hackathon ID: AZIS-4KJKKB**

Haze turns ordinary choices — a commute, a meal, an hour of AC — into a number you can see, and puts that number against a weekly ceiling you set yourself. The sky at the top of the page clears or hazes over as the week fills up, so you get the state of the week before reading a single digit.

**Live app:** https://chandan77480.github.io/Climate-Tech/
**Track:** Climate tech — carbon footprint tracker

---

## The five required features

1. **Log an activity** — pick a type, enter a quantity, set a date, add an optional note. The kg figure previews live before you save.
2. **CO₂ calculation** — fixed factors, exactly as the brief specifies:

   | Activity | Factor |
   |---|---|
   | Car travel | 0.20 kg/km |
   | Bus travel | 0.08 kg/km |
   | Flight | 0.25 kg/km |
   | Electricity | 0.80 kg/kWh |
   | Veg meal | 0.5 kg/meal |
   | Non-veg meal | 2.0 kg/meal |

3. **Dashboard** — total for the week, daily average, all-time total, activity count, plus a per-category breakdown as a stacked bar and a table with kg and share of total.
4. **Weekly target** — you set a kg ceiling for the week. A cumulative chart plots what you've logged against both the target line and an even-pace line, and the remaining daily budget is shown in plain words. Crossing the target changes the sky and the message; nothing is blocked.
5. **History & filter** — every activity, newest first, filterable by type and by date range, each one deletable.

## Beyond the brief

- **Four tabs** — Log & week, Insights, History, Settings — so nothing is buried and nothing is crowded.
- **A sky that reacts.** The header gradient clears or hazes over with the week's progress, readable before any number is.
- **One-tap quick log** for the repetitive things (10 km car, 1 veg meal, 5 kWh).
- **Day-by-day bars** for the current week; click any bar for a popup of that day's activities.
- **Eight-week trend** against your target line, plus weeks-under-target, heaviest day, your usual heavy weekday, and biggest single entry.
- **Week-on-week deltas** next to every category in the breakdown.
- **A what-if simulator.** Move sliders to shift car kilometres onto the bus, swap non-veg meals for veg, or trim electricity, and watch this week's actual total recompute — including whether it drops back under target.
- **Edit any entry** from history in a modal, not just delete.
- **Milestones** that mark real progress rather than awarding points.
- **CSV export, JSON backup and restore**, and a guarded delete-everything.
- **Onboarding modal** on first visit, reopenable from "How it works".
- **Guided tour** (top bar): an 8-step spotlight walk through every feature in the brief's order, with the feature numbers named in each step. Arrow keys move between steps, `Esc` ends it.
- **Impact**: turns this week's kilograms into everyday terms (km driven, phone charges, LED-bulb hours, tree-years) and projects a year at the current daily average.
- **Challenges**: four small weekly goals (even daily share, veg-forward, bus beats car, log every day) computed live from the log, with a counter on the button.
- **Share week**: draws a shareable PNG card on a canvas (its sky colour follows how the week is going) and writes a one-line summary you can copy.
- **Light and dark themes**: follows the system setting on first visit, then remembers the toggle. Chart colours and category colours retune for each theme.
- Keyboard: `L` jumps to the log form, `Enter` saves, `Esc` closes any modal, `←` `→` move through the tour.

## Tech

Plain HTML, CSS and vanilla JavaScript in a single `index.html`. No build step, no framework, no dependencies, no backend. Every chart — the cumulative week line, the daily bars, the eight-week trend — is hand-written SVG, and the share card is drawn straight onto a canvas, so there is no charting or image library to load or break. Data is stored in the browser's `localStorage`, wrapped in try/catch so the app still runs if storage is unavailable.

The choice was deliberate: a single static file deploys anywhere, loads instantly, and has nothing that can go down during judging.

## Run it locally

```bash
git clone <your-repo-url>
cd <repo>
# open index.html directly, or serve it:
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploying

Any static host works. GitHub Pages: push this repo, then Settings → Pages → Source: `main` branch, `/root`.

## Test credentials

None. **There is no authentication** — the app opens straight into all five features, as the brief requires.

On first load the app seeds five weeks of sample data so every chart has something to show. `Fill a sample week` regenerates it; Settings → `Clear everything` empties the app so you can see the blank states.

## Standard API

**Not implemented.** Features should be graded by a browser agent driving the UI. All state lives in the browser; there is no server to call.

## Decisions

The three decision points are answered in [DECISIONS.md](DECISIONS.md).

## A note on the numbers

The factors are fixed averages given by the brief, not measurements of your actual emissions. Haze is built to show patterns and relative weight between choices — it is not carbon accounting.
