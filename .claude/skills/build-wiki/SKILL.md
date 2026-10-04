---
name: build-wiki
description: Turn a folder of raw material (docs, meeting notes, PRDs, code, schema dumps) into a citation-grounded wiki that Claude can answer questions from. Use when the user says "build the wiki", "organize my domain knowledge", "make sense of these documents", or runs /build-wiki.
---

# build-wiki

You are turning raw material into a wiki that answers questions with sources. The person you're working with has put files into `sources/`. Your job is to read them, write short briefs into `generated/`, and fill in `CLAUDE.md` so every future session knows where to look.

Work in this order. Keep chat replies short; the files are the deliverable.

## 1. Ask three questions

Only if `CLAUDE.md` still has `<placeholders>` in it. Otherwise skip to step 2.

1. **What is this domain?** One line, e.g. "logistics at an e-commerce company" or "our payments platform".
2. **What counts as ground truth here?** Code in `sources/repos/`? A database schema in `sources/database/`? Official specs? This becomes Tier 1.
3. **What do you want to ask it?** Two or three example questions. These seed the routing table.

Fill the placeholders in `CLAUDE.md` with the answers. Do not add anything else to that file yet.

## 2. Inventory the sources

List what is in `sources/` by folder: how many files, what kinds, rough dates. Do not read everything yet. Write the inventory to `generated/_inventory.md` and show the person a five-line summary. If a folder is empty, say so and move on.

## 3. Write the overview

Read enough of `sources/` to explain how the domain works end to end, then write `generated/overview.md`: the flow in plain words, the main entities, the main actors, and where the boundaries are. Aim for one screen. Every claim carries a citation `(source: path/to/file)` or a flag `[unverified]`. Prefer a short cited overview to a long uncited one.

## 4. Find the initiatives

From the sources, list the distinct projects, features, or workstreams. For each one, create `generated/domains/<domain>/<initiative>/README.md` with: what it is, who it's for, the current state, the key decisions, and open questions. Same citation rule. Then write `generated/domains/<domain>/_index.md`: one line per initiative, linking to its README.

If the sources cover more than one domain, make one folder per domain under `generated/domains/`.

## 5. Start the glossary

Create `glossary.md` at the root with every internal term and acronym you met, one line each, cited. If two sources define a term differently, record both and flag `[contradicts]`.

## 6. Fill the routing table

Open `CLAUDE.md` and complete the routing table: one row per kind of question, naming the file that answers it. Use the person's example questions from step 1 as the first rows. Every file you wrote in steps 3 to 5 should be reachable from the table.

## 7. Report

Tell the person, in under ten lines: what you wrote, how many claims are flagged, what the sources don't cover, and which of their example questions the wiki can answer now. Offer to run again when they add more material.

## Rules that hold throughout

- **Sources are read-only.** Never edit, move, or delete anything in `sources/`.
- **Cite or flag.** A claim with no citation and no flag does not go into `generated/`.
- **Don't invent.** If the sources don't say, write `[unknown]` and add it to `generated/open-questions.md`.
- **Short beats complete.** A brief that fits on a screen gets read. One that doesn't, doesn't.
- **Save what you learn.** If you work out something that will help the next session (how a file is structured, which doc supersedes which), write it into `generated/playbook.md` and add a routing row for it.
