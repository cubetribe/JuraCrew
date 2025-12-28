# Legal-GodMode Workflows

This file describes the standard workflows for various legal tasks.

---

## Workflow Overview

| Workflow | Agent Chain | Duration | Complexity |
|----------|-------------|-------|-------------|
| **New Civil Mandate** | @recherche → @anwalt-zivilrecht → @formular → @mandatsmanager | 15-30 Min | High |
| **New Criminal Mandate** | @recherche → @anwalt-strafrecht → @formular → @mandatsmanager | 15-30 Min | High |
| **New Administrative Mandate** | @recherche → @anwalt-verwaltung → @formular → @mandatsmanager | 15-30 Min | High |
| **Quick Check** | @anwalt-[legal area] → @mandatsmanager | 5-10 Min | Low |
| **Opinion** | @recherche → @gutachter → @formular | 20-45 Min | Very High |
| **Pleading** | @anwalt-[legal area] → @formular → @mandatsmanager | 10-20 Min | Medium |
| **Research Only** | @recherche | 5-15 Min | Low |
| **Deadline Control** | @mandatsmanager | 2-5 Min | Low |

---

## 1. New Civil Mandate

### Description
Complete processing of a new civil law mandate from research to finished pleading.

### Agent Chain
```
@recherche → @anwalt-zivilrecht → @formular → @mandatsmanager
```

### Step-by-Step

#### 1. User Input
```
"New mandate: Civil law - Purchase price payment § 433 BGB"
```

#### 2. @recherche (Sonnet 4.5)
**Task**: Research case law on § 433 BGB

**Input**:
```
@recherche "§ 433 BGB purchase price payment case law 2024"
```

**Output**: `Agents/recherche-2025-XXX-433bgb-[date].md`
- At least 3 BGH decisions
- Commentary opinions
- Current legal developments

#### 3. @anwalt-zivilrecht (Opus 4.5)
**Task**: Mandate analysis and case review

**Input**:
```
@anwalt-zivilrecht "Mandate 2025-XXX: Purchase price payment
Facts: [Anonymized facts]
Research: [Link to research report]"
```

**Output**: `Agents/anwalt-zivilrecht-2025-XXX-[date].md`
- Legal bases (§§ 433, 434 BGB)
- Review of elements
- Prospects of success
- Litigation strategy

#### 4. @formular (Sonnet 4.5)
**Task**: Create complaint pleading

**Input**:
```
@formular "Complaint - Payment claim from sales contract
Mandate: 2025-XXX
Basis: [Link to mandate analysis]"
```

**Output**: `mandates/2025-XXX-purchase-price/complaint-draft.md`
- Formally correct pleading
- Complete subsumption
- Motion formulation

#### 5. @mandatsmanager (Sonnet 4.5)
**Task**: Calculate deadlines and create file structure

**Input**:
```
@mandatsmanager "Set deadlines for mandate 2025-XXX
Service: [Date]
Legal area: Civil law (ZPO)"
```

**Output**: `Agents/mandatsmanager-2025-XXX-[date].md`
- Deadline overview (§§ 276, 283 ZPO)
- Reminders
- File structure

### Final File Structure
```
mandates/2025-XXX-purchase-price/
├── mandate.md                        # Mandate overview
├── research-433-bgb.md              # Research report
├── analysis-civil-law.md            # Mandate analysis
├── complaint-draft.md               # Pleading
└── deadlines.md                     # Deadline control
```

---

## 2. Quick Check

### Description
Quick initial assessment without deep research (for consultation meetings).

### Agent Chain
```
@anwalt-[legal area] → @mandatsmanager
```

### Step-by-Step

#### 1. User Input
```
"Quick Check: Criminal law - Fraud § 263 StGB"
```

#### 2. @anwalt-strafrecht (Opus 4.5)
**Task**: Initial assessment

**Input**:
```
@anwalt-strafrecht "Quick Check: Fraud § 263 StGB
Facts: [Brief facts]"
```

