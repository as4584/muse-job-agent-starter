# Setup Guide

You do not need to be technical to set this up. You need a text editor,
an AI assistant that can connect to your email and calendar, and about
an hour of honest answering. Go in order.

## Step 1: Copy the templates

In the `profile/` folder:

- Copy `preferences.template.json` and rename the copy to
  `preferences.json`.
- Copy `candidate.template.md` and rename the copy to `candidate.md`.

The ledgers (`companies.jsonl`, `contacts.jsonl`,
`applications/submitted.jsonl`, `outreach/steps.jsonl`,
`tasks.jsonl`, `schedule.jsonl`) each contain
one example line with fake data, marked `"_example": true`. Delete
that line when you add your first real record. Each example line shows
every field the system expects.

## Step 2: Write your candidate profile

Open `profile/candidate.md` and fill in every section. Be plain and
exact. This file is the single source of truth your assistant checks
before it writes anything about you.

What matters most:

- **Your real experience**, with dates. Side projects, freelance work,
  family business help, self-hosted projects: it all counts if it is
  true and you can talk about it.
- **Honest skill notes.** Rate yourself the way a fair interviewer
  would after a week of working with you. The filter uses these notes
  to avoid roles whose walls you cannot honestly clear.
- **Things you must never claim.** Degrees you have not finished,
  jobs you did not hold, tools you have not used. Writing these down
  protects you: a good assistant checks this list before every
  application.
- **Your references policy.** How many professional references can you
  actually name today? Many people can name exactly one, or none. That
  is normal, and the system is built for it: roles that demand named
  references up front become a hard stop instead of a scramble (see
  Step 3). "References available on request" is fine; a form that
  requires two named references before you can submit is not.

## Step 3: Set your preferences

Open `profile/preferences.json`. Every field is explained in the
template. The ones to decide carefully:

- **Pay floor.** The lowest yearly salary or hourly rate worth your
  time. Jobs below it are killed automatically, with the reason
  recorded.
- **Commute bands.** How far you will travel, and how distance weighs
  against pay. A common setup: full credit within 10 miles, a mild
  penalty to 20, a real penalty to 30, and beyond 30 only for
  exceptional pay. Remote counts as 0 miles. For hybrid roles, weight
  the commute by in-office days per week.
- **Protected schedule blocks.** Classes, a current job, caregiving,
  anything a new job's schedule must survive. List them with days and
  times. The filter kills any role whose stated schedule collides with
  a protected block, and your assistant must never schedule over them.
- **Hard rules (booleans).** Switches like
  `never_apply_if_ssn_required_upfront` (an application that demands
  your full Social Security number before you are even a candidate is
  a walk-away), `never_apply_if_named_references_required_upfront`,
  `never_invent_references`, and `approval_required_before_submit`.
  Leave them all `true`. They exist because each one has burned a real
  job seeker before.
- **Target roles.** The exact job titles you want. Discovery searches
  for these.

## Step 4: Connect your accounts, safely

Your assistant needs three connections, each made inside the
assistant's own secure flow:

- **Email**, to send approved outreach and to watch for replies,
  rejections, and interview invites.
- **Calendar**, so schedule checks run against your real life, not a
  guess.
- **LinkedIn** (or your professional network of choice), for contact
  profiling and connection requests.

Rules that keep you safe:

- You always sign in yourself, on the service's own page, through the
  assistant's connection flow. You never type a password into a chat,
  and you never share one.
- One-time codes from email or text are yours. Many assistants can
  fetch and enter a code through a protected route with your approval;
  if that route fails on a given site, you paste the code once and the
  flow continues. A code is never stored or reused.
- If a site offers account-based applications (one account, many
  applications), prefer it: it avoids a fresh code challenge on every
  application.

## Step 5: Run your first sweep

Ask your assistant, in plain words:

> "Run a discovery sweep for my target roles. Verify each posting is
> still open on the company's own careers page. Score each one against
> my filter and show me the verdicts, including the exact line that
> killed any job you reject."

Start small: three strong applications beat ten thin ones. For each
survivor:

1. The assistant drafts the application from your profile facts only.
2. You read and approve the exact text.
3. It submits, and the application is logged with the date. That date
   starts the outreach cadence (see `docs/CADENCE.md`).

## Step 6: Settle into the daily rhythm

- **Morning:** check the board. Replies first, then today's due
  follow-ups, then any new applications to approve.
- **Follow-ups:** drafts wait for your approval. Sending is always
  your call, on the exact text.
- **When a reply lands:** the cadence for that company stops on its
  own and the conversation becomes yours.

## Troubleshooting

- **A job looks great but got killed.** Read the recorded kill reason
  in the ledger. If the reason is wrong (the posting changed, your
  preferences are stale), fix the source, not the verdict: update the
  preference or note the posting's new wording, then re-score.
- **A contact has no email.** Normal. The cadence skips email steps for
  that contact instead of guessing an address. A guessed address is
  marked unverified and produces no steps until verified.
- **No free connection notes left on LinkedIn.** Also normal on free
  accounts. Requests go out without a note, and your drafted note
  becomes the first message if they accept. See `docs/CADENCE.md`.
