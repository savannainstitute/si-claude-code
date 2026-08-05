# Plain-language explainers

Wording for the mechanical parts of Claude Code, checked against the official
documentation. These are easy to get subtly wrong from memory, so use these
framings rather than improvising, and adapt the examples to the person's work.

Introduce a term, define it in a sentence, move on.

Contents: Model; Effort; Tokens; Context window; Auto memory; When a
session fills up; /compact and /clear; Resuming a session; How CLAUDE.md
files are found; Permission rules; Data and privacy; Plan mode; Running
code; Skills; Delegation and subagents; Working directory; Desktop app
versus terminal; Features worth teaching early.

---

## Model

Which version of Claude is doing the thinking. Several exist, trading speed and
cost against depth of reasoning. Claude Code is the program around the model: it
provides the file access, the tools, and the interface, and the model does the
reasoning.

Faster, cheaper models suit quick well-defined work such as reformatting a list
or a small edit. Stronger models earn their cost on ambiguous, high-stakes, or
multi-step work such as drafting a protocol from scratch or planning an
analysis.

The named models run Haiku, Sonnet, Opus, Fable, in roughly ascending capability
and cost. Haiku for mechanical work that is already fully specified. Sonnet for
most of the day. Opus for harder reasoning. Fable for complex problems where
thoroughness is the requirement: an exhaustive pass rather than a spot check, a
problem with many interacting parts, or a long job it carries out largely on its
own. The picker is authoritative over that list, since which models appear
depends on the plan and version.

Change it with `/model`. Which options appear depends on their plan and version,
so tell them to read the list rather than expecting specific names. Selecting
one makes it the default for new sessions; pressing `s` on a row changes only
the current session.

Do not claim Claude can switch its own model. It cannot. `/model` is theirs to
press. What Claude can do is hand work to a stronger model as a subagent, which
is covered under Delegation below.

## Effort

How much reasoning the current model does before answering, without changing
which model it is. Adjust with `/effort`. Available levels depend on the model,
and `max` applies to the current session only. Leaving it alone is fine.

## Tokens

The units text is broken into for a model to process, roughly three and a half
characters of English each, so usually a word or part of one. Usage and cost are
counted in tokens.

Avoid saying tokens vary in size with task difficulty. A short task uses
fewer tokens; tokens themselves do not change size.

## Context window

Everything Claude can currently see: the conversation so far, files it has read,
command output, the CLAUDE.md files, and any skills in use. Working memory for
the session, with a fixed size.

The point that matters most: the conversation itself does not carry over.
Yesterday's discussion is gone. What comes back at the start of a new session is
what is written in files on disk and re-read automatically.

## Auto memory

Two different things come back, and the difference matters.

Claude also keeps its own notes between sessions, written automatically and
loaded at the start of the next one. They will see brief "Saved a memory" or
"Recalled a memory" indications. It is worth knowing about, so do not tell
them nothing carries over.

But those notes are Claude's own. They did not choose what went in and will
not necessarily notice what did not. A CLAUDE.md file is the opposite: they
wrote it, they can read it, and it is re-read in full every time. Anything
that must not be lost goes somewhere they control: auto memory is a
convenience and CLAUDE.md is the record.

## When a session fills up

Claude Code compacts automatically as the limit approaches, so the session
continues rather than stopping. It first clears older tool output, then
summarizes the conversation if it needs more room. Requests and important
material are kept; detailed instructions from early in a long conversation may
be lost.

What reliably survives is what gets re-read from disk, meaning the project and
personal CLAUDE.md files. That is the argument for putting anything durable in a
file rather than saying it once in conversation.

They are not powerless over it. Running `/compact` themselves before the
automatic pass, with a focus such as `/compact focus on the ID
reconciliation decisions`, keeps what they choose rather than what the
automatic pass infers. A "Compact Instructions" section in CLAUDE.md can
also say what to preserve. Do not tell them they have no control.

## `/compact` and `/clear`

Both address a long conversation, differently.

`/compact` summarizes and continues in the same session. Use it when the current
task is unfinished but the conversation has grown unwieldy. It takes optional
focus instructions.

