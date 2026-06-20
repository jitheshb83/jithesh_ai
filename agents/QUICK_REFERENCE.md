---
name: Quick Reference Guide
description: Cheatsheet for using the Skill Delivery Workflow and specialist agents
---

# Skill Delivery Workflow — Quick Reference Cheatsheet

## One-Minute Overview

```
Your Request
    ↓
/agent:skill-delivery-workflow
    ↓
Plan (Planner)  →  Build (Implementer)  →  Test (Validator)  →  Review (Reviewer)  →  Deliver
```

---

## Agent Triggers

| Agent | Command | Use When |
|-------|---------|----------|
| **Skill Delivery Workflow** | `/agent:skill-delivery-workflow` | Delivering end-to-end skills |
| **Planner** | `/agent:planner` | Need architecture, plan, or design |
| **Implementer** | `/agent:implementer` | Building code, infrastructure, docs |
| **Validator** | `/agent:validator` | Testing quality, finding issues |
| **Reviewer** | `/agent:reviewer` | Final sign-off before delivery |

---

## Workflow at a Glance

### Phase 1: Planning (30–90 min)
```
/agent:planner

Brief: [what you need]
Constraints: [time/scope/team]
Success criteria: [how to know it's done]

← Outputs: Plan (SDD, ADR, WBS, Risks, Roadmap, Executive Summary)
```

### Phase 2: Implementation (1–8 hours)
```
/agent:implementer

Plan: [reference the WBS]
Increment 1: [build this]

← Shows result
You: "Good, proceed to increment 2"
← Continues...
```

### Phase 3: Validation (15–60 min per increment)
```
/agent:validator

Deliverable: [the code/docs/infra]
Acceptance criteria: [from WBS]
Standards: [Python/AWS/Data/Docs]

← Outputs: PASS / FAIL report
```

### Phase 4: Review (30–90 min)
```
/agent:reviewer

Deliverable: [validated increment]
Audience: [who receives this?]

← Outputs: READY / NOT READY verdict
```

### Phase 5: Delivery
Package and deliver to stakeholder.

---

## Decision Tree: Which Agent Should I Use?

```
Do you have a vague request?
  ├─ YES → Use Planner (clarify and plan)
  └─ NO → Continue

Do you have a detailed plan and want to build?
  ├─ YES → Use Implementer
  └─ NO → Continue

Do you have something to test/validate?
  ├─ YES → Use Validator
  └─ NO → Continue

Do you want final sign-off before delivery?
  ├─ YES → Use Reviewer
  └─ NO → Done

Want to run the whole thing end-to-end?
  └─ Use Skill Delivery Workflow
```

---

## Common Workflows

### Scenario A: "I have a vague idea"
```
1. /agent:planner
   "I need to build [something]. Here's what it should do: [description]"
2. Wait for plan
3. Review and approve plan
4. /agent:implementer
   "Build this plan: [reference WBS]"
```

### Scenario B: "I have a plan, build it"
```
1. /agent:implementer
   "Implement this plan: [attach/reference plan]"
2. Review increments as they appear
3. When all done:
   /agent:validator
   "Validate this against: [acceptance criteria]"
4. /agent:reviewer
   "Review for delivery"
```

### Scenario C: "I built something, is it good?"
```
1. /agent:validator
   "Test this: [deliverable]"
2. If issues: go back to implementer
3. If pass:
   /agent:reviewer
   "Senior review?"
4. If ready: deliver
```

### Scenario D: "Full end-to-end"
```
/agent:skill-delivery-workflow
"Deliver this: [description]"
← Handles all phases automatically
```

---

## Verdict Guide

### Planner Outputs
- ✓ Solution Design Document (SDD)
- ✓ Architecture Decision Records (ADRs)
- ✓ Work Breakdown Structure (WBS) with acceptance criteria
- ✓ Risk Register
- ✓ Executive Summary
- ✓ Roadmap

**Next:** Confirm plan with stakeholder, then go to Implementer

---

### Validator Verdicts

| Verdict | Meaning | Next Step |
|---------|---------|-----------|
| **PASS** | All acceptance criteria met, no critical issues | → Go to Reviewer |
| **CONDITIONAL PASS** | Mostly good, minor/info issues only | → Go to Reviewer (note caveats) |
| **FAIL** | BLOCKER or MAJOR issues found | → Back to Implementer to fix |

**Severity levels:**
- 🔴 **BLOCKER** — Production failure, security issue, fails acceptance criteria
- 🟠 **MAJOR** — Reduces reliability/security materially
- 🟡 **MINOR** — Deviates from standards but doesn't break things
- 🔵 **INFO** — Observation, not a defect

---

### Reviewer Verdicts

| Verdict | Meaning | Next Step |
|---------|---------|-----------|
| **READY** | Approved for stakeholder delivery | → Deliver |
| **READY WITH CONDITIONS** | Approved if caveats are addressed | → Deliver, note conditions |
| **NOT READY** | Serious quality issues need fixing | → Back to Implementer |

**Assessment covers:**
- All 6 AWS Well-Architected pillars (Ops, Security, Reliability, Performance, Cost, Sustainability)
- Python code quality (architecture, maintainability, robustness)
- Data platform quality (lineage, contracts, operations)
- Consulting documentation (structure, decision-readiness, assumptions)

---

## Context to Provide Each Agent

### For Planner
```
Skill: [name]
Request: [what should it do?]
Constraints: [time/scope/team/dependencies]
Success criteria: [how to know it's done and good]
Audience: [who uses this?]
```

### For Implementer
```
Plan: [reference the WBS]
Increment: [which one you're building]
Acceptance criteria: [from WBS]
Standards: [Python/AWS/Data/Docs that apply]
```

