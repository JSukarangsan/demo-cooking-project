# Update Context — Workflow Reference

## Step 1: Read Current Kit State

Before parsing input, silently read the kit files. For each file, look in `./` first, then `./product/`, then `../product/` (first match wins — supports both cross-functional and legacy flat layouts):
- `CLAUDE.md` — current project summary and framing (always at `./CLAUDE.md`)
- `project.md` — full project manifest
- `decisions.md` — existing decision log
- `constraints.md` — current constraints
- `todo.md` — open questions and next steps
- `glossary.md` — existing terms

Note what's already captured so you don't create duplicate entries or overwrite existing content without flagging conflicts.

---

## Step 2: Parse Input and Classify

Read the input in full. Identify all distinct pieces of new information. Classify each one:

**Decisions** — something agreed on, confirmed, or explicitly ruled out:
- "we decided to X"
- "we're cutting Y from v1"
- "agreed: Z"
- Explicit descoping ("personalization is out of v1")

**Constraints** — a hard limit the project must work within:
- Infrastructure limitation discovered
- Legal or compliance requirement flagged
- Budget or headcount cap confirmed
- External dependency the team cannot control

**Scope changes** — what's in or out has shifted:
- Something added to scope
- Something moved out of scope
- MVP definition changed

**Delivery changes** — timeline, phases, milestones:
- Date moved
- Phase split or collapsed
- New milestone or deadline added

**Stakeholder or team changes** — who's involved:
- New stakeholder identified
- Sponsor or decision-maker changed
- Team member added or removed

**Open questions** — raised but not yet resolved:
- "we still need to figure out X"
- Something debated without conclusion
- A question surfaced that nobody answered

**Action items** — concrete next steps with an owner:
- "[Name] will do X by [date]"
- "[Team] needs to review Y"
- Follow-up assigned to someone

**New terms** — concepts, product names, or jargon introduced:
- A new feature name used for the first time
- An internal term or acronym not yet in the glossary
- A methodology or framework referenced

**Strategic shifts** — framing, goal, or priority changed meaningfully:
- Core problem statement evolved
- A different OKR is now driving the work
- The strategic bet or approach changed

Do NOT classify: opinions still being debated, background context already in the kit, filler conversation, restating what's already documented.

---

## Step 3: Show Routing Summary

Before writing anything, show a structured summary:

> "Here's what I found and where I'll route it. Type **write all** to confirm, or adjust anything first:"
>
> **decisions.md** (2 new entries)
> - Cut personalization from v1 — VP decision, compliance + infra reasons
> - Base search experience is the v1 MVP
>
> **constraints.md** (2 new entries)
> - Real-time indexing not supported by current infra [Technical]
> - Personalization may trigger compliance review before shipping [Legal]
>
> **project.md → Scope**
> - Move "personalized search results" from In Scope → Out of Scope
>
> **todo.md → Open Questions**
> - Who owns the Q3 personalization revisit? (no owner named)
>
> **CLAUDE.md**
> - Update project summary: personalization descoped from v1

If something is ambiguous (could be a decision or still open), flag it:
> "Not sure about this one — is it decided or still open? [item]"

---

## Step 4: Write All Changes

After confirmation, write all changes in a single pass. Order:

1. decisions.md
2. constraints.md
3. project.md
4. todo.md
5. glossary.md
6. CLAUDE.md (only if flagged in the routing summary)

### decisions.md
Insert new entries at the top of the log, following this format:

```markdown
## [Short name]
**Date:** YYYY-MM-DD
**Status:** open
**Decision maker:** [Name / Role]
**What we decided:** [1-2 sentences]
**Why:** [Rationale]
**Alternatives considered:** [What was ruled out]
**Impact:** [What this affects]
**Tags:** [scope | technical | legal | strategy | ux | data]

---
```

Tag inference:
- Engineering/infra/platform → `technical`
- Scope/cut/descope → `scope`
- Legal/privacy/compliance → `legal`
- Design/UX → `ux`
- Metrics/OKRs/strategy → `strategy`
- Data/analytics → `data`

### constraints.md
Append to the relevant section (Technical, Legal & Compliance, Business, Design, Dependencies):

```markdown
- [Constraint description] *(added YYYY-MM-DD)*
```

### project.md
Update in place — find the relevant section and edit it directly. Do not append a new section; update the existing one.

- Scope changes → update In Scope / Out of Scope lists
- Delivery changes → update the phases table or target date
- Team changes → update the team or stakeholders table
- Strategy shifts → update the relevant field(s) in Strategy section

### todo.md
Open questions — append to Open Questions:
```markdown
- [ ] [Question] — Owner: [name or TBD] — By: [date or TBD]
```

Action items — append to Next Steps:
```markdown
- [ ] [Action] — [Owner]
```

### glossary.md
Append new terms in alphabetical order:
```markdown
**[Term]** — [Definition, 1-2 sentences]
```

### CLAUDE.md — update only when:
- The project's core problem statement changed
- Scope changed materially (major descoping or significant addition)
- Strategic priority or the driving OKR shifted
- MVP definition changed

Do NOT update CLAUDE.md for individual decisions, minor tweaks, action items, or new open questions.

When updating: edit the project summary section to reflect current state. Keep it concise — CLAUDE.md is a context anchor, not a changelog.

---

## Step 5: Confirm

Single summary after writing — one line per file touched:

> "Kit updated:
> - decisions.md — 2 new entries
> - constraints.md — 2 entries added
> - project.md — Scope section updated
> - todo.md — 1 open question added
> - CLAUDE.md — project summary updated"

Do not re-read content back or repeat what was written.

---

## Edge Cases

**Input conflicts with an existing decision:**
Flag before writing:
> "This seems to conflict with an existing decision: **[decision name]**. Do you want to supersede it, or is this an amendment?"
If superseding: mark the old entry `Status: superseded`, add "Superseded by [new decision] on [date]" to its Impact field, then log the new decision.

**Something in the input is already in the kit:**
Skip it silently. No duplicates.

**Kit files not found:**
> "I can't find project.md or decisions.md in this folder or product/ subfolder. Are you in the right project directory?"

**Input is a single sentence (very sparse):**
If it's clearly just one decision or action, handle it directly without the full routing summary — don't add ceremony to a simple update. Use judgment.

**All items are already captured:**
> "Everything in this looks like it's already in the kit. Nothing new to write."
