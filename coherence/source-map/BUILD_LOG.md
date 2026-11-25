# Build log: verified rows (builder, 2026-11-25)

All pages below were opened with WebFetch on 2026-11-25. Quotes in sources.csv were checked against the fetcher's verbatim extract of each page.

## Pass constraints

- **URL provenance.** WebFetch opened only URLs that had appeared in WebSearch results, or links on a page fetched earlier. URLs built by hand were refused: Wayback captures, the CourtListener docket, the Justia docket, HF links quoted in a PDF, and redirect targets before they surfaced in search. As a result, no archived copy of a vanished A could be recovered in this pass.
- **Pages that failed:**
  - clinicaltrials.gov study pages returned no record data (client-side app).
  - pmc.ncbi.nlm.nih.gov/articles/PMC4320086 returned a reCAPTCHA page; PMC3359321 later loaded.
  - journals.plos.org/plosone/article?id=10.1371%2Fjournal.pone.0036941 was rate-limited on four attempts.
  - nvd.nist.gov returned only a header.
  - politifact.com article pages redirected to http (the api.politifact.com variant worked).
  - hansard.parliament.uk/Commons/2025-11-05 did not list PMQs.

## SM-001 AI Hallucination Cases Database: Mata v. Avianca
- Source page: https://www.damiencharlotin.com/hallucinations/?page=30 (2,338 cases; CC BY 4.0; last updated 25 Nov 2026)
- Finding: https://storage.courtlistener.com/recap/gov.uscourts.nysd.575368/gov.uscourts.nysd.575368.54.0_1.pdf (ECF 54, 2023-06-22, pp. 10-11 para. 26; bad-faith findings pp. 29-31)
- A: https://www.lawnext.com/wp-content/uploads/2025/06/Mata-v-Avianca-example-OCR.pdf (ECF 21, header "Document 21 Filed 03/01/23", p. 6 of 10)
- Also opened: https://storage.courtlistener.com/recap/gov.uscourts.nysd.575368/gov.uscourts.nysd.575368.44.1.pdf (ECF 44-1, citation repeated in the April 25 affidavit) and https://docs.justia.com/cases/federal/district-courts/new-york/nysdce/1:2022cv01461/575368/31 (order to show cause, 2023-05-04)
- B: no URL; the order records the Eleventh Circuit Clerk's confirmation.

## SM-002 FDA Notices of Noncompliance: Duchesnay, NCT02045901
- Source page: https://www.fda.gov/science-research/fdas-role-clinicaltrialsgov-information/clinicaltrialsgov-notices-noncompliance (11 notices)
- Finding: https://www.fda.gov/media/195948/download (2026-10-19; determination sentence; statutes cited)
- A: https://fdaaa.trialstracker.net/trial/NCT02045901 (completion 2017-03-31; reporting due 2018-03-31; 3156 days late)
- Corroboration (pre-finding): https://blogs.bmj.com/bmj/2018/06/26/unreported-clinical-trial-of-the-week-pyridoxine-doxylamine-for-nausea-and-vomiting-of-pregnancy-in-pregnant-adolescents-nct02045901/ ("87 days overdue" as of 2018-06-26)
- Failed: https://clinicaltrials.gov/study/NCT02045901 (no record data)

## SM-003 CVE records: CVE-2020-19909 (curl)
- Finding and A: https://cveawg.mitre.org/api/cve/CVE-2020-19909 (description, NOTE, tag "disputed", datePublished 2023-08-22, dateUpdated 2026-10-14)
- B: https://curl.haxx.se/bug/?i=4166 (PR "curl: cap the maximum allowed values for retry time arguments"; "to avoid integer overflows later when multiplying with 1000")
- Vendor ruling: https://curl.se/docs/CVE-2020-19909.html (dismissed 2023-08-26; fix merged 2019-07-29; MITRE declined to reject)
- Original description: https://daniel.haxx.se/blog/2023/08/26/

## SM-004 SEC administrative proceedings: Presto Automation
- Finding: https://www.sec.gov/files/litigation/admin/2025/33-11352.pdf (2025-01-14, paras. 6, 23, 24; without admitting or denying)
- A: https://www.sec.gov/Archives/edgar/data/1822145/000121390023001693/f424b30123_prestoautomation.htm (424B3 dated 2023-01-09, Summary of the Prospectus, Voice bullet)
- Also opened: https://sec.gov/Archives/edgar/data/1822145/000121390022080538/0001213900-22-080538-index.html (S-1/A filed 2022-12-16; main document URL not surfaced)
- B: private (first public in the order)

## SM-005 PLOS ONE retraction notices: Malik & Anees 2024
- Finding: https://journals.plos.org/plosone/article?id=10.1371%2Fjournal.pone.0351197 (notice 2026-06-23; Fig 2 similarity; reason: compromised peer review; references)
- A: https://journals.plos.org/plosone/article?id=10.1371%2Fjournal.pone.0296352 (published 2024-03-12; Fig 2 caption; retraction banner)
- B: https://journals.plos.org/plosone/article?id=10.1371%2Fjournal.pone.0327419 (LGD_Net, published 2025-08-08; Fig 1 caption; retracted 2026-04-08)
- Also opened, not used as B: https://mdpi.com/2075-4418/13/17/2772 (Diagnostics 2023, same first authors; no retraction notice seen)

