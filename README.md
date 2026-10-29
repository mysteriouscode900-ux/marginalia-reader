# Marginalia: EPUB/PDF Reader + Book Journal

A lightweight, local-first web app starter for reading and reflecting on books. It is designed to run on a laptop and can be installed as a PWA in supported browsers.

## Run it

**Recommended:** use Python's built-in local web server. You do not need to know Python.

1. Unzip the project.
2. Install Python if it is not already installed.
3. Open a terminal/command prompt in this folder.
4. Run `python -m http.server 8000`
5. Open `http://localhost:8000` in Chrome or Edge.
6. Click **Add books** and choose EPUB/PDF files.

On Windows, you can also create a file named `Start Marginalia.bat` with:
```bat
@echo off
cd /d "%~dp0"
python -m http.server 8000
pause
```
Double-click it, then open the URL above.

To install it like an app in Chrome/Edge, open the local URL and use the browser menu's **Install app** option if offered. For a phone, host it on a trusted HTTPS static host, or use a local Android wrapper in a later build.

## What's implemented in this starter

- Multi-file EPUB/PDF import, title-from-filename fallback, and local IndexedDB storage.
- EPUB metadata extraction when the EPUB engine is available.
- Library search, reading-list status filtering, sorting, and grid/list toggle.
- EPUB reading with chapter navigation and remembered CFI position.
- PDF page rendering, page navigation, and a basic text-content search.
- Save selected text as highlights, quotes, notes, or vocabulary entries.
- Per-book journal with autosaving summary, notes, review, takeaways, reading log, and rating.
- Global saved-passage list with search/filter, edit-note, copy, delete, and open-book actions.
- Light/dark/sepia appearance, adjustable EPUB text size and line spacing.
- JSON backup/restore of book metadata, journals, annotations, vocabulary and settings.
- Markdown journal export, CSV annotations export, and TXT quote/vocabulary export.
- Local-only storage for the library and journal data.

## Important limitations (not hidden)

This is a functional starter, not a fully QA-certified commercial app.

- EPUB.js and PDF.js are loaded from public CDNs. The reader engines need an internet connection the first time unless you vendor the library files locally. The library data and journal remain local.
- Browser file access is intentionally permission-based: you choose files. Browsers do not permit unrestricted silent folder scanning.
- Browser support for EPUB text selection/highlight anchoring varies. This starter saves selected passages and their approximate reading location, but does **not yet re-render highlights inline after reopening the book**.
- PDF highlights are saved as text records, not embedded into the PDF file. Scanned/image-only PDFs need OCR, which is not included.
- PDF text search currently scans up to the first 200 pages and reports matching page numbers.
- The JSON backup does not embed book files. Keep your originals separately and re-import them after restoring if needed.
- Metadata parsing for PDFs and cover-image extraction are limited. Covers are generated from book titles.
- Automatic background folder scanning, sync across devices, advanced vocabulary definitions/pronunciation, robust chapter-specific EPUB annotation anchoring, reading streaks, and complete accessibility testing are not implemented yet.

## Project structure

- `index.html`: app shell and reader UI
- `styles.css`: responsive visual design and themes
- `app.js`: IndexedDB, library, reader, annotations, journal, backup/export
- `manifest.json`: installable web app metadata
- `sw.js`: basic app-shell service worker

## Data safety

The app does not upload books, notes, or journal entries. Your browser stores the data locally. Export a backup before clearing browser data or uninstalling/resetting the browser. Treat the backup file as private because it contains your personal notes.
