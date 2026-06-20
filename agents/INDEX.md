---
name: Agents Index
description: Complete index and navigation guide for the Skill Delivery Workflow plugin system
---

# Skill Delivery Workflow Plugin — Complete Index

**Repository:** https://github.com/jitheshb83/jithesh_ai/tree/main/agents

**Status:** Production-ready. 5 specialist agents + comprehensive documentation.

---

## 📋 File Directory

```
agents/
├── README.md                    # Overview of all agents (START HERE)
├── QUICK_REFERENCE.md           # One-page cheatsheet
├── PLUGIN_SETUP.md              # Complete installation & setup guide
├── INDEX.md                     # This file
├── planner.md                   # Architect-first planning agent
├── implementer.md               # Technical execution agent
├── validator.md                 # Adversarial quality gate agent
├── reviewer.md                  # Senior architect review agent
└── skill-delivery-workflow.md   # Orchestrator agent (use this to start)
```

---

## 🚀 Quick Start (Choose Your Path)

### Path A: I'm New to This System
1. **Read:** `README.md` (5 minutes) — understand what the agents do
2. **Skim:** `QUICK_REFERENCE.md` (3 minutes) — see agent triggers and workflow
3. **Use:** `/agent:skill-delivery-workflow` with your request

### Path B: I Have a Specific Task
| Task | Go To | Agent |
|------|--------|-------|
| Design/architecture | `planner.md` | `/agent:planner` |
| Write code/infra | `implementer.md` | `/agent:implementer` |
| Quality check | `validator.md` | `/agent:validator` |
| Pre-delivery review | `reviewer.md` | `/agent:reviewer` |
| End-to-end delivery | `skill-delivery-workflow.md` | `/agent:skill-delivery-workflow` |

### Path C: I Need Setup Instructions
1. **Read:** `PLUGIN_SETUP.md` — detailed installation for all platforms
2. **Follow:** Choose Option A, B, or C based on your setup
3. **Verify:** Run the verification commands
4. **Start:** Use the agents

---

## 📚 Agent Specifications

### 1. Planner Agent
**File:** `planner.md`  
**Model:** claude-opus-4-5  
**Color:** cyan  
**Use when:** You need architecture, planning, or design thinking

**Outputs:**
- Solution Design Document (SDD)
- Architecture Decision Records (ADRs)
- Work Breakdown Structure (WBS)
- Risk Register
- Executive Summary
- Roadmap

**Triggers:**
- "plan this"
- "design this"
- "how should we approach"
- "create a roadmap"
- "architecture for"

**Time estimate:** 30–90 minutes

---

### 2. Implementer Agent
**File:** `implementer.md`  
**Model:** claude-sonnet-4-5  
**Color:** green  
**Use when:** You have a plan and need to build it

**Outputs:**
- Code (Python: PEP 8, type hints, pytest)
- Infrastructure (AWS CDK: L2/L3 constructs, least privilege)
- Documentation (Mermaid diagrams, ADRs, decision-ready writing)
- Test coverage and verification per increment

**Standards:**
- Python: PEP 8, type hints, Pydantic v2, pathlib, logging, pytest
- AWS: CDK, L2/L3 constructs, least privilege IAM, Secrets Manager, tagging
- Data: Airflow idempotency, dbt layer discipline, schema validation
- Docs: Mermaid diagrams, ADR format, decision-ready writing

**Triggers:**
- "implement this"
- "build this"
- "write the code for"
- "create the DAG"
- "set up the CDK stack"

**Time estimate:** 1–8 hours (depends on complexity)

---

### 3. Validator Agent
**File:** `validator.md`  
**Model:** claude-sonnet-4-5  
**Color:** red  
**Use when:** You need to quality-check a deliverable

**Outputs:**
- Structured pass/fail report
- Findings with severity: BLOCKER, MAJOR, MINOR, INFO
- Clear remediation path

**Test surfaces:**
- **Python:** Type safety, error handling, testing, code quality, dependencies
- **AWS:** IAM, secrets, tagging, observability, CDK-specific
- **Data:** Airflow, dbt, schema validation, DLQ presence
- **Documentation:** Structure, decision-readiness, assumptions, trade-offs