`/clear` starts a fresh conversation with nothing carried over. Use it when
moving to unrelated work, so old context does not influence a new question.

The habit worth teaching: one topic per session.

## Resuming a session

A closed session is not gone. In the terminal, `claude --continue` reopens the
most recent session in the current folder, and `claude --resume` opens a picker
of past ones. Sessions can be named, with `claude -n a-short-name` when starting
or `/rename` inside one, and a named session can be reopened directly with
`claude --resume` and the name. Naming is what makes the picker usable weeks
later, when "which of these held the analysis" is otherwise a guess.
`/export` writes the conversation to a plain text file, which is worth
mentioning to anyone who wants a record of how an analysis decision was reached.

The caveat: reopening a large old session offers a choice between resuming from
a summary and resuming the full session, and the summary loses detail. For work
picked up after weeks, a fresh session opened with a written handoff usually
beats resuming, which is why the walkthrough teaches asking Claude to write the
next session's opening prompt.

## How CLAUDE.md files are found

When Claude Code starts, it looks in the current folder and every folder above
it, collecting any CLAUDE.md files it finds. All of them are added together and
none overrides another. Content is ordered from the outermost folder inward, so
the file closest to where they started is read last.

Files in folders below where they started are not loaded at launch. Those load
only when Claude actually reads a file in that folder.

Three things worth telling them:

- The personal file at `~/.claude/CLAUDE.md` applies to every session anywhere.
- A project file lives in the project folder as `CLAUDE.md`.
- If two files give conflicting instructions there is no reliable rule for which
  wins. Claude may follow either. So the two files should complement each other,
  and the project file should not restate or contradict the personal one.

Do not describe this as precedence or override. It is concatenation.

## Permission rules

Two mechanisms shape what Claude does, and they fail differently.

Instructions, in a CLAUDE.md or in conversation, are context. Claude reads them
and usually follows them, but nothing enforces them, and a rule stated in
conversation can be lost when a long session compacts. Permission rules, kept in
a settings file, are enforced by Claude Code itself, the program around the
model, regardless of what the model decides. That is the line between "please do
not edit raw data" and an edit that is refused.

A deny rule on a folder covers Claude's own file tools and the common file
commands Claude Code recognizes in shell commands, such as `cat` and `sed`. It
does not cover a script that opens files itself. An R script Claude wrote and
ran can still overwrite a protected file, because the rule never sees what a
running script does internally. `/rewind` does not bring the file back either,
since it tracks only Claude's own edits.

So for irreplaceable data the honest ordering is: a real backup first, the
folder made read-only at the operating system level if they are willing, and
the deny rule as a guardrail on top. Do not present the deny rule alone as the
safety net.

## Data and privacy

Two questions matter here: whether this trains on their data, and how long
anything is kept.

Training: no, by default. On the Team plan, Anthropic does not train models
on code or prompts sent through Claude Code, unless an org admin has
explicitly opted the organization in, such as through the Developer Partner
Program. That is an organization-level decision, made outside any session.
The free, Pro, or Max version at claude.ai works differently, with its own
training toggle that may be on for that account.

Retention: conversations are kept server-side for 30 days. A plaintext copy
of the session also sits on the machine, under `~/.claude/projects/`, for 30
days, so a session can be resumed.

Two things do leave the machine and stay longer, and neither ever happens
without an explicit yes: `/feedback`, `/bug`, and `/share` send the
conversation and file contents, kept five years; the session-quality
survey's optional transcript follow-up, kept up to six months. The full
introduction's wrap-up already offers to turn both off.

## Plan mode

Claude researches and proposes without changing anything until they approve. It
can read files and explore, but edits stay blocked until the plan is accepted.

Two ways in: press Shift+Tab to cycle into it, or start a message with `/plan`
for a single request. Approving the plan exits plan mode. Declining does not:
the session stays in plan mode until they leave it themselves, with Shift+Tab
in the terminal or the mode selector in the desktop app.

Worth demonstrating once rather than describing.

## Running code

