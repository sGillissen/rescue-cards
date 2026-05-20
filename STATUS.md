# Rescue Cards — Status

**Stand: 2026-05-20**

## Aktueller Stand
- ✅ Cloudflare Pages Deployment: **https://rescue-cards.pages.dev**
- Auto-Deploy bei Push auf `main`
- **37 Karten** in der App:
  - 12 PDF-Algorithmen (AML1 + AML2) mit Medikamenten-Dosierungen
  - 7 davon Hybrid mit Klinik-Block (Anaphylaxie, Schlaganfall, Krampfanfall, Hypoglykämie, Schock/Hypovolämie, ACS, Hypertens. Notfall)
  - 24 rein klinische Karten aus alter CSV (Schlaganfall, Vergiftung, SHT, Lungenödem, Lungenembolie, Pneumonie, COPD, Asthma, Verbrennung, Eklampsie etc.)
- Datenarchitektur:
  - `algorithms.yaml` (Inhalte, 37 Karten, editierbar ohne Code-Berührung)
  - `index.html` (~700 Zeilen Layout/CSS/Renderer, lädt YAML beim Start)
  - `bilder/` (Krankheitsbild-PNGs, in Karten verlinkt über `bilder:`)

## Karten-Schema (einheitlich)
Jede Karte hat:
- `id`, `title`, `categories[]`, `bilder[]`
- `definition` (Block oben, Info-Icon)
- `abcde` (Block, Stethoskop-Icon, A–E pro Buchstabe multi-line)
- `diagnose[]` (Block, Fragezeichen-Icon, Leitsymptome als erste Zeile)
- `keypoints[]`, `medikamente[]`, `reevaluation{}` (PDF-Algorithmus, optional)
- `bilder` (eingebettet zwischen Reeval und Maßnahmen)
- `massnahmen[]` (Block, Kreuz-Icon, als Chips)
- `einteilung` (Block, Layer-Icon)
- `dd` (Block, Waage-Icon, Differentialdiagnose)

## Offene Punkte
- [ ] Atem-Kreislaufstillstand Erwachsene + Kinder (anderes Flussdiagramm-Layout, braucht eigenes Karten-Format)
- [ ] CSV-ABCDE bei den 5 Hybrid-Karten (Krampfanfall, Hypoglykämie, Schock, ACS, Hypertens.) noch nicht in PDF-ABCDE gemergt — aktuell nur PDF-Werte angezeigt
- [ ] Inhalte review/finetune: einige CSV-Quellen waren kompakt geschrieben (z.B. Einteilung-Texte), Sven prüft und passt in `algorithms.yaml` an
- [ ] Verbrennung-Karte hat sehr dünne CSV-Daten → könnte ausgebaut werden
- [ ] Bilder-Galerie könnte besser werden (Lightbox-Zoom)
- [ ] README.md füllen

## Workflow Inhaltspflege
1. **GitHub-Web-Editor** (schnell, ohne Setup) — Stift bei `algorithms.yaml`, commit, autodeploy
2. **Lokal** (Cursor / VSCode) — `algorithms.yaml` editieren, `git push`
3. **Via Claude** — Im Chat sagen was geändert werden soll, ich editiere + pushe

YAML-Spickzettel:
- 2 Spaces Einrückung (keine Tabs)
- Multi-Line: `|-` + eingerückt
- Strings mit Sonderzeichen: in `'...'`
- Listen: `- Element` neue Zeile

## Technik
- Single-Page Vanilla HTML/CSS/JS
- Daten: `algorithms.yaml` (geladen via fetch + js-yaml CDN 4.1.0)
- Deployment: Cloudflare Pages (Git-Connect, Output `/`)
- Auto-Deploy bei Push auf `main`
