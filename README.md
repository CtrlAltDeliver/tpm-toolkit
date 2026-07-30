# tpm-toolkit

**A small set of AI-agent skills I built to run a Technical Program Manager job search — score a role, tailor an application, find information about a company and the particular role and then run a realistic mock interview, and find a warm referral — as slash commands instead of manual busywork.**

These are [Claude Code](https://docs.claude.com/en/docs/claude-code) skills: a `SKILL.md` is a plain-English instruction file the agent follows when you invoke it. They're readable on their own — no code to run — and easy to adapt to your own search.

A bunch of varied tools in my arsenal, one helps me gather company context and prepare for an interview, one helps me find the best person for a referral from my warm connections list, one helps score a role against a rubric, and then another one helps me tailor my Resume to a position.

---

## The tools

| Tool | What it does | Status |
|------|--------------|--------|
| **[score](skills/score/SKILL.md)** | Scores a single job posting 1–5 against a fitment rubric and returns a Worth-Applying / Valid verdict. A fast gut-check before you spend time on a role. | Runnable skill |
| **[tailor](skills/tailor/SKILL.md)** | Picks the resume bullets that map to a JD, rewrites them in the JD's language (no fabrication), and drafts a cover letter in your voice. | Runnable skill |
| **[interview-prep](skills/interview-prep/SKILL.md)** | A realistic, interviewer-aware mock interview — figures out who's interviewing you and reshapes the round, asks cold, coaches after, checks headline-before-STAR, and tracks your weaknesses across sessions so prep compounds. | Runnable skill |
| **[referrals](skills/referrals/README.md)** | *Design note only.* How to find who in your network can refer you and gauge warmth from message metadata — without opening profiles, quoting messages, or acting on your behalf. | Concept writeup |

An interactive index of the tools is in [`index.html`](index.html) — open it in a browser for a browsable view with copy-able commands.

## How the fitment rubric works

`score` and `tailor` share one scoring contract: **[`rubric.md`](rubric.md)**. It defines the must-haves, positive signals, and anti-signals for the kind of role you want. Edit `rubric.md` for your own search and both tools follow the change — the rubric lives in one place, not baked into each skill.

## A note on `referrals`

The referrals tool is published as a **design writeup, not runnable code**. The working version drives a live, logged-in LinkedIn session, so shipping it would mean putting browser-automation against a third-party site — and a private session — into a public repo. The [design note](skills/referrals/README.md) captures what's actually worth sharing: how to build a network tool that stays inside a small, respectful footprint, defined as much by what it refuses to do (open profiles, quote messages, act for you, run at scale) as by what it does.

## Using these with Claude Code

Drop a skill folder into your project's `.claude/skills/` directory and invoke it by name (`/score`, `/tailor`). Point `rubric.md` at your own criteria and the skills work against your files. See the [Claude Code skills docs](https://docs.claude.com/en/docs/claude-code) for details.

## License

MIT — see [LICENSE](LICENSE).
