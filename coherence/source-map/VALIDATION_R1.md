# Validation R1: source map, first pass

Validator: agent:validator, 2026-11-25. Inputs: TASK.md, DECISIONS.md, sources.csv, schema.csv, rubric.csv, SUMMARY.md. BUILD_LOG.md was read only after all verified rows were checked, and only to explain the SM-005 discrepancy.

## 1. Structural (script: /home/claude/scratch/validator/structural.py, run with python3 -I)

- Header: 50 columns, names and order match the TASK.md table exactly. schema.csv lists the same 50 columns in the same order. All 33 rows have 50 fields; ids SM-001..SM-033 unique and well-formed.
- Allowed values: domain (18 values, all in the extended list in schema.csv), status, relevance prefix, quote_level prefix, blind_testable, effort_first_10 and 1-5 scores all conform. Every score has a rationale.
- Verified rows: every proof column is filled, except sample_b_url on SM-001, SM-004, SM-010, which schema.csv allows ("blank with reason in sample_b_locator"); each gives the reason. verified_by = agent:builder and verified_date set on all ten.
- Rejected rows: all four have a specific reject_reason. No non-rejected row has a reject_reason.
- Quotes: all under 25 words.
- SUMMARY.md: 33 rows, 18 domains, 10/19/4 status counts, 8 verified domains (list correct), blind_testable 7 Y / 2 N / 1 unknown with the right ids. All counts match the CSV. Five numbered lines as required.
- NON-BLOCKING: latest_case_date in SM-001 (">=2025-12-17 ..."), SM-016 ("2026 ..."), SM-017 ("2026-11 ..."), SM-025 ("2025 ...") is not YYYY-MM-DD; schema allows "with basis", but the prefix forms are inconsistent.
- NON-BLOCKING: SUMMARY line 4 picks three of six rows scored schema_stress 5 (SM-003, 009, 020, 022, 025, 030) without saying why these three.

## 2. Receipts, verified rows

### SM-001 Mata v. Avianca (legal)
- Case PDF opened: Opinion and Order on Sanctions, ECF 54, filed 2023-06-22. Finding quote "has confirmed that the decision is not an authentic ruling of the Court" found at p. 10, para. 26 (continues onto p. 11). OK.
- A opened (LawNext OCR copy): header "Case 1:22-cv-01461-PKC Document 21 Filed 03/01/23 Page 6 of 10"; claim quote found verbatim on p. 6 ("...under the Montreal Convention in the case of Varghese..."). OK.
- Source page opened: 2,338 cases, CC BY 4.0, "Last updated 25 November 2026", page 30 of 47, latest entry 2025-12-17. OK.
- Dates, finding_type (contradicted: authority does not exist), decision_status (adjudicated sanctions), blind_testable Y, coherence fit: OK.
- No issues.

### SM-002 FDA Notice of Noncompliance, Duchesnay NCT02045901 (clinical research)
- Case/B letter opened: dated 2026-10-19, to Duchesnay Inc., NCT02045901; finding quote verbatim ("...for the applicable clinical trial referenced above, as required under section 402(j)..."). Statutes cited as stated. OK.
- A opened (TrialsTracker): "Completion date: March 31, 2017", "Required reporting date: March 31, 2018", status Overdue. Claim quote found. OK.
- Source list opened: 11 notices, 2021-04-27 to 2026-10-19, current as of 10/30/2026. OK.
- NON-BLOCKING: a_date is defined as the date of the version of A under review; 2017-03-31 is a field value (completion date), not a record version date. The receipt's A is the record as it stood after 2018-03-31 with no results; state that and keep 2017-03-31 as the field value. Also note that TrialsTracker's "Completion date" stands in for the statutory primary completion date; the letter gives no date itself.
- NON-BLOCKING: A is a third-party current rendering, not a dated version of the registry record; ClinicalTrials.gov record history would give the dated version.

