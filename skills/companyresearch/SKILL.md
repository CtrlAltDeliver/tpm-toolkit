---
name: companyresearch
description: Deep-research a company you're interviewing with and turn it into a "how to tell my stories here" prep file — strategy, priorities, recent bets, what the role signals, culture and interview patterns — plus an "ideal candidate profile" you can use as a filter for which of your experiences to highlight. Use when you say "/companyresearch", "/companyresearch <Company>", or "research <Company> for my interview".
---

# Company research (deep)

Goal: walk into an interview knowing not just *what* the company does, but what
they're optimizing for right now, what this specific role is really for, and —
most usefully — **which of your stories to lead with and how to frame them**.

The output is a single markdown file, `company-context/<slug>.md`, written so
your interview-prep step (or you, the night before) can pull it straight into the
room. Pair it with `interview-prep`, which reads this file as one of its inputs.

> Configure the output folder once at the top of your setup. Nothing here assumes
> a specific company, vendor, or dataset.

---

## Step 1 — Which company, and which role

Ask which company the research is for (or take it from the command argument).
Then find the **specific role** you applied to — read the JD from wherever you
keep it (a company folder, a saved posting, a pasted description). Everything
below is grounded in that JD; a generic company writeup that ignores the role is
half the value.

If you already keep private notes on the company (a recruiter call, intel from a
friend), pull those in first under a **"What I already had"** section so you can
see existing knowledge vs. newly researched — and never overwrite it.

## Step 2 — Research deeply, not just a snapshot

Beyond the standard "what they do" snapshot, use web search to surface and cite:

- **Current strategy and priorities** — what the company is actually optimizing
  for right now, not its mission-statement boilerplate.
- **Recent product bets or organizational shifts** — launches, pivots, reorgs,
  funding, leadership changes in roughly the last six months.
- **What this specific role signals** — read the JD and the org context together.
  What is the company trying to fix or build by opening *this* req? That tells you
  what they'll press on in the interview.
- **Interview process at this company** — format, typical rounds for your target
  role, known question styles. Pull from public sources (Glassdoor, levels.fyi,
  Blind, Reddit, engineering blogs). Be specific: take-home, system-design depth,
  leadership principles, behavioral frameworks, panel composition.
- **Culture and values** — anything that should shape how you tell your stories:
  which behaviors to lead with, which frameworks land, what tone fits.
- **Recent product / eng work** worth referencing to show genuine interest.

Cite sources inline as links so you can verify. **Don't fabricate** — if you
can't find something (e.g. their interview process), say so explicitly rather
than guessing.

## Step 3 — Write the "ideal candidate profile"

This is the point of the whole exercise. Add a dedicated
`## Ideal candidate profile` section: a concrete description of the person the
company is trying to hire, grounded in the research + the JD. Cover:

- **What experiences** this person would have — domains, scale, types of programs
  or products.
- **What behaviors** would stand out *to this company specifically*.
- **What impact level and scope** their stories would demonstrate.

Be specific enough that you can use it as a **filter**: reading it, you should be
able to decide which of your experiences to highlight and which to leave out.
"They want a builder who's shipped 0-to-1 under ambiguity" is usable; "they want
a strong candidate" is not.

## Step 4 — Save it

Write everything to `company-context/<slug>.md` (kebab-case slug, e.g.
`shopify.md`). If a file already exists, **update** it — preserve prior research
under a dated `## Previous research` header and add new findings under today's
date, rather than overwriting. Surface the file path at the end so you know where
to find it.

---

## What NOT to do

- Don't stop at a snapshot. The strategy read, the role signal, and the ideal
  candidate profile are the parts that change how you interview.
- Don't fabricate interview questions, quotes, or process details. If a source
  paywalls or a fact can't be found, say so in the file.
- Don't overwrite an existing file — append under a dated header.
- Don't make the ideal candidate profile generic. If it can't be used to pick
  between two of your stories, it isn't done.
