# Close Project — Workflow Reference

Read this file to execute the `/close-project` skill. Follow each step in order.

---

## Step 1: Load Context

Read the project kit files. Search in order: `./file.md` → `./product/file.md` → `../product/file.md`

**Required:**
- `project.md` — project manifest (problem, scope, team, metrics)
- `decisions.md` — decision log

**Optional (use if present):**
- `constraints.md` — hard constraints
- `todo.md` — open questions and action items
- Any files in `briefs/` — feature briefs written during the project

If `project.md` is not found, stop and tell the user:
> "I can't find project.md. Are you in the right project folder?"

---

## Step 2: Ask What Shipped

Say:
> "What shipped? You can paste release notes, a Jira filter URL, a Slack thread, or just tell me what made it into production."

Accept any input format:
- Free text description of what was built
- Pasted release notes or changelog
- Jira ticket list or filter URL
- Slack thread paste
- "Everything in scope shipped" (compare against project.md scope_in)

If the user says everything shipped, confirm by listing scope_in items and asking if that's accurate.

---

## Step 3: Build the Launch Record

Construct the launch record with these sections:

### 3a: Project Summary
- Pull from project.md: project name, mission, problem statement, team
- Keep it to 2-3 sentences — this is an at-a-glance header

### 3b: What Shipped (Final Scope)
- Combine the user's input from Step 2 with scope_in from project.md
- List each feature/capability that made it to production
- Note the phase (MVP, v1, etc.) if applicable from project.md phases table

### 3c: What Was Descoped
- Diff scope_in from project.md against what actually shipped
- Include anything from scope_out that was originally in scope but moved out
- For each descoped item, note whether it's:
  - **Deferred** — planned for a future phase
  - **Cut** — removed from the roadmap
  - **Unknown** — ask the user if unclear

### 3d: Key Decisions (Final State)
- Read decisions.md and extract only the **current/final** decision for each topic
- Do NOT include the full chronological history — just the latest state
- If a decision was superseded, show only the superseding decision
- Format as a simple table: Decision | Date | Rationale

### 3e: Constraints That Shaped the Outcome
- Pull from constraints.md
- Only include constraints that actually influenced what shipped (skip boilerplate)
- If constraints.md doesn't exist or is empty, skip this section

### 3f: Open Items / Fast-Follows
- Pull from todo.md (unresolved items)
- Add any descoped items marked as "Deferred" from section 3c
- Add any open decisions from decisions.md
- Organize by priority if possible

### 3g: Success Metrics Baseline
- Pull from project.md measurement section: North Star, success metrics table, guardrails
- Note the baseline values and targets
- Flag any instrumentation gaps that were never resolved

### 3h: Team
- Pull from project.md: core team table and key stakeholders

---

## Step 4: Show Summary and Write

Show the user a preview of the launch record structure:

> Here's the launch record I'll write. Let me know if anything needs adjusting.
>
> **Project:** [name]
> **What shipped:** [summary — X features, Y screens, etc.]
> **What was descoped:** [count items, note deferred vs cut]
> **Key decisions:** [count]
> **Open items:** [count]
> **Metrics baseline:** [North Star + target]

Wait for confirmation. Then write to:
`product/deliverables/{project-slug}-launch-record.md`

If `product/deliverables/` doesn't exist, check `./deliverables/`. Create the directory if needed.

---

## Step 5: Offer Status Update

After writing, ask:
> "Want me to update project.md to mark this project as shipped?"

If yes, add a `status: shipped` line and a `shipped_date: YYYY-MM-DD` line to the project.md header.

---

## Step 6: Confirm and Wrap Up

Say:
> "Launch record written to `product/deliverables/{project-slug}-launch-record.md`."

Single line. No re-reading the file back.

---

## Launch Record Output Format

```markdown
# {Project Name} — Launch Record

**Mission:** {mission}
**Shipped:** {date}
**PM:** {pm name}

---

## Project Summary

{2-3 sentence summary of the problem and what was built}

## What Shipped

{Bulleted list of features/capabilities that made it to production}

## What Was Descoped

| Item | Status | Notes |
|------|--------|-------|
| {item} | Deferred / Cut | {reason or future phase} |

## Key Decisions

| Decision | Date | Rationale |
|----------|------|-----------|
| {decision} | {date} | {why} |

## Constraints That Shaped the Outcome

{Bulleted list of constraints that actually mattered}

## Open Items / Fast-Follows

- [ ] {item} — {context}

## Success Metrics

| Metric | Type | Baseline | Target | Timeframe |
|--------|------|----------|--------|-----------|
| {metric} | {leading/lagging} | {value} | {value} | {timeframe} |

**North Star:** {metric} — baseline: {value}, target: {value}
**Guardrails:** {metrics that must not regress}
**Instrumentation gaps:** {anything still not measured}

## Team

| Role | Name |
|------|------|
| {role} | {name} |
```
