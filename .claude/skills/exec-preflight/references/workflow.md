# Exec Preflight — Workflow Reference

## Step 1: Load Context

Read before reviewing the doc. For each file, look in `./`, then `./product/`, then `../product/` (first match wins):
- `project.md` — problem framing, goals, OKR connection, team
- `decisions.md` — open decisions that might surface as objections
- `constraints.md` — hard limits the exec might probe

If the PM has pasted or @ referenced a doc, read that too. If no doc was provided:
> "What doc should I review? Paste it or @ reference it and I'll run the preflight."

---

## Step 2: Run the Three Persona Reviews

Review from each persona sequentially in a single response.

### Persona 1 — Mission VP / Director (strategic fit)
- Does this connect clearly to mission OKRs or the current strategic priority?
- Why this over other things the team could be doing right now?
- What's the business case — is the upside sized anywhere?
- Is the problem statement strong enough, or does it feel like a solution looking for a problem?
- What's the ask, and is it clearly stated?

### Persona 2 — Engineering Lead (technical risk + scope realism)
- Is the scope realistic for the timeline stated?
- Are there technical dependencies or infrastructure gaps not called out?
- What decisions are still open that engineering needs before estimating?
- Is anything being promised that will be harder than it looks?
- Are there open decisions in decisions.md that could block engineering?

### Persona 3 — Editorial / Business Stakeholder (user + revenue impact)
- Is the user/reader impact clear and specific?
- Is there a revenue or subscription implication, and is it quantified?
- Does this create any risk to the brand, editorial trust, or subscriber relationship?
- Does this conflict with any ongoing editorial priorities or calendar moments?
- Is there a non-subscriber or growth story here?

---

## Step 3: Synthesize

```
**Synthesis**

Strong cards (what lands well across all three):
• [1-3 things that are genuinely compelling]

Buried lead (what should be up front but isn't):
• [The most persuasive thing currently mid-doc]

Pre-address before you walk in:
• [1-3 questions that will definitely come up — have the answer ready]

Open decisions that could derail the meeting:
• [Any entries from decisions.md that are open and relevant to this doc]
```

---

## Step 4: Ask Which Angle Matters Most

> "Which angle matters most for this meeting?
> 1. Strategic / OKR — roadmap or planning conversation
> 2. Revenue / subscription — budget or investment ask
> 3. Technical — engineering review follows
> 4. All three — full leadership review"

---

## Step 5: Reframe for the Chosen Angle

**Strategic / OKR:** Lead with OKR connection and why this is the right bet now. Make "why this over X" explicit. Surface the North Star metric prominently.

**Revenue / subscription:** Lead with the conversion or retention number (even rough). Frame as a funnel investment. Quantify upside even if estimated. Move subscriber/revenue data to the opening.

**Technical:** Lead with scope clarity and what's decided vs. open. Surface open decisions from decisions.md that engineering needs answered. Make the timeline realistic or flag the risk explicitly.

**All three:** Find the single strongest card across all three angles and lead with it. Sequence: strategic → technical → user.

---

## Step 6: Offer to Save

> "Want me to save the reframed version? I'll write it to `{doc-name}-preflighted.md`."

---

## Persona Customization

Default personas work for most NYT missions. If project.md names specific stakeholders or describes an unusual review audience, adapt accordingly:

- Games (no editorial stakeholder) → replace Persona 3 with "Growth / Subscription Marketing"
- Developer platform → replace Persona 3 with "External developer / partner"
- Data infrastructure → replace Persona 1 with "CTO / Platform leadership"

Use the stakeholders listed in `project.md` as the source of truth.
