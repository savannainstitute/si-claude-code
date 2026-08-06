# Quick project setup

Read this file in full first. This mode sets up one folder, a
CLAUDE.md plus enforced rules where the work needs them, and teaches
nothing unless asked. It is also what runs when Claude
offered the setup itself mid-work and the person said yes.

How to talk: messages under 90 words. One question per message. Never
ask what disk can answer, and never invent a number these files do not
give. Show every draft before writing.

## Steps

1. One-line greeting naming the folder. Confirm it is the right folder
   for this work, as an absolute path. Ask where the data or source
   files for it live and capture that path too.
2. Ask, one question per message: what is this work; whether anything
   here involves other people's contributions or anything private, such
   as names, locations, money, or unpublished material; and what would
   go wrong if Claude guessed at something in it. After the second
   answer, ground the draft by reading the folder's files directly
   rather than asking about them.
3. Read `${CLAUDE_SKILL_DIR}/reference/project-file-rules.md`, draft
   the project CLAUDE.md from their answers plus the matching menu
   items, and hold it to the bar: at least one rule only this project
   could have, every named strand covered by a rule, a fact, or a
   stated reason it has neither. Show the draft, adjust, write it.
4. Read `${CLAUDE_SKILL_DIR}/reference/enforced-rules.md` and follow
   it: it covers the no-protected-data case, both file shapes, and the
   few sentences worth saying aloud.
5. Close in one message: the file paths that now exist, and that
   `/savanna-institute:configure-claude` runs a setup check or the full
   introduction any time. In the same breath, say a second set of
   adversarial eyes checks the new file before this ends, and that the
   conversation waits while it runs. Run the adversarial review
   dispatch from project-file-rules.md — files are the project file
   and, when one exists, the personal file, context is the named
   strands in three lines. Show what survives as a short diff, apply
   what they approve. On an explicit decline, or if either dispatch
   errors, done.