**Verdicts:**
- ✅ PASS — Ready for next phase
- ⚠️ CONDITIONAL PASS — Minor issues, proceed with note
- ❌ FAIL — BLOCKERs found, needs rework

**Triggers:**
- "validate this"
- "check this against the plan"
- "does this pass"
- "quality gate"
- "is this production-ready"

**Time estimate:** 15–60 minutes per increment

---

### 4. Reviewer Agent
**File:** `reviewer.md`  
**Model:** claude-opus-4-5  
**Color:** purple  
**Use when:** You need final sign-off before stakeholder delivery

**Outputs:**
- Well-Architected Assessment (all 6 pillars)
- Required changes (if any)
- Recommended improvements
- Strengths assessment
- READY / NOT READY verdict

**Assessment lenses:**
1. **AWS Well-Architected** (all 6 pillars)
   - Operational Excellence
   - Security
   - Reliability
   - Performance Efficiency
   - Cost Optimisation
   - Sustainability

2. **Python Quality**
   - Architecture (SRP, abstraction, dependency direction)
   - Maintainability (readability, documentation, testability)
   - Robustness (boundary conditions, error handling, observability)

3. **Data Platform Quality**
   - Lineage and trust (traceability, reviewability, schema management)
   - Data contracts (explicit boundaries, breaking change handling)
   - Operational readiness (instrumentation, late data handling, DLQ monitoring)

4. **Consulting Deliverable Quality**
   - Structure and hierarchy (logical flow, headings, abstraction level)
   - Decision-readiness (specific recommendations, trade-offs, assumptions)
   - Executive summary quality (one-page, stakeholder-appropriate)

**Verdicts:**
- ✅ READY — Approved for delivery
- ⚠️ READY WITH CONDITIONS — Approved with caveats
- ❌ NOT READY — Serious issues, needs rework

**Triggers:**
- "review this"
- "is this ready"
- "final review"
- "pre-delivery check"
- "senior review"
- "would you sign off on this"

**Time estimate:** 30–90 minutes

---

### 5. Skill Delivery Workflow Agent
**File:** `skill-delivery-workflow.md`  
**Model:** claude-opus-4-5  
**Color:** gold  
**Use when:** You want end-to-end delivery with all quality gates

**Orchestrates:**
```
Plan (Planner)
  ↓
Build (Implementer)
  ↓
Test (Validator) ← if fail, loop back
  ↓
Review (Reviewer) ← if not ready, loop back
  ↓
Deliver
```

**Outputs:**
- Everything from all 4 agents
- Packaged deliverable with all documentation
- Clear next steps and ownership

**Triggers:**
- "deliver this skill"
- "run the delivery workflow"
- "execute full delivery"
- "end-to-end skill delivery"

**Time estimate:** 2–4 hours (simple feature) to 2–3 days (complex system)

---

## 📖 Documentation Files

### README.md
**Purpose:** High-level overview of all agents and how to deploy them

**Contains:**
- Agent table with roles and triggers
- Workflow diagram
- Deployment instructions for Claude Code, RAIWork, and other tools
- What's in each agent
- What's NOT in these agents

**Read time:** 5 minutes  
**Audience:** Anyone new to the system

---

### QUICK_REFERENCE.md
**Purpose:** One-page cheatsheet for quick lookup

**Contains:**
- Agent triggers table
- Workflow at a glance (each phase)
- Decision tree (which agent to use)
- Common workflows (4 scenarios)
- Verdict guides
- Rework loop diagrams
- Troubleshooting table
- Pro tips

**Read time:** 3–5 minutes  
**Audience:** Users who already understand the basics

---

### PLUGIN_SETUP.md
**Purpose:** Complete installation and setup guide

**Contains:**
- Quick start (5 minutes)
- Installation paths (3 options: local, direct, new device)
- Detailed workflow phases (all 5)
- Plugin architecture diagram
- Customization guide (how to adapt agents)
- Troubleshooting section
- Best practices (7 key points)
- FAQ (10 common questions)
- Support and updates

**Read time:** 10–15 minutes  
**Audience:** Users setting up for the first time or customizing

