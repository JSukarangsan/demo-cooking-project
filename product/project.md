# Cooking Search Personalization

**Mission:** Cooking
**PM:** Gaelle Sharma
**Team:** Gaelle Sharma (PM), Michelle Chiu (Design), Erik Jonsson (Eng Lead), Raquel Hamias (Data/Insights), Sora Kim (PgM)
**Last updated:** 2026-05-05

---

## Problem & Discovery

Search results on NYT Cooking are the same for every user regardless of their cooking history, dietary preferences, or skill level. A beginner searching "chicken" gets the same results as someone who's saved 200 recipes. This leads to low engagement with search -- users default to browsing or the "For You" shelf instead.

**Who experiences this:** Subscribers with meaningful cooking history (10+ saved recipes) who use search to find new recipes.

**When they experience it:** Every time they search -- results feel generic rather than tailored to their preferences and cooking style.

**Research & signals:**

- Users who save 10+ recipes have 2x higher retention
- Survey (Q4 2025): 40% of active users wish search "knew what they liked"
- Qualitative feedback from CookX interviews: search feels generic
- Users already try longer queries on Cooking -- signaling readiness for smarter search
- User feedback: geographic/seasonal mismatch ("You show me results according to your climate in the north hemisphere, but I live in Brazil")
- Personalization described as "table stakes" in Jan 2026 product review -- same ranking algorithm applied to all users today

**Prior work:**

- 2025 experiment boosted results based on cuisine affinity (simple heuristic, not ML-based) -- moved metrics only marginally
- "For You" shelf uses collaborative filtering, but search ranking has never been personalized
- Semantic Search MVP launched April 30, 2026 -- "No Result" searches down ~50% from pre-launch baseline
- 3 search intent prototypes currently in research (v1, v2, v3); search intent classification prompt in development
- NAPP Search team also exploring search entry points -- potential cross-mission alignment

**Key assumptions (not yet validated):**

- Users want personalized search and won't find it creepy
- There is enough signal from saves and cooking history to produce meaningfully different rankings

---

## Strategy

**Strategic priority:** Search & Personalization bet -- one of Cooking's four major bets for 2026. The thesis is that personalized experiences drive retention and reduce churn among mid-tenure subscribers.

**Business goal:** Increase search-driven recipe saves and reduce subscriber churn among users in months 3-12 of their subscription.

**User goal:** Users should feel like Cooking "knows them" -- that search results reflect what they actually cook, not just what's popular globally. A weeknight home cook should see different results than someone who does elaborate weekend projects.

**Why now:** The recommendation infrastructure from the "For You" shelf launched last quarter, so ML infrastructure is in place. Cooking's 2026 strategy explicitly calls out personalization. Churn data from Q4 shows mid-tenure subscribers are the biggest retention gap.

**Why this over alternatives:** Considered a fully personalized homepage but search is a higher-intent surface -- users are actively telling us what they want. Personalizing search is also a more contained scope than rethinking the whole browse experience.

**OKR connection:** Cooking OKR 2 -- "Increase 90-day retention for subscribers in months 3-12 by 5pp." Search personalization is one of three projects under this OKR.

---

## Scope

### In Scope

- Personalized re-ranking of search results based on user history (saves, cooks, ratings)
- A minimum-signal threshold so we don't personalize for new users
- An A/B experiment to validate impact

### Out of Scope

- New search UI or changes to the search input experience
- Query auto-complete changes
- Personalized search suggestions
- Cross-platform personalization (web only for MVP)
- Editorial content boosting

### Dependencies

- ML infrastructure team for user vectors
- Experiment platform team for user-level bucketing
- Legal for privacy review of save-history usage
- Design needs the minimum signal threshold from Data before starting

---

## Team & Stakeholders

### Core Team


| Role             | Person                                          |
| ---------------- | ----------------------------------------------- |
| PM               | Gaelle Sharma (Search & Personalization)        |
| Designer         | Michelle Chiu (Lead Product Designer, ADAPT/AI) |
| Engineering Lead | Erik Jonsson (EM, API/Discovery track)          |
| Data / Insights  | Raquel Hamias (Audience Insights)               |
| PgM              | Sora Kim                                        |


### Stakeholders


| Name / Role                           | Involvement                                                      |
| ------------------------------------- | ---------------------------------------------------------------- |
| Michael Linares (VP, Product)         | Strategic scope decisions, timeline sign-off                     |
| Lauren Rosenfield (Director, Product) | Product direction, cross-bet alignment                           |
| Camilla Velasquez (GM, Cooking)       | Sign-off if scope expands beyond search                          |
| Meg Adams (Engineering leadership)    | Engineering resourcing, technical feasibility                    |
| AlgoRecs team                         | Personalization algorithms, potential infrastructure partnership |
| Lauren Savoie (Editorial lead)        | Editorial recipe visibility impact                               |
| Legal                                 | Privacy review of save-history usage                             |
| Accessibility                         | Any new UI patterns (AA compliance)                              |


### Decision Maker

Gaelle Sharma for product decisions. Michael Linares for anything that changes the strategic scope or timeline.

---

## Delivery

**Target date:** Experiment live by end of Q2 2026 (June 30). No hard external deadline, but it's a commitment in the Q2 planning cycle.


