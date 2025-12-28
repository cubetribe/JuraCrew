# Legal-GodMode Agents

Orchestriertes Multi-Agent-System für juristische Gutachten.

## Agent-Übersicht

### 1. researcher.md - Legal Intelligence Unit
**Model:** Sonnet
**Tools:** Read, Grep, Glob, Bash
**Aufgabe:** Faktensammlung OHNE rechtliche Wertung
**Output:** RESEARCH_REPORT mit Chronologie, Dokumenten, Fristen

**Abgrenzung:**
- NICHT: Rechtliche Interpretation → Fachagenten
- NICHT: Wertungen, Empfehlungen → Fachagenten
- NUR: Rohdaten, Fakten, Fundstellen

---

### 2. agent-contract.md - Vertragsrechtlicher Gutachter
**Model:** Opus
**Tools:** Read, Grep, Glob
**Aufgabe:** Vertragsrecht (BGB AT, Schuldrecht AT, AGB)
**Output:** Gutachten im Gutachtenstil

**Zuständig für:**
- §§104-185 BGB (Rechtsgeschäftslehre)
- §§241-304 BGB (Schuldrecht AT)
- §§305-310 BGB (AGB-Recht)

**NICHT zuständig für:**
- Mietrecht → @agent-tenancy
- Strafrecht → @agent-criminal
- Unternehmensrecht → @agent-corp

---

### 3. agent-criminal.md - Strafrechtlicher Gutachter
**Model:** Opus
**Tools:** Read, Grep, Glob
**Aufgabe:** Strafrecht (StGB AT/BT, StPO)
**Output:** Gutachten im Gutachtenstil

**Zuständig für:**
- StGB AT (§§13-37 StGB)
- Vermögensdelikte (§§242-263a StGB)
- Körperverletzung (§§223-231 StGB)
- Beleidigung (§§185-187 StGB)

**NICHT zuständig für:**
- Zivilrechtliche Schadensersatzansprüche → @agent-contract
- Strafprozessuale Vertretung → Strafverteidiger (extern)

---

### 4. agent-tenancy.md - Mietrechtlicher Gutachter
**Model:** Opus
**Tools:** Read, Grep, Glob
**Aufgabe:** Mietrecht (§§535-580a BGB)
**Output:** Gutachten im Gutachtenstil

**Zuständig für:**
- Mietvertrag, Mietminderung (§§535-536 BGB)
- Kündigung (§§542-580a BGB)
- Kaution (§551 BGB)
- Mieterhöhung (§§557-561 BGB)
- Wohnraum & Gewerberaum

**NICHT zuständig für:**
- Allgemeines Vertragsrecht → @agent-contract
- Strafrecht → @agent-criminal

---

### 5. agent-corp.md - Unternehmensrechtlicher Gutachter
**Model:** Opus
**Tools:** Read, Grep, Glob
**Aufgabe:** Unternehmensrecht (HGB, GmbHG, AktG)
**Output:** Gutachten im Gutachtenstil

**Zuständig für:**
- Handelsrecht (§§1-372 HGB)
- GmbH-Recht (GmbHG)
- Aktienrecht (AktG - Grundlagen)
- GbR (§§705-740 BGB)
- Registerrecht

**NICHT zuständig für:**
- Allgemeines Vertragsrecht → @agent-contract
- Arbeitsrecht → @agent-labor (falls vorhanden)
- Insolvenzrecht → Fachanwalt (extern)

---

### 6. validator-legal.md - Quality Gate
**Model:** Sonnet
**Tools:** Read, Grep, Glob, Bash
**Aufgabe:** Formalkontrolle der Gutachten
**Output:** VALIDATION_REPORT

**Prüft:**
- Vollständigkeit der Struktur
- Konsistenz der Daten
- Abgrenzungs-Tabellen (PFLICHT!)
- Quellenangaben
- Format-Standards
- Rechtsgebiets-Abgrenzung (Hard Constraints!)

**NICHT prüft:**
- Inhaltliche Rechtsprüfung → Fachagenten
- Rechtliche Bewertungen → Fachagenten

**Status-Codes:**
- PASSED: Gutachten kann finalisiert werden
- WARNINGS: Kann finalisiert werden, Warnungen dokumentieren
- FAILED: Zurück an Fachagent zur Korrektur

---

### 7. scribe-legal.md - Dokumentation & Finalisierung
**Model:** Sonnet
**Tools:** Read, Write, Edit, Grep, Glob
**Aufgabe:** Finale Gutachten erstellen, MANDATE_REGISTRY pflegen
**Output:** FINAL_OPINION (mandantengerecht)

**Aufgaben:**
- Zusammenführung aller Fachgutachten
- Verständliche Sprache (kein Juristendeutsch!)
- Handlungsempfehlungen zusammenstellen
- Fristen-Übersicht
- MANDATE_REGISTRY aktualisieren
- Archivierung

**NICHT:**
- Rechtliche Aussagen ändern → Fachagenten
- Gutachten inhaltlich korrigieren → Fachagenten

---

## Workflow

