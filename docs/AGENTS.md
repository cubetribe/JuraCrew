# Legal-GodMode Agent Documentation

This file describes all available specialized agents, their tasks, model assignments, and areas of deployment.

---

## Overview

| Agent | Model | Expertise | Primary Task | Token Intensity |
|-------|-------|-----------|-----------------|------------------|
| @anwalt-zivilrecht | Opus 4.5 | BGB, HGB, ZPO | Civil law mandate processing | High |
| @anwalt-strafrecht | Opus 4.5 | StGB, StPO | Criminal law mandate processing | High |
| @anwalt-verwaltung | Opus 4.5 | VwGO, VwVfG | Administrative law mandate processing | High |
| @gutachter | Opus 4.5 | All legal areas | Deep subsumption, opinions | Very High |
| @recherche | Sonnet 4.5 | All legal areas | Statute/Case law/Literature | Medium |
| @formular | Sonnet 4.5 | All legal areas | Pleadings, contracts, templates | Low |
| @mandatsmanager | Sonnet 4.5 | Law firm organization | Deadlines, file management | Low |

---

## 1. @anwalt-zivilrecht (Opus 4.5)

### Expertise
- Civil Code (BGB)
- Commercial Code (HGB)
- Civil Procedure Code (ZPO)
- Contract Law
- Tort Law
- Family Law
- Inheritance Law

### Primary Tasks
- Mandate analysis and case review
- Identify legal bases for claims
- Assess prospects of success
- Develop litigation strategy
- Prepare complaints/motions

### Typical Inputs
```
"New mandate: Purchase price payment § 433 BGB"
"Quick Check: Damages from traffic accident"
"Litigation strategy: Rental dispute - ancillary costs"
```

### Output Format
```markdown
# Mandate Analysis - [Mandate No.] - [Date]

## I. Facts
[Anonymized facts]

## II. Legal Assessment

### A. Legal Basis
1. § XYZ BGB
   a) Elements
      aa) Definition
      bb) Subsumption
   b) Legal Consequence

### B. Prospects of Success
[Assessment with references]

## III. Recommendation for Action
[Next steps]

## IV. Deadlines
- [Deadline 1]: [Date]
- [Deadline 2]: [Date]

---
References:
- BGH NJW 2024, 123
- OLG München BeckRS 2024, 456
- Palandt/Grüneberg § 433 Rn. 12
```

### Workflow Integration
```
@recherche → @anwalt-zivilrecht → @formular → @mandatsmanager
```

---

## 2. @anwalt-strafrecht (Opus 4.5)

### Expertise
- Criminal Code (StGB)
- Code of Criminal Procedure (StPO)
- Ancillary Criminal Law
- Sentencing
- Defense Strategies

### Primary Tasks
- Criminal liability analysis
- Review of elements of crime
- Examine unlawfulness/culpability
- Develop defense strategy
- Assess sentencing

### Typical Inputs
```
"New mandate: Fraud § 263 StGB"
"Quick Check: Assault § 223 StGB"
"Defense strategy: Negligent homicide"
```

### Output Format
```markdown
# Criminal Law Analysis - [Mandate No.] - [Date]

## I. Facts
[Anonymized facts]

## II. Criminal Liability

### A. § XYZ StGB
1. Elements
   a) Objective Elements
      aa) Object of Crime
      bb) Criminal Act
      cc) Criminal Result
      dd) Causation
   b) Subjective Elements
      aa) Intent/Negligence
2. Unlawfulness
3. Culpability

### B. Sentencing
[§ 46 StGB Factors]

## III. Defense Strategy
[Recommended strategy]

## IV. Deadlines
- File inspection: [Date]
- Statement: [Date]
- Main trial: [Date]

---
References:
- BGH NStZ 2024, 123
- BVerfG NJW 2024, 456
- Fischer StGB § 263 Rn. 12
```

### Workflow Integration
```
@recherche → @anwalt-strafrecht → @formular → @mandatsmanager
```

---

## 3. @anwalt-verwaltung (Opus 4.5)

### Expertise
- Administrative Court Code (VwGO)
- Administrative Procedure Act (VwVfG)
- Building Law
- Immigration Law
- Social Law

### Primary Tasks
- Review administrative decisions
- Opposition strategy
- Justify complaints
- Review discretion
- Examine procedural law