---

### INDEX.md
**Purpose:** This file — complete navigation and reference

**Contains:**
- File directory
- Quick start paths (3 options)
- Agent specifications (one per agent)
- Documentation file guides
- Workflow overview
- Verdict quick reference
- Context templates
- Common issues and solutions

**Read time:** 10 minutes  
**Audience:** Users looking for specific information

---

## 🔄 Workflow Overview

### Standard Flow (All 5 Phases)

```
[USER REQUEST]
        ↓
[PLANNER] — Discovery interview, plan creation
        ↓ (Confirm with stakeholder)
[IMPLEMENTER] — Build increment by increment
        ↓ (Show each result)
[VALIDATOR] — Quality gate, structured findings
        ↓ 
    [FAIL?] → Back to IMPLEMENTER
        ↓ (PASS)
[REVIEWER] — Final sign-off, quality assessment
        ↓
    [NOT READY?] → Back to IMPLEMENTER
        ↓ (READY)
[DELIVERY] — Package and deliver
```

### Quick Validation Flow (Phase 3 only)

```
[DELIVERABLE] → [VALIDATOR] → PASS/FAIL report
```

### Quick Review Flow (Phase 4 only)

```
[VALIDATED DELIVERABLE] → [REVIEWER] → READY/NOT READY
```

---

## 🎯 Use Cases by Role

### Product Manager / Stakeholder
**Goal:** Clear plan before implementation  
**Use:** `/agent:planner` → Confirm plan → Proceed to engineering

**Or:** `/agent:skill-delivery-workflow` → Get full delivery with all gates

---

### Software Engineer
**Goal:** Build to spec with quality standards  
**Use:** `/agent:implementer` → Deliver increments

**Or:** `/agent:validator` → Self-check work before review

---

### QA / Quality Engineer
**Goal:** Validate deliverables against criteria  
**Use:** `/agent:validator` → Generate quality report

---

### Tech Lead / Architect
**Goal:** Design, review, and sign off  
**Use:** `/agent:planner` → Design phase
**Or:** `/agent:reviewer` → Final approval before delivery

---

### Consultant
**Goal:** End-to-end engagement delivery  
**Use:** `/agent:skill-delivery-workflow` → Manage complete delivery

---

## 📊 Decision Trees

### "Which agent should I use?"

```
Is the request vague or need architecture?
  YES → Use PLANNER
  
Do you have a clear plan and want to build?
  YES → Use IMPLEMENTER
  
Do you have something to test/quality-check?
  YES → Use VALIDATOR
  
Do you want final sign-off before delivery?
  YES → Use REVIEWER
  
Want the full end-to-end process?
  YES → Use SKILL-DELIVERY-WORKFLOW
```

### "What should I do after each agent completes?"

```
PLANNER outputs plan
  → Review and confirm with stakeholder
  → Proceed to IMPLEMENTER
  
IMPLEMENTER shows increment
  → Verify acceptance criteria met
  → Proceed to next increment or VALIDATOR
  
VALIDATOR finds issues
  → If FAIL: back to IMPLEMENTER
  → If PASS: proceed to REVIEWER
  
REVIEWER finds issues
  → If NOT READY: back to IMPLEMENTER
  → If READY: proceed to DELIVERY
```

---

## 🔧 Installation Quick Commands

### Claude Code (Recommended)
```bash
mkdir -p .claude/agents
cp ~/.raiwork/agents/jithesh/*.md .claude/agents/
```

### New Device
```bash
mkdir -p ~/.raiwork/agents/jithesh
git clone https://github.com/jitheshb83/jithesh_ai.git
cp jithesh_ai/agents/*.md ~/.raiwork/agents/jithesh/
```

### Verify Installation
```bash
ls -la ~/.raiwork/agents/jithesh/
# Should show all 9 files
```

---

## ✅ Verdict Quick Reference

### Planner
- Outputs: Detailed plan (SDD, ADR, WBS, etc.)
- Success: Plan approved by stakeholder

### Implementer
- Outputs: Code/infra/docs per increment
- Success: Acceptance criteria verified

