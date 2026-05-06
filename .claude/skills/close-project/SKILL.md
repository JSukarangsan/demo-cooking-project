---
name: close-project
description: >
  Generate a post-launch record for {PROJECT_NAME}. Reads the project kit
  to produce a clean artifact summarizing what shipped, what was descoped,
  final decisions, and success metrics baseline.
  Use when someone says "close out this project", "what shipped",
  "generate launch record", "post-launch doc", or "wrap up [project]".
---

# Close Project Skill

Generates a launch record after a feature ships.

## What I Need
- The project kit (project.md, decisions.md, constraints.md, briefs/)
- Optionally: release notes, Jira links, or a paste of what actually shipped

## What I'll Produce
- `product/deliverables/{project-slug}-launch-record.md`

## Full Workflow
See `references/workflow.md` for detailed steps.
