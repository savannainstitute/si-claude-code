# Claude Code setup for the research department

This repository holds a small plugin that configures Claude Code for research
work. It walks you through setting up your own environment: folders for your
projects, standing instructions so you stop repeating yourself, and the
practices that make sessions productive.

You run it once to get set up, and again whenever you start a new trial, grant,
or manuscript. It adapts to whatever you tell it about your work, so there is no
single correct configuration.

## Before you start

You need Claude Code, and git installed on your machine. If either is missing,
or you are not sure, ask Zack.

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
once, in either place. Or ask Zack.

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

It starts by asking about your work: what you are working on, where you are in
the field season, what files you already have, whether anyone else collected the
data. Everything after that is based on your answers.

Expect it to take half an hour or so the first time. Later runs, when you start
a new project, are much quicker.

Run it again any time:

- Starting a new trial, grant, or manuscript
- Coming back to a project after months away
- Wanting a second look at a setup that has gone stale

It works out which situation you are in and adjusts.

## What it sets up

- A folder for the work, with raw data kept separate and untouched
- A personal preferences file that applies to everything you do
- A project file holding the facts and rules for that specific work: which
  documents are authoritative, units and coordinate systems, naming
  conventions, and where the project currently stands
- Instructions covering the things Claude does silently by default: modifying
  raw data, deciding a blank means zero, dropping rows in a merge, inferring
  units
- The practices that matter most day to day: telling Claude what to read before
  giving it a task, keeping the state of the work in a file rather than in the
  conversation, and one bounded task per session
- A demonstration of plan mode, where Claude proposes before it acts

## If something goes wrong

Ask Zack. If a command above did not do what this page says it would, that is
worth reporting rather than working around.

## For maintainers

```
.claude-plugin/marketplace.json     the catalog that makes this installable
plugins/savanna-institute/          the plugin itself
  .claude-plugin/plugin.json        manifest
  skills/configure-claude/
    SKILL.md                        the walkthrough
    reference/project-file-rules.md  menu of instructions for project files
    reference/explainers.md         checked wording for the mechanics
```

The manifest deliberately has no `version` field. Hosted in git without one,
every commit counts as a new version, so pushing a change is all that is needed
to release it.

`reference/explainers.md` is checked against the official Claude Code
documentation. If Claude Code's behavior changes, correct that file rather than
letting the walkthrough improvise.
