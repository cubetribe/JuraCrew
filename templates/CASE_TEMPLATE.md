# Mandate File: [CASE-YYYY-NNNN]

**Status:** [INTAKE/REVIEW/ASSIGNED/EXPERT_WIP/VALIDATION/COMPLETED]
**Priority:** [🔴 URGENT / 🟠 HIGH / 🟡 MEDIUM / 🟢 LOW]
**Created:** [YYYY-MM-DD]
**Last Updated:** [YYYY-MM-DD]

---

## 1. CLIENT INFORMATION

### Client
- **Name/Company:** [Name]
- **Contact:** [Email/Phone]
- **Address:** [Address]
- **Representative:** [If legal entity]

### Opposing Party
- **Name/Company:** [Name]
- **Contact:** [If known]
- **Legal Representation:** [If present]

### Other Parties
| Name | Role | Contact | Relevance |
|------|-------|---------|----------|
| - | - | - | - |

---

## 2. FACTS

### Summary
[1-3 sentences: What is the core issue?]

### Detailed Facts

#### Chronology
| Date | Event | Evidence |
|-------|----------|--------------|
| [YYYY-MM-DD] | [What happened?] | [Document/Witness] |
| [YYYY-MM-DD] | [What happened?] | [Document/Witness] |

#### Fact Categories

**Contractual Relationships:**
- [Contract 1: Type, Date of conclusion, Parties, essential contents]
- [Contract 2: ...]

**Communication:**
- [Email from XX.XX.XXXX: Summary]
- [Letter from XX.XX.XXXX: Summary]

**Financial Aspects:**
- Amount in dispute: [Amount in EUR]
- Payments already made: [Amount]
- Claimed sum: [Amount]

**Deadlines:**
- [Deadline 1: Description, Date, Consequence if missed]
- [Deadline 2: ...]

---

## 3. EVIDENCE

### Documents
| No. | Document Type | Date | Location | Relevance |
|-----|---------------|-------|------------|----------|
| D-001 | [Contract/Email/Invoice] | [YYYY-MM-DD] | [Filename] | [Relevant for what?] |
| D-002 | [...] | [...] | [...] | [...] |

### Witnesses
| Name | Relationship to Case | Contact | Facts to Confirm |
|------|-------------------|---------|------------------------|
| - | - | - | - |

### Other Evidence
- [Photos, Videos, Screenshots, etc.]

---

## 4. LEGAL ASSESSMENT

### Identified Legal Questions
| No. | Legal Question | Legal Area | Priority | Responsible Agent |
|-----|-------------|--------------|-----------|-------------------|
| RF-001 | [Specific legal question?] | [CIV/LAB/CRIM/PUB/Special] | [HIGH/MEDIUM/LOW] | [@agent-xxx] |
| RF-002 | [...] | [...] | [...] | [...] |

### Affected Norms (preliminary)
- [§ XX BGB: Brief description]
- [§ XX StGB: ...]

### Legal Area Assignment
```
Main legal area: [Civil Law/Labor Law/...]
Secondary legal areas: [List]
```

---

## 5. CLIENT OBJECTIVES

**Primary Objective:**
[What does the client want to achieve?]

**Secondary Objectives:**
1. [Objective 1]
2. [Objective 2]

**Scenarios to Avoid:**
- [Scenario 1]
- [Scenario 2]

---

## 6. AGENT COORDINATION

### Assigned Agents
| Agent | Task | Status | Output | Completion |
|-------|---------|--------|--------|-----------|
| @agent-civillaw | [Review legal question RF-001] | [PENDING/WIP/DONE] | [Filename] | [YYYY-MM-DD] |
| @agent-speciallaw | [Review legal question RF-002] | [PENDING/WIP/DONE] | [Filename] | [YYYY-MM-DD] |

### Dependencies
```
@agent-civillaw → must be completed before @agent-speciallaw
@agent-speciallaw → parallel to @agent-publiclaw
```

### Handovers Between Agents
| From | To | Content | Date |
|-----|----|--------|-------|
| @agent-civillaw | @agent-speciallaw | [Contract law assessment] | [YYYY-MM-DD] |

---

## 7. OPINIONS & VALIDATION

### Created Opinions
| Filename | Agent | Created | Validator Status |
|-----------|-------|----------|------------------|
| OPINION_[CASE-ID]_civillaw_001.md | @agent-civillaw | [YYYY-MM-DD] | [APPROVED/REVISE/PENDING] |
| OPINION_[CASE-ID]_speciallaw_001.md | @agent-speciallaw | [YYYY-MM-DD] | [APPROVED/REVISE/PENDING] |

### Validation Report
**File:** VALIDATION_REPORT_[CASE-ID].md
**Status:** [APPROVED / REVISE / REJECTED]
**Reviewed by:** @validator-legal
**Date:** [YYYY-MM-DD]

**Validator Comments:**
- [Comment 1]
- [Comment 2]

---

## 8. FINAL DOCUMENTATION

### Final Opinion
**File:** FINAL_OPINION_[CASE-ID].md
**Created by:** @scribe-legal
**Date:** [YYYY-MM-DD]
**Status:** [DRAFT / FINAL]

### Recommendations for Action
1. [Specific recommendation 1 with justification]
2. [Specific recommendation 2 with justification]
3. [...]

### Deadlines & To-Do
| Deadline | Action | Responsible | Status |
|-------|----------|----------------|--------|
| [YYYY-MM-DD] | [What needs to be done?] | [Client/Lawyer] | [OPEN/DONE] |

---

## 9. CLIENT COMMUNICATION

### Questions to Client
| Date | Question | Answer Received | Impact on Case |
|-------|-------|------------------|-------------------|
| [YYYY-MM-DD] | [Specific question] | [YES/NO] | [Description] |

### Consultation Meetings
| Date | Participants | Topic | Minutes |
|-------|------------|-------|-----------|
| [YYYY-MM-DD] | [Names] | [Topic] | [Link to notes] |

---

## 10. COSTS & FEES

**Estimated Value in Dispute:** [Amount in EUR]
**Estimated Attorney's Fees:** [Amount according to RVG]
**Court Costs (if relevant):** [Amount]

**Cost Risk:**
[Assessment of cost risk in litigation]

---

## 11. ARCHIVING

**Mandate Completed:** [YYYY-MM-DD]
**Final Documents:**
- FINAL_OPINION_[CASE-ID].md
- VALIDATION_REPORT_[CASE-ID].md
- All OPINION_*.md files
- All evidence

**Archive Path:** `/Legal-GodMode/cases/[Year]/[CASE-ID]/`

---

## 12. NOTES & SPECIAL FEATURES

[Free text for important notes, special features of the case, strategic considerations, etc.]

---

## METADATA

**Template Version:** 1.0
**Created by:** Legal-GodMode Orchestrator
**Workflow Status:**

```
[ ] Facts completely recorded
[ ] Evidence collected
[ ] Legal questions identified
[ ] Agents commissioned
[ ] Opinions created
[ ] Validation APPROVED
[ ] Final opinion created
[ ] Client informed
[ ] Mandate completed
```

---

*This file is maintained by the Orchestrator and updated with each workflow step.*
