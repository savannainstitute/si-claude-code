# Instructions for a project CLAUDE.md: a menu

Contents: This list is a starting set, the interview supplies the
rest; Placement; What Anthropic's guidance says; How Claude reports;
Data handling; Analysis; Documents; Long-running work; The adversarial
review dispatch; Sensitivity and irreversible actions.

These items close the gap between Claude's defaults and how the person
already works. Offer each as what Claude does when left alone, never as
why the underlying standard matters; they know their own job. The
specific failures below are expectations from that pattern, and are not
incidents on record; never claim one has been seen. Keep the file short.
An overstuffed CLAUDE.md gets ignored, including the parts that
mattered. Pick what fits the work described, and write the rest from
the interview.

## This list is a starting set; the interview supplies the rest

The form is the transferable part: name what Claude does when left
alone, then state what to do instead. After picking from the list,
write the rules this person's work needs, in that form. Shapes to
prompt you, each specific to one kind of work:

- A breeding program has a reference build, a marker file format, and a
  pedigree that must stay consistent. Claude will pick whichever it
  finds first. Name the authoritative one.
- Imagery work has a band order, a nodata value, and a coordinate
  system per product. Claude will infer any of them from context.
- A budget or grant report has a fiscal year, cost categories, and an
  indirect rate Claude has no way to know and will supply plausibly.
- A long-running trial or program has codes and numbering that changed
  at some point. Claude will read the current scheme as universal.
- A communications calendar, donor list, or event plan has names and
  statuses whose meaning the files never state. Claude will read each
  as self-explanatory.

Ask what would go wrong if Claude guessed, then write the rule that
prevents it. The answer comes from them; the phrasing is your job.

Write rules in the file owner's voice: I and me for the person, you
for Claude. Never refer to the person in the third person, and never
use a pronoun for them that they have not used themselves. Plain
hyphens and words, not em dashes or arrow symbols, in anything
written to a file.

---

## Placement

Preferences true of all their work belong in the personal file. Rules and
facts of this work belong in the project file. Nothing belongs in both:
the files are concatenated rather than ranked, and when two instructions
conflict there is no reliable rule for which wins.

---

## What Anthropic's guidance says

From the official memory documentation
(code.claude.com/docs/en/memory.md), for the review pass and for anyone
asking why a rule is phrased the way it is:

- Add a line when Claude makes the same mistake a second time, when the
  same correction gets typed again, or when a new teammate would need the
  same context.
- Keep each file well under its guidance ceiling: "Target under 200 lines
  per CLAUDE.md file. Longer files consume more context and reduce
  adherence." The files this skill writes should sit far below that.
- Write instructions "concrete enough to verify": name the file, the
  unit, the format, the command. A rule that cannot be checked will not
  be followed consistently.
- Group with headers and bullets rather than dense paragraphs.
- "If two rules contradict each other, Claude may pick one arbitrarily."
  Review periodically and remove stale or conflicting lines.
- The user-level file is for personal preferences that apply everywhere;
  the project file is for this work's standards and facts, and travels
  with the folder.
- An instruction that must always run at a fixed point belongs in an
  enforced mechanism, a permission rule or a hook, and never only in a
  CLAUDE.md.

---

## How Claude reports

> State what you checked and what you found.

Its default is a summary that reads as a verdict.

> Never assert a fact about a file you have not read. Say when you are
> reasoning from inference rather than from the file.

Recall and invention are indistinguishable in its output.

> Ask rather than filling a gap.

Left alone it supplies a plausible value instead of stopping.

> Disagree when warranted.

Its default lean is agreeable, which is worst when being used as a check.

> Do not generalize from a single file, plot, or season without saying so.

---

## Data handling

Most relevant to anyone working with collected data.

> Never modify raw data in place. Work on copies and write outputs elsewhere.

> Never decide on your own whether a blank means missing, zero, or
> not-recorded. Ask.

Left alone it resolves the blank silently, and nothing downstream shows
that it did.

> Never drop rows or records without reporting the count and the reason.

Expect merges and filters to lose rows silently.

> Never infer units, coordinate reference systems, or projections. Ask if the
> file does not state them.

> Flag in the output when data from different seasons, observers, instruments,
> or protocols has been combined.

> Show identifier mismatches rather than resolving them.

Left alone, expect it to resolve near-matching IDs, names, or codes
across files without mentioning that it did.

---

## Analysis

> Return the script along with the result.

> Start with the simplest analysis that answers the question; add complexity
> only when the data shows it is needed, and say why.

> Before relying on a check, demonstrate it catches what it is meant to catch.

> Do not report a multi-part check as complete when only part of it has
> finished.

> Label provisional values as provisional.

Otherwise a working number gets carried into the next document as settled.

---

## Documents

> Treat these files as authoritative and do not search the web unless I ask:
> [funder guidelines, style guide, protocol, template, prior drafts].

> This document is for [funder / journal / partners / board / internal].

> When a figure appears in more than one document, reference the source rather
> than retyping it, and tell me which is the source.

> Do not reuse a name for a different concept without flagging it.

---

## Long-running work

Left alone, Claude keeps a single "where things stand" note inside
CLAUDE.md — it goes stale the moment a session ends unrevised, or
grows without bound if it doesn't. Offer instead:

- a current-state file (suggest `docs/current-task.md`), short,
  `@`-imported so it loads every session, rewritten entirely at each
  close, never appended to;
- a backlog file (suggest `docs/master-plan.md`) for known issues and
  planned work, named by path in CLAUDE.md and read on demand, never
  imported;
- an append-only dated log (suggest `docs/recent-summary.md`) of what
  each session tried and found, also named by path and read on
  demand, never imported.

Offer a session-close command that rewrites the first file, updates
the second, and appends to the third — the split drifts as easily as
a single note without one.

> When a rule here depends on an assumption, write the assumption down.

> Before renaming a column or changing a shared definition, find what else
> references it and tell me.

---

## The adversarial review dispatch

These files steer every future session, so before trusting them, run
this: one agent to find problems, each finding numbered, briefed to
check placement, duplication or contradiction within or between the
files, coverage of every named strand, fit with the guidance above, and
whether the copied Data handling rules that match the work are
present, leaving sound existing rules alone — and, for every claim it
makes, to verify it against the actual files, folder, and commands
first and report only what it verified, with the evidence. Then a
second, independent agent gets the numbered findings only, not the
first agent's reasoning, briefed to independently re-verify each one
against the same files and commands and say, by number, which do not
hold up and why, defaulting to not-confirmed when the evidence is
thin. Each agent's prompt carries the absolute paths of the files
under review, the context lines the calling step names — the strands the
coverage check runs against — and, copied in full, the Placement,
What Anthropic's guidance says, Data handling, and How Claude reports
sections above.

---

## Sensitivity and irreversible actions

> Names, locations, financial details, and unpublished material do not
> go into anything shared, published, or sent outward without asking me
> first.

> Ask before overwriting, deleting, sending, or submitting anything.
> Approval once is not approval thereafter.

Left alone, it treats consent to one action as consent to the pattern.
