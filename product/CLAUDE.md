# Cooking Search Personalization

**Mission:** Cooking | **PM:** Gaelle Sharma | **Created:** 2026-05-05

---

## Project Context

You are working on **Cooking Search Personalization** for the NYT Cooking mission.

**Problem:** Search results on NYT Cooking are the same for every user regardless of cooking history, dietary preferences, or skill level. Users default to browsing or the "For You" shelf instead of search.

**Goals:**
- Business: Increase search-driven recipe saves and reduce subscriber churn among months 3-12 subscribers
- User: Users feel like Cooking "knows them" -- results reflect what they actually cook
- Primary metric: Search-driven recipe save rate

**Team:** Gaelle Sharma (PM), Michelle Chiu (Design), Erik Jonsson (Eng Lead), Raquel Hamias (Data), Sora Kim (PgM)

**Target date:** Experiment live by end of Q2 2026 (June 30)

---

## Mission Context

NYT Cooking is a subscription product that helps people cook more, with less friction. It is one of The Times's standalone subscription products alongside Games, Wirecutter, and The Athletic.

**Core value prop:** The world's best recipes, organized to help you actually cook them.

**2026 Vision:** Become "Your Daily Cooking Companion." The north star for 2027 is becoming the destination for the world's best cooking talent.

**Business context:** Best recipe app with the best recipes, but facing real pressure: search and social headwinds, a fragmented market, planning apps gaining ground, and AI shifting consumer habits. Largest addressable audience among NYT sub-brands: 8.5M people willing to pay for Cooking with no existing NYT relationship.

**Competitive landscape:** ~1% of all ChatGPT conversations involve cooking queries. Differentiation: human-crafted tested content at scale, app-first multimedia destination, community and sharing, durable business model.

**Editorial relationship:** Cooking is editorially driven -- food editors and recipe developers have strong influence on product direction. Recipe quality (tested recipes) is a core brand differentiator that is never compromised for speed.

---

## Strategic Alignment

**Bet: Search & Personalization -- "More personal discovery"**

Make discovery more personal via "What's Cooking?" (Shortcuts on Home + refreshed search landing page), "Search My Way" (semantic search + first AI suggestion in results), personalized surfaces, and richer metadata (AI tag suggestions, expanded diet/nutrition tags).

**Key projects:** Shortcuts on app Home tab (Q1), Search Landing Page refresh (Q2), AI Suggestion in Search Results (Q2/Q3), Semantic Search, Personalized & dynamic Shortcuts algorithm (Q3/Q4), AI-powered tag suggestions.

**KPIs:** Search success (Result CTR, Cook Rate), engagement with personalized features (Shortcuts CTR), subscriber engagement.

Source: [Product Review: 2026 Cooking Roadmaps](https://docs.google.com/presentation/d/1wESGEraSjmY-vedL3uGq2JZr4t4scbWJWNf8Yb3_5e4)

---

## Success Framework

**Mission-level north star metrics:**
- Audience (non-sub WAUs): -3% YoY (ambitious given search declines)
- Starts (new subscriptions): +2% YoY
- Engagement: +1 percentage point (shift from weekly to daily habit)
- Regi pool growth: +20% YoY
- Ad revenue: +47% YoY

**Bet-level KPIs (Search & Personalization):** Search success (Result CTR, Cook Rate), engagement with personalized surfaces, subscriber engagement.

**Key metric definitions:**
- **Cook Rate:** Recipe is "cooked" if >5 min of total active time per day on that recipe
- **Search Success:** Composite of Result CTR (relevance) + Engagement Rate (quality) + Search Volume (usage)

---

## Key Stakeholders

**Mission leadership:**

| Person | Title |
|---|---|
| Camilla Velasquez | General Manager, Cooking |
| Michael Linares | VP, Product |
| Meg Adams | Engineering leadership |

**Product chain:** Lauren Rosenfield (Director, Product) > Gaelle Sharma (Technical Sr. PM, Search & Personalization)

**API track (this project's track):**
- Erik Jonsson -- EM, API (formerly Discovery)

**Editorial:** Lauren Savoie -- Editorial lead. Involve early on anything affecting content ranking or recipe visibility.

**Shared services:** AlgoRecs (personalization algorithms), Data Platforms (Statsig adoption), Legal (privacy, new data collection), Accessibility (launch reviews, AA compliance).

---

## Communication

**Planning cadence:** Annual strategic bets > Half (H1/H2) roadmap > Quarterly guidepost review > Biweekly sprints per track.

**Key Slack channels:**
- `#cooking-search-personalization-bet` -- bet-level updates
- `#cooking-api-team` -- API track standups
- `#cooking` -- team-wide announcements
- `#cooking-user-research` -- research updates and session invites
- `#ask-a-data-chef` -- data/analytics questions

**Team rituals:** Daily Standup (Slack bot), Product Alignment (weekly, cross-functional), Sprint Planning (biweekly), DDD -- Demos, Discussions, Decisions (biweekly).

---

## Product Files

| File | Purpose |
|------|---------|
| `project.md` | Full project manifest (read this for complete context) |
| `decisions.md` | Decision log (check before re-litigating past decisions) |
| `constraints.md` | Hard limits (check before proposing solutions) |
| `glossary.md` | Shared vocabulary |
| `todo.md` | Open questions and next steps |
| `briefs/` | Feature briefs and PRDs |
| `deliverables/` | Output artifacts (decks, exports) |

---

## How to Work with This Kit

Always read `project.md` before diving into any task -- it has the full context.

When I ask for help on a feature, I'll usually share:
- The feature name and basic description
- Any constraints or decisions already made
- Research or feedback I've collected

You can ask me for any of these if they're missing.