```
User → Task
  ↓
@researcher → Faktensammlung (RESEARCH_REPORT)
  ↓
@agent-[contract/criminal/tenancy/corp] → Gutachten (OPINION)
  ↓
@validator-legal → Quality Gate (VALIDATION_REPORT)
  ↓
  PASSED? → @scribe-legal → Finale Dokumente (FINAL_OPINION)
  FAILED? → Zurück an Fachagent
```

## Hard Constraints (KRITISCH!)

### Regel 1: Abgrenzungs-Tabelle PFLICHT!
Jeder Fachagent MUSS eine Abgrenzungs-Tabelle im Output haben:
- "Ich habe geprüft"
- "Ich habe NICHT geprüft"
- "Zuständig"

### Regel 2: Keine Rechtsgebiets-Überschreitungen!
- @agent-contract darf NICHT über Strafrecht schreiben
- @agent-criminal darf NICHT über Zivilrecht schreiben
- @agent-tenancy darf NICHT über Gesellschaftsrecht schreiben
- @agent-corp darf NICHT über Mietrecht schreiben

### Regel 3: Gutachtenstil für Fachagenten!
Alle Fachagenten arbeiten im klassischen Gutachtenstil:
1. Obersatz
2. Definition
3. Subsumtion
4. Ergebnis

### Regel 4: Validator prüft NUR formal!
@validator-legal prüft KEINE rechtlichen Inhalte, NUR:
- Vollständigkeit
- Konsistenz
- Format
- Abgrenzung

### Regel 5: Scribe ändert KEINE Rechtsaussagen!
@scribe-legal macht NUR redaktionelle Arbeit:
- Formatierung
- Rechtschreibung
- Verständlichkeit
- KEINE inhaltlichen Änderungen!

## Datei-Konventionen

### Research Report
- Dateiname: `RESEARCH_REPORT_[Mandate-ID].md`
- Erstellt von: @researcher
- Enthält: Fakten, Chronologie, Dokumente, Fristen

### Fachgutachten
- Dateiname: `OPINION_[Mandate-ID]_[Rechtsgebiet]_[Version].md`
- Erstellt von: @agent-contract, @agent-criminal, @agent-tenancy, @agent-corp
- Enthält: Gutachten im Gutachtenstil + Abgrenzungs-Tabelle

### Validation Report
- Dateiname: `VALIDATION_REPORT_[Mandate-ID].md`
- Erstellt von: @validator-legal
- Enthält: Prüfungsergebnis (PASSED/WARNINGS/FAILED)

### Final Opinion
- Dateiname: `FINAL_OPINION_[Mandate-ID].md`
- Erstellt von: @scribe-legal
- Enthält: Mandantengerechtes Gutachten + Executive Summary

## Mandate Registry

**Datei:** `/Legal-GodMode/MANDATE_REGISTRY.yaml`

Zentrale Übersicht aller Mandate:
- Mandate-ID
- Rechtsgebiet
- Parteien
- Status (OPEN/IN_PROGRESS/FINALIZED)
- Fristen
- Erfolgsaussichten
- Streitwert

Wird gepflegt von: @scribe-legal

## Quality Gates

### Gate 1: Research Complete
- Alle Dokumente erfasst?
- Chronologie lückenlos?
- Alle Fundstellen angegeben?

### Gate 2: Opinion Complete
- Gutachtenstil korrekt?
- Abgrenzungs-Tabelle vorhanden?
- Alle Normen zitiert?
- Ergebnis eindeutig?

### Gate 3: Validation Passed
- Vollständigkeit: OK?
- Konsistenz: OK?
- Rechtsgebiets-Abgrenzung: OK?
- Abgrenzungs-Tabelle: OK?

### Gate 4: Finalization Complete
- Verständliche Sprache?
- Handlungsempfehlungen konkret?
- Fristen hervorgehoben?
- MANDATE_REGISTRY aktualisiert?

## Beispiel-Mandate

### Beispiel 1: Mietrecht + Strafrecht
**Fall:** Vermieter fordert Miete, Mieter vermutet Betrug

**Workflow:**
1. @researcher → Fakten sammeln
2. @agent-tenancy → Mietrechtliche Prüfung (Mietforderung)
3. @agent-criminal → Strafrechtliche Prüfung (Betrug)
4. @validator-legal → Beide Gutachten prüfen
5. @scribe-legal → Zusammenführen zu FINAL_OPINION

### Beispiel 2: Vertragsrecht + Unternehmensrecht
**Fall:** GmbH-Gesellschafter anfechtet Gesellschaftsvertrag

**Workflow:**
1. @researcher → Fakten sammeln
2. @agent-contract → Anfechtung (§§119-123 BGB)
3. @agent-corp → GmbH-Satzungsmängel (GmbHG)
4. @validator-legal → Beide Gutachten prüfen
5. @scribe-legal → Zusammenführen zu FINAL_OPINION

## Version History

- **v1.0** (2025-12-28): Initial Release
  - 7 Agenten definiert
  - Workflow etabliert
  - Hard Constraints festgelegt

---

**Erstellt:** 2025-12-28
**Projekt:** Legal-GodMode
**Status:** Production Ready
