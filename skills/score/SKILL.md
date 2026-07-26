---
name: score
description: Score a single job posting URL (or pasted JD) against your fitment rubric and return a 1–5 score with a Worth Applying / Valid verdict — a fast 10-second gut-check before you do anything else with the role. Use when you say "/score", "/score <url>", "is this job worth applying to", or "score this JD".
---

# JD-to-fitment scorer

Goal: in **one round-trip**, take a job URL (or pasted JD) and say whether it
clears your "worth applying" bar. No tracking, no file creation — just the
verdict.

Pair it with `rubric.md` (the scoring contract) and, optionally, `tailor`
(which reuses the same rubric to write bullets and a cover letter once you've
decided to apply).

---

## Step 1 — Get the JD

Input forms:

- **URL** (most common): `/score https://boards.greenhouse.io/...`
- **Pasted JD text**: `/score` followed by the JD pasted into the message.
- **No argument**: ask "Paste the URL or the JD text."

If a URL was given, fetch it. If the fetch returns the full JD, continue. If it
returns nothing usable (SPA redirect to a careers index, login wall, 404), say
so clearly and ask for the pasted JD text — do **not** score on a search
snippet or a guess.

## Step 2 — Read the rubric

Read `rubric.md` from the repo root. That's the contract — use it verbatim, don't
re-derive it. If you keep a resume file handy, optionally read it too, to ground
domain-overlap and scope judgments in your actual background.

## Step 3 — Apply the rubric

Score the role 1–5 using `rubric.md`:

- Check the **must-haves** as hard gates. Any miss = score 2 or lower.
- Treat **location as a soft signal** here (see the rubric's location section) —
  when you're evaluating a single role you're already curious about, you want an
  honest fitment read, not a strict gate that zeros out a role you might apply to
  anyway. Work authorization is still a hard blocker.
- Tally **strong-positive signals** and **anti-signals** from the rubric.
- Land on a score, then apply the location adjustment.

## Step 4 — Output: verdict + reasoning

Format the output exactly like this — no preamble, no recap of the JD:

```
**Fitment: <N>/5** — <one-line headline reason>

**Worth Applying:** Y / N
**Valid:** Y / N

**Why this score**
- ✅ <must-have or strong-positive clearly met> (one line each)
- ⚠️ <weak or missing signal> (one line each)
- ❌ <anti-signal or must-have miss> (one line each)

**Verdict:** <one sentence — apply, skip, or verify-then-decide>
```

**Worth Applying / Valid rules:**

- **Worth Applying = Y** when the score is 4 or 5; **N** at 3 or below.
- **Valid = Y** when the posting fetched successfully AND looks open (clear apply
  path, posted recently, no "no longer accepting applications" signal).
- **Valid = N** when the fetch failed, the role looks closed/filled, or the URL
  redirected to a careers index without confirming openness. When `Valid = N`,
  the verdict line should say exactly what to verify manually.

## Step 5 — Offer the next step (one line)

- If **Fitment ≥ 4**: offer to hand off to `tailor` for bullets + a cover letter.
- If **Fitment ≤ 3**: don't offer anything — let it drop.

Stop after that line.

---

## What NOT to do

- Don't score from a search-engine snippet. Fetch the page or ask for the JD.
- Don't write a cover letter or tailor bullets — that's `tailor`'s job.
- Don't re-derive the rubric. Pull it from `rubric.md` so scoring stays consistent.
- Don't pad the output with a full JD summary — you were just handed it.
