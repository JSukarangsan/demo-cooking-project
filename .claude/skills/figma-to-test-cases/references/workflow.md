# Figma to Test Cases — Workflow Reference

Read this file to execute the `/figma-to-test-cases` skill. Follow each step in order.

---

## Step 1: Load Project Context

Read the project kit files. Search in order: `./file.md` → `./product/file.md` → `../product/file.md`

**Load if present:**
- `project.md` — project manifest
- `constraints.md` — hard constraints (accessibility, design system, platform rules)
- `decisions.md` — decision log (flag open decisions that affect ACs)

These provide grounding context. If none are found, proceed anyway — the Figma design is the primary input.

---

## Step 2: Get the Figma URL

If the user hasn't already provided a Figma URL, ask:
> "Paste the Figma URL for the designs you want test cases for. You can link to a specific frame or the whole file."

Also ask:
> "Is there a related feature brief I should cross-reference? (paste a path or say 'skip')"

---

## Step 3: Parse the Figma URL

Extract fileKey and nodeId from the URL:
- `figma.com/design/:fileKey/:fileName?node-id=:nodeId` → convert `-` to `:` in nodeId
- `figma.com/design/:fileKey/branch/:branchKey/:fileName` → use branchKey as fileKey

If no nodeId is provided, the skill will work with the full file context.

---

## Step 4: Get Design Context from Figma

Call the Figma MCP tools:

1. **`get_design_context`** with fileKey and nodeId — returns code representation, screenshot, and contextual hints (component docs, annotations, design tokens)
2. **`get_screenshot`** with fileKey and nodeId — visual reference for understanding the design

Read the returned context carefully. Pay attention to:
- Component names and documentation links
- Design annotations (notes from the designer)
- State variants (default, hover, active, disabled, error, loading, empty)
- Design tokens and CSS variables

If the design spans multiple frames/screens, call `get_design_context` for each key screen.

---

## Step 5: Extract Acceptance Criteria from Design

From the design context, identify and categorize:

### Screens & States
- What screens/views are shown?
- What states does each screen have? (default, loading, error, empty, success, partial)
- Are there conditional views (logged in vs. logged out, new user vs. returning)?

### Interactive Elements
- Buttons: what do they do? What are the enabled/disabled conditions?
- Inputs: what validation is implied? Character limits? Placeholder text?
- Toggles/switches: what do they control?
- Navigation: where do links/buttons take the user?

### Flows
- What is the happy path through the screens?
- Are there branching paths (success vs. error)?
- Are there multi-step flows (wizards, onboarding)?

### Edge Cases Visible in Design
- Text truncation (long names, titles)
- Overflow behavior (lists, grids)
- Responsive breakpoints (if multiple sizes shown)
- Empty states (no data, first-time use)

### Component Annotations
- Designer notes or callouts in the Figma file
- Component documentation links (from Code Connect)
- Specific interaction specs (animation, timing, gestures)

---

## Step 6: Cross-Reference with Constraints

If `constraints.md` exists, check for:
- Accessibility requirements (WCAG level, screen reader, keyboard nav)
- Design system rules (component usage, spacing, color)
- Platform-specific requirements (iOS vs. Android vs. web)
- Legal/compliance constraints that affect UI (disclaimers, consent)

Add ACs for any constraints that apply to the designed screens.

---

## Step 7: Cross-Reference with Feature Brief

If a feature brief was provided:
- Check if the brief has ACs that should be validated against the design
- Identify requirements in the brief that the design doesn't cover (flag as gaps)
- Identify design details not mentioned in the brief (flag as additions)

---

## Step 8: Assign Priority

Use the same P0/P1/P2 scheme as the test-cases skill:

| Priority | Definition | Examples |
|----------|-----------|----------|
| **P0** | Core functionality. If this fails, the feature is broken. | Happy path works, primary action completes, data saves correctly |
| **P1** | Important behavior. Feature works but experience is degraded. | Error states show correctly, loading states appear, validation works |
| **P2** | Polish and edge cases. Nice-to-have for launch. | Truncation handles gracefully, animations smooth, empty states styled |

---

## Step 9: Flag Gaps and Open Questions

Note anything that seems incomplete or ambiguous:
- Screens that seem missing from the flow (e.g., confirmation step, error recovery)
- States not designed (what happens on timeout? on network error?)
- Open design decisions (annotations that say "TBD" or "discuss")
- Constraints not reflected in the design
- Brief requirements with no corresponding design

Format these as a "Gaps & Open Questions" section at the end of the handoff.

---

## Step 10: Write the Handoff

Show a summary before writing:
> "I found [X] acceptance criteria across [Y] screens. [Z] are P0, [W] are P1, [V] are P2. [N] gaps flagged. Ready to write?"

Write to: `{feature-name}-figma-handoff.md` in the current directory (or `product/briefs/` if it exists).

Confirm with a single line:
> "Handoff written to `{feature-name}-figma-handoff.md`."

---

## Handoff Output Format

```markdown
# {Feature Name} — Figma Handoff

**Source:** {Figma URL}
**Date:** {date}
**Screens covered:** {count}

---

## P0 — Must Ship

### {Screen/Flow Name}

| # | Acceptance Criteria | Precondition | Verify | Pass When |
|---|-------------------|-------------|--------|-----------|
| 1 | {AC description} | {setup needed} | {action to take} | {expected result} |

## P1 — Should Ship

### {Screen/Flow Name}

| # | Acceptance Criteria | Precondition | Verify | Pass When |
|---|-------------------|-------------|--------|-----------|
| 1 | {AC description} | {setup needed} | {action to take} | {expected result} |

## P2 — Nice to Have

### {Screen/Flow Name}

| # | Acceptance Criteria | Precondition | Verify | Pass When |
|---|-------------------|-------------|--------|-----------|
| 1 | {AC description} | {setup needed} | {action to take} | {expected result} |

---

## Gaps & Open Questions

- [ ] {gap or question} — {context, source}

## Design Additions Not in Brief

- {detail from design that isn't covered in the brief}

## Brief Requirements Not in Design

- {requirement from brief with no corresponding design}
```
