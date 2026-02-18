# Skills

Skills are self-contained procedures that agents discover and activate on demand. Each skill defines how to do a specific thing, producing a verifiable artifact.

Skills follow the [Agent Skills](https://agentskills.io/) format. See the [specification](https://agentskills.io/specification) for the complete `SKILL.md` format, frontmatter schema, and directory conventions.

## How Skills Work

Skills are leaf procedures. The [agent](../AGENTS.md) handles coordination — decomposing tasks, sequencing dependencies, and recursing. Skills handle execution — the concrete steps that produce an artifact when the decomposition bottoms out.

## Structure

Each skill lives in its own folder per the spec:

```
skills/
  <skill-name>/
    SKILL.md
```

## Design Principles

- **Enhance, don't duplicate.** Personas define judgment and workflow. Skills add concrete procedures that personas don't have. Don't restate what a persona already covers.
- **Self-contained.** A skill executes to completion on its own. It does not depend on or route to other skills. If a skill's boundaries are ambiguous, improve the skill.
- **Leaf procedures.** The agent decomposes a task into a tree of subtasks. Skills are the leaves — they do the work where the decomposition bottoms out. They don't decompose further or orchestrate other skills.

## Skills

- [triage-issue/](triage-issue/) — Turn an objective into a well-defined issue.
- [implement/](implement/) — Turn an issue into verified code.
- [open-pull-request/](open-pull-request/) — Turn code into a reviewable pull request.
- [review-pull-request/](review-pull-request/) — Evaluate a pull request and provide feedback.
- [respond-to-review/](respond-to-review/) — Turn review feedback into resolved changes.
