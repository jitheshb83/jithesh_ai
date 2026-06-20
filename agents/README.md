# Personal Specialist Agents

4 portable agent definitions. Zero employer-specific references. Take them to any device, any project.

---

## The Agents

| Agent | Role | When to use |
|-------|------|-------------|
| `planner.md` | Architect-first planning | Start of any engagement — before any implementation |
| `implementer.md` | Technical execution | Implementing an agreed, specific plan |
| `validator.md` | Adversarial quality gate | Testing a deliverable against acceptance criteria |
| `reviewer.md` | Senior architect review | Final gate before anything goes to a stakeholder |

These agents are designed to work in sequence:

```
Planner → Implementer → Validator → Reviewer → Delivery
            ↑_____________|
          (fix and re-validate)
```

---

## How to Deploy

### Claude Code (primary use case)

Copy the 4 agent files into your project's `.claude/agents/` directory:

```bash
cp ~/.raiwork/agents/jithesh/*.md /path/to/your/project/.claude/agents/
```

They are then available as subagents immediately:

```
/agent:planner     — start a planning session
/agent:implementer — implement an increment
/agent:validator   — run a quality gate
/agent:reviewer    — senior review before delivery
```

Or reference them explicitly when using Claude Code directly:

```
use the planner agent to design the architecture for X
use the validator agent to check this against the acceptance criteria
```

### RAIWork (this device)

Reference them as `spawn` prompts. The agent files are already at `~/.raiwork/agents/jithesh/`. To use one, read it and pass the content as a system prompt to a spawned agent:

```
Spawn a planner agent using the spec at ~/.raiwork/agents/jithesh/planner.md
and give it this brief: [your brief]
```

### Any other AI tool

Paste the content of the relevant `.md` file as the system prompt for that tool. The YAML frontmatter can be ignored — it is only used by Claude Code and RAIWork for agent registration.

---

## Portability — New Device Setup

```bash
# Clone or copy this directory to the new device
mkdir -p ~/.raiwork/agents/jithesh
cp planner.md implementer.md validator.md reviewer.md README.md ~/.raiwork/agents/jithesh/

# For any Claude Code project on that device:
mkdir -p .claude/agents
cp ~/.raiwork/agents/jithesh/*.md .claude/agents/
```

That is the full setup. No other dependencies.

---

## What is in each agent

### Planner
- Discovery interview workflow (runs before any plan is produced)
- AWS Well-Architected Framework as the default planning lens
- Data platform patterns: Lake House, Data Mesh, pipeline design
- Deliverable formats: SDD, ADR, WBS, Risk Register, Executive Summary, Roadmap
- Mermaid diagram-first approach for architecture

### Implementer
- Python: PEP 8, type hints, Pydantic v2, pathlib, logging, pytest conventions
- AWS CDK (Python): L2/L3 constructs, least-privilege IAM, Secrets Manager, tagging, observability
- Airflow: idempotency, `execution_date` templating, DLQ patterns
- dbt: staging → intermediate → mart discipline, `schema.yml`, test coverage
- ADR and decision-ready writing format

### Validator
- Structured pass/fail report format with BLOCKER / MAJOR / MINOR / INFO severity
- Python: type safety, error handling, test coverage, code quality, dependencies
- AWS: IAM least privilege, secrets hygiene, tagging, observability
- Data: idempotency, schema validation, dbt test coverage, DLQ presence
- Docs: structure compliance, risks documented, trade-offs present

### Reviewer
- AWS Well-Architected: all 6 pillars, structured per-pillar assessment
- Python: SRP, abstraction level, maintainability, robustness
- Data: lineage, data contracts, operational readiness
- Consulting: decision-readiness, executive summary quality, assumptions visible

---

## What is not in these agents

- No DNB, IPA, Eufemia, or any employer-specific references
- No project-specific context
- No proprietary tooling assumptions

These are professional identity files. They reflect skills and standards, not any particular employer or project context.
