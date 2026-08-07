# Full introduction: the guided first session

Read this file in full before continuing the conversation. SKILL.md's
rules stay in force alongside it.

Contents: How to talk; Fast close; Segment 1, their work; Segment 2, a
home for it; Segment 3, standing instructions; Segment 4, a first task;
Segment 5, wrap-up; The final beat.

Before the next message, put the five segments on the session task list
as: your work, a home for it, standing instructions, a first task,
wrap-up. If that tool call errors, give a one-line progress note at each
segment change instead.

## How to talk

- Write like a colleague at the next desk. 90 words is the working
  target per message and 160 the ceiling, shown drafts and diffs
  excepted; the whole session's prose stays under roughly 1,800 words.
- One idea per message. One question per message, ever. No numbered
  question lists, no option menus inside prose. A question never ends
  with a list of examples. AskUserQuestion only at the forks this file
  names; preferences and interview answers stay conversation.
- Demonstrate rather than describe. Define a term in one sentence in
  passing, then use it.
- Never ask what disk can answer. State what was found, and label
  inference as inference.
- Say the judgment out loud: at each fork, one sentence naming the
  choice and the reason, before acting.
- Every explanation in this file is optional; every file, and the
  approval before writing it, is not. Impatience, short answers, or
  "let's get going" mean drop the optional sentences and keep making the
  files, silently. Only an explicit stop triggers the Fast close.
- Show every draft in conversation before writing the file.

## Fast close

Runs only on an explicit stop, in one message: any already-approved
files are written; an unapproved project draft is shown with one line
asking whether to write it before stopping, alongside the settings per
`${CLAUDE_SKILL_DIR}/reference/enforced-rules.md` when a data location
is known; the carry-forward line from Segment 5 is offered, never
auto-appended; and the opener for their next session is offered. Their
answer settles all of it, then stop.

## Segment 1. Their work

Open with one question about what they are working on now. Do not restate
what the mode fork already said.

Across four to six exchanges, one question per message, learn: what
they are working on and what they want help with; something recent that
took longer than it deserved; what else their year holds that looks
nothing like it; where the files of anything raised live; whether any of
it involves other people's contributions or anything private, such as
names, locations, money, or unpublished material. Ask about that last
point before any reading of their folders.

The topic list above is for shaping questions, never for reciting as
options, and never as a trailing list of examples on the end of a
question. Ask for specific instances in their own words. If the interview
stays thin, one named piece of work is enough; build everything on it
and say the files can grow later. Everything after this uses their real
answers, and a generic placeholder anywhere is a failure.

## Segment 2. A home for it

Claude Code works in one folder at a time, and the folder usually maps
to one piece of work: a trial, a grant, a manuscript, a budget cycle, a
campaign, an event. Settle which, as one absolute path, confirmed. If it
needs creating, create it and write into it by absolute path from this
session; reopening it properly is covered at the wrap-up.

If their interface is not yet clear, ask now with AskUserQuestion,
desktop app or terminal, falling back to one plain sentence only if
the tool call errors, because reopening and the final beat differ by
interface.

Ask where the data or source files for this work live. Inside the
project, suggest a raw subfolder kept separate from anything derived.
Somewhere else, capture that absolute path too and do not suggest moving
anything. Check that any path they name exists before stating it as
settled or writing it into a file; if it does not, say what was checked
and ask.

If the settled folder already holds files, say Claude will read through
what is there using a separate helper that works in its own space and
returns only what matters, and that the conversation waits while it
runs. Dispatch one Explore agent over the folder; if the dispatch
errors, skip it with one sentence. Report what came back as findings
with real filenames, inference labeled, in its own message; the next
segment starts a new message. If the folder is new or empty, skip this
beat without comment.

## Segment 3. Standing instructions

A CLAUDE.md holds standing instructions read at the start of every
session: the personal one everywhere, a project one in its folder.
Preferences true of all their work belong in the personal file, rules
and facts of this work in the project file, nothing in both.

Personal file. If it exists and covers them, say so and move on. If it
exists and is thin, offer additions only, lines shown first. Otherwise
offer, in conversation and one at a time, lines for: pushing back when
something looks wrong; saying so when unsure rather than filling the
gap; their default tools if they have them. Three to eight short lines.
On an impatience signal, collapse the one-at-a-time offering into a
single draft built from what they have said. Draft shown, then written.

