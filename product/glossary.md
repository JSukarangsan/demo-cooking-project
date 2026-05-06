# Glossary -- Cooking Search Personalization

Shared vocabulary for this project. Especially useful when engineering, design, editorial, and product use different words for the same things.

---

## Mission-Level Terms

### Product Terms

| Term | Definition |
|---|---|
| **RDP** | Recipe Detail Page -- the individual recipe page in the Cooking app/web |
| **SLP** | Search Landing Page -- the page users see when tapping into search before typing |
| **Cook Mode** | Full-screen, step-by-step cooking view. Cook Mode 2.0 adds ingredients in steps, timers, font size controls. |
| **ADAPT** | Current AI feature initiative (formerly "Subs & Mods" / Adaptations). Recipe modifications and substitutions via chatbot UX. |
| **Recipe Box** | User's personal saved recipe collection -- folders, notes, cooked status |
| **Shortcuts** | Personalized quick-access tiles on the app Home tab (e.g., "Weeknight Dinners") |
| **Cooked Signal** | Data event capturing that a user completed cooking a recipe (>5 min active time) |

### Business / Growth Terms

| Term | Definition |
|---|---|
| **Regi** | Registered (free) user -- not a subscriber |
| **Multi-day MAU** | Users visiting 2+ days/month -- best predictor a regi will convert |
| **Starts** | New subscription starts |
| **CVR** | Conversion rate |
| **WAU / MAU / DAU** | Weekly / Monthly / Daily Active Users |
| **AA** | All Access -- NYT's bundled subscription tier |
| **SubX** | Subscriber Experience team -- cross-product subscriber engagement and bundle strategy |

### Technical Terms

| Term | Definition |
|---|---|
| **Pantry** | Cooking's design system / visual language across all platforms |
| **TPL** | Times Product Language -- NYT-wide shared design system. Cooking uses TPL for shared components. |
| **Cooking Subgraph** | New GraphQL-based data architecture for Cooking. Major infrastructure initiative. |
| **Cooking-rose** | Internal search engine/system for Cooking recipes (Elasticsearch-based) |
| **Statsig** | Experimentation/feature flagging platform (replacing legacy ABRA) |
| **ABRA** | Legacy A/B testing platform being deprecated |
| **AlgoRecs** | Algorithmic recommendations system |
| **Fastly** | Edge cache / CDN layer. All requests hit Fastly first. |

### Organizational Terms

| Term | Definition |
|---|---|
| **Tracks** | Tech-stack-aligned delivery teams: Apps, Web, API, Publishing |
| **Big Rocks / Bets** | Annual strategic priorities (4 bets in 2026) |
| **DRI** | Directly Responsible Individual |
| **XFun** | Cross-functional -- the broader org encompassing standalone products |
| **DDD** | Demos, Discussions, and Decisions -- biweekly cross-engineering meeting |
| **DIG** | Data Insights Group -- research and analytics team |

## Project-Specific Terms

| Term | Definition |
|---|---|
| **User vector** | A computed representation of a user's preferences based on their history (saves, cooks, ratings) -- used to re-rank search results |
| **Re-ranking** | Applying a personalization layer after the base Elasticsearch query returns results -- safer than modifying the core search |
| **Signal threshold** | The minimum number of user interactions needed before personalization produces meaningful results |
| **User-level bucketing** | Experiment design where individual users (not content) are randomly assigned to treatment/control groups |

---

*Keep this current. When the team uses a term differently than the definition here, update the definition or add a new entry.*
