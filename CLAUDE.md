# <domain> wiki

A citation-grounded reference for <domain>. Claude answers questions from `generated/`. The rules below keep it true.

## Tiers of truth

- **Tier 1, ground truth:** <code in sources/repos/, the schema in sources/database/, official specs>. The only place a new claim gets verified.
- **Tier 2, hypotheses:** `sources/docs/` (meeting notes, PRDs, design docs). What people said and intended. Check against Tier 1 before relying on it.
- **Tier 3, the wiki:** `generated/` and `glossary.md`. Written by Claude. Trust its citations when answering. Re-verify only when adding or changing a claim.

## The citation rule

Every load-bearing claim written into `generated/` carries a citation, `(source: path/to/file)` or `(file.py:LINE)`, or a flag: `[unverified]`, `[hypothesis]`, `[from notes, not yet checked]`, `[contradicts: ...]`. No citation and no flag means strip it or flag it.

## How to answer

Answer first, in a few lines. Read the file the routing table names and trust its citations. If a load-bearing claim is flagged, say so, or check Tier 1 before answering. Offer the long version as a question; don't default to it.

## Routing table: where to read for each question

| Question | File |
|---|---|
| How does <domain> work, end to end? | `generated/overview.md` |
| What is initiative X? | `generated/domains/<domain>/<initiative>/README.md` |
| Which initiatives exist? | `generated/domains/<domain>/_index.md` |
| What does term X mean? | `glossary.md` |
| What's still unresolved? | `generated/open-questions.md` |

If a question has no row here, that is the signal a new file is needed. Write it, cite it, add the row.

## Notes for your future self

When you learn something the hard way (a trap in the data, which document supersedes which, a method that worked), write it into `generated/playbook.md` and add a routing row. The next session starts further along than this one did.
