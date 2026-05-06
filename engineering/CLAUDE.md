# Cooking Search Personalization -- Engineering

Engineering artifacts for **Cooking Search Personalization**.

---

## Tech Stack

### Frontend / Web
- **cooking-frontend** -- Next.js web application (SSR with `getServerSideProps`)
- **np-cooking** -- legacy Node.js backend/API (being decommissioned)
- **Storybook** -- component documentation with Chromatic preview deploys

### Mobile
- **iOS** -- SwiftUI (migrating to 100% declarative UI by end of 2026)
- **Android** -- Jetpack Compose (migrating to 100% declarative UI)
- Both platforms use Pantry (Cooking-specific) and TPL (shared NYT) design systems

### Backend / Data
- **Cooking Subgraph** -- new federated GraphQL architecture. Single biggest architectural bet for 2026.
- **Cooking-rose** -- internal search engine (Elasticsearch-based). Handles lexical and semantic search.
- **Scoop Platform / Entity Store** -- new publishing infrastructure.
- **REST APIs** -- legacy `cooking.nytimes.com/api/v1-v6/` being progressively migrated to GraphQL.

### Infrastructure
- **Fastly** -- edge cache / CDN. All requests hit Fastly first.
- **DVSP** -- Developer Velocity & Service Platform. Terraform-managed, Drone CI/CD.
- **GKE** -- Google Kubernetes Engine. Services run in GCP.
- **Datadog** -- monitoring and observability.
- **Statsig** -- experimentation platform (replacing ABRA). Client-side and server-side (Fastly Compute).
- **Sentry** -- error tracking.

---

## Active Initiatives

Relevant to the API track and this project:

1. **GraphQL Migration** -- Migrate Collections and Search to Cooking Subgraph by Thanksgiving 2026.
2. **Statsig for Cooking Search** -- Complete (CAPI-248). Feature gates and experiment values surfaced in HTTP response and GraphQL resolver.
3. **Semantic Search** -- MVP launched April 30, 2026. "No Result" searches down ~50%.
4. **cooking-llm-tagging** -- LLM-based recipe tagging service.

---

## Key Repos

| Repo | What |
|---|---|
| `nytimes/cooking-frontend` | Web frontend (Next.js) |
| `nytimes/np-cooking` | Legacy backend/API |
| `nytimes/fastly-cooking` | Fastly/VCL config |
| `nytimes/cooking-local` | Local dev environment |
| `nytimes/cooking-llm` | LLM tagging service |

---

## Constraints

- **GraphQL migration is in progress.** Some data comes from subgraph, some from legacy REST. Ask which source a feature needs.
- **Recipe data model changes are expensive.** New fields require API changes, client updates, and data migrations.
- **Experiment infrastructure required.** All metric-moving features must run through Statsig with holdback and ramp.
- **Platform parity is not automatic.** A feature on web may take additional quarters for iOS/Android. Scope explicitly.
- **Pantry design system required.** All UI must use Pantry (Cooking) and TPL (shared NYT). No custom one-offs.
- **Performance budget is real.** Crash-free session rate >99.7%. "Thanksgiving Ready" is the reliability bar.
- **Search index takes hours.** Cooking-rose ingests 80M+ articles. Index time is ~9 hours.

---

## Engineering Contacts

| Person | Role |
|---|---|
| Erik Jonsson | EM, API (formerly Discovery) -- this project's track |
| Meg Adams | Engineering leadership |

---

## Process

- **JIRA project:** CAPI (Cooking APIs)
- **Sprint cadence:** Biweekly
- **Code review:** PRs require 2 approvals before merge. Squash and merge required. Auto-requested reviewers via GitHub teams.
- **Checklist:** self-review, linting passes in Drone, tests pass, Storybook preview deployed.
- **Slack:** `#cooking-api-team`

---

## Suggested Structure

| Folder | What goes here |
|--------|---------------|
| `plans/` | Technical plans, architecture proposals |
| `rfcs/` | Request for comments, design docs |
| `bug-investigations/` | Root cause analyses, incident reviews |

---

## Project Context

- Full project context: `../product/project.md`
- Technical constraints: `../product/constraints.md`
- Decision log: `../product/decisions.md`
