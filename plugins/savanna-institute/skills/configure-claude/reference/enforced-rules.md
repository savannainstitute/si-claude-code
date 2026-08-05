# Enforced rules for a data folder

Read this when a mode file sends you here, at the settings step. Every
shape below is written to `.claude/settings.json` inside the project
folder; the personal settings file in the home `.claude` folder is a
different file and not touched here. The internal shape travels with
the folder. The external shape holds machine-specific absolute paths,
so when the project folder is shared with others through git or a
synced drive, write that shape to `.claude/settings.local.json` beside
it instead. The JSON and the syntax notes are for the file being
written and are never recited in conversation. The lines to say aloud
are at the end.

## No protected data anywhere

When the work has no raw data, no shared drive, and no files that must
not change, write no settings file. Say in one sentence that enforced
rules exist for when that changes, and return to the mode file.

## Raw data inside the project

```json
{
  "permissions": {
    "deny": ["Edit(/data/raw/**)"]
  }
}
```

Adapt the path to what they actually called the folder. Use `Edit(...)`;
path rules written against `Write` are accepted and then never consulted.
The single leading slash anchors at the project folder, so the rule
travels with it.

## Data outside the project

```json
{
  "permissions": {
    "additionalDirectories": ["<data folder path>"],
    "deny": ["Edit(//<data folder path, POSIX form>/**)"]
  }
}
```

Fill both placeholders from the one real path captured earlier; never
guess it. In the `additionalDirectories` entry write the path with
forward slashes (`C:/FieldData`), which JSON accepts unescaped. Scope
the deny to the raw portion when they name one, and to the whole
folder otherwise. The deny path is POSIX form with `//` in front: take
the path, convert to POSIX, drop its leading slash, prefix `//`.

- Windows: `C:\FieldData\raw` becomes `Edit(//c/FieldData/raw/**)`
- Mac: `/Volumes/FieldData/raw` becomes `Edit(//Volumes/FieldData/raw/**)`

Give only the example for their operating system. Both entries describe
this machine only; a colleague reaching the same data needs their own.

## Say aloud, adapted to their work, once each

- Instructions in a CLAUDE.md are context: Claude reads them and usually
  follows them. A permission rule in a settings file is enforced by
  Claude Code itself.
- The rule covers Claude's own file edits. A script Claude writes and
  runs is outside it, so a real backup remains the durable protection
  for anything irreplaceable.
- External data only: the first time they open this project, Claude Code
  shows a trust dialog naming the data folder, and accepting it is what
  turns the access on. The check that it worked is asking Claude to read
  one file from the data location.