### Validator
- ✅ PASS — Ready for Reviewer
- ⚠️ CONDITIONAL PASS — Minor issues, can proceed
- ❌ FAIL — BLOCKER/MAJOR issues, back to Implementer

### Reviewer
- ✅ READY — Approved for delivery
- ⚠️ READY WITH CONDITIONS — Approved with caveats
- ❌ NOT READY — Quality issues, back to Implementer

---

## 📋 Context Templates

### For Planner
```
Skill: [name]
Request: [what it should do]
Constraints: [time/scope/team/dependencies]
Success criteria: [how to know it's done]
Audience: [who uses this?]
```

### For Implementer
```
Plan: [reference WBS]
Increment: [which one to build]
Acceptance criteria: [from WBS]
Standards: [Python/AWS/Data/Docs applicable]
```

### For Validator
```
Deliverable: [code/docs/infra]
Acceptance criteria: [from WBS]
Standards: [Python/AWS/Data/Docs to check]
```

### For Reviewer
```
Deliverable: [code/docs/infra]
Validation report: [from Validator]
Audience: [who receives this?]
```

---

## 🐛 Common Issues & Solutions

| Issue | Solution |
|-------|----------|
| Agent not found in IDE | Check `.claude/agents/` directory exists, restart IDE |
| Unclear what agent is asking | Wait for explicit question, answer directly |
| Plan seems too detailed | Focus on the WBS and acceptance criteria sections |
| Validation seems harsh | That's intentional — catch issues early |
| Stuck in rework loop | Verify changes are actually being made |
| Not sure which agent to use | Use the Decision Tree above |
| Can't install agents | See PLUGIN_SETUP.md for troubleshooting |

---

## 📚 Related Resources

- **Main repo:** https://github.com/jitheshb83/jithesh_ai
- **Agent files:** https://github.com/jitheshb83/jithesh_ai/tree/main/agents
- **Skills folder:** https://github.com/jitheshb83/jithesh_ai/tree/main/skills

---

## 📝 File Manifest with Checksums

| File | Lines | Purpose | Last Updated |
|------|-------|---------|--------------|
| `planner.md` | ~200 | Architecture & planning | 2026-06-20 |
| `implementer.md` | ~220 | Code & infra | 2026-06-20 |
| `validator.md` | ~260 | Quality gates | 2026-06-20 |
| `reviewer.md` | ~280 | Senior review | 2026-06-20 |
| `skill-delivery-workflow.md` | ~250 | Orchestrator | 2026-06-20 |
| `README.md` | ~120 | Overview | 2026-06-20 |
| `PLUGIN_SETUP.md` | ~400 | Installation guide | 2026-06-20 |
| `QUICK_REFERENCE.md` | ~280 | Cheatsheet | 2026-06-20 |
| `INDEX.md` | ~500 | This file | 2026-06-20 |

**Total:** ~2,100 lines, ~60KB, zero external dependencies

---

## 🎓 Learning Path

**Recommended order:**
1. **First time?** Read `README.md` (5 min) → `QUICK_REFERENCE.md` (3 min) → Try `/agent:skill-delivery-workflow`
2. **Setting up?** Follow `PLUGIN_SETUP.md` (15 min) → Verify installation
3. **Need details?** Read specific agent `.md` file for that agent
4. **Customizing?** See PLUGIN_SETUP.md → Customization & Extension section
5. **Lost?** Check this file (`INDEX.md`) or `QUICK_REFERENCE.md`

---

## 🚀 Get Started

```
1. Read: README.md
2. Copy: agents to your project
3. Run: /agent:skill-delivery-workflow
4. Provide: Your request
5. Deliver: Professional, reviewed, production-ready skill
```

**Questions?** Check `QUICK_REFERENCE.md` or `PLUGIN_SETUP.md` FAQ.

**Ready to start?** Run:
```
/agent:skill-delivery-workflow

I need to deliver [skill]. Here's the request: [description]
```

---

**Last updated:** 2026-06-20  
**Status:** Production-ready  
**License:** Portable, zero employer-specific references  
**Repository:** https://github.com/jitheshb83/jithesh_ai/tree/main/agents
