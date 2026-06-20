# Skill Delivery Workflow Plugin

A comprehensive Claude plugin for professional end-to-end skill and feature delivery using orchestrated specialist agents.

## Overview

This plugin packages 5 specialist agents that work together in a structured workflow:

```
Planner → Implementer → Validator → Reviewer → Delivery
```

Each agent is a focused expert in its domain:
- **Planner** — Architecture-first planning and discovery
- **Implementer** — Technical execution to professional standards
- **Validator** — Adversarial quality gate with structured findings
- **Reviewer** — Senior architect final sign-off
- **Skill Delivery Workflow** — Orchestrator that manages all phases

## Installation

### With Copilot CLI

```bash
copilot plugin install jitheshb83/jithesh_ai/plugins/skill-delivery-workflow
```

Or add to your marketplace:

```bash
copilot plugin marketplace add jitheshb83/jithesh_ai
```

### Manual Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/jitheshb83/jithesh_ai.git
   ```

2. Install the plugin:
   ```bash
   copilot plugin install ./jithesh_ai/plugins/skill-delivery-workflow
   ```

## Usage

### Start a Skill Delivery

```bash
copilot /agent:skill-delivery-workflow

I need to deliver [skill name]. Here's the request: [description]
```

### Use Individual Agents

**Planning phase:**
```bash
copilot /agent:planner
```

**Implementation phase:**
```bash
copilot /agent:implementer
```

**Validation phase:**
```bash
copilot /agent:validator
```

**Review phase:**
```bash
copilot /agent:reviewer
```

## Plugin Contents

### Agents
- `agents/skill-delivery-workflow.md` — Orchestrator (gold)
- `agents/planner.md` — Planning (cyan)
- `agents/implementer.md` — Implementation (green)
- `agents/validator.md` — Validation (red)
- `agents/reviewer.md` — Review (purple)

### Skills
- `skills/agile-delivery-workflow.md` — Agile delivery patterns

### Documentation
- `agents/README.md` — Agent overview
- `agents/QUICK_REFERENCE.md` — Quick reference guide
- `agents/PLUGIN_SETUP.md` — Installation and setup guide
- `agents/INDEX.md` — Complete index and navigation

## Workflow Phases

### Phase 1: Planning (Planner)
- Discovery interview
- Solution Design Document
- Architecture Decision Records
- Work Breakdown Structure with acceptance criteria
- Risk Register
- Executive Summary and Roadmap

**Output:** Comprehensive plan approved by stakeholder

### Phase 2: Implementation (Implementer)
- Build increments one at a time
- Verify each against acceptance criteria
- Apply professional standards (Python/AWS/Data/Docs)

**Output:** Code, infrastructure, or documentation per increment

### Phase 3: Validation (Validator)
- Test against acceptance criteria
- Check Python/AWS/Data/Documentation standards
- Structured pass/fail report

**Output:** PASS / CONDITIONAL PASS / FAIL verdict

### Phase 4: Review (Reviewer)
- AWS Well-Architected assessment (all 6 pillars)
- Code quality, architecture, maintainability review
- Data platform quality check
- Consulting deliverable quality assessment

**Output:** READY / READY WITH CONDITIONS / NOT READY verdict

### Phase 5: Delivery
- Package all deliverables
- Include Executive Summary for stakeholders
- Include validation and review reports
- Clear next steps and ownership

**Output:** Stakeholder-ready, production-ready deliverable

## Standards Applied

### Python Standards
- PEP 8 style guide
- Type hints on all functions
- Pydantic v2 for data models
- pathlib for file operations
- logging (no print statements)
- pytest for testing
- Pinned version dependencies

### AWS Standards
- CDK with L2/L3 constructs
- Least privilege IAM policies
- Secrets in AWS Secrets Manager
- Comprehensive tagging (Environment, Project, Owner, CostCentre)
- CloudWatch observability
- Stack separation by lifecycle

### Data Platform Standards
- Airflow idempotency with `execution_date` templating
- dbt layer discipline (staging → intermediate → mart)
- Schema validation at ingestion
- Dead-letter queue handling
- Data contracts and lineage

### Documentation Standards
- Mermaid diagrams (flowchart, sequence, ER)
- Architecture Decision Records (ADR)
- Solution Design Documents (SDD)
- Decision-ready writing
- Executive summaries for stakeholders

## Key Features

✅ **Architect-first** — Plans before implementation
✅ **Increment-based** — Build and verify incrementally
✅ **Quality-gated** — Validation before review
✅ **Professionally reviewed** — Senior architect sign-off
✅ **Well-documented** — All decisions captured in ADRs
✅ **Portable** — No employer-specific references
✅ **Customizable** — Adapt standards to your needs
✅ **Zero dependencies** — Runs on its own

## Time Estimates

| Phase | Time |
|-------|------|
| Planning | 30–90 min |
| Implementation | 1–8 hours |
| Validation | 15–60 min |
| Review | 30–90 min |
| **Total** | **2–10 hours** |

(Depends on complexity and number of increments)

## Getting Help

- **Quick start:** See `agents/README.md`
- **Cheatsheet:** See `agents/QUICK_REFERENCE.md`
- **Setup guide:** See `agents/PLUGIN_SETUP.md`
- **Complete reference:** See `agents/INDEX.md`

## Requirements

- Claude Code (or other Claude agent environment)
- No external dependencies
- No API keys or credentials required

## License

MIT License. See LICENSE file in the repository.

## Support

- **GitHub Issues:** https://github.com/jitheshb83/jithesh_ai/issues
- **Repository:** https://github.com/jitheshb83/jithesh_ai/tree/main/plugins/skill-delivery-workflow

---

**Author:** Jithesh Bharathan  
**Version:** 1.0.0  
**Last Updated:** 2026-06-20
