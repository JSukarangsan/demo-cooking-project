---
name: exec-preflight
description: >
  Stress-test a brief, PRD, or deck outline before an exec review.
  Reviews from three perspectives (Mission VP, Engineering Lead, Editorial/Business),
  surfaces buried leads and likely objections, then reframes the narrative for
  the angle that matters most in your meeting.
  Use when someone says "preflight my brief", "prep me for [meeting]",
  "stress-test this", or "what will [exec] push back on?"
---

# Exec Preflight Skill

Runs a three-persona review of any doc before you walk into a room.

## What I Need
- The doc to review (paste it or @ reference it)
- Your project context files are loaded automatically (project.md, decisions.md, constraints.md)

## What I'll Do
1. Review from three NYT exec perspectives: Mission VP/Director, Engineering Lead, Editorial/Business stakeholder
2. Synthesize: what lands, what's buried, what's missing, what open decisions could derail the meeting
3. Ask which angle matters most for this specific meeting
4. Reframe the narrative for that audience

## Output
- Inline review with synthesis (no file write by default)
- Offer to save the reframed version as `{doc-name}-preflighted.md`

## Full Workflow
See `assembly/exec-preflight.yaml` in the Kit Builder repo for the complete persona definitions and reframing logic.
