# kubaul/kubaul — warianty README

Piaskownica z 5 niezależnymi pomysłami na profil. Obejrzyj je, wybierz jeden (albo złóż hybrydę), potem podepnemy repo i przeniesiemy do `README.md`.

---

## Warianty

| # | plik | styl | czego używa |
|---|---|---|---|
| 1 | `README-1-neofetch.md` | czysty terminal / ASCII | zero zewnętrznych SVG — tylko markdown i ASCII |
| 2 | `README-2-minimalist.md` | brutalistyczny, minimalistyczny | `capsule-render` (jeden banner) + `activity-graph` |
| 3 | `README-3-cyberpunk.md` | synthwave dashboard, kolorowy | `capsule-render` + `typing-svg` + `skill-icons` + `readme-stats` + `streak-stats` + `activity-graph` + `profile-3d-contrib` + `snk` |
| 4 | `README-4-blog.md` | literacki, tekstowy | tylko `activity-graph` (żadnych badge'ów ani kart) |
| 5 | `README-5-dashboard.md` | karty danych, metrics-heavy | `skill-icons` + `profile-summary-cards` + `activity-graph` + `readme-stats/pin` + `snk` + `ghpvc` |

Każdy wariant to zupełnie inna decyzja projektowa — nie są to wersje tego samego. Wybierz ten, który bardziej opowiada o tobie niż pokazuje statystyki.

---

## Jak obejrzeć

Większość SVG to requesty do zewnętrznych serwisów (Vercel, demolab), więc podgląd wymaga internetu. Masz trzy sensowne opcje:

**(1) VS Code / Cursor — szybkie, ale nie 1:1**
```
otwórz plik → ⇧⌘V (markdown preview)
```
Większość obrazków się załaduje. Nie renderuje niektórych HTML-owych konstrukcji (`<picture>`, `srcset`).

**(2) `grip` — 1:1 z GitHubem**
```bash
pip install grip
cd ~/repositories/kubaul
grip README-3-cyberpunk.md
# otwiera http://localhost:6419 — identyczny render jak github.com
```
Używa API GitHuba do parsowania markdowna, więc co widzisz tu == co zobaczysz na profilu. Darmowe 60 requestów/h bez tokena.

**(3) Pchnąć do repo testowego na GitHubie**
Najpewniejsze, bo pokazuje też SVG generowane przez GitHub Actions (snake, 3D contrib). Za chwilę i tak będziemy pchać do `kubaul/kubaul` — można podejrzeć tam na dowolnym branchu.

---

## Co trzeba dostawić zanim trafi na profil

Niektóre widgety wymagają **GitHub Action** po stronie repo `kubaul/kubaul`. Bez tego SVG zwróci 404 i zobaczysz pusty kwadrat. Poniżej co dotyczy którego wariantu:

### snake eating contributions (warianty 3, 5)
URL: `raw.githubusercontent.com/kubaul/kubaul/output/github-contribution-grid-snake-dark.svg`
Wymaga: workflow `.github/workflows/snake.yml` używający [`Platane/snk`](https://github.com/Platane/snk), który co 24h generuje SVG i commitu je do brancha `output`.

### 3D contribution graph (wariant 3)
URL: `raw.githubusercontent.com/kubaul/kubaul/output/profile-3d-contrib/profile-night-rainbow.svg`
Wymaga: workflow używający [`yoshi389111/github-profile-3d-contrib`](https://github.com/yoshi389111/github-profile-3d-contrib). Podobny schemat — branch `output`.

### wszystkie inne widgety
Działają od razu — to są endpointy generujące SVG na żądanie.

**Kiedy będziemy pchać, przygotuję ci gotowy `.github/workflows/generate.yml` jeśli wybierzesz wariant 3 lub 5.**

---

## Uwagi dotyczące konkretnych wariantów

### Wariant 1 (neofetch)
- ASCII art to arch linux logo, przerobione. Jeśli chcesz inny symbol (np. apple/nixos/coffee cup), łatwo podmienić.
- Sekcja `~/.plan` to pożyczka z `finger .plan` z BSD — można tam wrzucić coś prawdziwego lub żartobliwego.
- Wariant jest celowo monochromatyczny; możesz dodać kolor przez inline HTML jeśli chcesz.

### Wariant 2 (minimalist)
- Tagline `"I build things. Then I rewrite them."` jest oparty na tym co widzę w twoich repo (taskmaster v0/v1/v2, linio/linio.v2, cli/cli.v2, find-my-way/find-my-way-temp) — zmień jeśli nie oddaje.
- Przycisk "hire me" to placeholder — albo podepnij (mailto:, linkedin) albo usuń.

### Wariant 3 (cyberpunk)
- Najbardziej agresywny wizualnie. Ryzyko: przestaje działać jak widget padnie.
- Synthwave theme jest oficjalny w `readme-stats` (nie custom).
- Jeśli chcesz mniej neonu, podmień palette — `ff006e/8338ec/3a86ff` to Pantone-like synthwave. Alternatywy: `00ff9f/00b8ff/001eff` (outrun), `f72585/7209b7/3a0ca3` (vapor).

### Wariant 4 (blog)
- Nie ma tu ani jednego badge'a. To świadoma decyzja.
- Cytat z Saint-Exupéry'ego możesz wyrzucić — oryginał pochodzi z *Wiatr, piasek i gwiazdy*, jest kliszą wśród devów. Dobra alternatywa: Dijkstra, Knuth, Hoare, albo coś nie-technicznego.
- Link do `FsCopilot` zakłada że jest public — jeśli nie, usuń.

### Wariant 5 (dashboard)
- `komarev.com/ghpvc` to licznik odwiedzin — większość ludzi traktuje go jako vanity metric. Zostaw albo wyrzuć.
- `utcOffset=2` w productive-time to placeholder dla CET. W lecie zmień na 2, w zimie na 1, albo usuń (default UTC).
- `profile-summary-cards` używa theme `github_dark` — jest też `solarized`, `nord_bright`, `dracula`, `vue`.

---

## Decyzja do podjęcia

Który kierunek bliżej tego jak się widzisz?

1. **neofetch** — dla ludzi którzy chcą pokazać że są z terminala, nie z photoshopa
2. **minimalist** — dla ludzi, którym zależy na jednym mocnym statement zamiast listy skilli
3. **cyberpunk** — dla ludzi, którzy traktują profil jak portfolio wizualne
4. **blog** — dla ludzi, którzy chcą pisać, nie pokazywać metryk
5. **dashboard** — dla ludzi, którzy lubią patrzeć na wykresy

Jak wybierzesz, dociągniemy brakujące kawałki (linki, kontakty, Actions do snake'a itp.) i pchniemy do `github.com/kubaul/kubaul`.
