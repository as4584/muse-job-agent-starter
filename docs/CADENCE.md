# The Outreach Cadence

Applying into a portal and waiting is how applications go to die. The
cadence is the follow-up rhythm that puts a name and a face on yours:
two named humans per company, touched on a schedule, politely and with
something new to say each time.

## The shape

For every company you have **actually applied to**, the system
profiles two contacts:

- **The hiring manager**: whoever would manage the role.
- **A recruiter**: the person recruiting for the role, or a company
  recruiter if the role's recruiter is not named.

Every fact about a contact (name, title, email, LinkedIn) is recorded
in `contacts.jsonl` **with its source**. An email found on a company
page is "verified". An email guessed from a naming pattern is
"unverified", and an unverified email generates **no** steps.

## The rhythm

The anchor is your application date. Days count in **business days**.

| Day | What happens |
|-----|--------------|
| 1   | Application in. Connection request to both contacts; intro email to both (each needs a channel that exists). |
| 3   | Follow-up email, same thread, adding **one new detail** (a project, a result, a relevant fact). |
| 7   | Follow-up email, same thread, a **new angle** (a different strength, a thoughtful question about the team's work). |
| 11  | Close-the-loop email: brief, gracious, and it asks for a referral or a pointer if the role is filled. |

Follow-ups thread under the Day 1 email so the whole conversation is
one thread a busy person can read in ten seconds.

Every draft is written in your voice, checked against your profile
facts, and **approved by you, exact text, before anything sends**.
There is no "just checking in" copy anywhere in this system: each
touch adds a detail, an angle, or a graceful close.

## The unlock rule

Outreach is **locked** until the application is marked applied in the
ledger. No profiling, no steps, no messages for a job you have not
applied to. Applying is what starts the clock.

## Steps skip themselves

A step is only generated when its channel actually exists:

- No verified email for a contact → no email steps for that contact.
- No LinkedIn URL → no connection step.
- A contact with neither generates nothing, and the cadence record
  says why.

## The stop rules (automatic)

The cadence stops by itself, and pending steps are cancelled, when:

- **Anyone at the company replies** → `stopped_reply`. The
  conversation is now a real conversation; it is yours, not the
  system's.
- **A rejection arrives** → `stopped_rejection`. No arguing with a no.
- **An interview is set** → `stopped_interview`. Outreach gives way to
  interview prep.

A reply watcher (your assistant checking your email on a schedule)
flips these states. This is why connecting your email matters.

## The LinkedIn reality

Free LinkedIn accounts get a small monthly allowance of personalized
connection invitations, and it runs out fast. When it does:

- Requests go out **without a note** (a bare request still lands).
- Your drafted note is saved and sent as the **first message** if the
  person accepts.
- Connection requests themselves are a manual step in many setups:
  your assistant prepares everything and tells you exactly who to
  connect with, and you tap send. Either way, no message is ever sent
  in your name without your approval of the exact text.

## Volume

Three strong applications a day beat five thin ones. Each application
can generate up to eight touches over eleven business days, and every
one of them needs your glance. The bottleneck is your attention, so
the system spends it where the filter already said the job is worth
it.
