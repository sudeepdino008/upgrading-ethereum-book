# Whole book EPUB

This builds the whole text as a single EPUB file using `pandoc`. You don't need any of the usual installation to do this (no node, npm, etc.).

## Pre-requisites

Only `pandoc` is needed. Get a copy from the [pandoc repo](https://github.com/jgm/pandoc/releases/) and install it, or use your package manager:

```
# macOS
brew install pandoc

# Debian/Ubuntu
sudo apt install pandoc
```

Unlike the [PDF pipeline](../pdf/README.md), no LaTeX installation is required. Maths is converted to MathML, and the SVG diagrams are embedded as-is.

## Building the EPUB

Run the script at _bin/epub/make\_epub_:

```
bin/epub/make_epub src/book.md
```

or, equivalently:

```
npm run epubit
```

The output appears as _book.epub_ in your current directory.

## Notes

  - The table of contents is built three levels deep (parts, chapters, and sections).
  - Maths is rendered as MathML, which is part of the EPUB3 standard. Reader support varies: Apple Books and Calibre handle it well; older Kindle devices may not. If you need a Kindle format, convert the EPUB with [Calibre](https://calibre-ebook.com/) (`ebook-convert book.epub book.azw3`).
  - Metadata (title, author, language, licence) is set from the script, with the edition taken from the current git branch name.
