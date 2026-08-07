# Claude Code setup for Savanna Institute

This repository holds a small plugin that configures Claude Code for your work
at Savanna Institute. It walks you through setting up your own environment:
a folder for the work, standing instructions so you stop repeating yourself,
and the habits that make sessions productive, ending with a first real task
run the way sessions should run.

You go through it once. After that, when you are working in a folder that has
no instructions file yet, Claude offers to set one up in a few questions,
and you can run the command again any time for a quick project setup or a
check of what you already have. It adapts to what you tell it
about your work, so there is no single correct configuration.

## Before you start

You need Claude Code, and git installed on your machine. Installing Claude
Code is covered below; on Windows, git comes from
[Git for Windows](https://git-scm.com/downloads/win). If you are not sure
what is already there, open Claude Code and ask; it can check whether git is
present.

You do not need a GitHub account.

### Desktop app or terminal

Claude Code comes two ways, and they share everything: the same instruction
files, the same plugins, the same settings. Use whichever you prefer.

The desktop app is a normal application you install from an installer. You pick
which folder you are working in with a button, and it starts out proposing
changes and waiting for your approval before touching anything. Download it for
[macOS](https://claude.ai/api/desktop/darwin/universal/dmg/latest/redirect) or
[Windows](https://claude.com/download).

The terminal version is the same thing driven by typed commands. Install it with
`curl -fsSL https://claude.ai/install.sh | bash` on macOS, Linux or WSL, or
`irm https://claude.ai/install.ps1 | iex` in Windows PowerShell. Full options
are on the [setup page](https://code.claude.com/docs/en/setup).

Everything below works in both.

## Installing

Open Claude Code and type these three commands, one at a time.

Add this repository as a source:

```
/plugin marketplace add https://github.com/savannainstitute/si-claude-code.git
```

Install the plugin:

```
/plugin install savanna-institute@savanna-institute
```

A panel will open showing what the plugin adds and asking where to install it.
Choose User scope, so it is available in all your projects.

Activate it:

```
/reload-plugins
```

That is the whole installation. Nothing to download, nothing to unzip.

If the first command does not work in the desktop app, run it once in the
terminal instead. Plugins are shared between the two, so it only has to be done
once, in either place. If it still fails, paste what happened into Claude and
ask; the usual cause is git missing from the machine.

### Get updates automatically

Improvements arrive on their own if you turn that on once:

1. Type `/plugin`
2. Choose Marketplaces
3. Select savanna-institute
4. Choose Enable auto-update

Without this you keep the version you installed. To update by hand instead:

```
/plugin marketplace update savanna-institute
```

```
/plugin update savanna-institute@savanna-institute
```

## Using it

In Claude Code, type:

```
/savanna-institute:configure-claude
```

It checks what you already have, then asks which you want: the full
introduction, a quick project setup, or a check of an existing setup. The
full introduction starts with your work, in your words: what you are doing,
what took longer than it deserved lately, where the files live. Everything
after that is built from your answers. Later runs, when you start a new
piece of work, take a few questions.

Run it again any time: starting a new trial, grant, campaign, or report;
coming back to a project after months away; or wanting a second look at a
setup that has gone stale.

## What the full introduction sets up

- A folder for the work, with source data kept separate and untouched
- A personal preferences file that applies to everything you do
- A project file holding the facts and rules for that specific work, with
  an offered second-reviewer pass for placement, coverage, and fit with
  Anthropic's own guidance
- Where source data is involved, a rule Claude Code enforces that stops
  Claude editing it directly
- A first real task from your own work, run together, then a handoff into
  plan mode, where Claude proposes before it acts, for the next one
- The habit worth the most: an opener for your next session, written before
  this one ends

## If something goes wrong

Paste what happened into Claude and ask; it can usually name the missing
piece. For questions about how any of this works, the setup command has a
check option that answers them against your own setup. If a command above did
not do what this page says it would, that is a bug in this setup: report it
to Zack rather than working around it.

## For maintainers

```
.claude-plugin/marketplace.json     the catalog that makes this installable
plugins/savanna-institute/          the plugin itself
  .claude-plugin/plugin.json        manifest
  skills/configure-claude/
    SKILL.md                        mode routing, plus the setup check
    reference/full-introduction.md  the guided first session
    reference/project-setup.md      the quick per-folder setup
    reference/enforced-rules.md     permission-rule shapes for data folders
    reference/project-file-rules.md menu of instructions for project files
    reference/explainers.md         checked wording for the mechanics
```

The manifest deliberately has no `version` field. Hosted in git without one,
every push is a release: fresh installs get it immediately, and existing
installs get it when auto-update is on or they update by hand, per the
update section above. Push only states that are complete and tested.

`reference/explainers.md` is checked against the official Claude Code
documentation. If Claude Code's behavior changes, correct that file rather than
letting the walkthrough improvise.
