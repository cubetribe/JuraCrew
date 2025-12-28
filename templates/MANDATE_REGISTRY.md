# Mandate Registry

**Last Updated:** 2025-12-28

---

## Active Mandates

| Mandate-ID | Client | Status | Legal Areas | Assigned Agents | Created | Last Activity | Priority |
|-----------|---------|--------|---------------|-------------------|----------|------------------|-----------|
| - | - | - | - | - | - | - | - |

---

## Completed Mandates (last 10)

| Mandate-ID | Client | Legal Areas | Completed | Final Documents |
|-----------|---------|---------------|---------------|------------------|
| - | - | - | - | - |

---

## Archived Mandates

For complete archive see: `/Legal-GodMode/cases/[Year]/`

---

## Status Definitions

| Status | Description | Next Step |
|--------|--------------|------------------|
| **INTAKE** | Mandate received, facts being collected | @researcher-legal collects facts |
| **REVIEW** | Facts complete, legal questions being identified | Orchestrator assigns agents |
| **ASSIGNED** | Agents have been commissioned | Agents create opinions |
| **EXPERT_WIP** | Expert agents working on opinions | Waiting for completion |
| **VALIDATION** | Opinions at @validator-legal for review | @validator-legal reviews |
| **REVISE** | Validator requests revision | Affected agents correct |
| **SYNTHESIS** | Validation APPROVED, @scribe-legal finalizing | @scribe-legal creates FINAL_OPINION |
| **COMPLETED** | Final opinion created and delivered | Archiving |
| **ON_HOLD** | Mandate paused (e.g., waiting for client input) | User action required |
| **UPDATED** | Existing case updated with new facts | Create supplement opinion |

---

## Legal Area Abbreviations

| Code | Legal Area | Responsible Agent |
|--------|--------------|-------------------|
| **CIV** | Civil Law (BGB, Contract Law) | @agent-civillaw |
| **LAB** | Labor Law | @agent-laborlaw |
| **CRIM** | Criminal Law | @agent-criminallaw |
| **PUB** | Public Law | @agent-publiclaw |
| **IT** | IT Law, Data Protection | @agent-speciallaw |
| **IP** | Intellectual Property (Trademarks, Patents) | @agent-speciallaw |
| **MED** | Medical Law | @agent-speciallaw |
| **COMP** | Competition Law | @agent-speciallaw |

---

## Prioritization Rules

| Priority | Criterion | Treatment |
|-----------|-----------|------------|
| **🔴 URGENT** | Deadlines < 7 days | Immediate processing |
| **🟠 HIGH** | Deadlines < 30 days or high amount in dispute | Prioritized processing |
| **🟡 MEDIUM** | Standard mandate | Normal processing |
| **🟢 LOW** | Consultation without time pressure | As capacity allows |

---

## Usage

### Create New Mandate
```bash
Mandate-ID: CASE-YYYY-NNNN (e.g. CASE-2025-0001)
Client: [Name/Company]
Status: INTAKE
Legal Areas: [CIV, LAB, ...]
Assigned Agents: [TBD]
Created: [YYYY-MM-DD]
Priority: [URGENT/HIGH/MEDIUM/LOW]
```

### Update Status
Update status in table with each workflow step.

### Complete Mandate
1. Status → COMPLETED
2. Move row to "Completed Mandates"
3. Add archiving link

---

## Archiving Structure

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

## Statistics (2025)

| Metric | Value |
|--------|------|
| Total processed mandates | 0 |
| Completed mandates | 0 |
| Active mandates | 0 |
| Average processing time | - |
| Most common legal area | - |

---

*This Registry is automatically maintained by the Orchestrator.*
