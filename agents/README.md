# Legal-GodMode Agents

Orchestrated multi-agent system for legal opinions.

## Agent Overview

### 1. researcher.md - Legal Intelligence Unit
**Model:** Sonnet
**Tools:** Read, Grep, Glob, Bash
**Task:** Fact gathering WITHOUT legal evaluation
**Output:** RESEARCH_REPORT with chronology, documents, deadlines

**Demarcation:**
- NOT: Legal interpretation → Specialist agents
- NOT: Evaluations, recommendations → Specialist agents
- ONLY: Raw data, facts, references

---

### 2. agent-contract.md - Contract Law Specialist
**Model:** Opus
**Tools:** Read, Grep, Glob
**Task:** Contract law (BGB General Part, Law of Obligations General Part, Standard Terms)
**Output:** Opinion in opinion style

**Responsible for:**
- §§104-185 BGB (Legal transactions doctrine)
- §§241-304 BGB (Law of Obligations General Part)
- §§305-310 BGB (Standard Terms Law)

**NOT responsible for:**
- Tenancy law → @agent-tenancy
- Criminal law → @agent-criminal
- Corporate law → @agent-corp

---

### 3. agent-criminal.md - Criminal Law Specialist
**Model:** Opus
**Tools:** Read, Grep, Glob
**Task:** Criminal law (StGB General/Special Part, StPO)
**Output:** Opinion in opinion style

**Responsible for:**
- StGB General Part (§§13-37 StGB)
- Property offenses (§§242-263a StGB)
- Bodily injury (§§223-231 StGB)
- Insult (§§185-187 StGB)

**NOT responsible for:**
- Civil law claims for damages → @agent-contract
- Criminal procedural representation → Criminal defense lawyer (external)

---

### 4. agent-tenancy.md - Tenancy Law Specialist
**Model:** Opus
**Tools:** Read, Grep, Glob
**Task:** Tenancy law (§§535-580a BGB)
**Output:** Opinion in opinion style

**Responsible for:**
- Rental agreement, rent reduction (§§535-536 BGB)
- Termination (§§542-580a BGB)
- Deposit (§551 BGB)
- Rent increase (§§557-561 BGB)
- Residential & commercial space

**NOT responsible for:**
- General contract law → @agent-contract
- Criminal law → @agent-criminal

---

### 5. agent-corp.md - Corporate Law Specialist
**Model:** Opus
**Tools:** Read, Grep, Glob
**Task:** Corporate law (HGB, GmbHG, AktG)
**Output:** Opinion in opinion style

**Responsible for:**
- Commercial law (§§1-372 HGB)
- GmbH law (GmbHG)
- Stock corporation law (AktG - basics)
- Civil law partnership (§§705-740 BGB)
- Registry law

**NOT responsible for:**
- General contract law → @agent-contract
- Labor law → @agent-labor (if available)
- Insolvency law → Specialist lawyer (external)

---

### 6. validator-legal.md - Quality Gate
**Model:** Sonnet
**Tools:** Read, Grep, Glob, Bash
**Task:** Formal control of opinions
**Output:** VALIDATION_REPORT

**Checks:**
- Completeness of structure
- Data consistency
- Demarcation tables (MANDATORY!)
- Source citations
- Format standards
- Area of law demarcation (Hard Constraints!)

**Does NOT check:**
- Substantive legal review → Specialist agents
- Legal assessments → Specialist agents

**Status codes:**
- PASSED: Opinion can be finalized
- WARNINGS: Can be finalized, document warnings
- FAILED: Back to specialist agent for correction

---

### 7. scribe-legal.md - Documentation & Finalization
**Model:** Sonnet
**Tools:** Read, Write, Edit, Grep, Glob
**Task:** Create final opinions, maintain MANDATE_REGISTRY
**Output:** FINAL_OPINION (client-appropriate)

**Tasks:**
- Consolidation of all specialist opinions
- Understandable language (no legal jargon!)
- Compile action recommendations
- Deadline overview
- Update MANDATE_REGISTRY
- Archiving

**NOT:**
- Change legal statements → Specialist agents
- Correct opinions substantively → Specialist agents

