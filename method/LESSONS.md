# Lessons

Process lessons, newest first. Each states the rule and the incident that taught it.

## 2026-11-26: Review is a queue of small packets

**Rule.** Work comes to the human as a queue. Each item is one small packet with one decision: accept or reject. A reject carries a reason. Chat is the UI for now; no GitHub PRs.

**A packet holds only what the decision needs:**
- the decision asked
- claim (A): short quote, link, date
- evidence (B): short quote, link, date
- finding: short quote, link
- checks already done, and by whom (builder, validator, Claude)
- the one open point, if any

Everything else (full tables, build logs, validation reports) stays in git for whoever wants to dig.

**Incident.** The first source-map pass arrived as one PR carrying a 50-column table, build log and three validation reports, with three real decisions buried inside. Verifying it meant digging, which is exactly what Coherence Clearance exists to remove. Recurring tendency: dumping one huge artifact on the human. Hard to build, easy to verify applies to the review itself.
