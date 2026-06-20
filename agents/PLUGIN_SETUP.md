---
name: Skill Delivery Workflow Plugin
description: Complete installation and setup guide for the Skill Delivery Workflow plugin and all specialist agents.
---

# Skill Delivery Workflow Plugin — Installation & Setup Guide

This plugin packages the complete Skill Delivery Workflow system: 5 specialist agents working in orchestrated sequence to deliver production-ready skills and features.

## What's Included

| Component | Role | Triggers |
|-----------|------|----------|
| **Skill Delivery Workflow** | Orchestrator — manages handoffs between all agents | "deliver this skill", "run delivery workflow", "end-to-end delivery" |
| **Planner** | Architecture-first planning | "plan this", "design this", "create a roadmap" |
| **Implementer** | Technical execution, increment by increment | "implement this", "build this", "execute step N" |
| **Validator** | Adversarial quality gate with structured findings | "validate this", "quality gate", "is this production-ready" |
| **Reviewer** | Senior architect final gate | "review this", "final review", "senior review" |

**Workflow:** Planner → Implementer → Validator → Reviewer → Delivery

---

## Quick Start (5 minutes)

### For Claude Code Projects

1. **Clone or copy the agents folder to your project:**
   ```bash
   cp -r ~/.raiwork/agents/jithesh /path/to/your/project/.claude/agents/
   ```

2. **Start a skill delivery:**
   ```
   /agent:skill-delivery-workflow

   I need to deliver [skill/feature]. Here's the request: [description]
   ```

   The workflow agent will:
   - Guide you through discovery
   - Call Planner to create a detailed plan
   - Orchestrate Implementer for increment-by-increment work
   - Validate and review before stakeholder delivery

### For RAIWork or Other AI Tools

1. **Copy agents to your device:**
   ```bash
   mkdir -p ~/.raiwork/agents/jithesh
   cp planner.md implementer.md validator.md reviewer.md skill-delivery-workflow.md README.md ~/.raiwork/agents/jithesh/
   ```

2. **Reference the Workflow agent as your system prompt:**
   - Read `skill-delivery-workflow.md`
   - Pass its content as the system prompt to spawn an agent
   - Provide your skill/feature request as the user message

### For Any Other AI Tool

1. **Paste the agent files as system prompts:**
   - Open the relevant `.md` file (e.g., `skill-delivery-workflow.md`)
   - Copy everything AFTER the YAML frontmatter (`---`)
   - Paste into your tool's system prompt field
   - Send your request as the user message

---

## Installation Paths

### Option A: Local Development Machine (Recommended)

```bash
# One-time setup
mkdir -p ~/.raiwork/agents/jithesh
cd ~/.raiwork/agents/jithesh
git clone https://github.com/jitheshb83/jithesh_ai.git
cp jithesh_ai/agents/* .

# Verify installation
ls -la ~/.raiwork/agents/jithesh/
# Should show: planner.md, implementer.md, validator.md, reviewer.md, skill-delivery-workflow.md, README.md

# Use with any Claude Code project
mkdir -p /path/to/your/project/.claude/agents
cp ~/.raiwork/agents/jithesh/*.md /path/to/your/project/.claude/agents/
```

### Option B: Direct to Project

```bash
# Copy directly into a new or existing Claude Code project
mkdir -p /path/to/your/project/.claude/agents
cp /path/to/agents/* /path/to/your/project/.claude/agents/

# Verify
ls /path/to/your/project/.claude/agents/
```

### Option C: New Device Setup

```bash
# Clone the repo
git clone https://github.com/jitheshb83/jithesh_ai.git
cd jithesh_ai

# Install agents to device
mkdir -p ~/.raiwork/agents/jithesh
cp agents/*.md ~/.raiwork/agents/jithesh/

# Verify
cat ~/.raiwork/agents/jithesh/planner.md | head -5
# Should show YAML frontmatter with name: Planner
```

