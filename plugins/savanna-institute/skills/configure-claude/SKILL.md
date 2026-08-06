---
description: Sets up Claude Code for a person's own work, through a guided first session, a quick project setup, or a check of an existing setup. Use when someone new to Claude Code wants the full introduction, when work is underway in a project folder that holds real files but no CLAUDE.md, or when someone asks to review their CLAUDE.md files or how a Claude Code feature works.
---

# Configure Claude Code

This skill runs one of three modes. Detect the situation, let the person
choose, then follow the mode: the first two have their own file, the
third is the Setup check section below.

## Who this is for

A colleague whose day is their own profession: research, administration,
grants and development, communications, finance, or operations. Two rules
govern every mode:

1. Define Claude mechanics plainly the first time each comes up, in one
   sentence, in passing. Context windows, tokens, models, and modes are
   specific to this tool.
2. Frame every rigor item as a Claude default they will want to change,
   never as a standard they might not have considered. They know their
   own job; the useful information is what Claude does when left alone.

## Before saying anything

Check quietly, without narrating the checking:

- The personal instructions file: `$HOME/.claude/CLAUDE.md`, on Windows
  `%USERPROFILE%\.claude\CLAUDE.md`. Resolve the home directory to an
  absolute path first; a literal `~` does not expand. If it is already in
  context as a memory file, read it from there.
- The personal settings file beside it, `settings.json` in the same
  `.claude` folder. A different file from the personal CLAUDE.md; both
  matter later.
- A `CLAUDE.md` in the current folder.
- What the current folder holds: a real project or a default location.
- A `.git` folder. Note it silently. Never raise git unless they raise it
  first or something fails because it is missing.

## Choosing the mode

When the person invoked this skill themselves: say in one or two
sentences what already exists, with real paths, so they learn early where
these files live. Then ask which they want, using AskUserQuestion with
exactly these three options; if the tool call errors, ask the same
question as one plain sentence naming the options.

- Full introduction. The guided first session: their work, their files,
  the habits, a first real task.
- Quick project setup. A CLAUDE.md and settings for this folder, nothing
  else.
- Setup check. Read the existing files, propose improvements, or answer
  how any Claude Code feature works.

Recommend full introduction when the personal CLAUDE.md does not exist,
quick setup when it exists and this folder has no CLAUDE.md, and setup
check when both exist. The recommendation is a default; anyone may
choose the full introduction whatever exists on disk, and the mode
handles what is already present.

When Claude invoked this skill on its own mid-conversation because the
folder holds real work and no CLAUDE.md: offer quick setup in one
sentence and continue with what the person was doing if they decline. Do
not raise it again in this session or this folder, and never start the
full introduction unbidden. If they want the wider tour, name
`/savanna-institute:configure-claude`. If they already said yes to a
setup offer in this conversation, skip the offer and the mode fork:
read the project-setup file and begin.

For the first two, read the mode file as the next action and follow it:

- Full introduction: `${CLAUDE_SKILL_DIR}/reference/full-introduction.md`
- Quick project setup: `${CLAUDE_SKILL_DIR}/reference/project-setup.md`

The mode fork already told them what exists; the mode file continues from
there without restating it.

## Setup check

Messages under 90 words, one question per message, proposals shown
before any edit. A how-does-X-work question is answered from
explainers.md as described at the end of this file, and can be the
whole visit.

For a review of the files: read the personal file and the project
CLAUDE.md and settings in full, naming what was read. Ask in one
question what has changed in the work since they were written; "nothing"
is a complete answer and shortens the pass. Propose line-level edits,
each with its reason in one clause: rules that no longer match what they
do — verified against the actual code and files, not recall — a stale
where-things-stand note, duplicated or contradicting lines across the
two files, universal preferences sitting at project level, a strand of
the work no line covers, anything grown past what gets followed, and
fit with the Placement and What Anthropic's guidance says sections of
`${CLAUDE_SKILL_DIR}/reference/project-file-rules.md`. If nothing needs
changing, say so and stop. Make only approved edits and show what
changed. When the review surfaces several issues, offer in one
sentence the adversarial review dispatch from project-file-rules.md —
files are both CLAUDE.mds, context is what they said has changed, in
one line, or the strands as the files name them — showing what survives as a short diff and
applying what they approve.

## When a file already exists

The personal settings file may hold permission rules, hooks, and other
configuration this walkthrough did not put there and cannot reconstruct.
In every mode:

- Change an existing file with Edit after reading it in full. Keep Write
  for files that do not exist yet.
- Before the first change to an existing settings file, copy it beside
  itself as `settings.json.bak`.
- After changing a settings file, read it back. If it no longer parses as
  JSON or anything it held before is gone, restore the copy and say what
  went wrong before trying differently.
- Never edit a pre-existing personal file without showing the exact lines
  first, and skip any line an equivalent of which is already there,
  saying so.

## In every mode

- Never invent a number these files do not give, such as how long a step
  takes.
- Answer any how-does-this-work question from
  `${CLAUDE_SKILL_DIR}/reference/explainers.md`, leading with the
  matching entry's first two sentences and going further only if asked,
  then return to the step. This rule is what the Setup check's
  refresher role runs on.
- If anything fails or is uncertain, say so plainly rather than
  reporting success.
