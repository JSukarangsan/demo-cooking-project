# Cooking Search Personalization -- Insights

Insights artifacts for **Cooking Search Personalization**.

---

## Metric Definitions

| Metric | Definition | Used by |
|---|---|---|
| **Cook Rate** | Recipe is "cooked" if >5 min of total active time per day on that recipe. Measured per session, per day, and per week. | Search & Personalization bet |
| **Search Success** | Composite: Result CTR (relevance) + Engagement Rate (quality) + Search Volume (usage) | Search & Personalization bet |
| **Search-driven recipe save rate** | % of searches that result in a recipe save within the same session | This project's North Star |

---

## Dashboards & Tools

| Dashboard | Location | Owner |
|---|---|---|
| Cooking Productivity Metrics | [Jira Dashboard #12770](https://nytimes.atlassian.net/jira/dashboards/12770) | Kyle Oye |
| Cooking Web Team Metrics 2026 | [Jira Dashboard #14601](https://nytimes.atlassian.net/jira/dashboards/14601) | Subathra Thanabalan |
| Internal Search Dashboard | [Mode Report](https://app.mode.com/nytimes/reports/c848f0825c41) | Discovery team |
| Cooking Subgraph Dashboard | [Datadog](https://nytimes.datadoghq.com/dashboard/dky-rc5-cjs/cooking-subgraph) | API team |
| Search Reliability Dashboard | [Datadog](https://nytimes.datadoghq.com/dashboard/g2g-q8n-36g/cooking-search-reliability) | API team |
| Statsig experiments | [go.nyt.net/statsig](https://go.nyt.net/statsig) | Experimentation Platform |

---

## Data & Analytics Team

- **DIG (Data Insights Group) for Cooking** -- primary contact for audience and engagement data
- **Raquel Hamias** -- leads Audience Insights for Cooking and Wirecutter
- Slack: `#ask-a-data-chef`
- [Cooking DIG Hub (Coda)](https://coda.io/d/_duoWL0z8bUj/_su5adsUy) -- experimentation catalog, analyses, dashboards, SQL components
- Key limitation: "ETSOR" tables have known data issues and caveats documented in the hub

---

## Experimentation

- Migrating from **ABRA** to **Statsig** (target: all A/B experiments on Statsig by end of H1 2026)
- Client-side experiments via React hooks on web, Statsig SDK on mobile
- Server-side experiments via Fastly Compute
- All metric-moving features must run through experiment platform with holdback and ramp
- **Statsig for Cooking Search is ready** (CAPI-248 complete) -- feature gates and experiment values surfaced in HTTP response and GraphQL resolver

---

## Prior Research

### Search & Discovery
- Search is the primary way users discover and return to recipes
- Nearly 1% of all ChatGPT conversations involve recipes/cooking -- competitive pressure
- Users already try longer search queries on Cooking -- signaling readiness for smarter search
- Core Cooking strengths vs. LLM tools: trusted recipes, social proof, imagery, memory, guided cooking
- New search filters launched Dec 2025: "5 Ingredients", "Great Leftovers", Equipment filters

### Conversion & Growth
- Non-subscribing Cooking users are less interested in other NYT products -- Cooking-specific value matters most
- Multi-day visitation is the best predictor that a regi will convert
- Total non-sub WAUs declined 22% from H1 2022 to H1 2024, but starts held constant due to strong conversion

---

## Known Sources

| Type | Location | Notes |
|------|----------|-------|
| User research | Google Drive > Cooking Research > Search | Search-specific user research |
| Dashboards | Looker (Cooking Search dashboard) | Search metrics |
| Research hub | [NYT Cooking DIG Research Hub](https://sites.google.com/nytimes.com/cooking-dig) | Historical research decks |
| Data questions | Slack: `#ask-a-data-chef` | DIG team for Cooking |
| Research updates | Slack: `#cooking-user-research` | Session invites and updates |
| Weekly insights | Slack: `#aig-weekly-insights` | Weekly research from AIG |

---

## Suggested Structure

| Folder | What goes here |
|--------|---------------|
| `metrics/` | Metric definitions, KPI specs |
| `queries/` | SQL queries, data pulls |
| `dashboards/` | Dashboard configs, screenshots, links |
| `experiments/` | Experiment designs, results, analyses |

---

## Project Context

- Full project context: `../product/project.md`
- Success metrics and measurement plan: see Measurement section in `../product/project.md`
- Decision log: `../product/decisions.md`