---

## How to Use the Workflow

### Scenario 1: Deliver a New Feature (Full Workflow)

```
User: "Deliver this skill using the workflow"

Me (Skill Delivery Workflow): 
1. Confirm skill name and request
2. [CALL PLANNER] 
   "Create a plan for: [skill]. Constraints: [from user]. Success criteria: [from user]"
3. Planner outputs: SDD, ADR, WBS, Risk Register, Executive Summary
4. [CONFIRM WITH USER] "Does this plan look right? Ready to proceed to implementation?"
5. [CALL IMPLEMENTER]
   "Implement increment 1 of the plan: [from WBS]"
6. Implementer shows increment output → I confirm acceptance criteria met
7. [CALL VALIDATOR]
   "Validate this increment against: [acceptance criteria]"
8. Validator reports PASS/FAIL
   - If FAIL: back to Implementer to fix
   - If PASS: continue to Reviewer
9. [CALL REVIEWER]
   "Review this for stakeholder delivery"
10. Reviewer reports READY/NOT READY
    - If NOT READY: back to Implementer
    - If READY: ready for delivery
11. [DELIVER] Package all outputs: code, docs, architecture, runbooks
```

### Scenario 2: Review Existing Work

```
User: "Review this deliverable"

Me (Reviewer):
1. Ask: "What is this deliverable? Who is the stakeholder? What are the acceptance criteria?"
2. Assess against AWS Well-Architected (all 6 pillars)
3. Review Python/Data/Documentation quality
4. Report: READY | READY WITH CONDITIONS | NOT READY
```

### Scenario 3: Validate Before Delivery

```
User: "Validate this against the acceptance criteria"

Me (Validator):
1. Ask: "What is the deliverable? What are the acceptance criteria? What standards apply?"
2. Run systematic checks
3. Report: structured BLOCKER/MAJOR/MINOR/INFO findings
4. If issues exist: clear path to resolution
```

---

## Workflow in Detail

### Phase 1: Planning (Planner Agent)

**Input:**
- Skill/feature request (brief description)
- Constraints (time, scope, team, dependencies)
- Success criteria

**Output:**
- **Solution Design Document (SDD)** — problem, architecture, component breakdown, data flows, security, trade-offs, open decisions
- **Architecture Decision Records (ADRs)** — numbered decisions with context and consequences
- **Work Breakdown Structure (WBS)** — hierarchical decomposition with acceptance criteria per increment
- **Risk Register** — identified risks with probability, impact, mitigation
- **Executive Summary** — one-page stakeholder-ready summary
- **Roadmap** — phase-based delivery plan

**Time estimate:** 30–90 minutes depending on complexity

**Success criteria:** Plan is approved by stakeholder and ready for implementation

---

### Phase 2: Implementation (Implementer Agent)

**Input:**
- Approved plan (SDD, WBS, ADRs)
- Increment 1 description and acceptance criteria
- Any previous implementation notes

**Output (per increment):**
- Code, infrastructure, or documentation
- Test coverage and verification
- New ADRs if architectural decisions made
- Increment status: PASS / FAIL acceptance criteria

**Process:**
1. Show increment 1 result
2. Confirm acceptance criteria met
3. Move to increment 2
4. Repeat until all increments complete

**Time estimate:** 1–8 hours depending on complexity and number of increments

**Success criteria:** All increments pass acceptance criteria, verified by Implementer

---

### Phase 3: Validation (Validator Agent)

**Input:**
- Deliverable (code, documentation, infrastructure)
- Acceptance criteria from WBS
- Applicable standards (Python / AWS / Data / Documentation)

**Output:**
- **Validation Report** with verdict: PASS | CONDITIONAL PASS | FAIL
- **Findings:** BLOCKER, MAJOR, MINOR, INFO severity levels
- **Clear remediation path** if failures exist

**Rework loop (if needed):**
- Validator flags BLOCKERs/MAJORs → Implementer fixes → Validator re-validates
- Repeat until PASS

