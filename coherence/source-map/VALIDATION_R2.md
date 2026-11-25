# Validation R2: source map, after builder round 2

Validator: agent:validator, 2026-11-25. Inputs: current TASK.md, DECISIONS.md, sources.csv, schema.csv, rubric.csv, SUMMARY.md. I read only the "Round 2" section of BUILD_LOG.md, and only after my own checks.

## 1. Structural (script: /home/claude/scratch/validator/structural.py, python3 -I)

- Header: 50 columns, names and order match TASK.md; schema.csv has the same columns in the same order. All 33 rows have 50 fields. Ids are unique.
- Allowed values conform. Blank scores on SM-030 are allowed by the revised schema.csv ("1-5 | blank (unopened rejected row)"), and the rationales say "Unassessed".
- Verified rows: all proof columns are filled. Blank sample_b_url on SM-001, 004 and 010 comes with a reason in sample_b_locator. All quotes are 25 words or fewer.
- Rejected rows (5): each has a specific reject_reason.
- latest_case_date now follows a "date (basis)" or "unknown (basis)" form on SM-001, 016, 017 and 025. OK.
- SUMMARY.md counts: 33 rows, 18 domains, 10 verified / 18 candidate / 5 rejected, 8 verified domains, blind_testable 7 Y / 2 N / 1 unknown with the right ids. All of these match the CSV.
- **BLOCKING (wrong count): SUMMARY.md line 4 says the three stress rows were "chosen from the six rows scored 5". The CSV now has five rows with schema_stress 5 (SM-003, 009, 020, 022, 025), because round 2 blanked SM-030's scores. Change "six" to "five".**

## 2. Changed rows, re-checked

### SM-005 PLOS ONE retraction (verified): R1 blocking issue resolved
- Notice re-opened. The sentence reads: "In addition, in Fig 2 of this article [1], the top two rows in the columns labeled Covid-19, pneumonia, tuberculosis, lung cancer, edema, and consolidation lung appear similar to the COVID-19 Omicron and pneumonia rows in Fig 2 of [2, retracted in 3] and the Dataset 1 and Dataset 2 rows in Figure 1 of [4], despite representing different conditions."
- Ref [4] in the notice: Malik H, Anees T, Naeem A, Naqvi RA, Loh W-K, Bioengineering (Basel) 2023;10(2):203, doi 10.3390/bioengineering10020203. This matches the new B.
- Elided quote: both fragments ("appear similar to" and "the Dataset 1 and Dataset 2 rows in Figure 1 of [4], despite representing different conditions") are verbatim. The elided span is exactly the LGD_Net clause recorded in notes, so removing it does not change the meaning.
- B opened (mdpi.com/2306-5354/10/2/203, also surfaced by search): same five authors, published 3 February 2023. Figure 1 caption is verbatim: "Samples of CT scan images of COVID-19 were collected from Datasets 1 to 5." No retraction notice appears in the page text. B (2023-02-03) predates A (2024-03-12), as required.
- A re-confirmed via PMC10931489 in R1: 2024-03-12, RETRACTED banner.
- Row labels inside B's Figure 1 are image content and were not visible to the text fetcher. The notice states the match, and the row discloses this limit.
- NON-BLOCKING: sample_a_locator names only the "Covid-19 and pneumonia columns". The notice names six columns. "Different conditions" bites hardest for the non-COVID columns, because B shows only COVID-19 images: A's Covid-19 column matching B's COVID-19 rows is the same condition. Point the locator at the non-COVID columns (pneumonia, tuberculosis, lung cancer, edema, consolidation lung).

### SM-006 UKSA letter (verified)
- Finding quote is verbatim, including the curly apostrophe in "Government’s" and the en dash before "neither". It establishes the finding. finding_type ("untrue on its natural reading") and decision_status ("letter from the Chair of the UK Statistics Authority") now match the letter's substance and form. OK.

### SM-007 PolitiFact (verified)
- Transcript re-opened. Line order: "Three-point-five million people from ages 140 to 149." / audience: "Not true!" / "And money is being paid to many of them, and we're searching right now." Both fragments are verbatim. The elision removes only one audience interjection, so the meaning is unchanged. Locator now says the rating is the finding. OK.
- NON-BLOCKING: notes misdescribe the elided text as "audience interjections ('Not true!', 'Lies!') and further age brackets up to over 160". Only "Not true!" is elided. "Lies!" and "Those are lies!" come earlier, and the 150-159 and over-160 brackets come after the payment sentence. Correct the note.

### SM-008 Full Fact (verified)
- The full sentence is verbatim, including the em dash: "...40,000 of which are set to be improved—not 4,000, as Mr Lammy suggested." (confirmed in R1; quote now matches). OK.

