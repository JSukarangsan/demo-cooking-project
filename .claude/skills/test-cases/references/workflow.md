# Test Cases — Workflow Reference

## Step 1: Load Context

Read in this order before writing anything:

1. **The feature brief** — @ referenced file or pasted content. This is the primary input.
2. **`decisions.md`** — find any `open` decisions that could change what "done" means. Look in `./decisions.md`, `./product/decisions.md`, or `../product/decisions.md` (first match wins).
3. **`constraints.md`** — hard limits that test cases must respect. Same path search order as above.
4. **`project.md`** — North Star metric and guardrail metrics. Same path search order as above.

If no feature brief is provided:
> "Paste or @ reference the feature brief you want test cases for."

---

## Step 2: Extract Acceptance Criteria

Scan the brief for explicit ACs. If not present, infer them from the requirements section.

For each requirement or user story, derive:
- What the system must do (behavior)
- What the user must be able to do (outcome)
- What must NOT happen (guardrail / constraint)

Group ACs by feature area (e.g., "Personalization trigger", "Cold start fallback", "Experiment bucketing").

If the brief has requirements but no clear success criteria, note the gap — don't invent
criteria the PM hasn't stated.

---

## Step 3: Assign Priority

For each AC and derived test case, assign P0 / P1 / P2:

**P0 — Must pass before launch**
- Core happy path works end-to-end
- Guardrail metrics are protected (no regression on key metrics)
- Any hard constraint from constraints.md is respected
- Legal / compliance requirements are met
- Experiment bucketing is correct (if applicable)

**P1 — Should test before launch**
- Edge cases the PM explicitly called out in the brief
- Error states and failure modes (what happens when things go wrong)
- Degraded experience paths (e.g., cold start, sparse data, fallback behavior)
- Cross-platform parity issues (if the feature ships on multiple surfaces)

**P2 — Regression / good to have**
- Secondary user paths not central to the hypothesis
- Non-critical edge cases
- Known-but-acceptable rough edges documented for future cleanup

---

## Step 4: Write Test Cases

For each test case, use this format:

```
**[Short name]**
Precondition: [what state the user/system is in before this scenario]
Verify: [what must be true — outcome, not steps]
Pass criteria: [how you know it passed]
Priority: P0 / P1 / P2
```

Keep each test case to 3–4 lines. This is PM-level, not QA script level — scenarios
and outcomes, not step-by-step procedures.

Group by feature area, then by priority within each area.

---

## Step 5: Flag Open Decisions

Scan decisions.md for entries with `Status: open` that are relevant to this feature.

For each one, note:
- Which test cases it affects
- What the test case would look like under each possible resolution

Format:
> ⚠ **[Decision name]** is still open — this affects [test case name(s)].
> If resolved as X: [test case outcome]. If resolved as Y: [different outcome].

If no relevant open decisions, skip this section.

---

## Step 6: Identify PRD Gaps

List any areas where the brief doesn't specify behavior clearly enough to write a
complete test case. These are gaps the PM needs to resolve before engineering starts.

Format:
> **Gap: [area]** — The brief doesn't specify [what's unclear]. Needed before [test case X] can be finalized.

If no gaps, skip this section.

---

## Step 7: Write the Handoff Doc

Write `{feature-name}-handoff.md` to the current directory.

Structure:

```markdown
# [Feature Name] — Handoff Spec
**Source brief:** [filename or "pasted content"]
**Generated:** [date]
**Project:** [from project.md]

---

## Summary
[2-3 sentences: what this feature does, what the test cases cover, what's not covered]

---

## P0 — Must Pass Before Launch

### [Feature Area]
[test cases]

---

## P1 — Should Test Before Launch

### [Feature Area]
[test cases]

---

## P2 — Regression / Good to Have

### [Feature Area]
[test cases]

---

## Open Decisions Affecting This Spec
[flagged decisions, or "None — all relevant decisions are closed."]

---

## PRD Gaps to Resolve
[gaps, or "None identified."]
```

---

## Step 8: Confirm

Single line:
> "Written: **{feature-name}-handoff.md** — [N] P0, [N] P1, [N] P2 test cases. [N open decisions flagged / no open decisions affecting this spec.]"
