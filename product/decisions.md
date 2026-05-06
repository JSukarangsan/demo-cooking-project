# Decisions -- Cooking Search Personalization

A running log of key decisions. Newest entries at the top.

Log a decision when: scope changes, a technical approach is chosen, a user need is deprioritized, or stakeholder feedback shifts direction. Use `/log-decision` to add entries without breaking flow.

**Status key:** `open` = still in effect | `closed` = no longer applies | `superseded` = replaced by a later decision

---

## Deprioritize dark mode for search personalization feature

- **Status:** open
- **Date:** 2026-05-06
- **Decision maker:** Gaelle Sharma
- **Decision:** Dark mode will not be built as part of the search personalization feature.
- **Why:** Build complexity outweighs the value at this stage of the project.
- **Alternatives considered:** Implement later (deferred, not ruled out permanently).
- **Impact:** Reduces scope and engineering effort for Q2 MVP; dark mode support may be revisited in a future iteration.
- **Tags:** scope, design, MVP

---

## Search infrastructure: use cooking-rose with custom query templates

- **Status:** open
- **Date:** 2026-05-06
- **Decision maker:** Erik Hinton (Engineering Lead)
- **Decision:** Use cooking-rose with custom query templates for collections + keyword search work. Raquel's search platform team will handle tokenization improvements. 1-week turnaround.
- **Why:** Works today, query performance is fine at ~2M recipes. Elasticsearch re-index is 4 weeks + infra team support + over budget. Hybrid approach (cooking-rose + separate collection service) is unnecessary complexity for 3-5 curated collections.
- **Alternatives considered:**
  - New Elasticsearch index — ruled out (4-week setup, infra dependency, over budget)
  - Hybrid cooking-rose + separate collection service — ruled out (unnecessary complexity)
- **Impact:** Unblocks collections + keyword search. Tokenization work owned by Raquel's search platform team.
- **Source:** Erik Hinton, #cooking-search-eng, post-Friday spike
- **Tags:** engineering, search, infrastructure

---

<!-- ADD NEW DECISIONS ABOVE THIS LINE -->