**Time estimate:** 15–60 minutes per increment

**Success criteria:** Verdict is PASS or CONDITIONAL PASS

---

### Phase 4: Review (Reviewer Agent)

**Input:**
- Validated deliverable
- Validation report
- Stakeholder audience context

**Output:**
- **Well-Architected Assessment** (all 6 pillars: Operational Excellence, Security, Reliability, Performance, Cost, Sustainability)
- **Verdict:** READY | READY WITH CONDITIONS | NOT READY
- **Required before delivery** (if any)
- **Recommended improvements** (nice-to-haves)
- **Strengths** (what was genuinely well done)

**Rework loop (if needed):**
- Reviewer flags NOT READY → Implementer fixes → Validator re-validates → Reviewer re-reviews
- Repeat until READY

**Time estimate:** 30–90 minutes

**Success criteria:** Verdict is READY

---

### Phase 5: Stakeholder Delivery

**Deliverable Package:**
- ✓ Code / infrastructure / documentation (reviewed and approved)
- ✓ Executive Summary (from Planner)
- ✓ Architecture diagrams (Mermaid from SDD)
- ✓ ADRs (decisions made)
- ✓ Validation report (quality gates passed)
- ✓ Review report (senior approval)
- ✓ Runbooks or deployment guides (if applicable)
- ✓ Next steps and ownership (clear accountability)

**Time estimate:** 15–30 minutes to package and deliver

**Success criteria:** Stakeholder has everything they need to deploy, maintain, and extend

---

## Plugin Architecture

```
skill-delivery-workflow.md (Orchestrator)
├── Calls planner.md
│   └── Outputs: SDD, ADR, WBS, Risk Register, Executive Summary, Roadmap
├── Calls implementer.md
│   └── Outputs: Code/Infra/Docs, verified against acceptance criteria
├── Calls validator.md
│   ├── Checks Python / AWS / Data / Documentation standards
│   └── Outputs: PASS/FAIL report with severity levels
├── Calls reviewer.md
│   ├── AWS Well-Architected (all 6 pillars)
│   └── Outputs: READY / NOT READY verdict
└── Delivers stakeholder-ready package
```

Each agent is **independent** — you can call them individually without the workflow:
- `planner.md` alone for architecture reviews
- `implementer.md` alone for code generation
- `validator.md` alone for quality gates
- `reviewer.md` alone for pre-delivery sign-off

---

## Customization & Extension

### Adapting to Your Standards

Each agent has a **Standards** section. You can modify:

**Python Standards** (in `implementer.md` and `validator.md`)
- Change type hint requirements
- Adjust testing thresholds
- Update naming conventions

**AWS Standards** (in `implementer.md` and `validator.md`)
- Replace CDK with Terraform if preferred
- Add org-specific tagging standards
- Adjust IAM policy templates

**Data Platform Standards** (in `implementer.md` and `validator.md`)
- Swap Airflow for Prefect, Dagster, etc.
- Change dbt conventions
- Update schema validation approach

**Consulting Standards** (in `implementer.md`, `validator.md`, `reviewer.md`)
- Adjust document templates
- Change diagram tools
- Update stakeholder communication style

### Example: Adding Organization-Specific Requirements

```markdown
## Your Org Standards (added to each agent)

**CI/CD:**
- All code must pass GitHub Actions before merge
- Deployment to staging automatic on main push
- Production deployments require manual approval

**Documentation:**
- All PRs require a linked ADR (if architectural change)
- Breaking changes documented in CHANGELOG.md
- Runbooks in wiki with troubleshooting section

**Security:**
- All secrets in vault, never in code or logs
- Secrets rotation automated every 90 days
- Audit logs retained for 1 year
```

---

## Troubleshooting

### Agent is Not Available

**Problem:** `/agent:planner` or `/agent:skill-delivery-workflow` not recognized