### Typical Inputs
```
"New mandate: Opposition to building permit"
"Quick Check: Residence permit denied"
"Complaint strategy: ALG-II decision"
```

### Output Format
```markdown
# Administrative Law Analysis - [Mandate No.] - [Date]

## I. Facts
[Anonymized facts + decision]

## II. Legality of Decision

### A. Formal Legality
1. Jurisdiction
2. Procedure
3. Form

### B. Material Legality
1. Legal Basis
2. Elements
3. Legal Consequence/Discretion

## III. Legal Remedy

### A. Opposition
[§§ 68 ff. VwGO]

### B. Action for Rescission
[§ 42 Abs. 1 VwGO]

## IV. Recommendation for Action
[Next steps]

## V. Deadlines
- Opposition deadline: [Date]
- Complaint deadline: [Date]

---
References:
- BVerwG NVwZ 2024, 123
- OVG München BeckRS 2024, 456
- Kopp/Schenke VwGO § 42 Rn. 12
```

### Workflow Integration
```
@recherche → @anwalt-verwaltung → @formular → @mandatsmanager
```

---

## 4. @gutachter (Opus 4.5)

### Expertise
- All legal areas
- Deep subsumption
- Gutachtenstil
- Case analysis
- Legal balancing

### Primary Tasks
- Create legal opinions
- Perform complex subsumption
- Present dispute of opinion
- Refute opposing views
- Detailed case analysis

### Typical Inputs
```
"Opinion: Traffic accident § 823 BGB - Apparent evidence"
"Subsumption: Fraud § 263 StGB - Deceptive act"
"Legal assessment: Rent reduction § 536 BGB"
```

### Output Format
```markdown
# Legal Opinion - [Topic] - [Date]

## Question
[Legal question to be clarified]

## Opinion

### I. Legal Basis/Criminal Liability
[§ XYZ BGB/StGB/VwGO]

### A. Elements
1. [Element 1]
   a) Definition
      aa) Literature
      bb) Case Law
   b) Subsumption
      aa) Facts
      bb) Legal Assessment
      cc) Interim Result
   c) Dispute of Opinion
      aa) View 1 (prevailing view)
      bb) View 2 (opposing view)
      cc) Statement

2. [Element 2]
   [...]

### B. Legal Consequence
[...]

## Result
[Summary]

---
References:
- [At least 5-10 sources]
- BGH/BVerfG Decisions
- OLG/OVG Decisions
- Commentaries/Textbooks
```

### Workflow Integration
```
@recherche → @gutachter → @formular
```

---

## 5. @recherche (Sonnet 4.5)

### Expertise
- Statute research
- Case law research (BGH, BVerfG, OLG, etc.)
- Literature research (Commentaries, textbooks)
- Current legal developments

### Primary Tasks
- Find references
- Summarize case law
- Present state of opinion
- Identify statutory changes

### Typical Inputs
```
"Research: § 433 BGB case law 2024"
"Research: BGH decisions on § 823 BGB traffic accidents"
"Research: Literature on § 263 StGB deception"
```

### Output Format
```markdown
# Research Report - [Norm/Topic] - [Date]

## Task
[What was researched]

## Statutory Basis
§ XYZ BGB/StGB/VwGO
[Text of statute]

## Case Law

### BGH/BVerfG
1. **BGH NJW 2024, 123**
   - Key sentence: [...]
   - Relevance: [...]

2. **BVerfG NJW 2023, 456**
   - Key sentence: [...]
   - Relevance: [...]

### OLG/OVG
1. **OLG München BeckRS 2024, 789**
   - Key sentence: [...]
   - Relevance: [...]

## Literature

1. **Palandt/Grüneberg, BGB, 83rd ed. 2024, § 433 Rn. 12**
   - Statement: [...]

2. **MüKo-BGB/Kramer, 9th ed. 2024, § 433 Rn. 25**
   - Statement: [...]

## Summary
[Prevailing view vs. minority view]

---
References: [Number: at least 3-5]
```

### Workflow Integration
```
@recherche → @anwalt-[legal area]
@recherche → @gutachter
```

---

## 6. @formular (Sonnet 4.5)

### Expertise
- Pleading drafting
- Contract design
- Template management
- Formal correctness

### Primary Tasks
- Draft complaints/motions
- Write oppositions
- Create contracts
- Adapt templates

