# Muse Job Agent Starter

A personal job-application command center you run with your own AI
assistant. It finds jobs, filters out the ones that are not worth your
time, tracks every application, and runs a polite, persistent follow-up
rhythm with the actual humans doing the hiring, all from plain text
files you own and can read.

## What it does

- **Discovery sweeps.** Your assistant searches for fresh postings that
  match the roles you want, and verifies each posting is still open
  before it counts.
- **A "worth-it" filter you configure.** Pay floor, commute distance,
  schedule conflicts, degree walls, reference walls, and other hard
  rules you set. A job that fails any rule is killed with the reason
  written down, so you never re-check the same dead end twice.
- **Application ledgers.** Every company, contact, application, and
  follow-up step lives in simple `.jsonl` files (one JSON record per
  line). No database, no subscription, nothing you cannot open in a
  text editor.
- **An outreach cadence.** For each job you actually apply to, the
  system profiles two named humans at the company (the hiring manager
  and a recruiter) and follows up on Day 1, Day 3, Day 7, and Day 11
  (business days). The cadence stops by itself the moment anyone
  replies, a rejection arrives, or an interview is set.
- **A tracker board.** A simple view that mirrors the ledgers and
  ranks what needs your attention today, so you always know the one
  next move.

## Who it is for

Anyone job hunting who would rather spend their energy on a short list
of strong applications than on spraying hundreds of resumes into
portals. It was designed for people with real constraints: classes, a
current job, a long commute, a thin budget, or a short reference list.
The filter respects those constraints instead of pretending they do
not exist.

## Quickstart

1. Clone this repo.
2. Copy the templates and make them yours:
   - `profile/preferences.template.json` → `profile/preferences.json`
   - `profile/candidate.template.md` → `profile/candidate.md`
3. Fill in your profile honestly (see [SETUP.md](SETUP.md)). Your real
   experience, your real limits, your real rules.
4. Connect your email, calendar, and professional profiles inside your
   own AI assistant, using its secure connection flows. You never hand
   your assistant a password.
5. Ask your assistant to run a first sweep: find a few postings, score
   them against your filter, and show you the verdicts. Approve the
   good ones, apply, and the cadence clock starts.

Full walkthrough: [SETUP.md](SETUP.md). A complete worked example with
a fictional job seeker lives in [examples/jamie-rivera](examples/).

## How a week flows

1. **Sweep.** The assistant finds and verifies new postings.
2. **Filter.** Each posting is checked against your rules. Kills are
   recorded with the exact reason.
3. **Apply.** You approve the survivors; applications go in and are
   logged in the ledgers.
4. **Profile.** For each applied company, the assistant finds the
   hiring manager and a recruiter, with sources for every fact.
5. **Cadence.** Day 1 / 3 / 7 / 11 follow-ups are drafted for your
   approval. Nothing sends without your word on the exact text.
6. **Watch.** Replies, rejections, and interview invites stop the
   cadence automatically and move to the top of your board.

## Repo layout

```
profile/       Your preferences and candidate facts (templates included)
companies.jsonl        One row per target company
contacts.jsonl         One row per person profiled
applications/          submitted.jsonl: one row per application
outreach/              steps.jsonl: one row per planned follow-up touch
tasks.jsonl            One row per open task, ranked for the board
schedule.jsonl         One row per protected or scheduled block
docs/          FILTER.md, CADENCE.md, TRACKER.md, SAFETY.md, METRICS.md,
               AGENT_BUILD_BRIEF.md
examples/      A fully worked fictional example
```

Sharing this repo with a friend? Point their assistant at
`docs/AGENT_BUILD_BRIEF.md`. It is a step by step build spec written
for the receiving agent, so their Muse can set the whole system up,
board included, from these files alone.

## The rules that keep it honest

- Never invent experience, credentials, or references. Ever.
- A guessed email address is marked unverified and generates no
  outreach until it is verified.
- Outreach stays locked until you have actually applied.
- Nothing is submitted, sent, or posted without your approval of the
  exact text.
- Passwords and sign-in codes stay with you. Your assistant works
  through your own connected accounts, never around them.

Read [docs/SAFETY.md](docs/SAFETY.md) before your first real run.

## License

MIT. See [LICENSE](LICENSE).
