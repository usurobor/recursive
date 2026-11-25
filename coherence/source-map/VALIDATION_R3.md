# Validation R3: source map, after builder round 3

Validator: agent:validator, 2026-11-25. I ran my own checks first and read only the "Round 3" section of BUILD_LOG.md afterwards. The builder fetched no new pages in round 3, so I opened no URLs either. Every changed item rests on text I verified in R1 or R2.

## 1. Structural (my script: /home/claude/scratch/validator/structural.py, python3 -I)

- The 50 columns match TASK.md in name and order, and schema.csv matches. All 33 rows have 50 fields, and the ids are unique.
- All values are allowed. Every verified row has its proof fields filled; blank sample_b_url (SM-001, 004, 010) comes with a reason. All five rejected rows give a specific reason. Quotes are 25 words or fewer.
- SUMMARY.md counts match the CSV: 33 rows; 18 domains; 10 verified / 18 candidate / 5 rejected; 8 verified domains; blind_testable 7 Y (SM-001, 002, 003, 005, 006, 007, 008), 2 N (SM-004, 010), 1 unknown (SM-009). The rows scored schema_stress 5 are SM-003, 009, 020, 022 and 025: five, as line 4 now says.

## 2. The five round-3 items

1. SUMMARY line 4 now reads "chosen from the five rows scored 5 (SM-003, 009, 020, 022, 025)", which matches the CSV. **The R2 blocking issue is resolved.**
2. SM-007 notes now say the elision removes only "Not true!", and that "Lies!" comes earlier and the 150-159 and over-160 brackets come later. This matches the transcript order I read in R2. Resolved.
3. SM-029 notes no longer contain the "kept candidate" clause, so they are consistent with status=rejected. Resolved.
4. SM-005 sample_a_locator now points to the top two rows of Fig 2 in the non-COVID columns (pneumonia, tuberculosis, lung cancer, edema, consolidation lung) and notes that the Covid-19 column matches B's condition. This matches the notice's column list, verified in R2. Resolved.
5. SM-002 notes now state that the receipt has no dated version of A and that the overdue status before the finding rests on the BMJ post of 2018-06-26. The row is flagged for human review. Resolved; this remains a human-decision flag.

## 3. Proof fields unchanged since R2

I compared these fields for all ten verified rows against my R2 reading: finding_type, decision_status, case/A/B URLs and locators, both quotes, a/b/finding dates, blind_testable, the three scores and status. The only difference is the SM-005 sample_a_locator change in item 4. No regression.

## Not checkable by validator (tool refusal)

1. SM-003 B: github.com/curl/curl/pull/4166. Refused for provenance in R1 and not retried. The curl.se advisory backs up the row.

## Open human-decision flags (non-blocking)

- SM-009: should a rule about who may make a change count as a coherence case? If it is downgraded, verified rows drop from 10 to 9, below the TASK.md target.
- SM-002: a verified receipt with no dated version of A.
- Carried from earlier rounds: SM-005's B row labels are inside the image and were confirmed only through the notice's text.

Verdict: CONVERGED (no blocking issues).
