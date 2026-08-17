# matema-fest-2026 — project notes for Claude

> **Справка по фактам сайта** (структура, деплой, `/weights`, `/pagespeed`, конвенции). Рабочий процесс на новых задачах — арк-дисциплина: вход Claude Code — корневой `../CLAUDE.md`; поведение Cowork — `../COWORK.md`; арки — `../ARKA.md`; история — `../zhurnal/SVODKI.md`.

Single-page festival site, deployed via GitHub Pages from `main`. Pushes go
live in ~60–90s.

- **Live URL:** https://d1-d57.github.io/matema-fest-2026-preview/
- **Repo:** https://github.com/d1-d57/matema-fest-2026-preview

## Structure

```
.
├── index.html                  # the entire site — HTML + inline <style> + inline <script>
├── quiz/                       # standalone quiz page «Фракталы в природе» → matema-fest.ru/quiz/
│   ├── index.html              # self-contained; images via IMG map → img/*.webp (not base64)
│   └── img/                    # 16 optimised webp (each <500 KB); no attribution on page (intentional)
├── assets/                     # PNG / WebP / JPG images referenced from index.html
├── scripts/
│   ├── pagespeed.sh            # PageSpeed Insights v5 → cleaned JSON + summary.md
│   └── weights.sh              # local weight report (Python + Pillow)
├── .claude/
│   ├── CLAUDE.md               # this file
│   └── commands/               # slash commands: /weights, /pagespeed, /check
├── .github/workflows/
│   └── post-deploy-check.yml   # auto-PageSpeed on every meaningful push to main
└── .pagespeed/                 # historical reports, committed to the repo
```

External dependencies (CDN — not in this repo):

- Google Fonts (Cormorant + JetBrains Mono — subsetted to 4 weights + 1)
- GSAP and Lenis from unpkg, deferred
- TimePad widget (lazy, behind a button)
- Yandex Maps (lazy, behind a button)

## Workflow reminders

When the user makes changes that **affect bytes shipped to the browser**:

- any change to `index.html` (especially CSS or `<script>` blocks)
- adds, replaces, or renames any file in `assets/`
- introduces a new `.css` or `.js` file

→ **Remind them to run `/weights` before committing.** That catches oversized
images and `> 500 KB` files before they hit `main`.

When the user pushes a **non-trivial deploy** (layout, scripts, fonts, large
media — not just text/copy fixes):

→ After the push, **suggest `/pagespeed` ~2 minutes later** to confirm no
regression. The GitHub Action also runs automatically and commits a report —
that is a backup, not a substitute.

When the user is iterating on **small text / copy / colour edits**, do not
nag about `/weights` — it would be noise.

## Conventions

- Commits are made directly to `main`. No PR workflow.
- Commit messages are short, imperative, lowercase prefix:
  `tracks: …`, `apollon: …`, `perf: …`, `data: …`, `chore: …`.
- The post-deploy workflow commits as `github-actions[bot]` with the message
  `chore: post-deploy pagespeed report`. Do not edit those commits manually.
- `.pagespeed/` history is kept in the repo on purpose — it's the
  performance journal.
