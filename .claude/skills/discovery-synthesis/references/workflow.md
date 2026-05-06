# Discovery Synthesis — Workflow Reference

## Accepted Input Types
- Interview transcripts (Granola, Dovetail exports, raw text)
- Survey responses or exports
- Usability test notes or session summaries
- Competitor analysis notes
- Analytics data or reports
- Stakeholder feedback or executive comments

## Context Loading

Look for `project.md` in this order: `./project.md`, `./product/project.md`, `../product/project.md`. First match wins. Use it to understand the project problem space and goals — this frames how insights are interpreted and which recommendations are most relevant.

## Glean Queries (if configured)

| Trigger | Query | Purpose |
|---|---|---|
| After themes are identified | `{mission} {theme} user research prior findings` | Find prior research that corroborates or contradicts these themes |
| After recommendations are drafted | `{mission} {recommendation_area} prior experiments outcomes` | Find prior experiments that tested similar ideas |

## Synthesis Approach

Follow these steps in order. Don't skip to recommendations before completing the earlier steps.

1. **Inventory** — list all inputs provided, note any gaps or missing perspectives
2. **Immerse** — read/skim all inputs before drawing any conclusions
3. **Theme** — identify 3-5 recurring patterns across inputs
4. **Insight** — for each theme, state the so-what (not just what was observed — what does it mean for the product?)
5. **Tension** — call out contradictions or conflicting signals between sources
6. **Recommend** — translate insights into specific product or design directions
7. **Validate** — note what would need to be true for each recommendation to hold

## Output

Write two files to `./`:

**`{topic}-synthesis.md`**
- Research inputs inventory
- Key themes (3-5) with supporting evidence
- Insights per theme (the so-what)
- Contradictions and unresolved tensions
- Open questions

**`{topic}-recommendations.md`**
- Ranked recommendations with rationale
- Assumptions behind each recommendation
- Suggested next steps / validation methods
