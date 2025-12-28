# Mandats-Registry

**Letzte Aktualisierung:** 2025-12-28

---

## Aktive Mandate

| Mandat-ID | Mandant | Status | Rechtsgebiete | Zuständige Agenten | Erstellt | Letzte Aktivität | Priorität |
|-----------|---------|--------|---------------|-------------------|----------|------------------|-----------|
| - | - | - | - | - | - | - | - |

---

## Abgeschlossene Mandate (letzte 10)

| Mandat-ID | Mandant | Rechtsgebiete | Abgeschlossen | Finale Dokumente |
|-----------|---------|---------------|---------------|------------------|
| - | - | - | - | - |

---

## Archivierte Mandate

Für vollständiges Archiv siehe: `/Legal-GodMode/cases/[Jahr]/`

---

## Status-Definitionen

| Status | Beschreibung | Nächster Schritt |
|--------|--------------|------------------|
| **INTAKE** | Mandat eingegangen, Fakten werden gesammelt | @researcher-legal sammelt Sachverhalt |
| **REVIEW** | Fakten vollständig, Rechtsfragen werden identifiziert | Orchestrator ordnet Agenten zu |
| **ASSIGNED** | Agenten wurden beauftragt | Agenten erstellen Gutachten |
| **EXPERT_WIP** | Fachagenten arbeiten an Gutachten | Warten auf Abschluss |
| **VALIDATION** | Gutachten bei @validator-legal zur Prüfung | @validator-legal prüft |
| **REVISE** | Validator fordert Überarbeitung | Betroffene Agenten korrigieren |
| **SYNTHESIS** | Validation APPROVED, @scribe-legal finalisiert | @scribe-legal erstellt FINAL_OPINION |
| **COMPLETED** | Finales Gutachten erstellt und übergeben | Archivierung |
| **ON_HOLD** | Mandat pausiert (z.B. auf Mandanten-Input wartend) | User-Aktion erforderlich |
| **UPDATED** | Bestehender Fall mit neuen Fakten aktualisiert | Supplement-Gutachten erstellen |

---

## Rechtsgebiets-Abkürzungen

| Kürzel | Rechtsgebiet | Zuständiger Agent |
|--------|--------------|-------------------|
| **CIV** | Zivilrecht (BGB, Vertragsrecht) | @agent-civillaw |
| **LAB** | Arbeitsrecht | @agent-laborlaw |
| **CRIM** | Strafrecht | @agent-criminallaw |
| **PUB** | Öffentliches Recht | @agent-publiclaw |
| **IT** | IT-Recht, Datenschutz | @agent-speciallaw |
| **IP** | Immaterialgüterrecht (Marken, Patente) | @agent-speciallaw |
| **MED** | Medizinrecht | @agent-speciallaw |
| **COMP** | Wettbewerbsrecht | @agent-speciallaw |

---

## Priorisierungs-Regeln

| Priorität | Kriterium | Behandlung |
|-----------|-----------|------------|
| **🔴 URGENT** | Fristen < 7 Tage | Sofortige Bearbeitung |
| **🟠 HIGH** | Fristen < 30 Tage oder hoher Streitwert | Priorisierte Bearbeitung |
| **🟡 MEDIUM** | Standard-Mandat | Normale Bearbeitung |
| **🟢 LOW** | Beratung ohne Zeitdruck | Nach Kapazität |

---

## Nutzung

### Neues Mandat anlegen
```bash
Mandat-ID: CASE-YYYY-NNNN (z.B. CASE-2025-0001)
Mandant: [Name/Firma]
Status: INTAKE
Rechtsgebiete: [CIV, LAB, ...]
Zuständige Agenten: [TBD]
Erstellt: [YYYY-MM-DD]
Priorität: [URGENT/HIGH/MEDIUM/LOW]
```

### Status aktualisieren
Bei jedem Workflow-Schritt Status in Tabelle aktualisieren.

### Mandat abschließen
1. Status → COMPLETED
2. Zeile in "Abgeschlossene Mandate" verschieben
3. Archivierungs-Link hinzufügen

---

## Archivierungs-Struktur

```
/Legal-GodMode/cases/
├── 2025/
│   ├── CASE-2025-0001/
│   │   ├── FACTS_CASE-2025-0001.md
│   │   ├── OPINION_CASE-2025-0001_civillaw_001.md
│   │   ├── OPINION_CASE-2025-0001_speciallaw_001.md
│   │   ├── VALIDATION_REPORT_CASE-2025-0001.md
│   │   └── FINAL_OPINION_CASE-2025-0001.md
│   ├── CASE-2025-0002/
│   └── ...
```

---

## Statistiken (2025)

| Metrik | Wert |
|--------|------|
| Gesamt bearbeitete Mandate | 0 |
| Abgeschlossene Mandate | 0 |
| Aktive Mandate | 0 |
| Durchschnittliche Bearbeitungszeit | - |
| Häufigstes Rechtsgebiet | - |

---

*Diese Registry wird automatisch vom Orchestrator gepflegt.*
