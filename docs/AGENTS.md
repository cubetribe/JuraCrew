# Legal-GodMode Agenten-Dokumentation

Diese Datei beschreibt alle verfügbaren Spezial-Agenten, ihre Aufgaben, Model-Zuordnung und Einsatzgebiete.

---

## Übersicht

| Agent | Model | Expertise | Primäre Aufgabe | Token-Intensität |
|-------|-------|-----------|-----------------|------------------|
| @anwalt-zivilrecht | Opus 4.5 | BGB, HGB, ZPO | Zivilrechtliche Mandatsbearbeitung | Hoch |
| @anwalt-strafrecht | Opus 4.5 | StGB, StPO | Strafrechtliche Mandatsbearbeitung | Hoch |
| @anwalt-verwaltung | Opus 4.5 | VwGO, VwVfG | Verwaltungsrechtliche Mandatsbearbeitung | Hoch |
| @gutachter | Opus 4.5 | Alle Rechtsgebiete | Tiefe Subsumtion, Gutachten | Sehr Hoch |
| @recherche | Sonnet 4.5 | Alle Rechtsgebiete | Gesetz/Rechtsprechung/Literatur | Mittel |
| @formular | Sonnet 4.5 | Alle Rechtsgebiete | Schriftsätze, Verträge, Vorlagen | Niedrig |
| @mandatsmanager | Sonnet 4.5 | Kanzleiorganisation | Fristen, Aktenführung | Niedrig |

---

## 1. @anwalt-zivilrecht (Opus 4.5)

### Expertise
- Bürgerliches Recht (BGB)
- Handelsrecht (HGB)
- Zivilprozessrecht (ZPO)
- Vertragsrecht
- Deliktsrecht
- Familienrecht
- Erbrecht

### Primäre Aufgaben
- Mandatsanalyse und Fallprüfung
- Anspruchsgrundlagen identifizieren
- Erfolgsaussichten bewerten
- Prozessstrategie entwickeln
- Klage-/Antragsschriften vorbereiten

### Typische Inputs
```
"Neues Mandat: Kaufpreiszahlung § 433 BGB"
"Quick Check: Schadensersatz aus Verkehrsunfall"
"Prozessstrategie: Mietstreit - Nebenkosten"
```

### Output-Format
```markdown
# Mandatsanalyse - [Mandats-Nr.] - [Datum]

## I. Sachverhalt
[Anonymisierter Sachverhalt]

## II. Rechtliche Würdigung

### A. Anspruchsgrundlage
1. § XYZ BGB
   a) Tatbestand
      aa) Definition
      bb) Subsumtion
   b) Rechtsfolge

### B. Erfolgsaussichten
[Bewertung mit Fundstellen]

## III. Handlungsempfehlung
[Nächste Schritte]

## IV. Fristen
- [Frist 1]: [Datum]
- [Frist 2]: [Datum]

---
Fundstellen:
- BGH NJW 2024, 123
- OLG München BeckRS 2024, 456
- Palandt/Grüneberg § 433 Rn. 12
```

### Workflow-Integration
```
@recherche → @anwalt-zivilrecht → @formular → @mandatsmanager
```

---

## 2. @anwalt-strafrecht (Opus 4.5)

### Expertise
- Strafgesetzbuch (StGB)
- Strafprozessordnung (StPO)
- Nebenstrafrecht
- Strafzumessung
- Verteidigungsstrategien

### Primäre Aufgaben
- Strafbarkeitsanalyse
- Tatbestandsprüfung
- Rechtswidrigkeit/Schuld prüfen
- Verteidigungsstrategie entwickeln
- Strafzumessung bewerten

### Typische Inputs
```
"Neues Mandat: Betrug § 263 StGB"
"Quick Check: Körperverletzung § 223 StGB"
"Verteidigungsstrategie: Fahrlässige Tötung"
```