### For Validator
```
Deliverable: [code/docs/infra being tested]
Acceptance criteria: [from WBS]
Standards: [Python/AWS/Data/Docs to check]
```

### For Reviewer
```
Deliverable: [code/docs/infra being reviewed]
Validation report: [from Validator]
Audience: [who will use/receive this?]
```

---

## Rework Loops

### Validator Finds Issues
```
Validator: FAIL
  ↓ (BLOCKERs found)
Implementer: "Fix these: [list]"
  ↓
Validator: Re-validate
  ↓
  If PASS → Reviewer
  If FAIL → loop back
```

### Reviewer Finds Issues
```
Reviewer: NOT READY
  ↓ (Required changes listed)
Implementer: "Fix these: [list]"
  ↓
Validator: Re-validate
  ↓
Reviewer: Re-review
  ↓
  If READY → Deliver
  If NOT READY → loop back
```

---

## Key Questions to Answer

When you're stuck or unsure:

**For Planner:**
- "What outcome are we delivering?"
- "What are the constraints (time, scope, team)?"
- "How will we know it's done and good?"
- "What are the biggest risks?"

**For Implementer:**
- "Which increment am I building?"
- "What are the acceptance criteria?"
- "Is the plan clear, or do I need to ask?"
- "Did I verify against acceptance criteria?"

**For Validator:**
- "What are the stated acceptance criteria?"
- "What standards apply (Python/AWS/Data/Docs)?"
- "Did I find all the issues or just some?"
- "Is my verdict clear and specific?"

**For Reviewer:**
- "Would I put my name on this?"
- "Does it meet AWS Well-Architected standards?"
- "Is the documentation decision-ready?"
- "What would a technical director think?"

---

## Installation Commands

### Claude Code Project
```bash
# Copy agents to your project
mkdir -p .claude/agents
cp ~/.raiwork/agents/jithesh/*.md .claude/agents/

# Verify
ls .claude/agents/
# Shows: planner.md, implementer.md, validator.md, reviewer.md, skill-delivery-workflow.md
```

### Local Device (One-Time)
```bash
mkdir -p ~/.raiwork/agents/jithesh
git clone https://github.com/jitheshb83/jithesh_ai.git
cp jithesh_ai/agents/*.md ~/.raiwork/agents/jithesh/
```

### New Device
```bash
git clone https://github.com/jitheshb83/jithesh_ai.git
cp jithesh_ai/agents/*.md ~/.raiwork/agents/jithesh/
```

---

## File Manifest

| File | Purpose | Size |
|------|---------|------|
| `planner.md` | Architecture, planning, discovery | ~5KB |
| `implementer.md` | Code/infra generation, standards | ~7KB |
| `validator.md` | Quality gates, structured findings | ~7.5KB |
| `reviewer.md` | Final sign-off, quality assessment | ~7.5KB |
| `skill-delivery-workflow.md` | Orchestrator for full workflow | ~7.5KB |
| `README.md` | Agent overview and deployment | ~4KB |
| `PLUGIN_SETUP.md` | Complete installation guide | ~15KB |
| `QUICK_REFERENCE.md` | This file | ~4KB |

**Total:** ~58KB. No dependencies beyond the agents themselves.

---

## Customization

Each agent has a **Standards** section you can modify:

```markdown
# In any agent .md file, find the Standards section:

## Python Standards
- [Edit type hints, naming, testing, etc.]

## AWS Standards
- [Edit IAM, secrets, tagging, observability]

## Data Platform Standards
- [Edit Airflow, dbt, schema validation]

## Consulting Standards
- [Edit documentation, diagram formats]
```

Save your customized version in `.claude/agents/` for your projects.

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| Agent not found | Check `.claude/agents/` directory, restart IDE |
| Unclear what agent is asking | Wait for explicit question, answer directly |
| Validation is strict | That's intentional — it catches issues early |
| Plan seems too detailed | It's comprehensive; focus on the WBS and acceptance criteria |
| Stuck in rework loop | Check if the required changes are actually being made |
| Not sure which agent to use | Refer to the Decision Tree above |

---

## Pro Tips

1. **Read the Executive Summary first** — it's written for your audience
2. **Use acceptance criteria as your spec** — they define done
3. **Validate early and often** — don't wait until everything is built
4. **Document decisions in ADRs** — they're gold for future maintainers
5. **Review before stakeholder delivery** — "it works" ≠ "it's good"
6. **Keep the plan handy** — reference it when confused about scope
7. **Trust the Validator** — if it flags something, it's real

---

## When to Use Each Agent Alone

| Agent | Use Alone When |
|-------|---|
| **Planner** | You need architecture, plan, or design thinking |
| **Implementer** | You have a clear spec and need code/infra |
| **Validator** | You want to quality-check existing work |
| **Reviewer** | You want senior sign-off before delivery |
| **Workflow** | You want the complete end-to-end process |

---

## Summary

```
┌─────────────────────────────────────────┐
│   Skill Delivery Workflow Plugin        │
├─────────────────────────────────────────┤
│                                         │
│  Start: /agent:skill-delivery-workflow  │
│                                         │
│  Or use individual agents:              │
│  /agent:planner                         │
│  /agent:implementer                     │
│  /agent:validator                       │
│  /agent:reviewer                        │
│                                         │
│  Result: Production-ready, reviewed,    │
│          documented deliverables        │
│                                         │
└─────────────────────────────────────────┘
```

---

## For More Details

- **Full agent specs:** Read individual `.md` files
- **Installation guide:** See `PLUGIN_SETUP.md`
- **Agent overview:** See `README.md`
- **GitHub repo:** https://github.com/jitheshb83/jithesh_ai/tree/main/agents