## SM-006 UK Statistics Authority: Sunak "reduced debt"
- Finding: https://uksa.statisticsauthority.gov.uk/correspondence/response-from-sir-robert-chote-to-sarah-olney-mp-public-sector-debt (2023-12-19)
- A: https://hansard.parliament.uk/html/Commons/2023-11-22/CommonsChamber (PMQs, Engagements; "that we have indeed reduced debt")
- B: https://obr.uk/docs/dlm_uploads/November-2023-Economic-and-fiscal-outlook-presentation-script.pdf ("Underlying debt peaks at 93.2 per cent of GDP in 2026-27")

## SM-007 PolitiFact: "3.5 million people from ages 140 to 149"
- Finding: https://api.politifact.com/article/2025/mar/05/Trump-address-congress-fact-check-speech (2025-03-05; rated False)
- A: https://www.presidency.ucsb.edu/documents/address-before-joint-session-the-congress-4 (2025-03-04)
- B: https://www.ssa.gov/news/en/press/releases/2025-02-19.html ("These individuals are not necessarily receiving benefits.")
- Also opened while selecting a sample: https://politifact.com/factchecks/2024/may/15/joe-biden/joe-biden-wrong-that-he-inherited-9-inflatio/, https://politifact.com/factchecks/2024/feb/07/joe-biden/is-inflation-down-to-2-as-joe-biden-said-it-depend/ and https://api.politifact.com/article/2024/mar/08/fact-checking-joe-biden-on-inflation-the-deficit-a. Their A's are a video or an X post, or the article has no False rating.

## SM-008 Full Fact: Lammy "Four thousand military homes"
- Finding: https://fullfact.org/politics/david-lammy-deputy-pm-correction/ (2025-11-12)
- A: https://www.parallelparliament.co.uk/mp/leigh-ingham/debate/2025-11-05/commons/commons-chamber/oral-answers-to-questions (uncorrected Hansard text, 2025-11-05)
- B: https://www.gov.uk/government/news/defence-housing-strategy-a-9bn-generational-renewal-for-forces-family-housing-and-100000-new-homes-on-mod-land-to-drive-growth (2025-11-02)
- Confirmation: https://parallelparliament.co.uk/debate/2025-11-11/commons/written-corrections/prime-minister (written correction, 2025-11-11)

## SM-009 matplotlib PR review: PR #31132
- Finding and A: https://github.com/matplotlib/matplotlib/pull/31132 (title; closing comment)
- B: https://github.com/matplotlib/matplotlib/issues/31130 (maintainer comments reserving the issue for human contributors) and https://matplotlib.org/3.10.5/devel/contribute.html ("Restrictions on Generative AI Usage"; good-first-issue text)
- Date basis: https://www.theregister.com/2026/02/12/ai_bot_developer_rejected_pull_request/ ("On Tuesday", article 2026-02-12)

## SM-010 ORI findings: Eckert (UMB), PLoS One 2012 Fig 1B
- Finding: https://regulations.justia.com/regulations/fedreg/2024/08/15/2024-18289.html (FR Doc. 2024-18289; notice dated 2024-08-12, published 2024-08-15)
- A: https://pmc.ncbi.nlm.nih.gov/articles/PMC3359321 (published 2012-05-23; Figure 1 caption, panels B/C)
- B context: https://journals.plos.org/plosone/article?id=10.1371%2Fjournal.pone.0247222 (retraction 2021-02-11; Fig 1B labelled in raw records as Cyclin blot)
- Also opened (source survey): https://www.federalregister.gov/documents/2026/05/05/2026-08675/findings-of-research-misconduct, https://www.govinfo.gov/content/pkg/FR-2026-03-13/pdf/2026-04984.pdf and https://public-inspection.federalregister.gov/2025-15283.pdf. The last two name no published paper.

## Candidate rows with pages opened
- SM-011 FTC Workado:
  - Complaint: https://www.ftc.gov/system/files/ftc_gov/pdf/ContentatScaleAI-Complaint.pdf
  - Model card: https://huggingface.co/andreas122001/roberta-academic-detector and its commit history https://huggingface.co/andreas122001/roberta-academic-detector/commits/main/README.md
  - A was not recovered.
- SM-013 ASA: https://www.asa.org.uk/rulings/uab-commercecore-a25-1303252-uab-commercecore.html
- SM-014 IPSO: https://www.ipso.co.uk/rulings/02269-25/, https://www.ipso.co.uk/rulings/01663-25/ and https://www.ipso.co.uk/rulings/06653-25/
- SM-018 SEC comment letters: https://www.orrick.com/en/Insights/2024/12/SEC-Comment-Letter-Trend-AI-Related-Disclosures
- SM-019 PCAOB: https://pcaobus.org/news-events/news-releases/news-release-detail/pcaob-sanctions-james-pai-cpa-pllc-and-partner-for-audit-failures
- SM-020 BF Borgers: https://SEC.Gov/files/litigation/admin/2024/33-11283.pdf
- SM-021 GAO: https://www.gao.gov/products/b-423785
- SM-022 PTAB/Federal Circuit: https://www.cafc.uscourts.gov/opinions-orders/24-1492.OPINION.11-10-2025_2601155.pdf
- SM-025 NHTSA (volume basis): https://www.govinfo.gov/content/pkg/FR-2025-11-20/html/2025-20344.htm
- SM-028 curl HackerOne:
  - Author's blog: https://daniel.haxx.se/blog/?p=23836
  - Report mirrors: https://bugboard.rsecloud.com/report/2199174, https://bugboard.rsecloud.com/report/2298307 and https://vulners.com/hackerone/H1:2199174
