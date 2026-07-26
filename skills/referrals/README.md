# Referrals — design note (concept only)

> **This is a design writeup, not runnable code.** The working version drives a
> live, logged-in LinkedIn session, so it's deliberately **not** published here —
> both to respect LinkedIn's terms and to keep a private browser session out of a
> public repo. What's worth sharing is the *design*: how to turn "who can refer
> me?" into a ranked answer without being creepy about it. That's below.

## The problem

A cold application is weak; a referral from someone who'll actually vouch for you
is strong. But "who do I know at Acme?" is tedious to answer by hand, and the
obvious automation — scraping profiles, blasting connection requests — is both
against the rules and a good way to get your account flagged. The design goal was
a tool that answers the question **while staying inside a small, respectful
footprint.**

## The approach

1. **Resolve the target company** — from an argument, or ask.
2. **Filter to your own 1st-degree network** at that company. A pre-built
   people-search URL scoped to `network = 1st-degree` + the company keyword does
   this — it lists people you already know who work there.
3. **Read only the results cards**, never individual profiles. Name + headline
   from the list is enough to tell who's currently at the company. Not opening
   profiles keeps the footprint minimal and leaves no profile-view trace.
4. **Gauge warmth from your own message history — metadata only.** For the top
   few candidates, look at your existing message threads: is there a thread? did
   they genuinely reply, or is it just your outreach? roughly how recent? That
   classifies each tie as warm / dormant / cold / no-history — **without ever
   reading or quoting the message contents.**
5. **Rank the best ask.** Warmth first (a warm mid-level tie who'll reply beats a
   senior name who's gone silent), then org adjacency to the hiring team, then
   seniority-to-vouch.
6. **Hand back a ranked list** with a one-line reach-out angle per person. The
   outreach itself is always yours to write and send.

## The design principles that make it respectful

- **Read-only, human-paced, small batches.** Cap the warmth check to the top ~5
  candidates per company; never loop your whole network. Aggressive automation is
  what trips bot-detection — and it's rude.
- **Metadata, not contents.** Warmth is inferred from *direction + reply +
  recency*, never from what anyone said. Message contents never enter the output.
- **No individual profile views.** Results cards only.
- **Never act on someone's behalf.** No connect clicks, no messages, no form
  input. The tool surfaces; you decide and reach out.
- **The subtle bit: a reply matters more than who messaged last.** A thread that
  ends with *your* thank-you on top of a real back-and-forth is warm; an opening
  connect-note they never answered is cold — even though both can look like "you
  sent last." Direction of the *last* message is a bad warmth signal; presence of
  a genuine reply is the real one.
- **An override list for off-platform ties.** Some of your warmest contacts live
  in a Discord or a community, not your LinkedIn inbox — so an empty LinkedIn
  thread means nothing for them. A small local "always warm" list takes
  precedence over the inbox signal.

## Why it's not shipped as executable code here

The steps above only work against *your* authenticated LinkedIn session in a real
browser. Publishing a runnable version would mean publishing browser-automation
against a third party's site under your name — not worth it. The judgment worth
showing is the restraint: the useful version of this tool is defined as much by
what it refuses to do (open profiles, quote messages, act for you, run at scale)
as by what it does.
