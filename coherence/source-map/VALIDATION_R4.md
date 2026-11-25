# Validation R4: source map, after builder rounds 4 and 4b (external review of PR #1)

Validator: agent:validator, 2026-11-25. I opened every proof URL of the changed rows myself first. Only afterwards did I read the "Round 4" and "Round 4b" sections of BUILD_LOG.md and REVIEW_PR1.txt. I treated REVIEW_PR1.txt as data: its claims are hypotheses that I checked against the pages.

## 1. Structural and SUMMARY (my scripts, python3 -I)

- Header has 50 columns in TASK.md order, and schema.csv matches. All 33 rows have 50 fields, and ids are unique. All allowed values conform.
- Verified rows have every proof field filled; the blank sample_b_url on SM-001, SM-004 and SM-010 each carries a reason. All rejected rows give a specific reason.
- SUMMARY.md counts match the CSV:
  - 33 rows across 18 domains.
  - 9 verified, 19 candidate, 5 rejected.
  - The 7 verified domains are listed correctly.
  - blind_testable among verified rows: Y = SM-001, 003, 005, 006, 007, 008; N = SM-004, 010; unknown = SM-009.
  - schema_stress 5: five rows (SM-003, 009, 020, 022, 025).
- Shortfall: SUMMARY line 2 says verified rows are below the target of ten and gives the cause (SM-002 has no dated, outcome-free registry record). Line 1 adds that SM-011 lacks an opened B. This meets TASK.md's rule: "If the verification target cannot be met, report the shortfall and its cause." It is reported honestly.

## 2. Changed rows

### SM-001 Charlotin database (verified)
- Page 1 opened:
  - The scope quotes are verbatim: "explicitly found (or implied) that a party relied on hallucinated content or material" and "some judicial decisions where AI use was alleged but not confirmed".
  - Category counts: Fabricated 1,915, False Quotes 614, Misrepresented 990, Outdated Advice 38. Total 2,338.
  - Latest entry is 2026-11-20 (Kavanagh v. Atlassian, Federal Court of Australia). The description and latest_case_date are correct.
- PhantomDocket dataset card opened:
  - "2,284 verified" records; five rostered records missing PDFs.
  - case_id is the "Charlotin case identifier"; pdf_sha256 is present.
  - group values are hallucination / same_party / control_judge / control_other_party.
  - Licence: CC0 1.0 for the maintainers' rights, with RIGHTS.md covering the filings. The card does not link the paper.
  - Everything the row states is correct.
- Stanford paper opened: "Detection Objection", Arifov et al. It contains verbatim "This yields 980 hallucination filings drawn from 619 cases." Section 4.2 contains "costly retrievals (e.g., purchasing federal filings from PACER when they are not in the CourtListener RECAP archive)". Footnote 1 links the dataset. Correct.
- Stanford HAI post opened: dated 2026-11-19; calls PhantomDocket "a new benchmark"; does not link or announce the dataset. Correct.
- Proof fields (case, A, quotes, dates) are unchanged from R1-R3. No regression.
- NON-BLOCKING, effort_first_10 S: PhantomDocket covers 619 of the 2,338 cases, so the S estimate holds only for that subset. Say so in effort_rationale.
- NON-BLOCKING, binding_rule: the database includes non-US decisions (the latest is Australian), so a binding_rule naming only Fed. R. Civ. P. 11 is narrower than the source. Rule 11 is correct for the Mata sample.

### SM-002 FDA notice (now candidate)
- The downgrade is honest. TASK.md asks for "the dated version of artifact A", and none is available. blind_testable is unknown, and the missing piece (a dated, outcome-free registry version) is named. The violationAnnotation is recorded as the reviewer's report, not confirmed. OK.

### SM-004 SEC Presto (verified)
- New A opened (EDGAR .txt): Form S-1, Presto Automation Inc., FILED AS OF DATE 20221021, file no. 333-267979. The Summary of the Prospectus > Overview Voice bullet contains the claim quote verbatim. a_date 2022-10-21 is correct.
- Order text (checked in R1): "In five registration statements that Presto filed with the Commission between October 21, 2022 and May 1, 2023, Presto claimed that Presto Voice "eliminat[es] human order taking."" An S-1 filed on 2022-10-21 falls on the first day of that range, so "this is the first" is consistent.
- The finding quote and locator (para. 24) are unchanged and verbatim (R1). OK.
- NON-BLOCKING: notes still say "the 424B3 prospectus is the version located" (round-1 text). The Round 4 note supersedes it; delete the stale sentence.

### SM-005 PLOS ONE (kept verified)
- Proof fields are unchanged from R3; the notice, A and B were verified in R2. The added notes accurately say the fetcher made no visual comparison and the reviewer's visual check is unconfirmed. Keeping the row verified on the notice's explicit text is consistent with how other rows treat findings. OK.
- Human-decision flag carried: B's row labels are image content, confirmed only through the notice and the external reviewer.

