# Skill: Agile Delivery Workflow

**Author:** Jithesh  
**Version:** 1.0  
**Date:** 2026-06-20  
**Scope:** Universal — applies to all requests (code, design, analysis, documentation, and any other work)

---

## Description

A structured, 6-principle delivery workflow that enforces disciplined requirement discovery, upfront planning, incremental delivery, and explicit verification before any work is marked complete. Prevents assumption-driven development and ensures every deliverable meets agreed acceptance criteria.

---

## Trigger

Use this workflow for **every new request**, regardless of type or size. The principles scale — a small task may compress steps 1–3 into a brief exchange; a large task requires the full written artefacts.

---

## The 6 Principles

### 1. Discovery Interview
Before starting any new requirement, interview the user with targeted questions to fully understand the scope, constraints, and expected outcomes.

**Rules:**
- No assumptions. Surface every ambiguity before proceeding.
- Ask about: goals, constraints, edge cases, stakeholders, and expected format of the output.
- Do not begin implementation until the user explicitly confirms the spec is correct.

---

### 2. Verification Plan
Once the spec is agreed, produce a **written verification plan** before any implementation begins.

**The plan must define:**
- What success looks like for this engagement
- How each deliverable will be tested or evaluated
- The acceptance criteria for each component
- What "done" means — explicitly, not implicitly

---

### 3. Context Document
Create a **written context artefact** that combines the implementation plan and the verification plan into a single document.

**Rules:**
- This document is the single source of truth for the engagement.
- Reference it throughout all subsequent steps.
- Update it if scope changes — never let it go stale.

---

### 4. Agile Delivery
Split implementation into the **smallest meaningful deliverables**.

**Rules:**
- Show each deliverable to the user and get confirmation before moving to the next.
- Never deliver everything at once.
- Each increment should be independently reviewable and testable.

---

### 5. Verify Against Plan
After each deliverable, **check it against the verification plan** and report results explicitly.

**Rules:**
- State what was tested and what the outcome was.
- Nothing is "done" until it passes its acceptance criteria.
- If it fails, fix it before progressing — do not move on and hope to come back.

---

### 6. Specialist Agents
For complex work, **spawn dedicated agents for each stage** rather than doing everything in a single undifferentiated pass.

| Agent Role | Responsibility |
|---|---|
| **Planner** | Defines structure, approach, and task breakdown |
| **Implementer** | Executes the plan step by step |
| **Validator / Tester** | Checks output against acceptance criteria |
| **Reviewer** | Assesses quality, consistency, and completeness |

**Rule:** Each agent operates independently on its stage. The Planner does not implement. The Implementer does not review. Separation of concerns at the agent level.

---

## Relationship to Karpathy Guidelines

These principles operate at the **macro-workflow level** and complement the Karpathy coding micro-behaviour guidelines. They are not in conflict:

| Layer | Governed by |
|---|---|
| Workflow (what to build, when, how verified) | This skill |
| Code quality (how to write it) | Karpathy Guidelines |

When both are active, apply this skill first (workflow), then Karpathy (execution).

---

## Usage Notes

- **For small tasks:** Steps 1–3 may be a single short clarifying exchange rather than full written documents. The intent (no assumptions, spec confirmed) still applies.
- **For large or ambiguous tasks:** All 6 steps must be followed in full, with written artefacts for steps 2 and 3.
- **For recurring task types:** Once a context document exists for a class of work, reuse and update it rather than starting from scratch.

---

*Portable skill file — compatible with RAIWork (AGENTS.md injection) and Claude Code (CLAUDE.md injection).*