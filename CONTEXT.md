# Rescue Cards — Kontext

## Zweck
Notfallmedizin-Karten (Rettungsdienst, Notfallsanitäter) als mobile Web-App. Schnellzugriff auf Krankheitsbilder mit Klinik, Medikamenten-Algorithmen, Maßnahmen, Differentialdiagnose und Bildern. Ersetzt die alte „RescueCards V7.7" CSV-getriebene App, integriert Inhalte aus dem österreichischen Algorithmen-Buch (Arzneimittelliste 1 + 2).

## Stack
- Single-Page Vanilla HTML/CSS/JS (`index.html`, ~700 Zeilen)
- Datenhaltung: `algorithms.yaml` (37 Karten), geladen via js-yaml 4.1.0 CDN
- Bilder in `bilder/` (PNG/JPG aus alter App + neue)
- Cloudflare Pages Deployment

## Karten-Inhalte
**37 Karten gesamt:**
- 12 PDF-Algorithmen (Arzneimittelliste 1 + 2 zusammengeführt): Schwere Anaphylaxie, Allergische Reaktion, Schwellung Atemwege, Bronchospasmus, ACS, Hypertens. Notfall, Hypoglykämie, Hypovolämie/Schock, Übelkeit/Erbrechen, Krampfanfall, Fieberkrampf Kinder, Starke Schmerzen
- 5 davon Hybrid: PDF-Algorithmus + CSV-Klinik (Krampfanfall, Hypoglykämie, Schock, ACS, Hypertens.)
- 2 weitere Hybrid: Schlaganfall, Anaphylaxie
- 24 rein klinische Karten aus CSV: Lungenödem, Lungenembolie, Pneumonie, COPD, Asthma, Pseudokrupp, SHT, Bauchtrauma, Vergiftung, Hitze, Unterkühlung, Verbrennung, Ertrinken, Eklampsie, EUG, akutes Abdomen, etc.

## Karten-Schema (einheitliches Block-Layout)
Jede Karte besteht aus optionalen Blöcken in fester Reihenfolge:
1. **Definition** (Info-Icon) — kurzer Fließtext oben
2. **ABCDE** (Stethoskop-Icon) — pro Buchstabe konkrete Klinik-Werte (multi-line erlaubt)
3. **Diagnose** (Fragezeichen-Icon) — Leitsymptome + diagnostische Hinweise
4. **Keypoints** (Checkliste-Icon, optional) — Aktions-Liste aus PDF
5. **Medikamente** — grüne Boxen mit Dosierungstabelle, roter KI-Box, NW-Zeile; `{type: venenzugang}` als Separator
6. **Reevaluation** (Uhr-Icon) — Wiederholungs-Schemata, mehrere Notes möglich
7. **Bilder** — eingebettete Krankheitsbilder
8. **Maßnahmen** (Kreuz-Icon, optional) — als Chips (z.B. „15 l O₂", „Beine hoch", „NEF")
9. **Einteilung** (Layer-Icon, optional) — Klassifikation
10. **DD** (Waage-Icon, optional) — Differentialdiagnose-Liste

## Datenarchitektur — YAML
Inhalte leben in `algorithms.yaml`, das beim App-Start gefetched und mit js-yaml geparsed wird. Vorteile:
- Editierbar ohne JS-Kenntnisse (auch via GitHub-Web-Editor)
- Versioniert in Git
- Lesbar wie Markdown (Multi-Line via `|-`)
- Bei kaputter YAML zeigt App Fehlermeldung im UI

## Deployment
Cloudflare Pages (Git-Connect). URL: **rescue-cards.pages.dev**. Auto-Deploy bei Push auf `main`. Framework: None, Build leer, Output `/`. Wechsel von Workers (`*.workers.dev`) zu Pages erfolgte 2026-05-20 wegen Konsistenz mit anderen Projekten (sprachedirekt.pages.dev, stadtplan-graz.pages.dev).

## Quellen
- **PDF**: `Arzneimittelliste 2` (Sammel-PDF) + Einzel-PDFs für AML1-Algorithmen (Schwellung Atemwege, ACS, Bronchospasmus, Krampfanfall, Fieberkrampf, Schmerzen)
- **CSV**: Google Sheet aus alter App (32 Einträge, klinisch-symptomatische Krankheitsbild-Karten mit ABCDE-Befunden, Lagerung, O₂, DD, Bilder)
- Mapping CSV ↔ PDF in `MAPPING.md`

## Repo-Struktur
```
rescue-cards/
├── index.html         # Layout, CSS, Renderer (~700 Zeilen)
├── algorithms.yaml    # 37 Karten — DAS ist die Inhalts-Datei
├── bilder/            # 41 Krankheitsbild-PNGs/JPGs
├── index-v77.html     # alte App (Backup, weiterhin unter /index-v77.html erreichbar)
├── MAPPING.md         # CSV ↔ PDF Mapping-Tabelle
├── CONTEXT.md         # diese Datei
├── STATUS.md          # aktueller Stand + offene Punkte
└── README.md
```

## Wichtige Konventionen für YAML-Edits
- **2 Spaces Einrückung** (keine Tabs!)
- Multi-Line Strings mit `|-`:
  ```yaml
  A: |-
    Atemnot
    Stridor, Schwellung
  ```
- Strings mit Sonderzeichen in `'...'`: `definition: 'Schwere ...'`
- Listen: `- Element` jeweils neue Zeile
- Bilder: muss als Datei in `bilder/` existieren (Dateiname inkl. Endung)

## Nicht-Ziele
- Kein Backend, kein Auth, kein Login
- Keine Notfallruf-Funktion (kein Ersatz für Echtzeit-Algorithmus während eines Einsatzes — Lernkarte!)
- Keine medizinische Beratung — Tool für ausgebildetes Personal
