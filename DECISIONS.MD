# Decisions

## DP1 · The nudge — warn and redirect, never shame or block

When the weekly target is crossed, Haze keeps accepting entries and keeps counting. The sky behind the header hazes over as the week fills, so the state is visible before any text is read, and the message names the overshoot, names the category responsible for the largest share, and offers one concrete swap for it.

Blocking is the wrong tool because the app does not own the behaviour — refusing to log a trip that already happened just makes the data wrong, and a tracker with wrong data is worthless. Shame is worse: it makes people stop opening the app, which ends the only useful thing it does. A warning that points at the biggest contributor gives the user something to act on, which is the difference between feeling bad and doing something different next week.

## DP2 · Absurd input — flag it, park it, let the user decide

Each activity type has a plausibility ceiling (car and bus 1,000 km, flight 20,000 km, electricity 500 kWh, meals 20). Anything above it triggers a confirmation that shows the resulting kg in human terms — "about 21 years of the average person's CO₂ emissions worldwide" — and offers two choices: fix it, or keep it. Kept entries are saved with a "flagged as unusual" badge and are left out of totals by default, with a checkbox to count them.

Hard rejection is wrong because the ceiling is a guess, not a fact: a 25,000 km flight entry is silly, but a 15,000 km one is a real long-haul return trip, and an app that refuses real data teaches users to stop trusting it. Silently accepting is also wrong, because one mistyped entry can swamp a dashboard whose whole job is showing proportion. Flagging keeps the entry, keeps the charts readable, and leaves the judgement with the person who actually knows what happened.

## DP3 · The week — Monday to Sunday, local time, with pace instead of a single bar

A week runs Monday 00:00 to Sunday 23:59 in the user's own timezone. Monday is the ISO standard and matches how most people talk about a "work week"; a rolling seven-day window would technically be smoother, but a target that resets at an unpredictable moment can't be planned against, and the number would drift every time you opened the app.

Mid-week progress is shown three ways rather than as one percentage, because a percentage alone is misleading on a Tuesday. The chart plots cumulative kg against the target line and against an even-pace diagonal, so being at 40% on day two reads clearly as ahead of pace. Alongside it, the app states the remaining budget per remaining day. At the end of Sunday the week simply ends and Monday starts at zero — no rollover of savings or debt, since carrying a deficit forward turns one bad week into a discouraging month.