### SM-002 FDA notice (verified)
- No proof URL changed. TrialsTracker re-opened: Results Status "Overdue", Days late "3156". a_date now reads "none available" with a basis, and the field values are moved to notes.
- NON-BLOCKING, flag for human: the receipt now has no dated version of A. Verification and blind_testable Y rest on the 2018 BMJ blog showing the record overdue before the finding. That is honest and adequate for a retrospective receipt. A dated ClinicalTrials.gov history version would make it a full receipt.

### SM-003 CVE-2020-19909 (verified)
- finding_date 2023-08-28 equals cna.providerMetadata.dateUpdated (2023-08-28T08:04:05.477Z), checked in R1, and is labelled an upper bound. finding_type now separates the real overflow from the disputed security impact. OK.
- B (github.com/curl/curl/pull/4166) is still not directly checkable (R1 provenance refusal; not retried). It is corroborated by the curl.se advisory.

### SM-010 ORI (verified)
- ground_truth 4 with a rationale consistent with SM-004. "Voluntary Exclusion Agreement" is the notice's term (checked in R1). OK.

### SM-009 matplotlib PR (verified): judgment requested
- Proof fields are unchanged from R1, where all quotes and dates checked out.
- Is it a coherence case under TASK.md? Defensible on the letter of the Goal: "comparing a claim, change, or transaction against evidence or a rule" by someone "formally responsible", with a public trail. Here a change (the PR) is compared against a project rule (the issue is reserved for human newcomers) by the maintainer who is responsible for merging, and the ruling is public.
- Weaknesses that a human should weigh:
  - (a) The rule was stated ad hoc in the issue by the same maintainer who applied it. The written guide does not contain it.
  - (b) The checked property is the author's identity. Nothing in A's content (the PR title or diff) bears on the finding.
  - (c) A blind test would need provenance metadata that the content does not carry.
- NON-BLOCKING. **FLAG FOR HUMAN DECISION** (Peter): accept as a "rule coherence" sample, or downgrade. If downgraded, verified drops to 9, below the target of ten.

### SM-014 IPSO (candidate)
- Para. 15 re-opened: "It also noted that the publication had twice declined to set out what care it had taken over the accuracy of its headline when asked." The quote (from "the publication" to "when asked.") is verbatim. "A man v birminghammail.co.uk", concluded 12/11/2025 (finding_date 2025-11-12 OK), article 5 June 2025 (sample_a_locator OK). Status honest.
- NON-BLOCKING: latest_case_date "2026-05-07 (ruling 06653-25 published)" could not be confirmed; search did not surface that ruling. Unverified, not refused.
- NON-BLOCKING: the next sentence in para. 15 ("there was a breach of Clause 1 (i)") establishes the finding more directly than the quoted one.

### SM-011 FTC Workado (candidate)
- Complaint re-opened: Docket C-4822, issued 21 August 2025 (latest_case_date and finding_date OK). The 53.2% and 74.5% figures are in para. 14; para. 10 gives the model URL (sample_b_locator's "para. 10" is right for the card).
- Model card re-opened: it shows neither 53.2 nor 74.5, which confirms the stated blocker.
- Press release opened (found via search): 2023-07-25, quote verbatim. Candidate status honest.
- NON-BLOCKING: b_date "2023-05-07 to 2024-09-03 (model card commits)" is not shown on the card page. I did not open the commit history, so this is unverified, not refused.

### SM-029 TrialsTracker (now rejected)
- Reject reason holds and is consistent with SM-031.
- NON-BLOCKING: notes still say "kept candidate because the verdict has no formal authority", which contradicts status=rejected. Delete that clause.

### SM-030 NTSB (rejected)
- Scores blanked and marked unassessed; reject reason unchanged and still holds. OK.

### SM-001, 016, 017, 025: latest_case_date reformatted
- Values match what R1 observed (SM-001: 2025-12-17 on page 30 of 47). OK.

### SM-004, SM-020: notes only
- The validator observations were added and marked "not re-checked by builder". I had checked both in R1 (SM-004: "materially false statements" in para. 23-24; SM-020: "true and admitted" for bankruptcy-discharge purposes in Section V). OK.

## 3. Regression check, previously passing verified rows

- SM-001, SM-004, SM-009 and SM-010 proof URLs, locators, quotes and dates are unchanged from the values checked in R1.
- SM-002, 003, 006, 007 and 008 changed only in the fields re-checked above; their proof URLs are unchanged.
- No regression found.

## Not checkable by validator (tool refusal)

1. SM-003 B: github.com/curl/curl/pull/4166 (provenance refusal in R1; not retried). Corroborated through the curl.se advisory.

Unverified without refusal (search did not surface, or page not opened): SM-014 latest_case_date (ruling 06653-25); SM-011 b_date (model card commit history).

## Human-decision flags (non-blocking)

- SM-009: whether a rule about who may make a change counts as a coherence case. Verified count depends on it (10 vs 9).
- SM-002: a verified receipt without a dated version of A.

Verdict: NOT CONVERGED (1 blocking issue).
