# Philosophical Dictionary — Mario Bunge

A fast, elegant, single-file web reader for Mario Bunge's *Philosophical Dictionary* (Enlarged Edition): **1,441 entries**, full-text search, clickable cross-references, rendered mathematics, and a built-in annotation system, all in one self-contained HTML file with no build step and no dependencies.

Open `bunge_dictionary.html` in any modern browser and start reading.

---

## Features

### Reading and navigation
- **Complete lexicon**: 1,441 entries from *A = A* to *ZERO*, indexed under 24 letters (A–W and Z).
- **Index sidebar** listing every entry, with sticky letter headings and the current entry highlighted.
- **Letter grid on the home page** for jumping straight to the first entry of any letter.
- **Previous / next** links at the bottom of every entry.
- **Random entry** button for browsing by serendipity.
- **Clickable cross-references**: the ↑ arrows from the printed dictionary are live links (about 2,000 of them across the book).
- **Permalinks**: every entry has a stable address such as `bunge_dictionary.html#e0627`, so you can bookmark or share any entry.

### Search
- Searches **headwords and full entry text** across the whole dictionary.
- Results are ranked: exact headword match, then headword prefix, then headword contains, then body-text matches.
- Matches are highlighted in context snippets, and the top 150 results are shown.
- Multi-word queries match entries containing all the words.

### Annotations
Select any text inside an entry and a small toolbar appears:

| Tool | Effect |
|---|---|
| **Highlight** | Marker-style highlight |
| **Underline** | Straight underline |
| **Zigzag** | Wavy underline |
| **Comment** | Attach a written note to the selection |

- Six preset colours plus a custom colour picker.
- Click an existing annotation to edit, recolour, or delete it.
- The **✎ Notes** button opens a page listing every annotation you have made, with links back to the entries.
- Annotations are saved in your browser's `localStorage` (key `bd-ann`). They never leave your device.

### Typography and design
- Book-like page layout with running heads, entry numbers, ornaments, and a boxed drop-letter for each entry.
- Typeset in **EB Garamond** and **IM Fell English** (loaded from Google Fonts, with Georgia as a fallback).
- **Light and "lamplight" (dark) themes**, following your system setting by default, with a manual toggle (◐).
- **MathML** for formulas (for example ∀x (x = x)), rendered natively by the browser.
- Embedded figures and tables where the original entries contain them.
- Responsive layout with a collapsible index on phones and safe-area support for notched devices.

---

## Keyboard shortcuts

| Key | Action |
|---|---|
| `/` | Focus the search box |
| `Enter` (in search) | Open the top result |
| `Esc` (in search) | Clear the search and return to the entry |
| `Esc` (with annotation toolbar open) | Dismiss the toolbar |

---

## Getting started

### Run locally
1. Download or clone this repository.
2. Open `bunge_dictionary.html` in your browser.

That's it. There is nothing to install, build, or serve.

### Host on GitHub Pages
1. Rename `bunge_dictionary.html` to `index.html` (or link to it directly).
2. In your repository, go to **Settings → Pages**, choose your branch and the root folder, and save.
3. Your dictionary will be available at `https://<your-username>.github.io/<repo-name>/`.

> **Offline use:** the dictionary works fully offline. Only the web fonts come from Google Fonts; without a connection the page falls back to Georgia/serif automatically.

---

## How it works

Everything lives in one HTML file (about 2.3 MB):

- **Data**: a JSON array named `DATA` embedded in a `<script>` block. Each entry has four fields:

  | Field | Meaning |
  |---|---|
  | `i` | Stable entry ID, e.g. `e0627` |
  | `h` | Headword |
  | `t` | Plain-text version of the entry, used for search and snippets |
  | `b` | HTML body, including cross-reference links, MathML, tables, and figures |

- **Routing**: hash-based (`#e0627`, `#notes`), so it works from a plain file or any static host.
- **Figures**: embedded directly in the file as `data:` URIs.
- **Annotations**: stored as character offsets within each entry's body text, re-applied each time an entry is opened.
- **Vanilla JavaScript and CSS**: no frameworks, bundlers, or package manager.

### Editing or extending the content
To correct a typo or add an entry, edit the corresponding object in the `DATA` array. Keep `t` (plain text) in sync with `b` (HTML) so search stays accurate, and give any new entry a unique `i`. Cross-references use the form `<a href="#e0627" class="xref">…</a>`.

---

## Privacy

There is no server, no analytics, and no tracking. Your annotations are stored locally in your browser. Clearing site data for the page will delete them, and they are not synced between browsers or devices.

---

## Browser support

Any current version of Chrome, Edge, Firefox, or Safari. MathML rendering requires a reasonably recent browser.

---

## License and content notice

The application code (HTML, CSS, JavaScript) is released under the license in the [`LICENSE`](LICENSE) file.

The dictionary text and figures are the work of **Mario Bunge** and remain the property of their respective copyright holders. They are **not** covered by the code license. Please make sure you have the right to redistribute the text before sharing or publishing this repository.

---

## Acknowledgments

- **Mario Bunge** (1919–2020), whose systematic philosophy and *Philosophical Dictionary* this reader is built to serve.
- Fonts: [EB Garamond](https://fonts.google.com/specimen/EB+Garamond) and [IM Fell English](https://fonts.google.com/specimen/IM+Fell+English) via Google Fonts.