| Phase                    | Description                                                                                                         | Target     |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------- | ---------- |
| Phase 1 -- Scoping spike | Erik validates re-ranking approach, Raquel determines signal threshold, Sora confirms experiment platform readiness | April 2026 |
| Phase 2 -- Build         | Implement re-ranking, instrument metrics, design any UI indicators                                                  | May 2026   |
| Phase 3 -- Experiment    | Launch A/B test, monitor for 2-3 weeks                                                                              | June 2026  |


**Cut line:** UI indicators ("based on your saves" labels) go first. Then simplify the signal model -- saves only instead of saves + cooks + ratings. Absolute minimum is re-ranking based on saves with a simple threshold.

### Risks


| Risk                                                     | Likelihood | Impact                                      | Mitigation                                  |
| -------------------------------------------------------- | ---------- | ------------------------------------------- | ------------------------------------------- |
| Experiment platform may not support user-level bucketing | Medium     | High -- can't run experiment cleanly        | Sora checking with experiment platform team |
| Legal blocks use of save history for ranking             | Low        | High -- kills the approach                  | Early legal review (on Gaelle's list)       |
| Minimum signal threshold too high (50+ interactions)     | Medium     | High -- not enough users to personalize for | Raquel running historical data analysis     |


### Open Questions

- Can the experiment platform do user-level bucketing?
- What's the minimum signal threshold for meaningful personalization?
- Does Legal have concerns about save-history-based ranking?
- Should personalization be visible or invisible to users?
- Does Lauren Savoie have concerns about editorial recipe visibility?

---

## Measurement

**North Star:** Search-driven recipe save rate -- the percentage of searches that result in a recipe save within the same session.


| Metric                                 | Type    | Baseline | Target                             | Timeframe               |
| -------------------------------------- | ------- | -------- | ---------------------------------- | ----------------------- |
| Search-driven recipe save rate         | Primary | TBD      | TBD (experiment will establish)    | Per session             |
| Search result CTR                      | Leading | TBD      | Increase                           | Per session             |
| Position of clicked result             | Leading | TBD      | Higher (users click closer to top) | Per session             |
| Search sessions per user               | Leading | TBD      | Increase                           | Weekly                  |
| 90-day retention (personalized cohort) | Lagging | TBD      | +5pp vs. control                   | 90 days post-experiment |
| Recipe saves per subscriber per month  | Lagging | TBD      | Increase                           | Monthly                 |
| Search abandonment rate                | Lagging | TBD      | Decrease                           | Per session             |


**Guardrail metrics:**

- Search latency: p95 must stay under 300ms
- Editorial recipe visibility: editorially featured recipes can't drop more than 10% in impressions
- Content diversity: users shouldn't only see one cuisine

**Instrumentation gaps:**

- No real-time user vectors yet -- Raquel's team needs to build that
- May need to add position tracking for clicked search results

---

## Glean Findings

Key insights surfaced during project intake (2026-05-05):


| Insight                                                                             | Source                                                                                                                            |
| ----------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Semantic Search MVP launched April 30, 2026 -- "No Result" searches down ~50%       | [Slack: #cooking](https://nytimes.enterprise.slack.com/archives/CCU12V4Q4/p1777581028471729)                                      |
| Statsig experimentation for Cooking Search is complete (CAPI-248, all stories done) | [Jira: CAPI-248](https://nytimes.atlassian.net/browse/CAPI-248)                                                                   |
| Personalization described as "table stakes" -- same ranking for all users           | [Search & Personalization Review (Jan 2026)](https://docs.google.com/presentation/d/10tQAKRos20NDigp4EfQK_uel6YMdNxOW2sucxbRCKPY) |
| Users try longer queries -- readiness signal for smarter search                     | [Search & Personalization Review](https://docs.google.com/presentation/d/10tQAKRos20NDigp4EfQK_uel6YMdNxOW2sucxbRCKPY)            |
| Geographic/seasonal mismatch in results (user feedback)                             | [Search & Personalization Review](https://docs.google.com/presentation/d/10tQAKRos20NDigp4EfQK_uel6YMdNxOW2sucxbRCKPY)            |
| Cook Rate measured at session/day/week granularity for search success               | [Search & Personalization Review](https://docs.google.com/presentation/d/10tQAKRos20NDigp4EfQK_uel6YMdNxOW2sucxbRCKPY)            |
| Search Result Page redesign planned with AI suggestion area                         | [Search & Personalization Review](https://docs.google.com/presentation/d/10tQAKRos20NDigp4EfQK_uel6YMdNxOW2sucxbRCKPY)            |
| NAPP Search team exploring search entry points -- cross-mission alignment           | [NAPP Search Notes](https://docs.google.com/document/d/1wVCtHZK95kappBRP9JOvu_6BgktW-rTXk702tcNbzOo)                              |
| GraphQL migration in progress -- search data may come from subgraph or legacy REST  | [Cooking Apps Technical Strategy](https://docs.google.com/document/d/1oDpC57yLTkyGs_AwkjmjUFLvS70YAnDl_RclgBfBIak)                |
| All UI must use Pantry + TPL; 100% AA compliance target for mobile                  | [Cooking Apps Technical Strategy](https://docs.google.com/document/d/1oDpC57yLTkyGs_AwkjmjUFLvS70YAnDl_RclgBfBIak)                |
| 3 search intent prototypes in research; intent classification prompt in development | [Slack: #cooking-search-personalization-bet](https://nytimes.enterprise.slack.com/archives/C0A70LP1MC5/p1772226961763089)         |


---

*Generated by NYT Product Context System. Update as the project evolves.*