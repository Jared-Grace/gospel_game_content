# Gospel game content

Every sermon and conversation the game has written, kept in full history.

The game stores one copy of each file and forgets what it said before, so an
edit that turns out wrong has nothing to be restored from. This repo keeps every
version of every sentence, which is the difference between a copy and a backup.

## What is here

- `function/g_sermon_generate_upload/uploads/<CHAPTER>.json` — a sermon for one
  chapter of the Bible, generated.
- `function/g_sermon_write_upload/uploads/<CHAPTER>.json` — a sermon that a
  person has since edited by hand.
- `function/g_objection_generate_upload/uploads/<CHAPTER>.json` — objections an
  unbeliever might raise, with the passages that answer them.
- `function/g_verify_status/`, `function/g_verify_approval/` — which content has
  been read over and approved.
- `generations.json` — the version each file was at when it was last copied
  down. It is how a pass knows which files moved.

### `original/`

The same content as first written, before anyone edited it.

Editing happens in a browser, which can reach the store but not the machine that
generated the text. So for a chapter someone has rewritten, the generating
machine still holds the wording it was changed from, and nothing else does.
`original/` is that copy.

For most chapters the two agree exactly. Where they differ, `function/` has the
newer wording and `original/` has the older. Neither is simply the right one —
which you want depends on what you are asking.

`original/app_g_bible/` is the editing screen's own working copy: for each
passage, the English text, the preaching lines, and the Greek or Hebrew it was
translated from.

Chapter codes are three letters and two digits: `ROM01` is Romans 1, `1JN03` is
1 John 3.

Files are written out plainly here even where they are stored squeezed small,
so that the history shows which sentence changed rather than one unreadable line
changing all at once.

## How it is kept

A backup pass runs every six hours. It asks the store what version each file is
at, fetches only the ones that moved, and commits.
