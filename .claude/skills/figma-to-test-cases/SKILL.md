---
name: figma-to-test-cases
description: >
  Generate acceptance criteria and test cases from Figma designs for {PROJECT_NAME}.
  Takes a Figma URL, reads design context (screens, states, components, annotations),
  and produces a structured handoff doc with ACs organized by P0/P1/P2 priority.
  Use when someone says "write ACs from Figma", "test cases from designs",
  "generate ACs from this Figma", or pastes a Figma URL with "write test cases".
---

# Figma to Test Cases Skill

Generates acceptance criteria and test cases from Figma designs.

## What I Need
- A Figma file URL (figma.com/design/...)
- Optionally: a node ID for a specific flow or screen
- Optionally: the related feature brief (for cross-referencing)

## What I'll Produce
- `{feature-name}-figma-handoff.md`

## Full Workflow
See `references/workflow.md` for detailed steps.
