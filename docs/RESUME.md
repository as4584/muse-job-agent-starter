# Resumes: proof first, built with STAR

This system does not keep a generic resume. It keeps one **master
resume** built from a verified facts inventory, and tailors a fresh
copy for every application. This page is the method. It exists
because the failure mode of resume writing, human or agent, is
inventing plausible claims. Every rule below points at that.

## Start from facts, not adjectives

Before any resume work, build the facts inventory: every role,
project, tool, and number your human can stand behind, each with
its evidence. A claim that is not in the inventory does not go on a
resume. When a number matters (tests run, users served, money
saved), the inventory records where it was measured, not just the
figure.

Every entry also carries a **claim state**: production, in daily
use, in development, class project, or planned. Write the state's
truth and never stronger. A project that was never deployed is
framed on what it demonstrates (integrations, system design), never
as experience serving real users. One wrong label in the inventory
becomes a false claim on every resume built from it, so states are
set by the human, never inferred from the fact that code exists.

## Frame each application: Problem, Fit, Solution

For a specific posting, work in three parts before writing:

1. **Problem.** What the employer is actually hiring to fix, in
   their words from the posting.
2. **Fit.** The inventory facts that answer that problem, listed
   honestly, with the gaps listed too. A gap you name is a gap you
   can plan around; a gap you hide becomes a claim you cannot
   defend.
3. **Solution.** The tailored resume itself, presented as the
   answer: the experience and projects that solve their problem,
   ordered so the strongest fit reads first.

The same frame shapes recruiter emails and outreach messages: their
problem, the verified fit, the application as the solution.

## Format lock

Standard single-column format. Standard headings in this order:
Experience, Projects, Technical Skills, Education. Reverse
chronological. Real text bullets, action verbs, no decorative
formatting, no stylized headers, no symbol bullets.

**No Summary section. No Objective line.** Both were tried and both
were cut: a summary repeats what the bullets should prove, and an
objective tells the employer what you want instead of what they
get. The resume stands out by proof, not by framing.

## The STAR pass

Every Experience bullet is built with STAR, then compressed into
one line:

- **Situation:** the context. What was happening, at what scale.
- **Task:** what you were responsible for.
- **Action:** what you actually did, with the tools you used.
- **Result:** the measurable outcome. A number, a deliverable, or
  a live state ("in daily use", "in production").

Then the house ordering rule: **the written bullet leads with its
Result**, and the action and scope follow it. A bullet that opens
with a duty instead of a result fails the pass. Where a second
evidenced result exists, a Result closes the bullet too.

Worked example (fictional):

- Draft: "Responsible for helping customers with checkout
  problems."
- STAR underneath: Situation, a support queue with a two-day
  backlog. Task, resolve checkout and billing tickets. Action,
  built a triage flow and a macro library for the twelve most
  common issues. Result, average resolution time fell from two
  days to four hours across 300+ tickets a month.
- Shipped bullet: "Cut average ticket resolution time from 2 days
  to 4 hours by building a triage flow and macro library for the
  12 most common checkout issues, across 300+ tickets a month."

Rules that keep the pass honest:

- A bullet with no Result gets one **only** from inventory
  evidence. If no evidenced result exists, rewrite it as action
  plus deliverable, or drop the bullet. Never borrow a result from
  a similar job, and never round a number into a better one.
- **Objective skills only.** The Skills section lists teachable,
  measurable items with inventory evidence: languages, tools,
  platforms, certifications. Subjective claims are banned as skill
  lines: fast learner, hard worker, multitasking, communication
  skills, detail-oriented, team player, self-starter. A trait the
  resume wants to claim must be **proven** by a STAR bullet in
  Experience (a range of shipped stacks proves learning speed;
  sole-charge client support proves communication), never stated
  as an adjective.
- A skill earns its Skills-line place by also appearing inside at
  least one bullet that shows it in use. A skill that appears only
  in the list and nowhere in the work is a flag: evidence it in a
  bullet or drop it.
- **Tense discipline.** Present tense for roles still held, past
  tense for roles that have ended. One role, one tense, no mixing
  inside an entry.

## The QA gate

A tailored resume ships only after a verification pass:

1. Every number in the document is read back against the
   inventory. Any number that does not trace to a measured source
   comes out.
2. Every claim state is checked: nothing in development reads as
   production, nothing planned reads as shipped.
3. The STAR audit: count the bullets, count how many lead with a
   result, and fix or drop the ones that do not.
4. The packet is scored against the posting (the fit from the
   Problem, Fit, Solution pass, requirement by requirement). Below
   your pass line, the application does not go out; the gaps get
   recorded instead, so the same weak application is never rebuilt
   twice.

Only after the gate does the application move to the approval step
in `docs/SAFETY.md`, and only after submission does it land in
`applications/submitted.jsonl`.