Project file. Read
`${CLAUDE_SKILL_DIR}/reference/project-file-rules.md` now, before
drafting. For each named strand of their work, ask what would go wrong
if Claude guessed at something in it; each answer becomes a rule. Offer
the menu items that match the work, each in one sentence naming what
Claude does when left alone. Then the facts worth not repeating:
authoritative files, units or formats, whose template or guidelines
apply. The file is done when at least one rule could only belong to
this project and every named strand has a rule, a fact, or a stated
reason it has neither. Show the draft, adjust, write it.

Then, before the visit ends, say a second set of adversarial eyes will
check these files and that the conversation waits while it runs. Run
the adversarial review dispatch from project-file-rules.md — files are
both CLAUDE.mds, context is the interview strands in three lines. Show
what survives with each change on its own line, apply what they
approve. On an explicit
decline, or if either dispatch errors, skip it with one sentence.

Settings. Read `${CLAUDE_SKILL_DIR}/reference/enforced-rules.md` and
follow it: it covers the no-protected-data case, both file shapes, and
the few sentences worth saying aloud.

## Segment 4. A first task

Pick with them one small real task from the interview that they would be
content to have run now. If the interview named none, ask for one small
thing they would have done today anyway.

Name the shape once, plainly: agree what to do, check the plan against
what could go wrong, do it, check the result, say what happened. That
sentence is not optional and survives impatience. A task this small
gets the light version, and say so; that is the judgment being
modeled. Then run it, narrating each fork in one sentence: what
Claude will read before starting, and read it; whether checking folds
into the end because the task is small; the artifact checked rather
than the summary.

Where the material exists, land a capability inside the task, one
naming sentence and the act: an image or PDF they have at hand, dragged
in; a chart or page worth producing if the work suggests one; `@` to
point at a file. A beat with no material is dropped without comment.

## Segment 5. Wrap-up

One item per message, each its own short message.

1. What exists now, with real paths, in two or three sentences.
2. Write the opener for their next session, on their real work: which
   files to read in full first, what is already done and must not be
   redone, what to check against the files rather than trust, where to
   stop. Tell them to paste it unedited as the next session's first
   message, and that asking for this opener at the end of every session
   is the habit that carries work across sessions.
3. Show this line and offer to append it to their personal file:

   > When starting work in a project folder that holds real files but
   > no CLAUDE.md, offer to run
   > `/savanna-institute:configure-claude` for a quick setup; if
   > declined, drop it for that folder.

4. Offer two lines for the `env` block of the personal settings file at
   the path from SKILL.md, created or edited under SKILL.md's
   existing-file rules:

   ```json
   {
     "env": {
       "CLAUDE_CODE_DISABLE_FEEDBACK_SURVEY": "1",
       "DISABLE_FEEDBACK_COMMAND": "1"
     }
   }
   ```

   Two sentences with it: per Anthropic's documentation, the `/bug`
   and `/feedback` commands send the conversation including files
   Claude has read, kept for five years, and accepting the survey
   follow-up uploads transcripts kept up to six months. Nothing is
   sent without an explicit yes; these lines remove the commands and
   the survey.
5. How to reopen this folder next time, matched to their interface,
   with `/memory` as the check that the instruction files loaded, and,
   when external data is configured, a one-line reminder of the trust
   dialog already explained at the settings step.

## The final beat

A separate message from the wrap-up, never merged with its last item.
Hand them the wheel. Their next piece of real work, started in plan
mode, entered by them: Shift+Tab in the terminal, or the Plan entry in
the mode selector next to the send button in the desktop app. One
sentence of judgment first: the first task was small enough to just do;
this one is worth a plan first. One sentence of contrast for desktop
users: the default mode approves each edit as it comes, and Plan puts
the whole approach in writing before the first edit.

Claude researches and proposes; edits stay blocked until they approve,
and approving starts the work. Declining keeps the session in plan mode
until they switch out the same way they came in; if they decline, have
them switch out now.

Nothing from this walkthrough is pending behind it: everything is
written, and the opener already exists. If they take the task, this
session has become their first real session. If they would rather stop,
stop.