**Output**: `Agents/anwalt-strafrecht-quickcheck-[date].md`
- Criminal liability (without deep subsumption)
- Prospects of success (rough estimate)
- Recommendation for action

#### 3. @mandatsmanager (Sonnet 4.5)
**Task**: Create deadline note

**Input**:
```
@mandatsmanager "Deadline note for Quick Check Criminal law
Date: [Today]
Note: Request file inspection"
```

**Output**: `Agents/mandatsmanager-quickcheck-[date].md`
- Reminder: File inspection
- Follow-up: Mandate decision

### Duration
5-10 minutes

---

## 3. Opinion Creation

### Description
Detailed legal opinion with deep subsumption and dispute of opinion.

### Agent Chain
```
@recherche → @gutachter → @formular
```

### Step-by-Step

#### 1. User Input
```
"Opinion: Traffic accident § 823 BGB - Apparent evidence"
```

#### 2. @recherche (Sonnet 4.5)
**Task**: Comprehensive research

**Input**:
```
@recherche "§ 823 BGB traffic accident apparent evidence case law"
```

**Output**: `Agents/recherche-823bgb-apparent-evidence-[date].md`
- BGH case law (at least 5 decisions)
- Commentary opinions (prevailing view vs. opposing view)
- Literature

#### 3. @gutachter (Opus 4.5)
**Task**: Deep subsumption

**Input**:
```
@gutachter "Legal opinion: § 823 BGB traffic accident
Question: Apparent evidence in rear-end collision?
Research: [Link to research report]
Facts: [Anonymized facts]"
```

**Output**: `Agents/gutachter-823bgb-apparent-evidence-[date].md`
- Complete subsumption (Elements → Legal consequence)
- Dispute of opinion (prevailing view vs. opposing view)
- Statement with justification
- Result

#### 4. @formular (Sonnet 4.5)
**Task**: Format opinion

**Input**:
```
@formular "Format legal opinion
Basis: [Link to expert report]
Format: Formal opinion with cover page"
```

**Output**: `docs/opinion-823bgb-apparent-evidence-final.md`
- Cover page
- Table of contents
- Formatted opinion
- Index of references

### Duration
20-45 minutes

---

## 4. Pleading Creation

### Description
Creation of a pleading (complaint, response to complaint, opposition, etc.).

### Agent Chain
```
@anwalt-[legal area] → @formular → @mandatsmanager
```

### Step-by-Step

#### 1. User Input
```
"Pleading: Response to complaint - Mandate 2025-XXX"
```

#### 2. @anwalt-[legal area] (Opus 4.5)
**Task**: Develop strategy

**Input**:
```
@anwalt-zivilrecht "Response to complaint for mandate 2025-XXX
Opposing complaint: [Summary]
Our position: [Facts]"
```

**Output**: `Agents/anwalt-zivilrecht-response-[date].md`
- Defense strategy
- Offensive and defensive measures
- Legal arguments

#### 3. @formular (Sonnet 4.5)
**Task**: Formulate pleading

**Input**:
```
@formular "Response to complaint - Payment claim
Basis: [Link to strategy]
Court: District Court Munich
Case No.: 12 O 123/25"
```

**Output**: `mandates/2025-XXX/response-draft.md`
- Formally correct pleading
- Complete justification
- Motion formulation

#### 4. @mandatsmanager (Sonnet 4.5)
**Task**: Update deadlines

**Input**:
```
@mandatsmanager "Deadline: Response to complaint filed on [Date]
Next deadline: Reply (approx. 2 weeks after response)"
```

**Output**: Update in `Agents/mandatsmanager-2025-XXX-[date].md`

### Duration
10-20 minutes

---

## 5. Research Only

### Description
Research statutes/case law/literature without mandate reference.

### Agent Chain
```
@recherche
```

### Step-by-Step

#### 1. User Input
```
"Research: § 263 StGB deceptive act implied"
```

#### 2. @recherche (Sonnet 4.5)
**Task**: Find references

**Input**:
```
@recherche "§ 263 StGB deceptive act implied case law literature"
```

