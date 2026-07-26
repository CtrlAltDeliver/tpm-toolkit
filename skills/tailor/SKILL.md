---
name: tailor
description: Tailor your resume bullets and draft a cover letter for a specific role. Reads the JD, mirrors its language against your resume without fabricating anything, and saves a cover letter file. Use when you say "/tailor", "/tailor <Company>", "tailor my resume for X", or "write a cover letter for X".
---

# Tailor resume + cover letter for a role

Goal: produce (1) **3–5 tailored resume bullets** rewritten to mirror the JD's
language and emphasis, and (2) **a cover letter** saved as a file, written in
your voice.

Keep it **simple and fast** — a single round-trip: read inputs → produce
outputs → done. No multi-step interrogation.

---

## Step 1 — Identify the role

The skill takes a company name as an argument (e.g. `/tailor Acme`).

- **If a company name was provided**, locate its role folder (e.g.
  `roles/<Company>/`). If it doesn't exist, list the folders you do have and ask
  which company was meant.
- **If no argument was provided**, list the role folders and ask which one.

Inside the folder, find the JD file (e.g. `<Company>.docx`, `JD.docx`, or
`<Role Title>.docx`). If there are multiple documents and none is obviously the
JD, ask which one it is. (No local folder? Ask for the JD to be pasted instead.)

## Step 2 — Read the inputs in parallel

Read these in one batch:

1. **The JD** — extract the role title, key responsibilities, required
   qualifications, and nice-to-haves. Note the company's distinctive language
   (e.g. "customer obsession," "ship fast," any named values).
2. **Your resume** — the resume file you keep for this (a PDF or doc). Pull the
   full bullet list across roles.
3. **A voice/style guide (optional)** — if you keep a `style-guide.md` for how
   you write (greetings, sign-off, tone), read it so the cover letter sounds
   like you. Skip silently if absent.
4. **Company notes (optional)** — if you keep a `company-notes/<company>.md`,
   read it to sharpen the letter with recent product/eng work you can reference.

## Step 3 — Tailored resume bullets (output)

Pick **3–5 bullets from your existing resume** that map most directly to the
JD's top responsibilities. For each:

```
**1. <One-line label for the requirement this addresses>**
- Original: <verbatim resume bullet>
- Tailored: <rewritten bullet>
- Why: <which JD line this lands>
```

**Rules:**
- **Never fabricate** metrics, tech, or scope. Same scope, same numbers — just
  reframed. If the JD wants experience you don't have, pick a different bullet.
- Mirror the JD's vocabulary (if it says "drive cross-functional execution,"
  favor "drive" and "cross-functional" over "manage" and "coordinate").
- Lead each bullet with the strongest **verb + outcome**, not the context.

## Step 3b — Tailored summary (always)

Always propose a tailored version of the resume's **Summary** — the reader hits
it first, and the JD's bullseye keyword is often missing from it.

- Show the **current summary** verbatim.
- Show a **tailored summary** that reweights your existing facts to lead with
  the JD's top theme — same numbers, nothing invented.
- Call out **what changed and why** in 2–4 lines.
- If the tailored version runs long, offer a trimmed variant.
- If the current summary already leads with the JD's core theme, say so rather
  than inventing an edit.

## Step 4 — Draft the cover letter and save it

Write ~250–350 words in your voice:

1. **Opening (2–3 sentences)** — warm, specific to the company. Reference
   something concrete (from the JD or company notes) — never generic ("I'm
   excited to apply for the X role at Y").
2. **Middle (1–2 paragraphs)** — the single most relevant thread from your
   resume that maps to the role's biggest ask, with one concrete metric. Then a
   shorter beat connecting a second thread to a secondary requirement.
3. **Close (2–3 sentences)** — what you want in the next role (framed as impact,
   not titles) and a soft call to talk.
4. **Sign-off** — per your style guide.

**Voice rules:**
- Warm and specific, not transactional. No corporate-speak ("synergy,"
  "leverage," "passionate about disrupting"). Short sentences.
- Don't open with "I am writing to apply for…" — lead with something specific
  about the company.
- Never fabricate. Frame your closest adjacent experience honestly rather than
  claiming experience you don't have.

**Save** the letter as a file in the role folder (e.g. `Cover Letter.docx` or
`.md`). If one already exists, ask before overwriting.

## Step 5 — Summarize (chat)

Two or three sentences:
- Confirm the saved file path.
- Flag any **honest gaps** between your resume and the JD to be ready for in an
  interview (e.g. "JD wants 5+ years of direct people management; your resume
  shows program leadership without direct reports — be ready for that").
- Don't pad.

---

## What NOT to do

- Don't ask for the JD to be pasted if it's already in the folder — read it.
- Don't write a separate "tailored resume" file. Bullets go in chat to copy into
  whatever resume version you're editing.
- Don't invent quotes, awards, or metrics.
