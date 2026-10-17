# The Worth-It Filter

Every posting your assistant finds gets checked against your filter
before anyone spends a minute applying. A posting must pass **every**
check. When one fails, the job is killed and the exact reason is
recorded in the ledger, so the same dead end never gets re-checked.

All thresholds live in `profile/preferences.json`. The filter is only
as honest as the facts in `profile/candidate.md`.

## The checks, in order

1. **Still open.** The posting is verified live on the company's own
   careers page, not just on an aggregator. Syndicated copies go stale
   and sometimes misstate pay, location, or duties; the official page
   is the source of truth.
2. **Pay, verified in the posting.** The posting itself must show pay
   at or above your floor: a yearly number for salary roles, an hourly
   number for hourly roles. "Competitive pay" is not a number. If the
   official posting shows no pay, the job does not pass on hope.
3. **Degree-flexible in the posting's own words.** If you have no
   completed degree, the posting must say so itself: "or equivalent
   experience", "degree not required", and similar wording. A posting
   that requires a finished degree you do not have is a wall, not a
   stretch goal.
4. **No experience wall you cannot honestly clear.** A role demanding
   4+ years in a specialty you have never worked is killed. Your real
   experience (freelance, projects, other industries) counts where the
   posting's wording genuinely accepts it. It is never rounded up,
   stretched, or renamed to fit.
5. **No reference wall.** If the application requires two or more
   named professional references before you can submit, and you cannot
   name that many, it is a hard stop. "References available on
   request" is fine.
6. **No SSN gate.** An application that demands your full Social
   Security number up front is abandoned, full stop. Legitimate
   employers ask for that after an offer, through their own secure
   process.
7. **No training-repayment traps.** Some staffing programs bill you
   thousands if you leave early. If a contract or program description
   includes a repayment penalty for quitting, it is out.
8. **Schedule survives your protected blocks.** The role's stated
   schedule (including rotations and on-call) must not collide with
   the protected blocks in your preferences: classes, a current job,
   caregiving. A rotating shift that *could* land on a protected block
   is flagged as a gating item to settle before you accept anything,
   not waved through.
9. **Commute weight.** Distance from your home base is scored in
   bands (see your preferences): full credit within 10 miles, mild
   penalty to 20, real penalty to 30, and beyond 30 only when pay is
   exceptional for the tier. Remote counts as 0 miles. Hybrid roles
   are weighted by anchor days per week, so two days a week at 25
   miles can beat five days at 15.

## Scoring the survivors

Jobs that pass every check get a fit score and a plain-language
ranking. The score weighs honest skill match against your candidate
profile, pay against your target, commute band, and schedule fit. The
score ranks your application order; it never resurrects a killed job.

## How to tune it

- **Too few survivors?** Lower a floor slightly, widen a distance
  band, or add target role titles. Do not loosen the honesty rules
  (checks 3-6); loosen the numbers.
- **Too many low-quality survivors?** Raise the pay floor, tighten the
  over-30 band, or add industries to `industries_to_skip`.
- **A kill reason looks wrong?** Fix the source: if the posting
  changed, note the new wording and re-score. If your preferences are
  stale, update them. Never hand-wave a verdict.
- **Review monthly.** Your constraints change (a semester ends, a
  reference list grows, a lease moves). The filter should change
  with your life, on purpose, in writing.
