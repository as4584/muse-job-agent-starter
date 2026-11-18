# Platforms: where the jobs live and how you apply

Almost every posting this system touches lives on one of a small set
of applicant tracking systems (ATS), each with a public job board and,
for the big ones, a public API an agent can sweep without any login.
This page is the catalog. Its machine-readable twin is
`platforms.jsonl` at the repo root: one row per platform, with the
board URL pattern, the API pattern, and how an application actually
goes through. When you meet a platform that is not listed, add it
there and note it here.

Two files work together:

- `platforms.jsonl`: the catalog of platforms and channels, shipped
  filled in. It is reference data, not your data.
- `board-registry.jsonl`: the companies you actually sweep, one row
  per company board: name, which ATS it runs on, its board slug, the
  board URL, when you last checked it, and how many postings it held.

## How discovery works

A sweep walks `board-registry.jsonl`. For each row it calls the
platform's public postings API for that company's slug, pulls every
open posting, and hands the list to the filter in `docs/FILTER.md`.
No accounts, no scraping of search result pages: the ATS serves the
same feed its own board renders from.

To add a company: find its careers page, identify the ATS from the
URL it lands on, read the slug out of the board URL, verify the board
is live, and add the registry row. A company whose careers page is a
plain page with an email address is not a registry row; it is a
direct channel (see below) and goes in `companies.jsonl` only.

## The ATS platforms

- **Greenhouse.** Board: `https://job-boards.greenhouse.io/{slug}`.
  API: `https://boards-api.greenhouse.io/v1/boards/{slug}/jobs`
  (add `?content=true` for full descriptions). Applying is a web
  form on the board; usually no account. The largest platform in
  practice.
- **Ashby.** Board: `https://jobs.ashbyhq.com/{slug}`. API:
  `https://api.ashbyhq.com/posting-api/job-board/{slug}` (add
  `?includeCompensation=true` for pay bands). Applying is a web
  form; no account.
- **Lever.** Board: `https://jobs.lever.co/{slug}`. API:
  `https://api.lever.co/v0/postings/{slug}?mode=json`. Applying is
  a web form; no account.
- **Workable.** Board: `https://apply.workable.com/{slug}`. API:
  `https://apply.workable.com/api/v1/widget/accounts/{slug}`.
  Applying is a web form; no account.
- **SmartRecruiters.** Boards: `https://jobs.smartrecruiters.com/{slug}`
  and `https://careers.smartrecruiters.com/{slug}`. API:
  `https://api.smartrecruiters.com/v1/companies/{slug}/postings`.
  Applying is a web form; an optional account exists.
- **Rippling.** Board: `https://ats.rippling.com/{slug}/jobs`. API:
  `https://api.rippling.com/platform/api/ats/v1/board/{slug}/jobs`.
  Applying is a web form; no account.
- **Breezy HR.** Board: `https://{slug}.breezy.hr`. No public API in
  our use; read the board page. Applying is a web form.
- **Recruitee.** Board: `https://{slug}.recruitee.com`. Read the
  board page. Applying is a web form.

## Account portals

Some employers run portals where you hold a candidate account with
that employer (or that tenant), and apply from inside it:

- **Workday.** `{company}.wd{N}.myworkdayjobs.com`. One account per
  employer tenant.
- **Paylocity.** `recruiting.paylocity.com`. Account-based.
- **ADP Workforce Now.** `workforcenow.adp.com`. Account-based.
- Employer-specific portals (a single company's own system, or a
  staffing agency's portal) behave the same way.

Prefer the account flow when a portal offers one: a saved account
skips the per-application email verification codes that plain forms
often demand. Two warnings from real runs:

- A portal form may have **no resume upload step at all**. Before
  you record an application as submitted, check what the form
  actually carried. A submission the portal accepted without your
  resume is still a submission, but the ledger notes must say so.
- A confirmation email can land minutes after the confirmation
  screen. Recheck the inbox before you declare a submission failed.

## Job boards and aggregators

Indeed, LinkedIn, Built In, Handshake, and similar boards are
**discovery sources, not systems of record**. They list postings
that live on the employer's own board, and they go stale. A posting
counts only when it verifies live on the employer's own board or
ATS. Follow the listing out to the real board, apply there, and
record that platform on the application row. LinkedIn has a second
job in this system: identifying the recruiter and hiring manager
for the cadence in `docs/CADENCE.md`.

## Direct channels

Some employers take applications with no ATS at all:

- **Email application:** the posting names an address to send a
  resume to. The send is the application; the sent message is your
  readback.
- **Company website form:** a contact or application form on the
  employer's own site.
- **Hosted forms:** a Google Form or similar standing in for an ATS.
  Fields vary wildly; read the whole form before filling anything,
  and note anything it asks that your human has not approved
  (see `docs/SAFETY.md`).

## Rules that hold on every platform

- Verify the posting is live on the employer's own board before
  applying. Aggregator copies do not count.
- An application is `submitted` only with a system-of-record
  readback: a confirmation screen, a confirmation email, or the
  sent email itself for direct channels. No readback, no submitted
  status; record it as attempted and say why.
- Record the platform and the board or posting URL on every row of
  `applications/submitted.jsonl`, so a later agent can retrace
  exactly where the application went.
- Nothing submits without your human's approval of the exact
  application, per `docs/SAFETY.md`. The platform never changes
  that gate.
