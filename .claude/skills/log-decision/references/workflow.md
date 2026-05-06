# Log Decision — Workflow Reference

## Step 1: Detect Input Mode

**Path A — PM states a decision directly:**
Message contains a decision statement ("we decided to X", "we're going with Y", "we agreed on Z").
→ Go to Step 2A.

**Path B — PM pastes raw text:**
Message contains multi-line text that looks like meeting notes, a Slack thread, or an email.
→ Go to Step 2B.

---

## Step 2A: Direct Statement Path

Parse the decision from the PM's message. Extract:
- What was decided (required — parse from message)
- Who decided (optional — parse from message if named)
- Why (optional — parse from message if given)
- Alternatives considered (optional — parse from message if given)

Ask only for what's missing, in a single message, max 3 questions:

> "Got it — logging that. Quick gaps:
> - Who made this call? (name or role)
> - What drove the decision? (optional — skip if obvious)
> - Anything else that was considered and ruled out?"

Skip any question already answered in the original message.
After the PM replies, write to decisions.md immediately — no additional confirmation step.

---

## Step 2B: Raw Text Extraction Path

Identify all decision-shaped statements in the pasted text:
- Something agreed on ("we'll go with X", "decided to Y", "confirmed: Z")
- Something explicitly ruled out ("not doing X in v1", "descoped Y")
- A constraint accepted ("must ship by X", "legal requires Y")

Do NOT include: open questions still being debated, action items or next steps, opinions without resolution.

Show a numbered list before writing:
> "I found [N] decisions in this text. Confirm before I log them:
>
> 1. **[Short name]** — [what was decided, 1 sentence]
> 2. **[Short name]** — [what was decided, 1 sentence]
>
> Type 'log all' or remove/adjust anything."

After confirmation, write all confirmed entries. Flag uncertain items:
> "I wasn't sure about these — want me to log them as open questions in todo.md instead?
> - [uncertain item]"

---

## Step 3: Write to decisions.md

Find `decisions.md` by looking in `./decisions.md`, `./product/decisions.md`, or `../product/decisions.md` (first match wins). Insert the new entry at the top, immediately after `<!-- ADD NEW DECISIONS ABOVE THIS LINE -->`.

```markdown
## [Short name]
**Date:** YYYY-MM-DD
**Status:** open
**Decision maker:** [Name / Role]
**What we decided:** [1-2 sentences]
**Why:** [Rationale]
**Alternatives considered:** [What was ruled out]
**Impact:** [What this affects]
**Tags:** [inferred tags]

---
```

**Tag inference:**
- engineering/tech/infra mentioned → `technical`
- scope/in-out/cut mentioned → `scope`
- legal/privacy/compliance mentioned → `legal`
- design/UX/interface mentioned → `ux`
- metrics/OKRs/strategy mentioned → `strategy`
- data/analytics/instrumentation mentioned → `data`

Default status: `open`. Default decision maker: `[unspecified]` if not named.

---

## Step 4: Confirm

Single line only:
> "Logged: **[Short name]** → decisions.md"

Do not re-read the entry back or repeat the content.

---

## Edge Cases

**"Change the status to closed"** → Find the entry, update Status field. Confirm: "Updated [name] → closed."

**"We reversed the decision on X"** → Find the existing entry, set Status to `superseded`, add to Impact: "Superseded by [new decision] on [date]." Log the new decision as a separate entry.

**decisions.md doesn't exist** → Create it using the template format, then write the entry.