### Output-Format
```markdown
# Strafrechtsanalyse - [Mandats-Nr.] - [Datum]

## I. Sachverhalt
[Anonymisierter Sachverhalt]

## II. Strafbarkeit

### A. § XYZ StGB
1. Tatbestand
   a) Objektiver Tatbestand
      aa) Tatobjekt
      bb) Tathandlung
      cc) Taterfolg
      dd) Kausalität
   b) Subjektiver Tatbestand
      aa) Vorsatz/Fahrlässigkeit
2. Rechtswidrigkeit
3. Schuld

### B. Strafzumessung
[§ 46 StGB Faktoren]

## III. Verteidigungsstrategie
[Empfohlene Strategie]

## IV. Fristen
- Akteneinsicht: [Datum]
- Stellungnahme: [Datum]
- Hauptverhandlung: [Datum]

---
Fundstellen:
- BGH NStZ 2024, 123
- BVerfG NJW 2024, 456
- Fischer StGB § 263 Rn. 12
```

### Workflow-Integration
```
@recherche → @anwalt-strafrecht → @formular → @mandatsmanager
```

---

## 3. @anwalt-verwaltung (Opus 4.5)

### Expertise
- Verwaltungsgerichtsordnung (VwGO)
- Verwaltungsverfahrensgesetz (VwVfG)
- Baurecht
- Ausländerrecht
- Sozialrecht

### Primäre Aufgaben
- Bescheidprüfung
- Widerspruchsstrategie
- Klagebegründung
- Ermessensabwägung
- Verfahrensrecht prüfen

### Typische Inputs
```
"Neues Mandat: Widerspruch gegen Baugenehmigung"
"Quick Check: Aufenthaltstitel abgelehnt"
"Klagestrategie: ALG-II Bescheid"
```

### Output-Format
```markdown
# Verwaltungsrechtsanalyse - [Mandats-Nr.] - [Datum]

## I. Sachverhalt
[Anonymisierter Sachverhalt + Bescheid]

## II. Rechtmäßigkeit des Bescheids

### A. Formelle Rechtmäßigkeit
1. Zuständigkeit
2. Verfahren
3. Form

### B. Materielle Rechtmäßigkeit
1. Rechtsgrundlage
2. Tatbestand
3. Rechtsfolge/Ermessen

## III. Rechtsschutz

### A. Widerspruch
[§§ 68 ff. VwGO]

### B. Anfechtungsklage
[§ 42 Abs. 1 VwGO]

## IV. Handlungsempfehlung
[Nächste Schritte]

## V. Fristen
- Widerspruchsfrist: [Datum]
- Klagefrist: [Datum]

---
Fundstellen:
- BVerwG NVwZ 2024, 123
- OVG München BeckRS 2024, 456
- Kopp/Schenke VwGO § 42 Rn. 12
```

### Workflow-Integration
```
@recherche → @anwalt-verwaltung → @formular → @mandatsmanager
```

---

## 4. @gutachter (Opus 4.5)

### Expertise
- Alle Rechtsgebiete
- Tiefe Subsumtion
- Gutachtenstil
- Fallanalyse
- Rechtliche Abwägungen

### Primäre Aufgaben
- Rechtsgutachten erstellen
- Komplexe Subsumtion durchführen
- Meinungsstreit darstellen
- Gegenmeinungen entkräften
- Ausführliche Fallanalyse

### Typische Inputs
```
"Gutachten: Verkehrsunfall § 823 BGB - Anscheinsbeweis"
"Subsumtion: Betrug § 263 StGB - Täuschungshandlung"
"Rechtliche Bewertung: Mietminderung § 536 BGB"
```

