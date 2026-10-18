# Measuring the pipeline: proof-of-work stats

A job agent that cannot show its own numbers is just a story. This page
describes the stats view the starter kit recommends, so you (and anyone
you share your setup with) can tell whether the workflow is actually
efficient or just busy.

## What to count

Everything below reads straight out of the ledgers you already keep
(`companies.jsonl`, `contacts.jsonl`, `applications/submitted.jsonl`,
`outreach/steps.jsonl`). No new database. If a number is not in a
ledger, do not put it on the dashboard.

**Output counts**

- Companies researched
- Contacts profiled (the two-humans-per-company rule makes this easy)
- Applications submitted, total and per day
- Outreach touches sent, drafted, and pending
- Money pipeline: grants and scholarships submitted, in progress, and
  the dollar value still in play

**Efficiency ratios**

- **Vetting pass rate:** postings that survived the filter divided by
  postings checked. A very high pass rate means the filter is asleep;
  a very low one means discovery is spraying. Healthy systems land
  somewhere in the single digits to low teens, because most postings
  genuinely fail on pay, distance, or experience walls.
- **Kill reasons:** group the rejected postings by the rule that killed
  them (pay, distance, experience wall, references, stale posting).
  This is the fastest way to learn which boards are worth rechecking
  and which are dry wells.
- **Cadence health:** follow-ups drafted vs. sent vs. stopped by a
  reply. A cadence that never stops is a cadence nobody is reading.
- **Stage movement:** applications that moved (reply, interview,
  offer) divided by applications submitted. Early on this number is
  small and noisy; track it weekly, not daily.

**Activity log**

One line per finished action, dated: what was done, where the proof
lives (the ledger file, the confirmation email, the submitted form),
and what is still open. The log is the receipt trail behind every
number above. If a stat cannot point at log lines, it does not ship.

## Keeping it honest

- Only count verified outcomes. A submitted application is a form the
  site confirmed, not a tab you opened.
- Never count income that has not been worked or money that has not
  landed.
- Mark estimates as estimates. A pay band printed in a posting is a
  fact about the posting, not a promise about an offer.
- Update the stats when the ledgers change, from the same source, so
  the dashboard can never drift away from the underlying records.

## Sharing it

When you share your setup, share the method and an anonymized example,
never your real ledgers. Replace names, companies, and amounts with
clearly fictional ones (the worked example in `examples/` shows the
pattern) and keep your real numbers in your own tracker.

## Worked example (fictional)

Jamie Rivera, the example candidate in `examples/`, after one week:

- 41 companies researched, 63 contacts profiled
- 9 applications submitted (1.8 per active day)
- 214 postings checked, 11 passed the filter (5.1% pass rate)
- Top kill reasons: pay below floor (61), experience wall (48),
  distance (37)
- 22 outreach touches sent, 4 cadences stopped by replies
- Money pipeline: 1 grant submitted ($2,500), 2 in progress

None of these numbers are real. They show the shape of the report a
healthy week produces, nothing more.
