# JuraCrew

> **7 KI-Anwälte, die sich gegenseitig auf die Finger schauen**

Ein orchestriertes Multi-Agent-System für juristische Analysen - weil ein einzelnes LLM bei Rechtsfragen gerne mal kreativ wird. Und "kreativ" ist bei Jura selten gut.

Basiert auf dem [Multi-Agent Team Blueprint](https://github.com/cubetribe/ClaudeCode_GodMode-On) - spezialisiert auf deutsches Recht.

---

## Das Problem

Du fragst eine KI nach Mietrecht und plötzlich erklärt sie dir, warum das auch strafrechtlich relevant sein könnte - mit erfundenen Paragraphen. Classic LLM-Move.

## Die Lösung: JuraCrew

**7 spezialisierte Agenten**, die nur eines wirklich gut können: **Nein sagen.**

```
"Architecture by Exclusion" - Die Qualität entsteht durch das,
was die Agenten NICHT tun dürfen.

Oder wie wir sagen: "Nicht mein Rechtsgebiet, frag den Kollegen."
```

Jeder Agent hat **Hard Constraints** - unverletzbare Regeln, was er NICHT anfassen darf. Plus eine **Abgrenzungs-Tabelle** in jedem Gutachten, damit transparent ist, wer was bearbeitet hat.

---

## Die Crew

| Agent | Rolle | Persönlichkeit |
|-------|-------|----------------|
| `@researcher` | **Der Türsteher** - Stellt nervige Rückfragen | "Haben Sie das Kündigungsschreiben dabei?" |
| `@agent-contract` | Vertragsrecht (BGB AT, Schuldrecht, AGB) | Der Pedant mit dem Rotstift |
| `@agent-criminal` | Strafrecht (StGB, StPO) | "Interessant, aber erstmal nichts sagen." |
| `@agent-tenancy` | Mietrecht (§§535-580a BGB) | Der Anwalt, den jeder Mieter kennt |
| `@agent-corp` | Unternehmensrecht (HGB, GmbHG, AktG) | Trägt metaphorisch immer Anzug |
| `@validator-legal` | **Der Kritiker** - Findet jeden Fehler | "Aber haben Sie auch an §XY gedacht?" |
| `@scribe-legal` | **Der Übersetzer** - Macht Juristendeutsch lesbar | "Was der Kollege sagen wollte..." |

---

## So läuft das ab

```
[Deine Anfrage]
      │
      ▼
┌─────────────────┐
│  @researcher    │ ◄── Stellt erstmal 10 Fragen
│  (Türsteher)    │     (Ja, alle sind wichtig)
└────────┬────────┘
         │
         ▼ "Akte vollständig, startet die Spezialisten!"
┌────────────────────────────────────────┐
│      DIE FACHLEUTE ARBEITEN PARALLEL   │
│  @agent-contract  @agent-criminal      │
│  @agent-tenancy   @agent-corp          │
│                                        │
│  (Jeder macht nur SEIN Ding)           │
└────────────────────────┬───────────────┘
                         │
                         ▼ "Fertig! Zur Qualitätskontrolle!"
              ┌─────────────────────┐
              │  @validator-legal   │ ◄── APPROVED / REVISE / "Das geht so nicht"
              └──────────┬──────────┘
                         │
                         ▼ "Alles korrekt, jetzt verständlich machen!"
              ┌─────────────────────┐
              │   @scribe-legal     │ ◄── Übersetzt in Mandanten-Sprache
              └──────────┬──────────┘
                         │
                         ▼
              [FINAL_OPINION.md]
              (Verständlich UND korrekt!)
```

**Das Beste:** Läuft automatisch durch! Hooks sei Dank.

---

## Installation

### Was du brauchst

- [Claude Code CLI](https://docs.anthropic.com/en/docs/claude-code) oder Claude Desktop
- Git
- Einen Rechtsfall (optional, aber empfohlen)

### Los geht's

```bash
# Repository klonen
git clone https://github.com/cubetribe/JuraCrew.git
cd JuraCrew

# Das war's. Ernsthaft.
# CLAUDE.md wird automatisch geladen.
```

### Starten

```bash
# Terminal öffnen im JuraCrew-Ordner
claude

# Oder: Claude Desktop öffnen und den Ordner auswählen
```

---

## Schnellstart

### Beispiel 1: "Mein Vermieter spinnt"

```
Du: "Mein Vermieter hat mir wegen Eigenbedarf gekündigt,
     aber ich glaube der will die Wohnung nur teurer vermieten."

@researcher (Türsteher):
├── Wann genau kam die Kündigung?
├── Haben Sie das Schreiben?
├── Seit wann wohnen Sie dort?
└── Wer soll angeblich einziehen?

[Du antwortest]

System: "Okay, das riecht nach Mietrecht UND evtl. Betrug..."

Automatisch gestartet:
├── @agent-tenancy → "Kündigung unwirksam weil..."
└── @agent-criminal → "Für Betrug bräuchten wir..."

@validator-legal: "Beide Gutachten checken... APPROVED!"

@scribe-legal erstellt: FINAL_OPINION_CASE-2025-0001.md
→ Verständliche Zusammenfassung mit Handlungsempfehlungen
```

### Beispiel 2: Schnelle Frage

```
Du: "Quick Check: Kann ich wegen Schimmel die Miete mindern?"

→ Geht direkt an @agent-tenancy
→ Antwort im Chat (kein großes Mandat nötig)
```

---

## Was macht die Agenten besonders?

### Hard Constraints ("Was ich NICHT tue")

Jeder Agent hat **verbotene Zonen**:

```markdown
## Was ich NICHT tue (und zwar NIEMALS)

- ❌ Strafrecht → @agent-criminal ist zuständig
- ❌ Mietrecht → @agent-tenancy kümmert sich
- ❌ Unternehmensrecht → @agent-corp macht das

Ich sage lieber "Frag den Kollegen" als Unsinn zu erzählen.
```

### Die Abgrenzungs-Tabelle (Pflicht in jedem Gutachten!)

| Rechtsfrage | Meine Zuständigkeit | Übergabe an | Warum |
|-------------|--------------------:|-------------|-------|
| Betrug bei Eigenbedarf? | ❌ Nope | @agent-criminal | Ist Strafrecht |
| Kündigung wirksam? | ✅ Mein Job | - | Ist Mietrecht |

**Warum?** Zwingt zum Nachdenken: "Ist das wirklich mein Bereich?"

---

## Dateistruktur

```
JuraCrew/
├── CLAUDE.md           ← Das Hirn (lädt automatisch!)
├── README.md           ← Du bist hier
│
├── agents/             ← Die Crew-Definitionen
│   ├── researcher.md   ← Der Türsteher
│   ├── agent-contract.md
│   ├── agent-criminal.md
│   ├── agent-tenancy.md
│   ├── agent-corp.md
│   ├── validator-legal.md  ← Der Kritiker
│   └── scribe-legal.md     ← Der Übersetzer
│
├── templates/          ← Vorlagen für Outputs
│   ├── MANDATE_REGISTRY.md
│   ├── CASE_TEMPLATE.md
│   └── OPINION_TEMPLATE.md
│
├── mandates/           ← Hier landen deine Fälle (gitignored!)
│   └── CASE-2025-0001/
│       ├── FACTS_*.md
│       ├── OPINION_*.md
│       └── FINAL_OPINION_*.md
│
└── config/
    └── settings.json   ← Hooks & Model-Zuweisungen
```

---

## Befehle

| Sag einfach... | Was passiert |
|----------------|--------------|
| `Neues Mandat: [Sachverhalt]` | @researcher startet die Befragung |
| `Quick Check: [Frage]` | Direktantwort ohne großes Theater |
| `Status CASE-2025-0001` | Wo steht der Fall gerade? |
| `Gutachten CASE-2025-0001` | Zeig mir das Ergebnis |

---

## Eigene Agenten hinzufügen?

1. Neue Datei: `agents/agent-family.md` (Familienrecht, anyone?)
2. Von bestehendem Agenten kopieren
3. **Hard Constraints definieren** (Das Wichtigste!)
4. In `CLAUDE.md` eintragen
5. Model in `config/settings.json` zuweisen

---

## FAQ

### Kann ich damit echte Rechtsberatung machen?

**Nein.** JuraCrew ist ein Analyse-Tool, keine Rechtsanwaltskanzlei. Alle Gutachten sind unverbindlich. Für echte Rechtsberatung: Echten Anwalt fragen.

### Warum 7 Agenten statt einer Super-KI?

- **Spezialisierung** > Generalisierung
- **Hard Constraints** verhindern Halluzinationen
- **Parallele Arbeit** bei komplexen Fällen
- **Quality Gate** fängt Fehler ab

Oder kurz: Weil ein Alleskönner meist ein Nichtskönner ist.

### Brauche ich MCP-Server?

**Nein.** JuraCrew läuft mit Standard-Tools (Read, Grep, Glob, Write). Keine externen Server nötig. Plug & Play.

---

## Disclaimer

**JuraCrew ersetzt KEINE professionelle Rechtsberatung!**

- Alle Gutachten sind unverbindlich
- Ohne Gewähr
- Nicht als Rechtsrat zu verstehen

**Bei echten Rechtsproblemen: Echten Anwalt konsultieren!**

*(Die KI-Anwälte können nicht vor Gericht erscheinen. Noch nicht.)*

---

## Lizenz

MIT License - siehe [LICENSE](LICENSE)

---

## Kontakt

**Erstellt von:** Dennis Westermann
**E-Mail:** d.westermann@ol-mg.de
**Version:** 1.0
**Datum:** 2025-12-28

---

*JuraCrew - 7 KI-Anwälte, die sich gegenseitig kontrollieren. Weil Vertrauen gut ist, aber Kontrolle besser.*
