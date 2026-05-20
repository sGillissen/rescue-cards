# Rescue Cards — Daten-Mapping CSV ↔ PDF

**Stand: 2026-05-20**

Quelle CSV: [Google Sheet, 32 Einträge](https://docs.google.com/spreadsheets/d/e/2PACX-1vQBMZadFA7O2nMGOeaUcnEZz5MuNW2WeHdmSU_m94SI9VDdUiI8AfsJXJ-KAhtxv0zRZ6pkRIM_jj1X/pubhtml)
Quelle PDF: `Desktop/arzneimittelliste-2.pdf` + `Desktop/algorithmen.html` (AML1+AML2 zusammengeführt)

Spalten:
- **Status:** ✅ klarer Treffer · ⚠️ unklar/Teil-Treffer · ➕ neuer Eintrag (nur PDF) · 🔹 bleibt nur CSV
- **Endgültiger Karten-Name** = Vorschlag, anpassbar

| # | Endgültiger Karten-Name | CSV-Eintrag (Klinik) | PDF-Algorithmus (Medikamente) | Status | Kategorie |
|---|---|---|---|---|---|
| 1 | Schwere anaphylaktische Reaktion | Anaphylaxie (meta) | AML1 + AML2 Schwere Anaphylakt. Reaktion | ✅ | Allergie/Resp/Cardio |
| 2 | Allergische Reaktion (leicht) | — | AML2 Allergische Reaktion | ➕ | Allergie |
| 3 | Schwellung obere Atemwege | Atemnot Schwellung/Verlegung (resp) | AML1 Schwellung obere Atemwege | ✅ | Resp |
| 4 | Pseudokrupp | Pseudokrupp (resp) | — | 🔹 | Resp |
| 5 | Akuter Bronchospasmus / Asthma | Asthma bronchiale (resp) | AML1 Akuter Bronchospasmus | ✅ | Resp |
| 6 | COPD | COPD (resp) | AML1 Akuter Bronchospasmus | ✅ | Resp |
| 7 | Atemnot (Dyspnoe) – Übersicht | Atemnot Dyspnoe (resp) | — | 🔹 | Resp |
| 8 | Lungenödem | Lungen-Ödem (resp) | — | 🔹 | Resp/Cardio |
| 9 | Lungenembolie | Lungen-Embolie (resp) | — | 🔹 | Resp/Cardio |
| 10 | Pneumonie | Lungen-Entzündung (resp) | — | 🔹 | Resp |
| 11 | Hyperventilation / Tetanie | Hyperventil. tetanie (resp) | — | 🔹 | Resp |
| 12 | Spannungspneumothorax | Spannungspneu (resp) | — | 🔹 | Resp/Trauma |
| 13 | Akutes Koronarsyndrom (ACS) | ACS (cardio) | AML1 ACS + AML2 ACS i.v. | ✅ | Cardio |
| 14 | Hypertensiver Notfall | Hypertensiver Notfall (cardio) | AML2 Hypertensiver Notfall | ✅ | Cardio |
| 15 | Schock / Hypovolämie | Schock (cardio) | AML2 Hypovolämie | ✅ | Cardio |
| 16 | Kollaps / Synkope | Kollaps (cardio) | — | 🔹 | Cardio/Neuro |
| 17 | Atem-Kreislaufstillstand Erwachsene | — | AML2 Atem-Kreislaufstillstand Erw. | ➕ | Reanimation |
| 18 | Atem-Kreislaufstillstand Kinder | — | AML2 Atem-Kreislaufstillstand Kind | ➕ | Reanimation |
| 19 | Schlaganfall | Schlaganfall (neuro) | — | 🔹 | Neuro |
| 20 | Zerebraler Krampfanfall | Krampfanfall (neuro) | AML1 Bestehender zereb. Krampfanfall | ✅ | Neuro |
| 21 | Fieberkrampf (Kinder) | — | AML1 Fieber mit Krampfanfall Kinder | ➕ | Neuro/Päd |
| 22 | Hypoglykämie | Diabetes Hypoglykämie (meta) | AML2 Hypoglykämie | ✅ | Meta/Neuro |
| 23 | Hyperglykämie | Diabetes Hyperglykämie (meta) | — | 🔹 | Meta |
| 24 | Exsikkose | Exsikkose (meta) | — | 🔹 | Meta |
| 25 | Vergiftung / Intoxikation | Vergiftung (meta) | — | 🔹 | Sonstiges |
| 26 | Übelkeit und Erbrechen | — | AML2 Übelkeit und Erbrechen | ➕ | Sonstiges |
| 27 | Starke Schmerzen | — | AML1 + AML2 Starke Schmerzen | ➕ | Schmerz |
| 28 | SHT (Schädel-Hirn-Trauma) | SHT (trauma) | — | 🔹 | Trauma/Neuro |
| 29 | Wirbelsäulentrauma | Wirbelsäulentrauma (trauma) | — | 🔹 | Trauma |
| ~~30~~ | ~~Nicht-traumat. Rückenschmerzen~~ | weggelassen | — | — | — |
| 31 | Bauchtrauma | Bauchtrauma (trauma) | — | 🔹 | Trauma |
| 32 | Brustkorbverletzung | Brustkorb Verletzung (trauma) | — | 🔹 | Trauma |
| 33 | Akutes Abdomen | akutes Abdomen (other) | — | 🔹 | Sonstiges |
| 34 | Hitzenotfall | Hitze (other) | — | 🔹 | Sonstiges |
| 35 | Unterkühlung | Unterkühlung (other) | — | 🔹 | Sonstiges |
| 36 | Verbrennung | Verbrennung (other) | — | 🔹 | Trauma |
| 37 | Ertrinken | Ertrinken (other) | — | 🔹 | Resp |
| 38 | Extrauteringravidität | ExtraUterin-Gravidität (other) | — | 🔹 | Sonstiges |
| 39 | Schwangerschaftshypertonie / Eklampsie | Schwangerschaft (other) | — | 🔹 | Sonstiges |
| 40 | Kinder-Dosierungen (Übersicht) | — | AML2 Anhang Kinder-Dosierungen | ➕ | Übersicht |

## Zahlen
- **Gesamt:** ~40 Karten
- ✅ Echte Hybride: 7
- ⚠️ Unklare Teil-Treffer: 4 (→ entscheiden ob 1 Karte oder 2)
- ➕ Nur PDF (neu): 8
- 🔹 Nur CSV (bleibt klinisch): 21

## Karten-Struktur (Hybrid)
Jede Karte hat optional:
1. **Klinik-Block** (aus CSV): Definition, Leitsymptome, ABCDE-Befund, Lagerung, O₂, Absaugen, DD, Bilder
2. **Algorithmus-Block** (aus PDF): ABCDE-Befund (kann mergen), Diagnose, Keypoints, Medikamente, Reevaluation

Bei reinen CSV- oder PDF-Karten fehlt der jeweils andere Block.

## Offene Punkte (zum Reviewen)
- [ ] Sind die 4 ⚠️-Zuordnungen so OK?
  - COPD → eigene Karte oder mit Bronchospasmus mergen?
  - Schock vs. Hypovolämie → eine Karte oder zwei?
  - Rückenschmerzen / Bauchtrauma / Brustkorb → eigene Klinik-Karten, "Starke Schmerzen" als getrennter Medikamenten-Algorithmus?
  - Schwangerschaftshypertonie/Eklampsie → eigene Karte oder Verweis auf Hypertens. Notfall?
- [ ] Karten-Reihenfolge: alphabetisch oder gruppiert nach Kategorie?
- [ ] Bilder aus `bilder/`: pro Karte zuordnen (aus CSV-Spalte `picture` + `explanation_img`)?
- [ ] Atem-Kreislaufstillstand-Layout: braucht ein anderes Karten-Format (Flussdiagramm Schockbar/Nicht-Schockbar) — separat planen
