# The Tracker Board

The ledgers are the truth. The tracker is the truth, arranged so a
tired human can see what matters in ten seconds. It never holds its
own version of events: every card on the board is a view of a ledger
row, and anything you change on the board writes back to the same
records your assistant works from.

## What the board shows

- **Now**: the single highest-priority task, with its score and a
  one-line reason it ranks first, plus today's time blocks and your
  next few deadlines.
- **Tasks**: everything open, ranked highest to lowest. Each row shows
  its score and why. Rows live in `tasks.jsonl`.
- **Outreach**: one card per application, built for the question
  "where does this application actually stand with the humans?" Each
  card shows three dates across the top: the date the application was
  submitted, the date first contact was made with a person at the
  company, and the interview date once one is set. Under the role it
  names the two people profiled for that company, the recruiter and
  the hiring manager, plus company, role, pay, status, and the next
  cadence touch due. A date stays blank until the real event happens;
  it is never backfilled with a guess. At the top, the view totals
  the pipeline: applications submitted, first contacts made,
  interviews set, and how many roles have both people named.
- **Schedule**: your day and week, with protected blocks (classes,
  shifts, study time) shown as walls that work is planned around,
  never over. Blocks live in `schedule.jsonl`.
- **Money** (optional): what is actually available now, what is
  coming and when, and any long-term target you are working toward,
  shown only from numbers that were verified, never estimated into
  existence.

## Where the Outreach dates come from

- **Application date** is `date_submitted` in
  `applications/submitted.jsonl`, recorded from the portal's own
  confirmation at the moment the application goes in.
- **First contact date** is `first_contact_date` on the same row. It
  is set on the day the first cadence step for that application is
  actually sent (a connection request with a note, an intro email, or
  a first message after a connection is accepted), and it must match
  a `sent` row in `outreach/steps.jsonl`. A drafted or approved step
  does not count.
- **Interview date** is `interview_date` on the same row, set only
  when an interview is actually scheduled, with the time and place
  recorded in the row's notes.
- **The two people** on each card come from `contacts.jsonl`, matched
  on `company_id`, one `recruiter` and one `hiring_manager`. If a
  person is named but has no public contact channel, the card says so
  plainly instead of inventing one. A guessed email stays marked
  unverified and generates no steps.
- When a reply, a rejection, or an interview stops the cadence, the
  card reflects it the same day, because the board reads the same
  ledgers the assistant works from.

## How tasks are ranked

Each task gets a numeric score from three honest inputs:

1. **Deadline urgency.** Due today or overdue outranks due next week.
   No deadline means no urgency points, and the row says so.
2. **Weight.** A weight you (or your assistant, with your rules)
   recorded on the task itself: the interview prep matters more than
   the inbox tidy-up.
3. **Links.** A task tied to something live counts more: a follow-up
   linked to an active application, a prep task linked to a booked
   interview, a step linked to a scheduled shift.

Ties break on the earlier deadline, then alphabetically, so the order
is always explainable. Every row carries its reason in plain words:
"due today, highest weight, linked to Tuesday's interview" beats a
bare number you have to trust.

## Keeping it true

- **One source.** If the board and a ledger ever disagree, the ledger
  wins and the board re-syncs. Never edit one and not the other.
- **Deadlines carry life logistics.** A deadline card can hold the
  practical ring around the event: what to eat or prepare beforehand,
  what to bring, when to leave. A 5 PM commitment is really a 3 PM
  prep, a 4:30 departure, and a meal that has to fit somewhere.
- **Done is a button.** Marking a task done, rescheduling it, or
  flagging it "talk this through" should be one tap from the row
  itself, and the change lands in the same records your assistant
  reads each morning.
- **Stale is a smell.** If the board shows something you know is
  finished, out of date, or wrong, say so. A board that drifts from
  reality is worse than no board, because you stop trusting it, and
  trust is the whole product.
