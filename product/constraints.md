# Constraints -- Cooking Search Personalization

Hard limits the project must work within. If something here becomes negotiable, move it to decisions.md with rationale.

---

## Mission-Level Constraints

These apply to all projects in the Cooking mission. Pre-populated from mission context.

### Technical

- **GraphQL migration is in progress.** Some data comes from subgraph, some from legacy REST. Ask which source a feature needs.
- **Recipe data model changes are expensive.** New fields require API changes, client updates, and data migrations.
- **Experiment infrastructure required.** All metric-moving features must run through Statsig with holdback and ramp.
- **Platform parity is not automatic.** A feature on web may take additional quarters for iOS/Android. Scope explicitly.
- **Pantry design system required.** All UI must use Pantry (Cooking) and TPL (shared NYT). No custom one-offs.
- **Performance budget is real.** Crash-free session rate >99.7%. "Thanksgiving Ready" is the reliability bar.
- **Auth/subscription is shared infrastructure.** Login, subscription status, and paywall logic are owned by NYT shared platform.
- **Search index takes hours.** Cooking-rose ingests 80M+ articles. Index time is ~9 hours. Changes to search logic need careful release planning.

### Design

- All UI must use Pantry (Cooking-specific) and TPL (shared NYT) design systems.
- 100% AA accessibility compliance target for mobile features by end of 2026.
- VQA/DQA (Visual/Design Quality Assurance) is required before launch.

### Guardrail Metrics

| Guardrail | Context |
|---|---|
| Starts / conversion efficiency | Cannot let cost-per-start degrade |
| Platform stability / uptime | Crash-free session rate >99.7%. "Thanksgiving Ready" bar. |
| Recipe quality | Tested recipes are a core differentiator. Never trade quality for speed. |
| Holiday search traffic | Q4 search dip in 2024 was a warning. Must mitigate further erosion. |
| Newsletter traffic | Declined due to Google unsub issue. Being fixed with unique sender addresses. |

---

## Project-Level Constraints

These are specific to this project. Populated from the intake interview.

### Technical
- Can't degrade search latency -- current p95 is 200ms, can't exceed 300ms
- Must confirm whether search data comes from Cooking Subgraph (GraphQL) or legacy REST before building
- Statsig experimentation infrastructure for Cooking Search is ready (CAPI-248 complete)
- **cooking-rose filter cap:** Max ~50 filters per query. Current collections approach uses 8-12 (safe headroom). Do not let scope creep push past 30 — performance degrades beyond that. *(Source: Erik Hinton, 2026-05-06)*
- **Ingredient matching is English-only.** Multilingual tokenization is a separate body of work, Q3 earliest per Raquel. *(Source: Erik Hinton, 2026-05-06)*
- **cooking-rose API rate limit: 200 req/sec.** Web allocation is fine. If Osvaldo's apps team wants access to the collections API, they need their own rate limit allocation — do not share ours. *(Source: Erik Hinton, 2026-05-06)*

### Measurement
- **Recipe Save Rate excludes logged-out users.** ~22% of search traffic is logged-out; saves cannot be tracked for them. All save rate baselines and targets reflect logged-in users only. *(Source: Priya Sharma, DIG, 2026-05-27)*
- **Looker cannot segment by subscription tier (free vs. subscriber).** Adding that dimension requires a 2-week lead time from Priya's team. If tier segmentation is needed for launch metrics, the request must go out immediately. *(Source: Priya Sharma, DIG, 2026-05-27)*
- **Use Q2 2025 baseline (7.9%) for Recipe Save Rate comparisons, not Q4 (11.1%).** Q4 has a known holiday seasonality spike (Nov-Dec). We are measuring impact in Q2. *(Source: Priya Sharma, DIG, 2026-05-27)*

### Legal & Compliance
- Need legal review before using save history to affect search rankings
- Privacy implications of using behavioral data for personalization TBD

### Business
- Web only for MVP -- cross-platform personalization is explicitly out of scope
- Editorial recipe visibility cannot drop more than 10% in impressions (guardrail)
- Content diversity must be maintained -- no single-cuisine filter bubbles

### Design
- Must use Pantry components for any UI changes
- Visible vs. invisible personalization is an open product decision
- Design work blocked until minimum signal threshold is determined by Data
- **Max 2 type weights per screen.** Brand guidelines prohibit 3+ type weights on a single screen (e.g., regular + medium + bold). Search results page already corrected in design mocks. Do not reintroduce a third weight in any screen. *(Source: Michelle Park, brand review, 2026-05-27)*

### Dependencies (Blocking)

| Dependency | Owner | Status |
|---|---|---|
| User vectors (real-time) | Raquel Hamias / ML infrastructure team | Not yet built |
| User-level bucketing in experiment platform | Sora Kim / Experiment platform team | Checking feasibility |
| Legal privacy review of save-history usage | Gaelle Sharma / Legal | Not yet started |
| Minimum signal threshold analysis | Raquel Hamias | In progress |

---

*Update as new constraints are discovered. Date each entry.*
