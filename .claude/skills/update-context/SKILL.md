---
name: update-context
description: >
  Keep the project kit current mid-project. Takes any input — meeting notes,
  Slack thread, email, Google Doc paste, voice memo transcript — and routes
  changes to the right kit files. Updates decisions.md, constraints.md,
  project.md, todo.md, glossary.md, and CLAUDE.md as needed in a single pass.

  Use when someone says "update my kit", "here's what happened", "sync this",
  "we had a meeting", or pastes raw notes or a thread mid-project.
---

# Update Context Skill

Takes whatever you throw at it and keeps the kit honest.

## What I Need

Any of the following — one or more at a time:
- Pasted meeting notes or transcript
- Slack thread (copy/paste is fine)
- Email thread
- Google Doc content (paste it in)
- A plain description of what changed or was decided

## What I'll Do

1. Read the current state of all kit files
2. Parse your input and identify what's new or changed
3. Show a routing summary — what goes where — before touching anything
4. Write all confirmed changes in one pass
5. Confirm what was updated

## Where Things Route

| What it is | Goes to |
|---|---|
| Decision made or explicitly ruled out | decisions.md |
| Hard constraint (technical, legal, infra, budget) | constraints.md |
| Scope change (in or out) | project.md → Scope |
| Timeline or phase change | project.md → Delivery |
| Stakeholder or team change | project.md → Team & Stakeholders |
| Open question (unresolved) | todo.md → Open Questions |
| Action item with an owner | todo.md → Next Steps |
| New term or concept introduced | glossary.md |
| Strategic shift (goal, framing, priority, MVP) | project.md → Strategy + CLAUDE.md |

## Full Workflow

See `references/workflow.md` for the complete parsing and routing logic.
