# НАВИГАТОР арки «kvyz-fraktaly»

## Адрес проекта
`/Users/ivanyakovlev/Documents/GitHub/matema-fest` (git-репо; деплой GitHub Pages → `main` → `matema-fest.ru`). Нужен для заходов Code; обновить при переносе.

## Концепция
Добавить на сайт фестиваля отдельную страницу-квиз о фракталах в природе — `matema-fest.ru/quiz/`. 9 вопросов в формате ЧГК (составитель — Николай Русскин), полноэкранная галерея: сцена на вопрос, крупная картинка + вопрос + варианты, таймер, разбор-оверлей, финал. Дизайн-система — как у основного сайта.

## Границы (anti-scope)
- Главную `index.html` и другие страницы НЕ трогаем — квиз standalone (ссылку с главной добавим отдельной задачей позже).
- Дизайн, тексты, логику квиза НЕ переделываем — они утверждены. Работа Code — только: разместить страницу по адресу, заполнить картинки, задеплоить.

## Указатели — места сайта
- `index.html` (корень) — эталон дизайн-системы: CSS-переменные (`--color-bg-dark #16140F`, `--color-accent #C89A3D` амбер, `--color-accent-deep #B8623C` терракота, `--text-main #ECE3D0`), шрифты Cormorant Garamond + JetBrains Mono + Golos Text. Квиз уже собран под них. НЕ править.
- `lectures/<имя>/index.html`, `gallery/index.html`, `singularnost/` — образцы подстраниц (папка + index.html). Квиз кладём так же: `quiz/index.html`.
- `.claude/CLAUDE.md` — факты сайта: деплой, конвенции коммитов (`tracks:`/`perf:`/`data:`/`chore:`), `/weights`, `/pagespeed`.
- `zhurnal/2026-07-09_kvyz-fraktaly/kvyz-source.html` — собранная в Cowork страница квиза (исходник; base64-картинки внутри, 16 слотов размечены `data-needs-image` + `need:`).

## Скиллы арки
`agentic-coding-session-brief` (заходы Code), `site-cross-device-audit` (перед публикацией HTML), `visual-design-review` (для Code — рендер→взгляд при вставке картинок).

## Процедуры
вход в сессию → `../../ARKA.md §3` · план → `PLAN.md` · хэндофф → `../../ARKA.md §6` · закрытие → `../../ARKA.md §7` · заход Code → `../../RUKOVODSTVO-zahodami.md` (канал — `kod_kvyz.md`).
