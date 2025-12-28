# Changelog

All notable changes to Legal-GodMode will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [1.0.0] - 2025-12-28

### Added
- **Initial Release** of Legal-GodMode
- **7 Specialized Legal Agents:**
  - @anwalt-zivilrecht (Opus 4.5) - Civil law mandate processing
  - @anwalt-strafrecht (Opus 4.5) - Criminal law mandate processing
  - @anwalt-verwaltung (Opus 4.5) - Administrative law
  - @gutachter (Opus 4.5) - Legal opinions and subsumption
  - @recherche (Sonnet 4.5) - Statute/Case law/Literature
  - @formular (Sonnet 4.5) - Pleadings, contracts, templates
  - @mandatsmanager (Sonnet 4.5) - Deadline control, file management

- **Orchestrator Prompt** for automatic agent chains
  - Workflow: New Mandate (Research → Specialist → Template → Mandate Manager)
  - Workflow: Quick Check (Specialist → Mandate Manager)
  - Workflow: Opinion (Research → Expert → Template)

- **Hard Constraints System:**
  - Data Protection: Anonymization MANDATORY
  - Quality Assurance: At least 3 references per legal question
  - Git Workflow: NEVER push without explicit user permission
  - Subsumption: Complete Elements → Legal Consequence structure

- **Configuration System:**
  - `config/CLAUDE-system.md` - Global law firm identity
  - `config/CLAUDE-projekt.md` - Project-specific workflows
  - `config/settings.json` - Claude Code Settings with model assignment

- **Folder Structure:**
  - `/agents/` - Agent definitions
  - `/config/` - Configuration files
  - `/templates/` - Pleading/contract templates
  - `/scripts/` - Automation scripts
  - `/docs/` - Project documentation
  - `/mandates/` - Mandate files (not in Git)
  - `/Agents/` - Subagent reports

- **Documentation:**
  - README.md with project overview
  - AGENTS.md with agent descriptions
  - WORKFLOWS.md with standard workflows

### Security
- `.gitignore` configured for:
  - Mandate files (`/mandates/`)
  - Final documents (`*.final.md`)
  - Credentials (`.env`, `*.pem`, `*.key`)
  - Sensitive data

### Development
- Git workflow with strict push protocol
- Token management with auto-compact
- Model selection: Opus for specialist agents, Sonnet for support agents

---

## [Unreleased]

### Planned Features
- [ ] Integration with Juris/Beck-Online API for research
- [ ] Automatic deadline calculation according to ZPO/StPO
- [ ] Template library for standard pleadings
- [ ] Export function (PDF, DOCX)
- [ ] Mandate dashboard with deadline overview
- [ ] Multi-mandate parallel processing
- [ ] Integration with law firm software (RA-MICRO, etc.)

---

## Version History

- **1.0.0** (2025-12-28) - Initial Release
