# Rescue Cards — Kontext

## Zweck
Notfallmedizin-Karten (Rettungsdienst) als mobile Web-App. Schnellzugriff auf Krankheitsbilder mit Maßnahmen, Symptomen, Bildern.

## Stack
- Single-File Vanilla HTML/CSS/JS (`index.html`)
- PapaParse (CDN) für CSV-Import
- Bilder in `bilder/` (PNG/JPG, Krankheitsbild-bezogen)
- Aktuelle Version: **V7.7 Full Stable**

## Kategorien
Neuro (lila) · Meta (orange) · Resp (grün) · Cardio (rot) · Trauma (blau) · Other (grau)

Zusätzliche Farb-Codes Spalten A–E: AB=blau, C=rot, D=gelb, E=grün

## Features (aus Code erkennbar)
- Sticky Header mit Suchfeld + Side-Menu
- Filter-Chips (horizontal scrollbar) inkl. Reset
- Karten mit klappbarem Header
- Mobile-optimiert (viewport locked, kein User-Zoom)

## Status der Entwicklung
Bisher direkt auf GitHub editiert (`Update index.html` Commits). Lokale Entwicklung beginnt jetzt.

## Repo
- GitHub: [sGillissen/rescue-cards](https://github.com/sGillissen/rescue-cards)
- Lokal: `/Users/sven/Desktop/Claude-Workspace/Code/rescue-cards/`

## Deployment
Cloudflare Pages (Git-Connect). URL: **rescue-cards.pages.dev**. Auto-Deploy bei Push auf `main`. Framework: None, Build-Command leer, Output `/`.

⚠️ Output ist Root → CONTEXT.md, STATUS.md, README.md sind öffentlich erreichbar (z.B. `rescue-cards.pages.dev/STATUS.md`). Nicht sicherheitskritisch, aber bei Bedarf Site in `public/`-Ordner verschieben und das als Output setzen.
