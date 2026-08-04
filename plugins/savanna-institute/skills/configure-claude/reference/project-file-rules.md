# Instructions for a project CLAUDE.md: a menu

These close the gap between Claude's defaults and how the person already works.
They are not lessons in research practice, and must never be delivered as
though they were. The scientist knows why a blank cell is not a zero. What they
do not know is that Claude, left to itself, would quietly treat it as one.

So when you offer an item, frame it as what Claude does by default, not why the
underlying standard matters. "Left alone, Claude would be expected to resolve
near-matching plot IDs across files without mentioning it" is useful.
"Identifier consistency is important in multi-year trials" is telling a field
scientist their own job.

One limit on how hard to assert any of this. What is evidenced is the general
pattern: where Claude lacks the knowledge a step requires, it supplies something
plausible and reports it in the same register it uses when it is right. The
specific forms below, the blank cell read as a zero, the silently dropped rows,
the fuzzy-matched identifier, are what that pattern would be expected to produce
on field data. They are not incidents on record. Offer them as defaults worth
closing off in advance, and do not claim any of them has been seen.

Length is a real constraint. An overstuffed CLAUDE.md gets ignored, including
the parts that mattered, and Anthropic's guidance is to keep these short and
human-readable. Pick what fits the work described in the interview. They can add
more when they notice themselves repeating something.

## This list is a starting set; the interview supplies the rest

The items below cover failures common to anyone handling collected data. They
will not cover the work you just heard about in the interview, and they are not
supposed to. Use them for two things: coverage of the common cases, and a
demonstration of the form.

The form is the transferable part. Name what Claude does when left alone, then
state what to do instead. Anything about a person's work can be written that
way once you know the work, and you just spent an interview finding it out.

So after picking from the list, write the rules their work actually needs. A few
shapes to prompt you, none of which belong in a fixed list because they are
specific to one person:

- A genomic selection program has a reference build, a marker file format, and a
  pedigree that has to stay consistent across analyses. Claude will pick
  whichever it finds. Name the authoritative one.
- Remote sensing work has a band order, a nodata value, a resampling method, and
  a coordinate system per product. Claude will infer any of them from context.
- A budget or report has a fiscal year, cost categories, and an indirect rate
  that Claude has no way to know and will supply plausibly.
- A long-running trial has treatment codes and a plot numbering scheme that
  changed at some point. Claude will read the current one as universal.
- An ecosystem, cropping systems, or agroforestry study has species codes, a
  block and treatment layout, and site names that carry meaning the files never
  state. Claude will read each as self-explanatory.

Ask what would go wrong if Claude guessed, then write the rule that prevents it.
The answer comes from them; the phrasing is your job.

---

## How Claude reports

> State what you checked and what you found, not that something is fine.

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
> not-measured. Ask.

This is the highest-value line in most data projects, because the failure is
invisible downstream.

> Never drop rows or records without reporting the count and the reason.

Expect merges and filters to lose rows silently.

> Never infer units, coordinate reference systems, or projections. Ask if the
> file does not state them.

> Flag in the output when data from different seasons, observers, instruments,
> or protocols has been combined.

> Show identifier mismatches rather than resolving them.

Left alone, expect it to resolve near-matching plot, tree, or accession IDs
across files without mentioning that it did.

---

## Analysis

> Return the R script, not only the result.

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
> [funder guidelines, journal style guide, protocol, prior drafts].

> This document is for [journal / funder / collaborators / internal].

> When a figure appears in more than one document, reference the source rather
> than retyping it, and tell me which is the source.

> Do not reuse a name for a different concept without flagging it.

---

## Multi-year work

> Keep a short "where things stand" section in this file current: what has been
> done, what is next, what is unresolved.

Worth arguing for on any trial that outlives a grant cycle. It costs nothing
because Claude maintains it as work happens.

> When a rule here depends on an assumption, write the assumption down.

> Before renaming a column or changing a shared definition, find what else
> references it and tell me.

---

## Sensitivity and irreversible actions

> Collaborator identities, precise field locations, and unpublished results do not
> go into anything shared, published, or sent outward without asking me first.

> Ask before overwriting, deleting, sending, or submitting anything. Approval
> once is not approval thereafter.

The "every time" clause matters, because consent to one action is otherwise
treated as consent to the pattern.

---

## Mention at the end of setup

- Add to it when they catch themselves re-explaining something.
- Remove rules that no longer apply; a stale rule is followed as readily as a
  live one.
- Avoid contradictions between the personal and project files. When two
  instructions conflict there is no reliable rule for which wins.
- Rerunning `/savanna-institute:configure-claude` in an existing project gives
  a review pass.