### Output-Format
```markdown
# Rechtsgutachten - [Thema] - [Datum]

## Fragestellung
[Zu klärende Rechtsfrage]

## Gutachten

### I. Anspruchsgrundlage/Strafbarkeit
[§ XYZ BGB/StGB/VwGO]

### A. Tatbestand
1. [Tatbestandsmerkmal 1]
   a) Definition
      aa) Literatur
      bb) Rechtsprechung
   b) Subsumtion
      aa) Sachverhaltsmerkmale
      bb) Rechtliche Würdigung
      cc) Zwischenergebnis
   c) Meinungsstreit
      aa) Ansicht 1 (h.M.)
      bb) Ansicht 2 (a.A.)
      cc) Stellungnahme

2. [Tatbestandsmerkmal 2]
   [...]

### B. Rechtsfolge
[...]

## Ergebnis
[Zusammenfassung]

---
Fundstellen:
- [Mindestens 5-10 Quellen]
- BGH/BVerfG Urteile
- OLG/OVG Urteile
- Kommentare/Lehrbücher
```

### Workflow-Integration
```
@recherche → @gutachter → @formular
```

---

## 5. @recherche (Sonnet 4.5)

### Expertise
- Gesetzesrecherche
- Rechtsprechungsrecherche (BGH, BVerfG, OLG, etc.)
- Literaturrecherche (Kommentare, Lehrbücher)
- Aktuelle Rechtsentwicklungen

### Primäre Aufgaben
- Fundstellen finden
- Rechtsprechung zusammenfassen
- Meinungsstand darstellen
- Gesetzesänderungen identifizieren

### Typische Inputs
```
"Recherche: § 433 BGB Rechtsprechung 2024"
"Recherche: BGH Urteile zu § 823 BGB Verkehrsunfall"
"Recherche: Literatur zu § 263 StGB Täuschung"
```

### Output-Format
```markdown
# Recherche-Report - [Norm/Thema] - [Datum]

## Aufgabe
[Was wurde recherchiert]

## Gesetzliche Grundlage
§ XYZ BGB/StGB/VwGO
[Gesetzestext]

## Rechtsprechung

### BGH/BVerfG
1. **BGH NJW 2024, 123**
   - Leitsatz: [...]
   - Relevanz: [...]

2. **BVerfG NJW 2023, 456**
   - Leitsatz: [...]
   - Relevanz: [...]

### OLG/OVG
1. **OLG München BeckRS 2024, 789**
   - Leitsatz: [...]
   - Relevanz: [...]

## Literatur

1. **Palandt/Grüneberg, BGB, 83. Aufl. 2024, § 433 Rn. 12**
   - Aussage: [...]

2. **MüKo-BGB/Kramer, 9. Aufl. 2024, § 433 Rn. 25**
   - Aussage: [...]

## Zusammenfassung
[Herrschende Meinung vs. Mindermeinung]

---
Fundstellen: [Anzahl: mindestens 3-5]
```

### Workflow-Integration
```
@recherche → @anwalt-[rechtsgebiet]
@recherche → @gutachter
```

---

## 6. @formular (Sonnet 4.5)

### Expertise
- Schriftsatzerstellung
- Vertragsgestaltung
- Template-Management
- Formelle Korrektheit

### Primäre Aufgaben
- Klagen/Anträge formulieren
- Widersprüche schreiben
- Verträge erstellen
- Templates anpassen

### Typische Inputs
```
"Klage: Zahlungsanspruch aus Kaufvertrag"
"Widerspruch: Baugenehmigung"
"Vertrag: Mietvertrag"
"Strafanzeige: Betrug § 263 StGB"
```

### Output-Format
```markdown
# [Schriftsatz-Art] - [Mandat] - [Datum]

An das
[Gericht/Behörde]
[Adresse]

In Sachen
[Kläger/Antragsteller]
./.
[Beklagter/Antragsgegner]

Az.: [Aktenzeichen]

[SCHRIFTSATZ-TYP]

Sehr geehrte Damen und Herren,

namens und in Vollmacht der/des Kläger(in)/Antragsteller(in) erhebe ich

K l a g e / W i d e r s p r u c h

[...]

I. Sachverhalt
[...]

II. Rechtliche Würdigung
[...]

III. Antrag
[...]

Mit vorzüglicher Hochachtung

[Unterschrift]
Rechtsanwalt/Rechtsanwältin

---
Anlagen:
- Vollmacht
- [weitere Anlagen]
```

