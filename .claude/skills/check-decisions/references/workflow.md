# Check Decisions — Workflow Reference

## Step 1: Read decisions.md

Find `decisions.md` by looking in `./decisions.md`, `./product/decisions.md`, or `../product/decisions.md` (first match wins). Read the full file.

If the file doesn't exist or is empty:
> "No decisions have been logged yet for this project. Want me to start the log?"

---

## Step 2: Match the Query

Search for entries relevant to the PM's question. Match on:
- Topic / subject matter (semantic — not just keyword)
- Names of features, systems, or people mentioned
- Type of decision (scope, technical, legal, etc.)

**One clear match** → Step 3.

**Multiple partial matches** → Return all with a note:
> "Found [N] related decisions — here's what's in the log:"
Then list each in full.

**Nothing matches** → Step 4.

---

## Step 3: Return the Decision

Show the full entry, then add a one-line interpretation:

```
**[Short name]** · [Date] · Status: [open/closed/superseded]

What we decided: [text]
Why: [text]
Alternatives considered: [text]
Impact: [text]
Decision maker: [text]
Tags: [text]
```

> **What this means for your question:** [1-2 sentences interpreting the decision in context]

**If status is `open`:**
> ⚠ This decision is marked open — it hasn't been fully resolved. Don't treat it as settled.

**If status is `superseded`:**
> Note: This was superseded — check the Impact field for the replacement decision.

---

## Step 4: Not Found

> "Nothing in the decision log for '[topic]'.
>
> Options:
> 1. Log it as an open question in todo.md
> 2. Log a decision now if it's been resolved
> 3. Skip — treat as undecided"

Wait for the PM's choice and act accordingly.

---

## What This Skill Does Not Do
- Does not query Slack, Glean, or any external system
- Does not infer decisions from project.md or constraints.md — reads decisions.md only
- Does not reopen closed decisions without explicit PM instruction