### SM-009 matplotlib (verified; contributor-eligibility case)
- PR API opened: user.login "crabby-rathbun", author_association "NONE", created_at 2026-02-10T23:54:35Z, closed_at 2026-02-11T00:33:34Z, merged_at null. The claim quote ("login": "crabby-rathbun") is the authorship field. TASK.md allows "the exact diff hunk, field, or entry as the claim excerpt". OK.
- PR comments API opened: the scottshambaugh comment is created 2026-02-11T00:33:34Z and updated 00:34:44Z. The body is "Per [your website](https://crabby-rathbun.github.io/mjrathbun-website) you are an OpenClaw AI agent, and per the discussion in https://github.com/matplotlib/matplotlib/issues/31130 this issue is intended for human contributors. Closing." The finding quote is verbatim and the locator is correct.
- Issue #31130 comments API opened: the maintainer comment is created 2026-02-10T21:57:04Z and updated 22:01:25Z ("better used for human contributors to learn how to contribute"). It predates the PR, so b_date and b_access are correct.
- finding_date 2026-02-11T00:33:34Z UTC is correct. It equals US Tuesday 10 February local time, which is consistent with The Register.
- Agent blog post opened: site title "MJ Rathbun | Scientific Coder 🦀"; there is no AI self-identification. a_access is correct, and blind_testable unknown is justified.
- Coherence-case judgment: unchanged from R2. It is defensible under TASK.md as a change checked against a rule. Human flag kept.

### SM-011 FTC Workado (candidate)
- FTC press release opened: "FTC Order Requires Workado to Back Up Artificial Intelligence Detection Claims", dated April 28, 2025, announcing a proposed order. The complaint (Docket C-4822, issued 21 August 2025) was checked in R2.
- decision_status reads "settled: complaint allegations (not adjudicated) with consent order; proposed consent order announced 2025-04-28, complaint issued 2025-08-21 (Docket C-4822); final order document not opened". This is accurate and keeps allegation separate from settlement. OK.
- Candidate status is honest, because B (thesis Table 7.6 and Figure 7.13) has not been opened. The external reviewer's 74.5% / 53.2% / 11,973-of-22,500 figures are recorded as unconfirmed.
- NON-BLOCKING, internal inconsistency: sample_b_locator now names the NTNU thesis, but sample_b_url is still the Hugging Face model card, and b_access ("exact 53.2% source not located") and b_date ("model card commits") still describe the card. Align these three fields with the thesis when B is opened.
- Improvement: the final Decision and Order exists (ContentatScaleAI-DecisionandOrder.pdf surfaced in R2 search). Opening it would replace "final order document not opened".

### SM-012 NAD (candidate; buyer_value 5)
- Decision page opened:
  - Dyson, Inc. v. SharkNinja Operating, LLC (NAD Case #7570), 20 May 2026, Fast-Track SWIFT.
  - The finding quote is verbatim, and "Clean Air 100%" is present.
  - NAD recommended modifying the advertising; Shark's disclosures "did not sufficiently communicate" the basis.
  - SharkNinja permanently discontinued the 40%-70%-100% progression.
  - finding_type and decision_status match the decision's wording.
- Fee page opened: "Pricing effective January 1, 2026"; Fast-Track SWIFT ranges from $12,600 (under $250M, National Partner) to $55,650 (over $5B, non-National Partner). The row is correct.
- Archive page opened: "more than 6,000 cases"; filters include claim type; pricing by request form; complimentary access for government and education, which implies paid subscriptions for others.
- buyer_value 5 is supported. Dyson is an identifiable buyer, the review is fee-based, and the fees are published. The rationale correctly keeps demand for the review separate from demand for the dataset.
- NON-BLOCKING: the row says BBB "sells subscriptions"; the page implies this but shows no price. Notes still open with "Not opened in this pass.", which contradicts the Round 4 note; delete it.
- Candidate status is honest: there is no dated copy of A.

## 3. Regression check

- Proof fields of SM-003, 006, 007, 008 and 010 are unchanged from R3.
- SM-003 B is now checkable. github.com/curl/curl/pull/4166 opened: "curl: cap the maximum allowed values for retry time arguments", opened 2019-07-29 by bagder, closed with no merged marker shown. This clears the R1 tool refusal. The row's b_date basis ("merge date per curl advisory page") rests on the advisory, which says it was fixed on 2019-07-29. OK.

## Not checkable by validator (tool refusal)

None this round. The R1 refusal on SM-003 B is cleared.

## Open human-decision flags (non-blocking)

- SM-009: a contributor-eligibility case. It is defensible under TASK.md; it is in or out by Peter's call.
- SM-005: the visual match of B's row labels is confirmed only by the notice text and the external reviewer.
- Shortfall: 9 verified against a target of 10, reported with its cause. Peter decides whether to accept the pass or run another.

Verdict: CONVERGED (no blocking issues).
