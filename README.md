# Talks

Public talks and presentations by Guillaume Moigneu, published via GitHub Pages.

**Live:** https://gmoigneu.github.io/talks/

## Structure

Each talk is a self-contained folder (reveal.js deck with bundled theme, fonts, and assets — no external dependencies). The root `index.html` is the landing page that links to each one.

```
talks/
├── index.html              # landing page
└── 2026-scd-masterclass/   # one folder per talk
    ├── index.html
    ├── lib/                 # bundled reveal.js + Upsun "Dispatch" theme
    └── resources/           # talk-specific assets (QR codes, images)
```

## Adding a talk

1. Drop a self-contained deck folder in the repo root (kebab-case, year-prefixed slug).
2. Add a `<a class="card">` entry to `index.html`.
3. Commit and push — Pages redeploys automatically.

## Local preview

```sh
python3 -m http.server 8000
# open http://localhost:8000/
```
