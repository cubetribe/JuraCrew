# Legal-GodMode Workflows

Diese Datei beschreibt die Standard-Workflows für verschiedene juristische Aufgaben.

---

## Workflow-Übersicht

| Workflow | Agent-Kette | Dauer | Komplexität |
|----------|-------------|-------|-------------|
| **Neues Zivilmandat** | @recherche → @anwalt-zivilrecht → @formular → @mandatsmanager | 15-30 Min | Hoch |
| **Neues Strafmandat** | @recherche → @anwalt-strafrecht → @formular → @mandatsmanager | 15-30 Min | Hoch |
| **Neues Verwaltungsmandat** | @recherche → @anwalt-verwaltung → @formular → @mandatsmanager | 15-30 Min | Hoch |
| **Quick Check** | @anwalt-[rechtsgebiet] → @mandatsmanager | 5-10 Min | Niedrig |
| **Gutachten** | @recherche → @gutachter → @formular | 20-45 Min | Sehr Hoch |
| **Schriftsatz** | @anwalt-[rechtsgebiet] → @formular → @mandatsmanager | 10-20 Min | Mittel |
| **Reine Recherche** | @recherche | 5-15 Min | Niedrig |
| **Fristenkontrolle** | @mandatsmanager | 2-5 Min | Niedrig |

---

## 1. Neues Zivilmandat

### Beschreibung
Vollständige Bearbeitung eines neuen zivilrechtlichen Mandats von der Recherche bis zum fertigen Schriftsatz.

### Agent-Kette
```
@recherche → @anwalt-zivilrecht → @formular → @mandatsmanager
```

### Schritt-für-Schritt

#### 1. User-Input
```
"Neues Mandat: Zivilrecht - Kaufpreiszahlung § 433 BGB"
```

#### 2. @recherche (Sonnet 4.5)
**Aufgabe**: Rechtsprechung zu § 433 BGB recherchieren

**Input**:
```
@recherche "§ 433 BGB Kaufpreiszahlung Rechtsprechung 2024"
```

**Output**: `Agents/recherche-2025-XXX-433bgb-[datum].md`
- Mindestens 3 BGH-Urteile
- Kommentarmeinungen
- Aktuelle Rechtsentwicklungen

#### 3. @anwalt-zivilrecht (Opus 4.5)
**Aufgabe**: Mandatsanalyse und Fallprüfung

**Input**:
```
@anwalt-zivilrecht "Mandat 2025-XXX: Kaufpreiszahlung
Sachverhalt: [Anonymisierter Sachverhalt]
Recherche: [Link zu Recherche-Report]"
```

**Output**: `Agents/anwalt-zivilrecht-2025-XXX-[datum].md`
- Anspruchsgrundlagen (§§ 433, 434 BGB)
- Tatbestandsprüfung
- Erfolgsaussichten
- Prozessstrategie

#### 4. @formular (Sonnet 4.5)
**Aufgabe**: Klage-Schriftsatz erstellen

**Input**:
```
@formular "Klage - Zahlungsanspruch aus Kaufvertrag
Mandat: 2025-XXX
Basis: [Link zu Mandatsanalyse]"
```

**Output**: `mandates/2025-XXX-kaufpreiszahlung/klage-entwurf.md`
- Formell korrekter Schriftsatz
- Vollständige Subsumtion
- Antragsformulierung

#### 5. @mandatsmanager (Sonnet 4.5)
**Aufgabe**: Fristen berechnen und Aktenstruktur erstellen

**Input**:
```
@mandatsmanager "Fristen setzen für Mandat 2025-XXX
Zustellung: [Datum]
Rechtsgebiet: Zivilrecht (ZPO)"
```

**Output**: `Agents/mandatsmanager-2025-XXX-[datum].md`
- Fristenübersicht (§§ 276, 283 ZPO)
- Wiedervorlagen
- Aktenstruktur

### Finale Aktenstruktur
```
mandates/2025-XXX-kaufpreiszahlung/
├── mandat.md                        # Mandatsübersicht
├── recherche-433-bgb.md             # Recherche-Report
├── analyse-zivilrecht.md            # Mandatsanalyse
├── klage-entwurf.md                 # Schriftsatz
└── fristen.md                       # Fristenkontrolle
```

---

## 2. Quick Check

### Beschreibung
Schnelle erste Einschätzung ohne tiefe Recherche (für Beratungsgespräche).

### Agent-Kette
```
@anwalt-[rechtsgebiet] → @mandatsmanager
```

### Schritt-für-Schritt

#### 1. User-Input
```
"Quick Check: Strafrecht - Betrug § 263 StGB"
```

#### 2. @anwalt-strafrecht (Opus 4.5)
**Aufgabe**: Erste Einschätzung

**Input**:
```
@anwalt-strafrecht "Quick Check: Betrug § 263 StGB
Sachverhalt: [Kurz-Sachverhalt]"
```

**Output**: `Agents/anwalt-strafrecht-quickcheck-[datum].md`
- Strafbarkeit (ohne tiefe Subsumtion)
- Erfolgsaussichten (grobe Einschätzung)
- Handlungsempfehlung