### Workflow-Integration
```
@anwalt-[rechtsgebiet] → @formular → @mandatsmanager
@gutachter → @formular
```

---

## 7. @mandatsmanager (Sonnet 4.5)

### Expertise
- Fristenberechnung (ZPO, StPO, VwGO)
- Aktenführung
- Mandatsverwaltung
- Wiedervorlagen

### Primäre Aufgaben
- Fristen berechnen
- Wiedervorlagen setzen
- Aktenstruktur erstellen
- Mandatsnummern vergeben

### Typische Inputs
```
"Fristen für Mandat 2025-001"
"Neue Mandatsakte: Zivilrecht - Kaufvertrag"
"Wiedervorlage: Schriftsatz-Zustellung"
```

### Output-Format
```markdown
# Mandatsmanagement - [Mandat] - [Datum]

## Mandatsinfo
- **Mandats-Nr.**: 2025-XXX
- **Rechtsgebiet**: [Zivil/Straf/Verwaltung]
- **Kurzbeschreibung**: [...]
- **Angelegt**: [Datum]

## Fristen

| Frist | Datum | Berechnung | Status |
|-------|-------|------------|--------|
| Klageerwiderung | 2025-02-15 | Zustellung + 2 Wochen (§ 276 ZPO) | Offen |
| Replik | 2025-03-01 | Nach Klageerwiderung | Offen |

## Wiedervorlagen

- [ ] Akteneinsicht beantragen - bis 2025-01-15
- [ ] Schriftsatz vorbereiten - bis 2025-02-08
- [ ] Mandant informieren - bis 2025-01-20

## Aktenstruktur
```
mandates/2025-XXX-[anonymisiert]/
├── mandat.md
├── recherche-433-bgb.md
├── gutachten-final.md
└── klage-entwurf.md
```

---
Erstellt von @mandatsmanager | Sonnet 4.5 | [Timestamp]
```

### Workflow-Integration
```
@anwalt-[rechtsgebiet] → @mandatsmanager
@formular → @mandatsmanager
```

---

## Agent-Auswahl Flowchart

```
START
  ↓
Neues Mandat?
  ├─ JA → Welches Rechtsgebiet?
  │         ├─ Zivilrecht → @recherche → @anwalt-zivilrecht → @formular → @mandatsmanager
  │         ├─ Strafrecht → @recherche → @anwalt-strafrecht → @formular → @mandatsmanager
  │         └─ Verwaltung → @recherche → @anwalt-verwaltung → @formular → @mandatsmanager
  │
  ├─ Quick Check?
  │   └─ @anwalt-[rechtsgebiet] → @mandatsmanager
  │
  ├─ Gutachten?
  │   └─ @recherche → @gutachter → @formular
  │
  ├─ Nur Recherche?
  │   └─ @recherche
  │
  ├─ Nur Schriftsatz?
  │   └─ @anwalt-[rechtsgebiet] → @formular → @mandatsmanager
  │
  └─ Nur Fristen?
      └─ @mandatsmanager
```

---

## Best Practices

### 1. Immer Recherche vor Fachagent (außer Quick Check)
```
✅ RICHTIG: @recherche → @anwalt-zivilrecht
❌ FALSCH: @anwalt-zivilrecht (ohne Recherche bei komplexen Fragen)
```

### 2. Immer Mandatsmanager am Ende
```
✅ RICHTIG: @formular → @mandatsmanager
❌ FALSCH: @formular (Fristen vergessen!)
```

### 3. Gutachter für tiefe Analyse
```
✅ RICHTIG: @gutachter (bei komplexem Meinungsstreit)
❌ FALSCH: @anwalt-zivilrecht (zu oberflächlich)
```

### 4. Formular für finale Dokumente
```
✅ RICHTIG: @anwalt-zivilrecht → @formular
❌ FALSCH: @anwalt-zivilrecht (Entwurf direkt nutzen)
```

---

*Diese Dokumentation beschreibt alle 7 Spezial-Agenten von Legal-GodMode.*
*Letzte Aktualisierung: 2025-12-28*
