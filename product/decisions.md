# Decisions -- Cooking Search Personalization

A running log of key decisions. Newest entries at the top.

Log a decision when: scope changes, a technical approach is chosen, a user need is deprioritized, or stakeholder feedback shifts direction. Use `/log-decision` to add entries without breaking flow.

**Status key:** `open` = still in effect | `closed` = no longer applies | `superseded` = replaced by a later decision

---

## DEC-001 · Deprioritize dark mode for Search Personalization MVP

- **Status:** open
- **Date:** 2026-05-06
- **Decision maker:** Gaelle Sharma (PM)
- **Decision:** Dark mode support will not be included in the Search Personalization MVP.
- **Why:** Timeline constraints — experiment must be live by end of Q2 2026 (June 30). Dark mode implementation adds scope without contributing to the primary metric (search-driven recipe save rate).
- **Alternatives considered:** Full dark mode support at launch.
- **Impact:** Users on dark mode may see suboptimal UI in personalized search surfaces. Can be addressed post-experiment if the feature ships.
- **Tags:** `scope`, `design`, `mvp`, `timeline`

---

## DEC-002 · Use cooking-rose with custom query templates for collections + keyword search

- **Status:** open
- **Date:** 2026-05-06
- **Decision maker:** Erik Hinton (Engineering Lead)
- **Decision:** Use cooking-rose with custom query templates (option 2 of 3) for the collections + keyword search work.
- **Why:** Works today without infra team involvement. Query performance is acceptable at ~2M recipes. Option 1 (new Elasticsearch index) was 4 weeks + infra support + over budget. Option 3 (hybrid: cooking-rose + separate collection service) added unnecessary complexity for 3-5 curated collections.
- **Alternatives considered:** (1) New Elasticsearch index — clean but 4-week setup, needs infra team, over budget. (3) Hybrid cooking-rose + separate collection service — unnecessary complexity.
- **Impact:** Raquel Hamias's search platform team will own tokenization work for ingredient matching. ~1-week turnaround confirmed.
- **Tags:** `technical`, `search`, `infrastructure`, `collections`

---

<!-- ADD NEW DECISIONS ABOVE THIS LINE -->
