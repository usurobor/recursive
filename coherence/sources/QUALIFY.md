# Qualified sources

The acceptance artifact for source discovery is a **qualified source**: a public, continuously updated source of coherence cases whose items carry enough data to run a coherence check and score it. Intermediate data (maps, logs, samples) stays on working branches; only qualified-source packets are presented for acceptance.

## Properties

A source qualifies when each property holds and carries evidence a reviewer can check in minutes.

| # | Property | Evidence required |
|---|---|---|
| P1 | **Public.** Readable without a paid account or a request. | Link to the listing page. |
| P2 | **Continuously updated.** | Items per year (last full year), earliest item date, latest item date; each with a link that shows it. |
| P3 | **Items are retrievable.** For a random sample of items, A (the claim), B (what it is checked against) and the finding can each be retrieved. | Sample of 10 items: count retrievable out of 10, with one line per item. |
| P4 | **Authoritative finding.** A formally responsible body decides, and its decision names the specific claim. | Who decides, under what rule; count of sampled findings that name the claim. |
| P5 | **Pre-outcome availability (a grade).** Share of sampled items where A and B were public before the finding. Blind-testable items are the benchmark; the rest are retrospective. | Count out of 10. |
| P6 | **Negatives.** The source or a sibling provides comparable items without an adverse finding. | Link to the negatives and how they are matched. "None" is a valid answer and lowers the grade. |
| P7 | **Access, rights, stable identifiers.** Machine retrieval (API, bulk, or stable scrapeable pages); terms that permit use; identifiers that keep a receipt checkable over time. | Access route, terms link, identifier scheme. |

Thresholds are provisional until Peter sets them: P1, P4 and P7 must hold; P3 at least 7/10; P2 at least 12 items in the last full year with an item in the last 90 days. P5 and P6 are reported as grades.

## Sample protocol

- Draw 10 items at random from the source's listing over the last three full years (or its whole life if shorter). Record the listing URL, the draw method and the drawn item IDs before inspecting any item, so the draw can be repeated.
- An item counts as retrievable only if A, B and the finding each open from a public link, or B is shown to be legitimately private (then P5 is N for that item but P3 can still count it if the finding states B's content).
- Never invent a URL, date, count or quote. Unknown is a valid answer.

## Packet (what Peter sees)

One packet per source, one screen:

- **Decision:** accept SM-xxx as a qualified source? accept / reject (reject carries a reason)
- P1–P7: one line each, value + link
- **Sample:** e.g. "7/10 retrievable · 5/10 blind-testable · negatives: yes (controls)"
- **Open point:** one line, if any

## Process

1. A qualifier agent per source gathers the evidence and writes the packet plus its working notes (working notes stay on the branch).
2. A validator agent, independent of the qualifier, re-checks every link and count in the packet.
3. Claude spot-checks and sends the packet to Peter in chat.
4. Peter accepts or rejects. Accepted packets are committed to `coherence/sources/qualified/` on main.
