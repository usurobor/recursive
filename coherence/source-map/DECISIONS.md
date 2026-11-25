# Decisions: source map

Each accepted decision states why.

## 2026-11-25

**D1. Search where review already happens and leaves a public trail.** Accepted. The FTC case was found by chance; this heuristic turns that chance into a method. Practitioners' own terms are the search vocabulary.

**D2. The unit of discovery is a repeatable source, proven by one sample case.** Accepted. One receipt shows a source contains a mineable case. How many cases have accessible evidence is a later finding, from mining the first ten.

**D3. Separate finding_type from decision_status.** Accepted. "Contradicted" says what the authority found; "adjudicated" says how it decided. A maintainer ruling or audit finding can be strong ground truth without a court.

**D4. Separate claim quote from finding quote, and record access to A and B separately.** Accepted. A reviewer judges the match side by side. If B first became public in the verdict, the sample can be retrospective but never blind; recording it saves hours of trying to rebuild an impossible pre-outcome test.

**D5. blind_testable is a property of the sample.** Accepted. Retrospective cases still have value; blind ones are what a benchmark needs. Keeping both visible keeps the distinction.

**D6. latest_case_date replaces leakage_risk.** Accepted. Training-data exposure depends on the model being tested; a date lets that be judged per model.

**D7. Three separate scores, no combined priority.** Accepted. The same sheet answers three questions: what to mine first (effort, directness of proof), where to test the schema (schema_stress), what to sell (buyer_value). A combined score hides the difference.

**D8. Add a `domain` column and use "domain" for professional fields.** Accepted. Coverage is reported per domain, so it needs a column; "field" also means a sheet column and confused the spec.

**D9. Rejected rows stay in the sheet with a reason.** Accepted. They are the first negatives of the loop: practice discovers what fails.

**D10. CSV in git is the source of truth; the Google Sheet is a published view.** Accepted. Git keeps history and review; the Sheet is for reading and sorting.

**D11. Builder and validator agents iterate until the validator has no blocking issues; then Claude verifies; then Peter accepts.** Accepted. Agent verification and human acceptance stay separate decisions; the builder never grades its own work.
