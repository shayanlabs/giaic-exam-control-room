# GIAIC Exam Control Room

A single-page (`index.html`) exam-prep Kanban board with 46 cards, each backed by an
English + Roman-Urdu study note shown in an in-page modal.

## Data flow

```
study-notes/*.md      (46 English notes, source of truth)
study-notes-ur/*.md    (46 Urdu notes, source of truth)
tools/notes-index.tsv  (id <-> en_file <-> ur_file <-> title — the lookup table)
        │
        │  node tools/notes.mjs build
        ▼
assets/js/notes-data.js      (English notes, keyed by card id)
assets/js/notes-data-ur.js   (Urdu notes, keyed by card id)
        │
        ▼
index.html: TASKS[] (line ~216, one entry per card: id, module, priority, title, keys)
            openNote(id, lang) (line ~343) looks up NOTES[id] or NOTES_UR[id] and
            renders note.title / note.html into the #noteOverlay modal.
```

Card ids follow a module prefix: `r*` Roles, `e*` Ecosystem, `l*` Loop Engineering,
`h*` Harness Engineering, `v*` Evals, `t*` Runtime, `w*` Web Agents, plus a few others
for local AI / marathon topics. `tools/notes-index.tsv` is the fast way to resolve any
id to its files and title — it's ~46 lines, cheap to read whole.

## Hard rules

- **Never grep or Read `assets/js/notes-data.js` / `assets/js/notes-data-ur.js`
  directly.** Each note is one JSON line, but the two files are still ~140KB each —
  a broad grep match dumps the whole line. Use `node tools/notes.mjs find <term>`
  (searches only the `.md` sources) or grep `study-notes/`/`study-notes-ur/` instead.
- **Never hand-edit the generated `notes-data*.js` files.** Edit the `.md` source in
  `study-notes/` or `study-notes-ur/`, then run `node tools/notes.mjs build` and
  commit the source + regenerated output together. GitHub Pages serves these as
  static files, so the generated output must stay committed (no build step at
  serve time).
- **Exclude `Archives/`** from searches — it holds untracked, stale standalone
  copies of earlier board versions, not the live app.

## Tools

```
node tools/notes.mjs build         # regenerate notes-data*.js + notes-index.tsv from *.md
node tools/notes.mjs check         # verify no drift between .md sources and committed output
node tools/notes.mjs find <term>   # grep .md sources only, print compact id/file:line hits
```

`tools/notes.mjs` is zero-dependency plain Node (no `package.json` by design).

## Markdown -> HTML conversion (in `tools/notes.mjs`)

The notes use a deliberately small markdown subset: `#`/`##`/`###` headings, `-`
bullets, `1.` numbered lists, `**bold**`. No tables, code fences, blockquotes, or
images. `#` sets the note title (numeric prefix like `1. ` is stripped); `##`/`###`
become `<h2>`/`<h3>`; a run of `-` lines becomes `<ul>`, a run of `N.` lines becomes
`<ol>` — even when it immediately follows a prose line with no blank line in
between; everything else in a block becomes one `<p>`. `**x**` becomes
`<strong>x</strong>`; bare `&` is escaped to `&amp;`; backticks and single
`*asterisks*` are left as literal characters (not converted to `<code>`/`<em>`).
