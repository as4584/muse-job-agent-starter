# Safety Rules

This system writes and applies in your name. That only works if it is
more careful than a tired human at midnight. These rules are not
settings to relax when a deadline looms; they are the load-bearing
walls. Most of them also live as booleans in
`profile/preferences.json`, set to `true`, on purpose.

## Never invent

- **Never invent references.** If you can name one professional
  reference, the system uses one. If an application demands two, the
  application dies. There is no version of this where a name appears
  that you did not provide.
- **Never invent experience, credentials, or dates.** No rounded-up
  years, no "led a team" for showing a coworker something once, no
  degree that is "basically done". Your candidate profile lists what
  you must never claim; the system checks it before every submission.
- **Never invent contact facts.** A person's email, title, or employer
  is recorded only with a source. Guessed emails are marked
  unverified and generate no outreach.

## Your credentials stay yours

- **Passwords are never shared, typed into chat, or stored by the
  assistant.** You sign in yourself, through each service's own secure
  flow, inside your assistant's connection screens.
- **One-time codes are never guessed, stored, or reused.** Where your
  assistant supports it, a code is fetched and entered through a
  protected route that shows you an approval first. Where a site's
  code widget defeats that route, you paste the code once for that
  step and the flow moves on.
- **Account-based applications are preferred** where a site offers
  them: one sign-in you control, instead of a fresh email-code
  challenge on every application.

## Approval is real

- **Nothing submits, sends, or posts without your approval of the
  exact text.** A batch approval covers only the items you were
  shown. New items need a new approval.
- **Legal attestations are yours alone.** Certifications of
  eligibility, consent forms, agreements: anything that speaks for
  you legally is clicked by you, after reading it. An assistant can
  prepare everything up to that click and no further.
- **Public posts in your name need your word**, every time, on the
  exact wording.

## Money and hard stops

- **The assistant never buys anything for you.** No fees, no
  "premium" unlocks, no paid job boards. If a step costs money, it
  stops and tells you.
- **Full Social Security number on an application = abandon the
  application.** Same for any demand wildly out of proportion to the
  stage you are at.
- **Training-repayment contracts are a kill**, not a negotiation
  (see `docs/FILTER.md`).

## Data hygiene

- Your filled-in profile and ledgers are **git-ignored by default** in
  this starter. Your job hunt is your business; a public repo should
  only ever contain the templates, the docs, and fictional examples.
- Before sharing your setup with anyone, search the whole repo for
  your name, email, and phone number. If the search finds them outside
  the fictional example folder, stop and clean first.

## When in doubt

The system stops and asks, with the blocked step named plainly. A
paused application is a small cost. A fabricated reference, a shared
password, or a sent message you never approved is not.