### Typical Inputs
```
"Complaint: Payment claim from sales contract"
"Opposition: Building permit"
"Contract: Rental agreement"
"Criminal complaint: Fraud § 263 StGB"
```

### Output Format
```markdown
# [Pleading Type] - [Mandate] - [Date]

To the
[Court/Authority]
[Address]

In the matter of
[Plaintiff/Applicant]
./.
[Defendant/Respondent]

Case No.: [Case Number]

[PLEADING TYPE]

Dear Sir or Madam,

on behalf and with authority of the Plaintiff/Applicant, I hereby file

C o m p l a i n t / O p p o s i t i o n

[...]

I. Facts
[...]

II. Legal Assessment
[...]

III. Motion
[...]

Respectfully submitted,

[Signature]
Attorney at Law

---
Exhibits:
- Power of Attorney
- [further exhibits]
```

### Workflow Integration
```
@anwalt-[legal area] → @formular → @mandatsmanager
@gutachter → @formular
```

---

## 7. @mandatsmanager (Sonnet 4.5)

### Expertise
- Deadline calculation (ZPO, StPO, VwGO)
- File management
- Mandate administration
- Reminders

### Primary Tasks
- Calculate deadlines
- Set reminders
- Create file structure
- Assign mandate numbers

### Typical Inputs
```
"Deadlines for mandate 2025-001"
"New mandate file: Civil law - Sales contract"
"Reminder: Pleading service"
```

### Output Format
```markdown
# Mandate Management - [Mandate] - [Date]

## Mandate Info
- **Mandate No.**: 2025-XXX
- **Legal Area**: [Civil/Criminal/Administrative]
- **Brief Description**: [...]
- **Created**: [Date]

## Deadlines

| Deadline | Date | Calculation | Status |
|-------|-------|------------|--------|
| Response to complaint | 2025-02-15 | Service + 2 weeks (§ 276 ZPO) | Open |
| Reply | 2025-03-01 | After response to complaint | Open |

## Reminders

- [ ] Request file inspection - by 2025-01-15
- [ ] Prepare pleading - by 2025-02-08
- [ ] Inform client - by 2025-01-20

## File Structure
```
mandates/2025-XXX-[anonymized]/
├── mandate.md
├── research-433-bgb.md
├── opinion-final.md
└── complaint-draft.md
```

---
Created by @mandatsmanager | Sonnet 4.5 | [Timestamp]
```

### Workflow Integration
```
@anwalt-[legal area] → @mandatsmanager
@formular → @mandatsmanager
```

---

## Agent Selection Flowchart

```
START
  ↓
New mandate?
  ├─ YES → Which legal area?
  │         ├─ Civil Law → @recherche → @anwalt-zivilrecht → @formular → @mandatsmanager
  │         ├─ Criminal Law → @recherche → @anwalt-strafrecht → @formular → @mandatsmanager
  │         └─ Administrative → @recherche → @anwalt-verwaltung → @formular → @mandatsmanager
  │
  ├─ Quick Check?
  │   └─ @anwalt-[legal area] → @mandatsmanager
  │
  ├─ Opinion?
  │   └─ @recherche → @gutachter → @formular
  │
  ├─ Research only?
  │   └─ @recherche
  │
  ├─ Pleading only?
  │   └─ @anwalt-[legal area] → @formular → @mandatsmanager
  │
  └─ Deadlines only?
      └─ @mandatsmanager
```

---

## Best Practices

### 1. Always research before specialist agent (except Quick Check)
```
✅ CORRECT: @recherche → @anwalt-zivilrecht
❌ WRONG: @anwalt-zivilrecht (without research for complex questions)
```

### 2. Always mandate manager at the end
```
✅ CORRECT: @formular → @mandatsmanager
❌ WRONG: @formular (deadlines forgotten!)
```

### 3. Expert for deep analysis
```
✅ CORRECT: @gutachter (for complex dispute of opinion)
❌ WRONG: @anwalt-zivilrecht (too superficial)
```

### 4. Template for final documents
```
✅ CORRECT: @anwalt-zivilrecht → @formular
❌ WRONG: @anwalt-zivilrecht (use draft directly)
```

---

*This documentation describes all 7 specialized agents of Legal-GodMode.*
*Last Updated: 2025-12-28*
