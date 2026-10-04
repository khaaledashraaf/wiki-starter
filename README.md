# wiki-starter

A folder that turns your raw material into a wiki Claude can answer questions from, with sources.

It is the starter version of the setup described in [How I use Claude to make informed decisions](https://khaledashraf.me/blog/informed-decisions).

## Use it

```bash
git clone https://github.com/khaaledashraaf/wiki-starter my-wiki
cd my-wiki
```

Drop your material into `sources/`:

- `sources/docs/` for meeting notes, PRDs, design docs
- `sources/database/` for schema dumps
- `sources/repos/` for read-only clones of your code

Then open Claude Code in the folder and run:

```
/build-wiki
```

It asks three questions, reads your sources, and writes the wiki into `generated/`. Every claim it writes is either cited back to a source or flagged as unverified.

## What's in here

```
my-wiki/
├── CLAUDE.md                      the rules: tiers of truth, cite or flag, routing table
├── sources/                       what you put in (read-only)
├── generated/                     what Claude writes
└── .claude/skills/build-wiki/     the skill that does the first pass
```

`CLAUDE.md` is the whole method. Read it once; it's short.

## After the first pass

Add more to `sources/` whenever you have it and run `/build-wiki` again. It only asks the three questions the first time.

`sources/repos/` is gitignored. Clone your code into it; it never gets committed with the wiki.