#### 3. @mandatsmanager (Sonnet 4.5)
**Aufgabe**: Fristnotiz erstellen

**Input**:
```
@mandatsmanager "Fristnotiz für Quick Check Strafrecht
Datum: [Heute]
Hinweis: Akteneinsicht beantragen"
```

**Output**: `Agents/mandatsmanager-quickcheck-[datum].md`
- Erinnerung: Akteneinsicht
- Wiedervorlage: Mandatsentscheidung

### Dauer
5-10 Minuten

---

## 3. Gutachten-Erstellung

### Beschreibung
Ausführliches Rechtsgutachten mit tiefer Subsumtion und Meinungsstreit.

### Agent-Kette
```
@recherche → @gutachter → @formular
```

### Schritt-für-Schritt

#### 1. User-Input
```
"Gutachten: Verkehrsunfall § 823 BGB - Anscheinsbeweis"
```

#### 2. @recherche (Sonnet 4.5)
**Aufgabe**: Umfassende Recherche

**Input**:
```
@recherche "§ 823 BGB Verkehrsunfall Anscheinsbeweis Rechtsprechung"
```

**Output**: `Agents/recherche-823bgb-anscheinsbeweis-[datum].md`
- BGH-Rechtsprechung (mindestens 5 Urteile)
- Kommentarmeinungen (h.M. vs. a.A.)
- Literatur

#### 3. @gutachter (Opus 4.5)
**Aufgabe**: Tiefe Subsumtion

**Input**:
```
@gutachter "Rechtsgutachten: § 823 BGB Verkehrsunfall
Fragestellung: Anscheinsbeweis bei Auffahrunfall?
Recherche: [Link zu Recherche-Report]
Sachverhalt: [Anonymisierter Sachverhalt]"
```

**Output**: `Agents/gutachter-823bgb-anscheinsbeweis-[datum].md`
- Vollständige Subsumtion (Tatbestand → Rechtsfolge)
- Meinungsstreit (h.M. vs. a.A.)
- Stellungnahme mit Begründung
- Ergebnis

#### 4. @formular (Sonnet 4.5)
**Aufgabe**: Gutachten formatieren

**Input**:
```
@formular "Rechtsgutachten formatieren
Basis: [Link zu Gutachter-Report]
Format: Formelles Gutachten mit Deckblatt"
```

**Output**: `docs/gutachten-823bgb-anscheinsbeweis-final.md`
- Deckblatt
- Inhaltsverzeichnis
- Formatiertes Gutachten
- Fundstellenverzeichnis

### Dauer
20-45 Minuten

---

## 4. Schriftsatz-Erstellung

### Beschreibung
Erstellung eines Schriftsatzes (Klage, Klageerwiderung, Widerspruch, etc.).

### Agent-Kette
```
@anwalt-[rechtsgebiet] → @formular → @mandatsmanager
```

### Schritt-für-Schritt

#### 1. User-Input
```
"Schriftsatz: Klageerwiderung - Mandat 2025-XXX"
```

#### 2. @anwalt-[rechtsgebiet] (Opus 4.5)
**Aufgabe**: Strategie entwickeln

**Input**:
```
@anwalt-zivilrecht "Klageerwiderung für Mandat 2025-XXX
Gegnerische Klage: [Zusammenfassung]
Unsere Position: [Sachverhalt]"
```

**Output**: `Agents/anwalt-zivilrecht-klageerwiderung-[datum].md`
- Verteidigungsstrategie
- Angriffs- und Verteidigungsmittel
- Rechtliche Argumente

#### 3. @formular (Sonnet 4.5)
**Aufgabe**: Schriftsatz formulieren

**Input**:
```
@formular "Klageerwiderung - Zahlungsanspruch
Basis: [Link zu Strategie]
Gericht: LG München
Az.: 12 O 123/25"
```

**Output**: `mandates/2025-XXX/klageerwiderung-entwurf.md`
- Formell korrekter Schriftsatz
- Vollständige Begründung
- Antragsformulierung

#### 4. @mandatsmanager (Sonnet 4.5)
**Aufgabe**: Fristen aktualisieren

**Input**:
```
@mandatsmanager "Frist: Klageerwiderung eingereicht am [Datum]
Nächste Frist: Replik (ca. 2 Wochen nach Erwiderung)"
```

**Output**: Update in `Agents/mandatsmanager-2025-XXX-[datum].md`

### Dauer
10-20 Minuten

---

## 5. Reine Recherche

### Beschreibung
Gesetz/Rechtsprechung/Literatur recherchieren ohne Mandatsbezug.

### Agent-Kette
```
@recherche
```

### Schritt-für-Schritt

#### 1. User-Input
```
"Recherche: § 263 StGB Täuschungshandlung konkludent"
```

#### 2. @recherche (Sonnet 4.5)
**Aufgabe**: Fundstellen finden

**Input**:
```
@recherche "§ 263 StGB Täuschungshandlung konkludent Rechtsprechung Literatur"
```

**Output**: `Agents/recherche-263stgb-tauschung-[datum].md`
- Gesetzestext
- BGH/BVerfG Rechtsprechung
- Kommentarmeinungen
- Zusammenfassung (h.M. vs. a.A.)

