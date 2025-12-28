# Changelog

All notable changes to Legal-GodMode will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [1.0.0] - 2025-12-28

### Added
- **Initial Release** of Legal-GodMode
- **7 Spezialisierte Jura-Agenten:**
  - @anwalt-zivilrecht (Opus 4.5) - Zivilrechtliche Mandatsbearbeitung
  - @anwalt-strafrecht (Opus 4.5) - Strafrechtliche Mandatsbearbeitung
  - @anwalt-verwaltung (Opus 4.5) - Verwaltungsrecht
  - @gutachter (Opus 4.5) - Rechtsgutachten und Subsumtion
  - @recherche (Sonnet 4.5) - Gesetz/Rechtsprechung/Literatur
  - @formular (Sonnet 4.5) - Schriftsätze, Verträge, Vorlagen
  - @mandatsmanager (Sonnet 4.5) - Fristenkontrolle, Aktenführung

- **Orchestrator-Prompt** für automatische Agent-Ketten
  - Workflow: Neues Mandat (Recherche → Fachagent → Formular → Mandatsmanager)
  - Workflow: Quick Check (Fachagent → Mandatsmanager)
  - Workflow: Gutachten (Recherche → Gutachter → Formular)

- **Hard Constraints System:**
  - Datenschutz: Anonymisierung PFLICHT
  - Qualitätssicherung: Mindestens 3 Fundstellen pro Rechtsfrage
  - Git-Workflow: NIEMALS push ohne explizite User-Erlaubnis
  - Subsumtion: Vollständige Tatbestand → Rechtsfolge Struktur

- **Konfigurationssystem:**
  - `config/CLAUDE-system.md` - Globale Kanzlei-Identität
  - `config/CLAUDE-projekt.md` - Projekt-spezifische Workflows
  - `config/settings.json` - Claude Code Settings mit Model-Zuordnung

- **Ordnerstruktur:**
  - `/agents/` - Agent-Definitionen
  - `/config/` - Konfigurationsdateien
  - `/templates/` - Schriftsatz-/Vertrags-Vorlagen
  - `/scripts/` - Automation-Scripts
  - `/docs/` - Projekt-Dokumentation
  - `/mandates/` - Mandatsakten (nicht in Git)
  - `/Agents/` - Subagenten-Reports

- **Dokumentation:**
  - README.md mit Projekt-Übersicht
  - AGENTS.md mit Agent-Beschreibungen
  - WORKFLOWS.md mit Standard-Workflows

### Security
- `.gitignore` konfiguriert für:
  - Mandatsakten (`/mandates/`)
  - Finale Dokumente (`*.final.md`)
  - Credentials (`.env`, `*.pem`, `*.key`)
  - Sensible Daten

### Development
- Git-Workflow mit strengem Push-Protokoll
- Token-Management mit Auto-Compact
- Model-Auswahl: Opus für Fachagenten, Sonnet für Support-Agenten

---

## [Unreleased]

### Planned Features
- [ ] Integration mit Juris/Beck-Online API für Recherche
- [ ] Automatische Fristenberechnung nach ZPO/StPO
- [ ] Template-Bibliothek für Standard-Schriftsätze
- [ ] Export-Funktion (PDF, DOCX)
- [ ] Mandats-Dashboard mit Fristenübersicht
- [ ] Multi-Mandat-Parallelverarbeitung
- [ ] Integration mit Kanzlei-Software (RA-MICRO, etc.)

---

## Version History

- **1.0.0** (2025-12-28) - Initial Release