**Solution:**
1. Confirm agents are in `.claude/agents/` directory:
   ```bash
   ls .claude/agents/
   # Should show: planner.md, implementer.md, validator.md, reviewer.md, skill-delivery-workflow.md
   ```
2. Restart your IDE
3. Confirm file names match exactly (case-sensitive on some systems)

### Workflow Seems to Stall

**Problem:** Agent is waiting for input but it's not clear what

**Solution:**
- Look for explicit questions: "Do you want to proceed?" "Shall I continue?"
- Answer directly: "Yes, proceed" or "No, I need X first"
- The workflow requires confirmation at each phase transition

### Validation or Review Verdict is Unclear

**Problem:** Validator or Reviewer report is hard to parse

**Solution:**
1. Look at the **Verdict** field first (PASS, FAIL, READY, NOT READY)
2. Read the **Findings** section (BLOCKER items are stop-gaps)
3. Implement the required changes
4. Re-validate / re-review

### Need to Backtrack

**Problem:** Realized plan was incomplete after implementation started

**Solution:**
1. Pause implementation
2. Call Planner again with updated scope
3. Update WBS and acceptance criteria
4. Resume implementation with updated plan
5. All validation/review happens on final deliverable

---

## Best Practices

### 1. Never Skip Planning
Even if you think you know what to build, run Planner. It surfaces assumptions and risks that emerge in discovery.

### 2. Validate After Each Increment
Do not wait until all implementation is done. Validate as you go. Fixing issues early is cheaper.

### 3. Review Before Delivery
"It works" is not the same as "it's good." Reviewer catches quality issues that don't show up in validation.

### 4. Document Decisions
Every ADR is a record of why something was chosen. This is gold for future maintainers.

### 5. Capture Risks
Risk Register is not a compliance exercise. It's a map of what could go wrong and how to prepare.

### 6. Get Stakeholder Sign-Off on Plan
Before implementation, confirm the plan addresses the request. This prevents large rework.

### 7. Read the Executive Summary
It's written for stakeholders. If it doesn't make sense to you, it won't make sense to them either.

---

## FAQ

**Q: Can I use just the Implementer without the workflow?**
A: Yes. Call Implementer directly. But you lose planning rigor and quality gates.

**Q: Can I skip Validator?**
A: Not recommended. Validator catches issues that are expensive to fix in production.

**Q: What if I don't have acceptance criteria?**
A: Planner produces them. If Planner doesn't, that's a red flag — the scope is unclear.

**Q: How long does a full workflow take?**
A: Depends on complexity. Simple feature: 2–4 hours. Complex data platform: 2–3 days.

**Q: Can I customize the agents?**
A: Yes. Copy them to your project, edit the standards sections. They remain fully functional.

**Q: What happens if Reviewer says NOT READY?**
A: Implementer fixes the issues, Validator re-validates, Reviewer re-reviews. Repeat until READY.

**Q: Can I run multiple skills in parallel?**
A: Yes. Each skill gets its own workflow run. Agents are stateless.

---

## Support & Updates

- **Agent updates:** Check the [GitHub repository](https://github.com/jitheshb83/jithesh_ai/tree/main/agents) for the latest versions
- **Report issues:** Open an issue on the repo if you find bugs or gaps
- **Contribute:** Submit PRs to improve agents or add new ones
- **Documentation:** Refer to individual agent `.md` files for detailed specs

---

## Summary

The Skill Delivery Workflow plugin gives you a **professional, repeatable process** for delivering skills that are:
- ✓ Well-planned (no surprises mid-implementation)
- ✓ Technically sound (standards-based, quality-gated)
- ✓ Well-documented (decisions, risks, architecture visible)
- ✓ Ready for stakeholder delivery (reviewed by senior architect)

**Start a delivery:**
```
/agent:skill-delivery-workflow

I need to deliver [skill]. Here's what it should do: [description]
```

The workflow handles the rest.