### Dauer
5-15 Minuten

---

## 6. Fristenkontrolle

### Beschreibung
Fristen berechnen und Wiedervorlagen setzen.

### Agent-Kette
```
@mandatsmanager
```

### Schritt-für-Schritt

#### 1. User-Input
```
"Fristen für Mandat 2025-XXX
Zustellung Klage: 2025-01-15"
```

#### 2. @mandatsmanager (Sonnet 4.5)
**Aufgabe**: Fristen berechnen

**Input**:
```
@mandatsmanager "Fristenberechnung Mandat 2025-XXX
Rechtsgebiet: Zivilrecht (ZPO)
Zustellung: 2025-01-15"
```

**Output**: `Agents/mandatsmanager-2025-XXX-fristen-[datum].md`
- Klageerwiderung: 2025-01-29 (§ 276 ZPO: 2 Wochen)
- Replik: ca. 2 Wochen nach Erwiderung
- Hauptverhandlung: wird noch bestimmt

### Dauer
2-5 Minuten

---

## Workflow-Auswahl Tabelle

| Situation | Empfohlener Workflow | Begründung |
|-----------|---------------------|------------|
| **Mandant ruft an, unsicher ob Fall übernehmen** | Quick Check | Schnelle Einschätzung ohne Zeitaufwand |
| **Neuer Fall, Mandatsvertrag unterschrieben** | Neues [Rechtsgebiet]-Mandat | Vollständige Bearbeitung von Anfang an |
| **Komplexe Rechtsfrage, unsicher** | Gutachten | Tiefe Analyse mit Meinungsstreit |
| **Gegner hat geklagt, Frist läuft** | Schriftsatz-Erstellung | Fokus auf Erwiderung |
| **Unklare Rechtslage zu § XYZ** | Reine Recherche | Fundstellen sammeln |
| **Brief vom Gericht, Frist unklar** | Fristenkontrolle | Fristversäumnis vermeiden |

---

## Best Practices

### 1. Immer Recherche VOR Fachagent (außer Quick Check)
```
✅ RICHTIG: @recherche → @anwalt-zivilrecht
❌ FALSCH: @anwalt-zivilrecht (ohne Recherche bei komplexen Fragen)
```

**Begründung**: Fachagenten benötigen aktuelle Rechtsprechung für fundierte Analyse.

### 2. Immer Mandatsmanager AM ENDE
```
✅ RICHTIG: @formular → @mandatsmanager
❌ FALSCH: @formular (Fristen vergessen!)
```

**Begründung**: Fristversäumnis ist berufshaftungsrelevant.

### 3. Gutachter NUR für tiefe Analyse
```
✅ RICHTIG: @gutachter (bei komplexem Meinungsstreit)
❌ FALSCH: @gutachter (für einfache Fälle → zu teuer/langsam)
```

**Begründung**: Opus 4.5 ist token-intensiv, nur bei Bedarf nutzen.

### 4. Formular für FINALE Dokumente
```
✅ RICHTIG: @anwalt-zivilrecht → @formular
❌ FALSCH: @anwalt-zivilrecht (Entwurf direkt nutzen)
```

**Begründung**: Formular garantiert formelle Korrektheit.

---

## Fehlerbehandlung

### Problem: Keine Fundstellen gefunden
```
Lösung: @recherche mit spezifischerer Norm/Frage erneut aufrufen
Eskalation: Mindestens 3 Fundstellen sind PFLICHT
```

### Problem: Subsumtion unvollständig
```
Lösung: @gutachter einschalten für tiefe Analyse
Eskalation: Tatbestand → Rechtsfolge muss vollständig sein
```

### Problem: Frist unklar
```
Lösung: @mandatsmanager mit Zustelldatum aufrufen
Eskalation: Bei Unsicherheit immer kürzeste Frist annehmen
```

### Problem: Template fehlt
```
Lösung: @formular mit Beispiel-Vorgabe aufrufen
Eskalation: In templates/ ablegen für zukünftige Nutzung
```

---

## Token-Optimierung

### Workflow-Optimierung nach Token-Verbrauch

| Workflow | Token-Verbrauch | Optimierung |
|----------|----------------|-------------|
| Neues Mandat | Hoch (Opus) | Recherche-Report in Datei, nicht in Chat |
| Quick Check | Mittel (Opus) | Kurz-Output anfordern |
| Gutachten | Sehr Hoch (Opus) | `/compact` nach Abschluss |
| Schriftsatz | Mittel | Template wiederverwenden |
| Recherche | Niedrig (Sonnet) | OK für mehrfache Nutzung |
| Fristen | Niedrig (Sonnet) | OK für mehrfache Nutzung |

### Session-Hygiene

- **Nach jedem abgeschlossenen Mandat**: `/clear`
- **Bei langen Multi-Mandat-Sessions**: `/compact` bei 70% Token-Usage
- **Große Agent-Reports**: IMMER in Dateien schreiben, nicht in Chat ausgeben

---

*Diese Dokumentation beschreibt alle Standard-Workflows von Legal-GodMode.*
*Letzte Aktualisierung: 2025-12-28*
