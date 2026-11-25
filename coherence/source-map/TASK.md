# Task: map public sources of historical coherence cases

Converged by Peter, Claude and GPT, 2026-11-25. Decisions: [DECISIONS.md](DECISIONS.md).

## Goal

Map public sources of historical coherence cases. Find places where someone is paid or formally responsible for comparing a claim, change, or transaction against evidence or a rule, and where their decision leaves a public trail. Use each domain's vocabulary for the decision. Record the search terms that actually led you to cases.

The unit of discovery is a repeatable source, such as one regulator's advertising decisions or one project's review process. Give each source one row. To verify it, provide one real case a reader can check directly. The receipt must answer three questions:

1. **What was under review?** Link to the dated version of artifact A and identify the exact claim, code, entry, or change.
2. **What was it checked against, and why?** Identify artifact B and state the binding rule in one sentence. Give a locator precise enough to inspect B. If the decisive evidence first became public in the finding, say so. If the finding refers to evidence that remains private, say that instead.
3. **What did the authority actually conclude?** Link to the decision and quote the passage that establishes the finding. Preserve distinctions such as an allegation, a failure to substantiate, and a demonstrated contradiction.

## Deliverable

Three CSV files in this directory, later published as one Google Sheet with matching tabs:

- `sources.csv`: the rows
- `schema.csv`: each column, its allowed values, and whether it describes the source or the sample
- `rubric.csv`: the score definitions

Plus `SUMMARY.md`, five lines: domain coverage, status counts, blind-testable count among verified samples, the three sources that most stress the schema and why, and the most common obstacle to verification.

## Columns of `sources.csv`

| Group | Fields |
|---|---|
| Source identity | id, name, domain, publisher, url, description, practitioner_terms |
| Coherence fit | relevance, artifact_a, artifact_b, binding_rule, verdict_authority, verdict_type |
| Source mineability | access_method, license_or_terms, volume, period, cadence, latest_case_date |
| Sample finding | finding_type (e.g. unsubstantiated, contradicted, rule violation), decision_status (e.g. alleged, settled, adjudicated, maintainer ruling, audit finding). Use the authority's own term where it is more precise. |
| Sample proof | sample_case_url, sample_case_locator, sample_a_url, sample_a_locator, sample_b_url, sample_b_locator (or availability explanation), sample_claim_quote, sample_finding_quote. For code or structured data, use the exact diff hunk, field, or entry as the claim excerpt. |
| Sample timing and access | a_access, b_access, a_date, b_date, finding_date, quote_level, blind_testable. Record the access route and the basis for the dates. |
| Ranking | ground_truth, ground_truth_rationale, schema_stress, schema_stress_rationale, buyer, buyer_value, buyer_value_rationale, effort_first_10, effort_rationale |
| Review | status (candidate / verified / rejected), reject_reason, verified_by, verified_date, notes. Identify agent verification explicitly. Human acceptance is a separate decision. |

`domain` uses a short open list the agent may extend: advertising, securities, consumer finance, product safety, clinical research, scientific publishing, software, audit, procurement, transport safety.

## Verification rules

- `candidate` means promising but incomplete. `verified` means the sample receipt checks out. `rejected` requires a specific reason. Failure to access a page on one attempt leaves the row a candidate.
- Open every proof link used for verification and check each excerpt at its locator. A finding that quotes a vanished original is valuable for discovery, but it does not establish independent access to A. Keep that row as a candidate until you recover A.
- `blind_testable` applies to the sample. Mark Y only if the needed versions of A and B were publicly available before the finding and can be reconstructed without revealing the outcome to the checker. Mark N when a known fact rules that out and unknown when timing or access is uncertain. A retrospective sample can be verified even when blind testing is impossible.
- Record the latest case date you can substantiate. Training-data exposure depends on the model being tested; a date makes that assessment possible later. Cite the basis for volume, licensing, and buyer-spend claims, and leave unknowns visible.
- Quotes stay short: the minimum passage that establishes the claim or the finding.

## Rubric

Score each dimension separately on a 1–5 scale. No combined score.

| Dimension | 1 | 3 | 5 |
|---|---|---|---|
| ground_truth | Informal or ambiguous judgment | Specific documented finding with limited evidentiary support | Explicit, authoritative determination with a basis the reviewer can inspect |
| schema_stress | Fits the FTC example cleanly | An existing field needs a broader interpretation | The sample exposes a distinction the schema cannot represent. Name it. |
| buyer_value | No buyer identified | Plausible buyer identified | Evidence that an identifiable buyer already spends on this review |

`buyer_value` measures demand for the review activity. A buyer for the resulting dataset is a further hypothesis. Estimate `effort_first_10` as S for up to one person-day, M for more than one and up to five, or L for more than five.

## Scope and stop

Stop after the first mapping pass. Aim for 25–40 total source rows across at least eight domains, including at least ten verified samples. Keep rejected rows in that total. Use one proof case per source. If the verification target cannot be met, report the shortfall and its cause.

## Process

1. **Builder** agent performs the mapping pass and writes the deliverable.
2. **Validator** agent, which has not seen the builder's reasoning, re-opens every proof link of every `verified` row, checks each quote at its locator, checks dates, statuses and scores against these rules, and lists blocking and non-blocking issues.
3. Builder fixes blocking issues, or downgrades the row's status with a reason. Repeat 2–3 until the validator reports no blocking issues.
4. Claude verifies the converged output independently.
5. Peter accepts or rejects rows. Human acceptance is the final gate.
