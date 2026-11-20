# bibliography

`references.bib` is the one bibliography of all the ModelFlow books
(`https://ibhansen.github.io/<book>/`). This is the master: edit it here, nowhere else.

The repo is `IbHansen/bibliography` on GitHub (public); locally it is
`C:\mfmodeller\modelflow_material\Litteratur\references`.

## How the books get it

- **On GitHub Pages.** The book repos do not hold a copy. Their workflow
  (`.github/workflows/deploy.yml`, master in `C:\deploy\bookcontrol\shared`) downloads
  `https://raw.githubusercontent.com/IbHansen/bibliography/main/references.bib` just
  before `jupyter book build`. The repo must therefore stay public, and the file must
  stay at the root of `main`. If the download fails, the build fails (rather than
  publishing a book without its references).
- **Locally.** `publish.bat` copies the file into each book folder (kind `book`,
  `shared:` in `C:\deploy\publish\publish.yml`), so `book`, `book pdf` and `book md`
  work offline. The copy is ignored by git in the book repos.

## After a change

1. Commit and push this repo.
2. Rebuild the books whose references changed: Actions → Build and Deploy → Run
   workflow in each book repo (or push something to it). A book is not rebuilt by a
   push here.
3. Locally: `publish.bat book` (or restart a running `book` live server).

## Conventions

- Keys as Zotero makes them: `author_firstwordoftitle_year`. Never two entries for one
  work; Zotero's `-1` copies go.
- `doi = {10....}` without `https://doi.org/`; `url` only when there is no DOI or it
  points somewhere better.
- World Bank and similar working papers are `@techreport` (`institution`, `type`,
  `number`), edited volumes have `editor`, not `author`.
- MyST (Jupyter Book 2) reads the file, so keep it plain BibTeX: one `field = {...},`
  per line.
