# Feature Brief — Workflow Reference

## Context Loading

Look for `project.md` in this order: `./project.md`, `./product/project.md`, `../product/project.md`. First match wins (supports both new cross-functional layout and legacy flat layout). If not found, ask the user to share it or answer a few context questions before proceeding.

## Glean Queries (if configured)

| Trigger | Query | Purpose |
|---|---|---|
| After feature name is established | `{feature_name} prior art spec PRD` | Find existing specs or prior attempts |
| After user stories are drafted | `{mission} {feature_name} user research usability` | Find research that validates or complicates these stories |
| After technical approach is discussed | `{feature_name} technical design doc architecture` | Find related architecture decisions |

## Interview Sections

### 1. Feature Overview
- What's the feature name and one-line description?
- Which project does this belong to? (read from project.md)
- What user problem does this specifically solve?

### 2. User Stories
- Who are the primary users of this feature?
- Walk me through the core user journey — what does success look like?
- What are the edge cases or failure states we need to design for?

### 3. Scope
- What's in scope for this feature?
- What's explicitly out of scope?
- Any dependencies on other teams or systems?

### 4. Success Criteria
- How will you know this feature is working? What metrics will move?
- What does "done" look like for v1?

### 5. Constraints & Open Questions
- Any technical, legal, or design constraints specific to this feature?
- What are the biggest open questions before you can ship?

## Output

Write `{feature-name}-brief.md` to `./product/briefs/`, `./briefs/`, or `./` — use the first path that exists as a directory. Create `product/briefs/` if in a cross-functional kit and it doesn't exist yet.

**Required sections in the output file:**
- Problem statement (user + business)
- Scope: in scope / out of scope / explicitly deferred
- User stories or job stories
- Acceptance criteria
- Open questions and dependencies
- Success metrics (tied to North Star from project.md)
