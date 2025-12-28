# JuraCrew

> **7 AI Lawyers Keeping Each Other in Check**

An orchestrated multi-agent system for legal analysis - because a single LLM tends to get creative with legal questions. And "creative" is rarely good in law.

Based on the [Multi-Agent Team Blueprint](https://github.com/cubetribe/ClaudeCode_GodMode-On) - specialized for German law.

---

## The Problem

You ask an AI about tenancy law and suddenly it's explaining why this could also be criminally relevant - with made-up statutes. Classic LLM move.

## The Solution: JuraCrew

**7 specialized agents** who are really good at one thing: **Saying no.**

```
"Architecture by Exclusion" - Quality emerges from what
the agents are NOT allowed to do.

Or as we say: "Not my jurisdiction, ask my colleague."
```

Each agent has **Hard Constraints** - inviolable rules about what they must NOT touch. Plus a **Demarcation Table** in every opinion, making it transparent who handled what.

---

## The Crew

| Agent | Role | Personality |
|-------|------|-------------|
| `@researcher` | **The Bouncer** - Asks annoying questions | "Do you have the termination letter?" |
| `@agent-contract` | Contract Law (BGB AT, Obligations, Standard Terms) | The pedant with the red pen |
| `@agent-criminal` | Criminal Law (StGB, StPO) | "Interesting, but better say nothing for now." |
| `@agent-tenancy` | Tenancy Law (§§535-580a BGB) | The lawyer every tenant knows |
| `@agent-corp` | Corporate Law (HGB, GmbHG, AktG) | Metaphorically always wears a suit |
| `@validator-legal` | **The Critic** - Finds every mistake | "But did you consider §XY?" |
| `@scribe-legal` | **The Translator** - Makes legalese readable | "What my colleague meant to say..." |

---

## How It Works

```
[Your Request]
      │
      ▼
┌─────────────────┐
│  @researcher    │ ◄── Asks 10 questions first
│  (Bouncer)      │     (Yes, all are important)
└────────┬────────┘
         │
         ▼ "File complete, let's start the specialists!"
┌────────────────────────────────────────┐
│      SPECIALISTS WORK IN PARALLEL      │
│  @agent-contract  @agent-criminal      │
│  @agent-tenancy   @agent-corp          │
│                                        │
│  (Each does ONLY their thing)          │
└────────────────────────┬───────────────┘
                         │
                         ▼ "Done! Quality control!"
              ┌─────────────────────┐
              │  @validator-legal   │ ◄── APPROVED / REVISE / "This won't work"
              └──────────┬──────────┘
                         │
                         ▼ "All correct, now make it understandable!"
              ┌─────────────────────┐
              │   @scribe-legal     │ ◄── Translates into client language
              └──────────┬──────────┘
                         │
                         ▼
              [FINAL_OPINION.md]
              (Understandable AND correct!)
```

**The Best Part:** Runs automatically! Thanks to hooks.

---

## Installation

### What You Need

- [Claude Code CLI](https://docs.anthropic.com/en/docs/claude-code) or Claude Desktop
- Git
- A legal case (optional, but recommended)

### Let's Go

```bash
# Clone repository
git clone https://github.com/cubetribe/JuraCrew.git
cd JuraCrew

# That's it. Seriously.
# CLAUDE.md loads automatically.
```

### Start

```bash
# Open terminal in JuraCrew folder
claude

# Or: Open Claude Desktop and select the folder
```

---

## Quick Start

### Example 1: "My Landlord Is Acting Crazy"

```
You: "My landlord terminated my lease for personal use,
     but I think he just wants to rent it out for more money."

@researcher (Bouncer):
├── When exactly did you receive the termination?
├── Do you have the letter?
├── How long have you lived there?
└── Who is supposedly moving in?

[You answer]

System: "Okay, this smells like tenancy law AND possibly fraud..."

Automatically started:
├── @agent-tenancy → "Termination invalid because..."
└── @agent-criminal → "For fraud we'd need..."

@validator-legal: "Checking both opinions... APPROVED!"

@scribe-legal creates: FINAL_OPINION_CASE-2025-0001.md
→ Understandable summary with action recommendations
```

### Example 2: Quick Question

```
You: "Quick Check: Can I reduce rent due to mold?"

→ Goes directly to @agent-tenancy
→ Answer in chat (no major mandate needed)
```

---

## What Makes the Agents Special?

### Hard Constraints ("What I DO NOT Do")

Each agent has **forbidden zones**:

```markdown
## What I DO NOT Do (and I mean NEVER)

- ❌ Criminal Law → @agent-criminal is responsible
- ❌ Tenancy Law → @agent-tenancy handles this
- ❌ Corporate Law → @agent-corp does that

I'd rather say "Ask my colleague" than spout nonsense.
```

### The Demarcation Table (Mandatory in Every Opinion!)

| Legal Question | My Responsibility | Hand Over To | Why |
|----------------|------------------:|--------------|-----|
| Fraud in personal use case? | ❌ Nope | @agent-criminal | It's criminal law |
| Termination valid? | ✅ My job | - | It's tenancy law |

**Why?** Forces reflection: "Is this really my area?"

---

## File Structure

```
JuraCrew/
├── CLAUDE.md           ← The Brain (loads automatically!)
├── README.md           ← You are here
│
├── agents/             ← The Crew Definitions
│   ├── researcher.md   ← The Bouncer
│   ├── agent-contract.md
│   ├── agent-criminal.md
│   ├── agent-tenancy.md
│   ├── agent-corp.md
│   ├── validator-legal.md  ← The Critic
│   └── scribe-legal.md     ← The Translator
│
├── templates/          ← Output Templates
│   ├── MANDATE_REGISTRY.md
│   ├── CASE_TEMPLATE.md
│   └── OPINION_TEMPLATE.md
│
├── mandates/           ← Your cases land here (gitignored!)
│   └── CASE-2025-0001/
│       ├── FACTS_*.md
│       ├── OPINION_*.md
│       └── FINAL_OPINION_*.md
│
└── config/
    └── settings.json   ← Hooks & Model Assignments
```

---

## Commands

| Just Say... | What Happens |
|-------------|--------------|
| `New Mandate: [facts]` | @researcher starts questioning |
| `Quick Check: [question]` | Direct answer without ceremony |
| `Status CASE-2025-0001` | Where does the case stand? |
| `Opinion CASE-2025-0001` | Show me the result |

---

## Add Your Own Agents?

1. New file: `agents/agent-family.md` (Family law, anyone?)
2. Copy from existing agent
3. **Define Hard Constraints** (Most important!)
4. Register in `CLAUDE.md`
5. Assign model in `config/settings.json`

---

## FAQ

### Can I use this for actual legal advice?

**No.** JuraCrew is an analysis tool, not a law firm. All opinions are non-binding. For real legal advice: Ask a real lawyer.

### Why 7 agents instead of one super AI?

- **Specialization** > Generalization
- **Hard Constraints** prevent hallucinations
- **Parallel work** on complex cases
- **Quality Gate** catches errors

Or simply: Because a jack-of-all-trades is usually a master of none.

### Do I need MCP servers?

**No.** JuraCrew runs with standard tools (Read, Grep, Glob, Write). No external servers needed. Plug & Play.

---

## Disclaimer

**JuraCrew does NOT replace professional legal advice!**

- All opinions are non-binding
- Without warranty
- Not to be understood as legal counsel

**For real legal issues: Consult a real lawyer!**

*(The AI lawyers can't appear in court. Not yet.)*

---

## License

MIT License - see [LICENSE](LICENSE)

---

## Contact

**Created by:** Dennis Westermann
**Email:** d.westermann@ol-mg.de
**Version:** 1.0
**Date:** 2025-12-28

---

*JuraCrew - 7 AI lawyers keeping each other in check. Because trust is good, but control is better.*