Claude runs the script, reads the actual error message, fixes the script,
and runs it again, without the copy and paste loop a browser chat needs. For analysis work this loop is where most of
the value is, so demonstrate it on something real rather than describing it.

Mechanics worth knowing:

- A command gets two minutes by default, and Claude can extend a single command
  to ten. Something still running at the limit is moved to the background rather
  than killed, and Claude picks up the output when it finishes.
- Very long output is saved to a file rather than shown whole; Claude gets the
  file path and a preview, and reads more as it needs it.
- Each command starts fresh, so environment state does not carry from one
  command to the next. An environment activated mid-session does not stay
  active. Anyone using conda or a virtualenv should activate it before
  launching Claude Code.
- The documentation describes a general shell tool and never names R. An
  installed R runs through it like any other command, so expect `Rscript` to
  work, but present that as how the mechanism works rather than as a documented
  promise about R.

## Skills

A skill packages instructions so a procedure does not have to be re-explained.
The setup walkthrough is itself one. Claude can invoke a relevant skill on its
own, or they can type its name.

The useful property: a skill's content only loads when it is actually used, so
having several costs nothing until needed.

## Delegation and subagents

Claude can hand a self-contained piece of work to a separate assistant that
works in its own context and returns just the result, and it can choose a
stronger model for that assistant than the one in the main conversation.

The benefit worth naming: heavy work such as searching many files does not fill
up the main conversation, and only the answer comes back. The main conversation
waits while the assistant works, so a dispatch reads as a short pause with a
progress note.

The setup walkthrough can demonstrate this, reading through the project
folder and as an offered second set of eyes over the newly written
instruction files. The everyday form is one sentence: for anything
high-stakes, ask Claude to have a separate reviewer check it. Be precise
about which part is automatic: Claude delegates on its own routinely, but
those assistants normally run on the same model as the main conversation,
so a stronger model for a subagent is a choice to ask for.

## Working directory

Claude Code works within one folder at a time. It sees that folder's files and
picks up that folder's CLAUDE.md. Started somewhere generic, it has neither.

How they set it depends on which interface they use.

## Desktop app versus terminal

Both run the same Claude and share the same configuration: the same CLAUDE.md
files, the same skills and plugins, the same settings. Nothing in this
walkthrough is specific to one.

Desktop app. A normal application installed from an installer, with no command
line involved. The Code tab, with Local selected, gives a Select folder button,
which is a graphical picker with no typed paths. It starts in a mode where
Claude proposes changes and waits for approval. Files, PDFs, and images can be
dragged into the prompt. On Windows, git must be installed for local sessions;
most Macs already have it.

Terminal. Open a terminal, change into the project folder with `cd`, and run
`claude`. More capable in a few advanced respects and the right choice for
anyone already comfortable there.

Recommend the desktop app to anyone who prefers buttons to typed commands.

One caveat: plugins and marketplaces are shared configuration, so adding one
from either interface makes it available in both. If a marketplace cannot be
added from the desktop app's plugin browser, adding it once from the terminal
covers both.

## Features worth teaching early

Interrupting. Escape in the terminal, the stop button in the desktop app. Work
already done is kept and the conversation continues, so stopping Claude the
moment it heads somewhere wrong is free. Anthropic's guidance is to correct
as soon as you notice.

Images and files. Dragging an image, screenshot, or PDF into the conversation
works in both interfaces, and in the terminal pasting a copied image also works.
Claude reads diagrams, screenshots, figures, and photographs, so a photographed
data sheet or a figure that looks wrong can be shown rather than described.

Typing `@` to reference files, which opens a picker with completion and is
faster than describing where a file lives.

`/rewind`, which restores the conversation, the files, or both. A genuine safety
net, but it only tracks edits Claude made directly through its own file tools,
so it is not a substitute for keeping copies of anything irreplaceable. The
checkpointing page documents it without tying it to an interface and never
names the desktop app's Code tab, so in the desktop app treat it as expected
rather than documented: have them run `/rewind` once and read what appears.

Two failed corrections. If a request has gone wrong twice, starting a fresh
session with a better-worded request usually beats continuing to patch.