**Output**: `Agents/recherche-263stgb-deception-[date].md`
- Text of statute
- BGH/BVerfG case law
- Commentary opinions
- Summary (prevailing view vs. opposing view)

### Duration
5-15 minutes

---

## 6. Deadline Control

### Description
Calculate deadlines and set reminders.

### Agent Chain
```
@mandatsmanager
```

### Step-by-Step

#### 1. User Input
```
"Deadlines for mandate 2025-XXX
Service of complaint: 2025-01-15"
```

#### 2. @mandatsmanager (Sonnet 4.5)
**Task**: Calculate deadlines

**Input**:
```
@mandatsmanager "Deadline calculation mandate 2025-XXX
Legal area: Civil law (ZPO)
Service: 2025-01-15"
```

**Output**: `Agents/mandatsmanager-2025-XXX-deadlines-[date].md`
- Response to complaint: 2025-01-29 (§ 276 ZPO: 2 weeks)
- Reply: approx. 2 weeks after response
- Main trial: to be determined

### Duration
2-5 minutes

---

## Workflow Selection Table

| Situation | Recommended Workflow | Justification |
|-----------|---------------------|------------|
| **Client calls, uncertain whether to take case** | Quick Check | Quick assessment without time investment |
| **New case, mandate agreement signed** | New [Legal area] Mandate | Complete processing from the start |
| **Complex legal question, uncertain** | Opinion | Deep analysis with dispute of opinion |
| **Opponent has filed complaint, deadline running** | Pleading Creation | Focus on response |
| **Unclear legal situation on § XYZ** | Research Only | Gather references |
| **Letter from court, deadline unclear** | Deadline Control | Avoid missing deadlines |

---

## Best Practices

### 1. Always research BEFORE specialist agent (except Quick Check)
```
✅ CORRECT: @recherche → @anwalt-zivilrecht
❌ WRONG: @anwalt-zivilrecht (without research for complex questions)
```

**Justification**: Specialist agents need current case law for well-founded analysis.

### 2. Always mandate manager AT THE END
```
✅ CORRECT: @formular → @mandatsmanager
❌ WRONG: @formular (deadlines forgotten!)
```

**Justification**: Missing deadlines is professionally liable.

### 3. Expert ONLY for deep analysis
```
✅ CORRECT: @gutachter (for complex dispute of opinion)
❌ WRONG: @gutachter (for simple cases → too expensive/slow)
```

**Justification**: Opus 4.5 is token-intensive, only use when needed.

### 4. Template for FINAL documents
```
✅ CORRECT: @anwalt-zivilrecht → @formular
❌ WRONG: @anwalt-zivilrecht (use draft directly)
```

**Justification**: Template guarantees formal correctness.

---

## Error Handling

### Problem: No references found
```
Solution: Call @recherche again with more specific norm/question
Escalation: At least 3 references are MANDATORY
```

### Problem: Subsumption incomplete
```
Solution: Engage @gutachter for deep analysis
Escalation: Elements → Legal consequence must be complete
```

### Problem: Deadline unclear
```
Solution: Call @mandatsmanager with service date
Escalation: When in doubt, always assume shortest deadline
```

### Problem: Template missing
```
Solution: Call @formular with example specification
Escalation: Store in templates/ for future use
```

---

## Token Optimization

### Workflow Optimization by Token Consumption

| Workflow | Token Consumption | Optimization |
|----------|----------------|-------------|
| New Mandate | High (Opus) | Research report in file, not in chat |
| Quick Check | Medium (Opus) | Request brief output |
| Opinion | Very High (Opus) | `/compact` after completion |
| Pleading | Medium | Reuse template |
| Research | Low (Sonnet) | OK for multiple uses |
| Deadlines | Low (Sonnet) | OK for multiple uses |

### Session Hygiene

- **After each completed mandate**: `/clear`
- **For long multi-mandate sessions**: `/compact` at 70% token usage
- **Large agent reports**: ALWAYS write to files, not output in chat

---

*This documentation describes all standard workflows of Legal-GodMode.*
*Last Updated: 2025-12-28*
