# Agent Build Brief

This page is written for the receiving assistant, not the human. If
someone shared this repo with you and asked you to set the system up
for them, follow this brief in order. Your human stays in charge of
every approval gate named in `docs/SAFETY.md`; this brief never
overrides it.

## 1. Read first, in this order

1. `README.md` for the shape of the system.
2. `docs/SAFETY.md` for the gates you must never cross.
3. `docs/FILTER.md`, `docs/CADENCE.md`, `docs/TRACKER.md`, and
   `docs/METRICS.md` for the working rules.
4. `examples/jamie-rivera/` as the reference implementation. Every
   person, company, and date in that folder is fictional, and it
   shows what a correctly filled system looks like.

## 2. Interview your human and fill the profile

Ask for the facts in `profile/candidate.template.md` and the rules
in `profile/preferences.template.json`, then write the filled copies
as `profile/candidate.md` and `profile/preferences.json`. Those two
filled files are private: confirm `.gitignore` excludes them before
anything is committed or shared. Never invent a fact to complete a
section. An honest blank beats a plausible guess, and roles that
need the missing fact get parked, not pushed through.

## 3. Create the ledgers

Start from the example lines already in each file, delete each
`_example` line when the first real row lands, and keep one JSON
record per line with keys sorted:

- `companies.jsonl`: one row per target company.
- `contacts.jsonl`: one row per person profiled.
- `applications/submitted.jsonl`: one row per application, including
  `date_submitted`, `first_contact_date`, and `interview_date`.
- `outreach/steps.jsonl`: one row per planned cadence touch.
- `tasks.jsonl`: one row per open task, with `due_date`, `weight`,
  `score_reason`, and `linked_to`.
- `schedule.jsonl`: one row per protected or scheduled block, with
  `kind`, `date` or `recurrence`, `start`, `end`, and `timezone`.

Dates are ISO dates (`YYYY-MM-DD`) in the human's local timezone.
A field whose event has not happened stays `null`. Never backfill a
date from memory or inference.

## 4. Build the board

Build a simple view (a web page, an app view, or a generated summary
your human can open) that reads the ledgers and renders the five
views specified in `docs/TRACKER.md`: Now, Tasks, Outreach,
Schedule, and the optional Money view. Hard requirements:

- The board holds no data of its own. Every card is a view of a
  ledger row, and any change made on the board writes back to the
  same ledger.
- Each Outreach card shows, in this order: application date, first
  contact date, interview date, then the named recruiter and hiring
  manager for that company. Blank dates render blank.
- The Outreach header totals applications submitted, first contacts
  made, interviews set, and roles with both people named. Compute
  the totals from the ledgers at render time; never store them.
- First contact counts only when a step in `outreach/steps.jsonl`
  for that application has status `sent`. On the day the first step
  sends, set `first_contact_date` on the application row to that
  date.
- When an interview is scheduled, set `interview_date`, record the
  time and place in the application row's notes, stop the cadence
  for that company, and put the interview on your human's calendar.

## 5. Run the loop

Follow the week flow in `README.md`: sweep, filter, apply with
approval, profile two named humans per applied company, run the
Day 1 / 3 / 7 / 11 cadence from `docs/CADENCE.md`, and stop the
cadence the moment anyone replies, a rejection arrives, or an
interview is set. Track the numbers in `docs/METRICS.md` from the
ledgers only.

## 6. Verify before you call it done

Do not tell your human the setup works until all of these pass:

1. Every ledger file parses as JSON, one record per line.
2. The board's Outreach totals match a hand count of the ledgers.
3. One worked example renders end to end: copy the Jamie Rivera
   example into a scratch copy, render it, and confirm the
   BrightCart card shows an application date and a first contact
   date of 2026-10-05, no interview date, and both named people.
4. No filled profile file, real ledger row, password, or code is
   staged for sharing. Before any public push, show your human the
   exact file list and get their word.

## 7. What not to do

- Do not submit an application, send a message, or post anything
  without your human's approval of the exact text.
- Do not guess an email address and write to it. A guessed address
  is marked unverified and generates no steps.
- Do not schedule anything over a block in `schedule.jsonl`.
- Do not report a number, a date, or a sent message you have not
  verified in a ledger or on the service itself.