- SM-029 TrialsTracker: same page as SM-002 A.
- Scientific-publishing survey (no row): https://retractionwatch.com/2023/08/31/stanford-president-retracts-two-science-papers-following-investigation

## Round 2 (validator R1 fixes, 2026-11-25)

Pages fetched in round 2:
- https://journals.plos.org/plosone/article?id=10.1371%2Fjournal.pone.0351197 (twice): Fig 2 paragraph and references [1]-[4]; confirmed the contiguous span "the Dataset 1 and Dataset 2 rows in Figure 1 of [4], despite representing different conditions".
- https://www.mdpi.com/2306-5354/10/2/203: Bioengineering 2023;10(2):203, published 2023-02-03; Figure 1 caption; no retraction notice in page text.
- https://uksa.statisticsauthority.gov.uk/correspondence/response-from-sir-robert-chote-to-sarah-olney-mp-public-sector-debt (twice): span ending "neither of which is the case", including the en dash before "neither".
- https://fullfact.org/politics/david-lammy-deputy-pm-correction/: full sentence ending "not 4,000, as Mr Lammy suggested."
- https://www.presidency.ucsb.edu/documents/address-before-joint-session-the-congress-4 (twice): "Three-point-five million people from ages 140 to 149." is followed by an interjection; "And money is being paid to many of them, and we're searching right now." comes later.
- https://cveawg.mitre.org/api/cve/CVE-2020-19909: containers.cna.providerMetadata.dateUpdated 2023-08-28T08:04:05.477Z.
- https://www.ipso.co.uk/rulings/02269-25/: para. 15 span "the publication had twice declined ... when asked."
- https://regulations.justia.com/regulations/fedreg/2024/08/15/2024-18289.html: "Voluntary Exclusion Agreement".
- FTC promotion attempt:
  - https://www.digitaljournal.com/pr/news/press-advantage/content-at-scale-announces-major-update-to-free-ai-content-detector: 2023-07-25 press release with "98.3%".
  - https://huggingface.co/andreas122001/roberta-academic-detector and https://huggingface.co/andreas122001/roberta-wiki-detector/raw/main/README.md: neither shows 53.2 or 74.5.

Changes per row:
- SM-005 (blocking): B corrected. The notice compares A's Fig 2 with Fig 2 of LGD_Net [2] (published 2025-08-08, after A, and itself retracted) and with Figure 1 of Bioengineering 2023 [4] (published 2023-02-03, same first two authors).
  - B is now [4], which predates A. binding_rule, artifact_b, finding_type, b_access and b_date were re-derived. The finding quote now covers [4], with one marked elision. LGD_Net is recorded in notes.
  - Status stays verified. Caveat: the row labels inside [4] Figure 1 were not visible to the text fetcher; the notice states the match.
- SM-006 (blocking):
  - Finding quote now ends "neither of which is the case".
  - finding_type restated as "untrue on its natural reading".
  - decision_status now uses the authority's form ("letter from the Chair").
  - b_access explains that the PM's office relied on the OBR forecast.
- SM-007 (blocking): claim quote extended with a marked elision to "And money is being paid to many of them". The locator states that the rating is the finding.
- SM-008 (blocking): finding quote is now the full 25-word sentence, including "not 4,000, as Mr Lammy suggested."
- SM-014 (blocking): finding quote corrected to the verbatim span ending "when asked."
- SM-002: a_date says no dated version is available. The field values (completion 2017-03-31, due 2018-03-31) moved to notes.
- SM-003: finding_date is now 2023-08-28, the CNA update carrying the quoted NOTE. finding_type and notes say the overflow was real and the dispute concerns security impact.
- SM-010: ground_truth 5 -> 4. "Voluntary Exclusion Agreement" replaces the wrong term.
- SM-029: candidate -> rejected (no formal authority, same ground as SM-031).
- SM-009: notes justify it as a rule-coherence check and flag it as borderline for human acceptance.
- SM-030: scores blanked as unassessed.
- SM-001, 016, 017, 025: latest_case_date put into "date (basis)" or "unknown (basis)" form.
- SM-004 and SM-020: validator notes added and marked as not re-checked.
- SM-011: promotion attempt recorded. It stays candidate because B (the 53.2% result) was not located.
- Schema: quote columns now allow marked elisions; scores may be blank on unopened rejected rows.
- SUMMARY: counts are now 10/18/5, and line 4 says why the three rows were chosen.