### SM-003 CVE-2020-19909 curl (software)
- Case/A opened (CVE JSON): first sentence "Integer overflow vulnerability in tool_operate.c in curl 7.65.2 via a large value as the retry delay."; NOTE quote verbatim; tags ["disputed"]; datePublished 2023-08-22; dateUpdated 2026-10-14. OK.
- curl advisory opened (https://curl.se/docs/CVE-2020-19909.html): fix in PR 4166 merged 2019-07-29, curl 7.66.0; MITRE denied rejection and flagged DISPUTED; blog 2023-08-26. Supports b_date and the curl finding_date.
- B (https://curl.haxx.se/bug/?i=4166 -> redirect to github.com/curl/curl/pull/4166): NOT CHECKABLE BY VALIDATOR (tool refusal, provenance). PR number, title area and date corroborated only through the curl advisory page.
- NON-BLOCKING: finding_date 2023-08-26 is curl's dismissal, while sample_finding_quote is MITRE's NOTE. The CNA container's providerMetadata.dateUpdated is 2023-08-28T08:04:05Z, a usable upper-bound basis for the NOTE date; record it.
- NON-BLOCKING: the claim quote ("Integer overflow ... in curl 7.65.2") is true per B (the bug existed and was fixed in 7.66.0). The contradicted part is the implied security impact. Say so in finding_type or notes so a reader does not take B as contradicting the quoted words.

### SM-004 SEC In re Presto Automation (securities)
- Case opened: Rel. 33-11352, File 3-22413, 2025-01-14; para. 24 contains the finding quote verbatim (starts mid-sentence after "because the"); para. II: findings "without admitting or denying". decision_status correct.
- A opened: 424B3 prospectus dated 2023-01-09 (Reg. No. 333-267979); claim quote verbatim in the Summary Overview Voice bullet. OK.
- B private; blind_testable N correct.
- NON-BLOCKING: the order cites "five registration statements ... between October 21, 2022 and May 1, 2023" and quotes "eliminat[es] human order taking". The 424B3 is a prospectus under registration 333-267979, not itself a registration statement; note this, or locate the S-1/S-1A for the same registration.
- NON-BLOCKING: finding_type "contradicted" is the builder's term; the authority's term is "materially false statements".

### SM-005 PLOS ONE retraction, Malik & Anees 2024 (scientific publishing)
- Case opened: notice e0351197, 2026-06-23; reason "concerns about compromised peer review"; finding quote "appear similar to the COVID-19 Omicron and pneumonia rows" verbatim; author TA disagreed. decision_status OK.
- A: journals.plos.org page fetched (Fig 2 caption verbatim). PMC copy (PMC10931489, via search) confirms PLoS One 2024 Mar 12;19(3):e0296352 and the RETRACTED banner. a_date OK.
- **BLOCKING: wrong B locator.** The notice reads "...appear similar to the COVID-19 Omicron and pneumonia rows in Fig 2 of [2, retracted in 3]", where [2] is LGD_Net. sample_b_locator says "Fig 1, cited by the notice". The notice cites Fig 2. (BUILD_LOG line 45 shows the builder read LGD_Net's Fig 1 caption.) Fix the locator to Fig 2 and re-check that LGD_Net's Fig 2 holds the COVID-19 Omicron and pneumonia rows.
- B (https://journals.plos.org/plosone/article?id=10.1371%2Fjournal.pone.0327419): NOT CHECKABLE BY VALIDATOR (rate-limited three times; PMC mirror PMC12334061 refused for provenance). b_date 2025-08-08 therefore unverified by validator.
- NON-BLOCKING: B was itself retracted (the notice says "retracted in 3"; BUILD_LOG gives 2026-04-08). The row does not say so; b_access should.
- NON-BLOCKING: B (2025-08-08) postdates A (2024-03-12). The similarity check is symmetric, but B cannot be the source A reused; the earlier comparison article (Bioengineering 2023;10(2):203) was not opened. binding_rule ("must not reuse images") fits the 2023 article better than LGD_Net.

### SM-006 UK Statistics Authority letter on debt (official statistics)
- Case opened: letter of 19 December 2023, Sir Robert Chote to Sarah Olney MP. Assesses the 7 Nov video ("debt is falling") and PMQs 22 Nov ("we have indeed reduced debt").
- A opened (Hansard 22 Nov 2023): "...that we have indeed reduced debt", PM replying to Keir Starmer. OK.
- B opened (OBR script): "Underlying debt peaks at 93.2 per cent of GDP in 2026-27 and then falls..."; dated November 2023 only. OK.
- NON-BLOCKING: sample_finding_quote is truncated and given a full stop that is not in the source; the sentence continues "...may have undermined trust in the Government's use of statistics...". It also does not establish the finding. The passage that does: the average person would take the claims to mean debt was already falling or had been lowered by policy, "neither of which is the case."
- NON-BLOCKING: finding_type "contradicted by forecasts" misreads the letter. The PM's office relied on the OBR forecast (debt falls as a share of GDP in the final year); the letter finds the natural reading of the claim untrue, not the forecast contradicting it. decision_status "public reprimand" is the builder's word, not the authority's.

### SM-007 PolitiFact, Trump joint address (fact-checking)
- Case opened: 2025-03-05; item rated False; finding quote verbatim. A opened: 2025-03-04 transcript contains "Three-point-five million people from ages 140 to 149." B opened: SSA statement 2025-02-19 contains "These individuals are not necessarily receiving benefits." All dates OK.
- NON-BLOCKING: the claim quote stops before the part that is false. The transcript continues "And money is being paid to many of them"; that is what B and the 89,000 figure contradict. Records of such ages did exist in the database per B ("people in our records with a Social Security number ... who do not have a date of death"). Extend the claim quote to include the payment sentence.
- NON-BLOCKING: the finding quote is evidence, not the rating; the rating "False" is the finding.

### SM-008 Full Fact, Lammy military homes (fact-checking)
- Case opened: 2025-11-12, Tony Thompson. A opened (ParallelParliament, 5 Nov 2025): claim quote verbatim. B opened (GOV.UK, 2 Nov 2025): "more than 40,000 military homes to be modernised, refurbished or rebuilt". Written correction opened (11 Nov 2025): 4,000 -> 40,000. Dates OK.
- NON-BLOCKING: sample_finding_quote is truncated with an added full stop; the source sentence continues "—not 4,000, as Mr Lammy suggested." That clause is the contradiction; include it.

### SM-009 matplotlib PR #31132 (software)
- Case/A opened: title "[PERF] Replace np.column_stack with np.vstack().T", closed; closing comment contains "this issue is intended for human contributors. Closing." No dates shown.
- B opened: issue #31130 ("Marking this as an easy first issue"; scottshambaugh: "better used for human contributors to learn how to contribute"); contribute guide 3.10.5 'Restrictions on Generative AI Usage' supports "authentic engagement" and "fully understand the proposed changes", and does not reserve first issues for humans (as the row says).
- The Register opened: published Thursday 2026-02-12, "On Tuesday, Scott Shambaugh ... rejected"; 2026-02-10 inference correct.
- NON-BLOCKING: borderline coherence case. The PR is checked against a rule, but the checked property is the author's identity; the claim quote (PR title) plays no part in the finding. The row discloses this (relevance Medium, schema_stress 5). Human acceptance should decide whether it counts toward the ten.

### SM-010 ORI finding, Eckert / PLoS One 2012 (research integrity)
- Case opened (Justia mirror of FR Doc. 2024-18289): published 2024-08-15, dated 2024-08-12; "ORI found that Respondent engaged in research misconduct"; Fig 1B item contains the finding quote verbatim; 13 papers and 2 grant applications. OK.
- A opened (PMC3359321): PLoS One 2012 May 23;7(5):e36941; Figure 1 caption contains "B/C TAM67-FLAG is expressed in keratinocytes." OK.
- Retraction notice opened (e0247222): 2021-02-11; TAM67-Flag panel "labelled in the raw data records as results of a Cyclin western blot experiment". b_date OK. blind_testable N correct.
- NON-BLOCKING: ground_truth 5 requires "a basis the reviewer can inspect"; the raw records are private. SM-004 scored 4 for the same situation. Use 4 for consistency.
- NON-BLOCKING: practitioner_terms lists "Voluntary Settlement Agreement"; this notice uses "Voluntary Exclusion Agreement". Add it.

## 3. Scores

- ground_truth, schema_stress, buyer_value on all verified rows match the rubric given their rationales, except SM-010 ground_truth (see above, non-blocking).
- Every buyer_value is 3 or lower with "No spend evidence opened in this pass"; consistent with the rubric (5 needs spend evidence). No row reaches 4 or 5, so the sheet does not yet answer "what to sell".
- NON-BLOCKING: SM-030 (rejected, never opened) carries ground_truth 5 and schema_stress 5. Scores on an unopened, rejected source add noise; leave them blank or mark them as unassessed.

## 4. Candidates and rejects

Candidates spot-checked by opening the case page (5): SM-011, SM-013, SM-014, SM-020, SM-021.
- SM-011 FTC Workado complaint: both quotes verbatim (paras 9.A and 17); Exhibit A gives URL and capture dates (10-3-23). Candidate status honest: A only via the complaint exhibit. decision_status correctly separates complaint allegations from the consent agreement.
- SM-013 ASA ruling (26 Nov 2025, upheld): both quotes verbatim; ad was a YouTube ad with no URL or ID. Candidate status honest.
- SM-014 IPSO 02269-25 (26 Nov 2025, partly upheld): headline verbatim; NON-BLOCKING: finding quote is not verbatim (source: "...accuracy of its headline when asked."), although quote_level claims it was checked verbatim. Candidate status honest (headline amended; original not found).
- SM-020 SEC BF Borgers order (3 May 2024): finding quote verbatim (para. 49); "at least 1,625 public filings" (para. 3); no clients named. Candidate status honest. NON-BLOCKING: the order also states the findings are "true and admitted" for bankruptcy-discharge purposes; decision_status could note that.
- SM-021 GAO B-423785 (18 Dec 2025, sustained): finding quote verbatim. Candidate status honest (evaluation record under protective order). Improvement: the solicitation is identified (RFP N00174-24-R-3002-0003) and may be recoverable as B.
- SM-029 (read, not opened): NON-BLOCKING status inconsistency. It is kept candidate "because the verdict has no formal authority", the same ground on which SM-031 is rejected (fails D1). Either reject it with that reason or state what would make it verifiable.

Rejected rows (all four read):
- SM-030 NTSB: reason holds (cause-of-event findings, no claim under review), though the source was not opened.
- SM-031 Community Notes: reason holds (no formally responsible reviewer).
- SM-032 Data Colada: reason holds (allegations, no authority).
- SM-033 PubPeer: reason holds (comments, no authority).

## Not checkable by validator (tool refusal)

1. SM-003 B: github.com/curl/curl/pull/4166 (provenance refusal after redirect). Corroborated through curl.se advisory.
2. SM-005 B: journals.plos.org e0327419 (rate-limited three times) and its PMC mirror (provenance refusal).

## Consequence for the target

If SM-005 is downgraded rather than fixed, verified rows drop to 9, below the TASK.md target of ten; the builder must then report the shortfall.

Verdict: NOT CONVERGED (1 blocking issue).