---

## Workflow

```
User → Task
  ↓
@researcher → Fact gathering (RESEARCH_REPORT)
  ↓
@agent-[contract/criminal/tenancy/corp] → Opinion (OPINION)
  ↓
@validator-legal → Quality Gate (VALIDATION_REPORT)
  ↓
  PASSED? → @scribe-legal → Final documents (FINAL_OPINION)
  FAILED? → Back to specialist agent
```

## Hard Constraints (CRITICAL!)

### Rule 1: Demarcation table MANDATORY!
Every specialist agent MUST have a demarcation table in output:
- "I examined"
- "I did NOT examine"
- "Responsible"

### Rule 2: No area of law transgressions!
- @agent-contract may NOT write about criminal law
- @agent-criminal may NOT write about civil law
- @agent-tenancy may NOT write about corporate law
- @agent-corp may NOT write about tenancy law

### Rule 3: Opinion style for specialist agents!
All specialist agents work in classic opinion style:
1. Rule
2. Definition
3. Application
4. Conclusion

### Rule 4: Validator checks ONLY formally!
@validator-legal does NOT check legal content, ONLY:
- Completeness
- Consistency
- Format
- Demarcation

### Rule 5: Scribe does NOT change legal statements!
@scribe-legal does ONLY editorial work:
- Formatting
- Spelling
- Comprehensibility
- NO substantive changes!

## File Conventions

### Research Report
- Filename: `RESEARCH_REPORT_[Mandate-ID].md`
- Created by: @researcher
- Contains: Facts, chronology, documents, deadlines

### Specialist Opinions
- Filename: `OPINION_[Mandate-ID]_[Area-of-law]_[Version].md`
- Created by: @agent-contract, @agent-criminal, @agent-tenancy, @agent-corp
- Contains: Opinion in opinion style + demarcation table

### Validation Report
- Filename: `VALIDATION_REPORT_[Mandate-ID].md`
- Created by: @validator-legal
- Contains: Validation result (PASSED/WARNINGS/FAILED)

### Final Opinion
- Filename: `FINAL_OPINION_[Mandate-ID].md`
- Created by: @scribe-legal
- Contains: Client-appropriate opinion + executive summary

## Mandate Registry

**File:** `/Legal-GodMode/MANDATE_REGISTRY.yaml`

Central overview of all mandates:
- Mandate-ID
- Area of law
- Parties
- Status (OPEN/IN_PROGRESS/FINALIZED)
- Deadlines
- Prospects
- Amount in dispute

Maintained by: @scribe-legal

## Quality Gates

### Gate 1: Research Complete
- All documents recorded?
- Chronology complete?
- All references provided?

### Gate 2: Opinion Complete
- Opinion style correct?
- Demarcation table present?
- All norms cited?
- Result unambiguous?

### Gate 3: Validation Passed
- Completeness: OK?
- Consistency: OK?
- Area of law demarcation: OK?
- Demarcation table: OK?

### Gate 4: Finalization Complete
- Understandable language?
- Action recommendations concrete?
- Deadlines highlighted?
- MANDATE_REGISTRY updated?

## Example Mandates

### Example 1: Tenancy law + Criminal law
**Case:** Landlord demands rent, tenant suspects fraud

**Workflow:**
1. @researcher → Gather facts
2. @agent-tenancy → Tenancy law examination (rent claim)
3. @agent-criminal → Criminal law examination (fraud)
4. @validator-legal → Check both opinions
5. @scribe-legal → Consolidate into FINAL_OPINION

### Example 2: Contract law + Corporate law
**Case:** GmbH shareholder contests partnership agreement

**Workflow:**
1. @researcher → Gather facts
2. @agent-contract → Avoidance (§§119-123 BGB)
3. @agent-corp → GmbH articles defects (GmbHG)
4. @validator-legal → Check both opinions
5. @scribe-legal → Consolidate into FINAL_OPINION

## Version History

- **v1.0** (2025-12-28): Initial Release
  - 7 agents defined
  - Workflow established
  - Hard Constraints established

---

**Created:** 2025-12-28
**Project:** Legal-GodMode
**Status:** Production Ready
