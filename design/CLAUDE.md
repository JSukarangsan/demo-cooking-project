# Cooking Search Personalization -- Design

Design artifacts for **Cooking Search Personalization**.

---

## Design System

### Pantry (Cooking-specific)

- Cooking's own design system covering typography, grid, styles, and components.
- Used across all platforms: web (Storybook), iOS, Android.
- Principles: warmth first, food is visual, progressive disclosure, touch-first.
- Slack: `#pantry`
- In 2025, Pantry transitioned from a dedicated initiative to a shared responsibility -- system work is addressed in the context of features.

### TPL (Times Product Language)

- NYT-wide shared design system providing foundational tokens and components.
- Cooking uses TPL for shared NYT components (e.g., auth flows, paywall UX).

### Design Tools


| Tool          | Use                                                        |
| ------------- | ---------------------------------------------------------- |
| **Figma**     | Primary design tool                                        |
| **Storybook** | Web component documentation with Chromatic preview deploys |
| **Coda**      | Team hubs, design docs, sprint planning                    |
| **FigJam**    | Retros and collaborative exercises                         |


---

## Brand & Typography

Pantry's type system uses 4 NYT font families:


| Font                      | Role                                                             |
| ------------------------- | ---------------------------------------------------------------- |
| **Cheltenham** (serif)    | Editorial voice -- headlines, recipe titles. The "Cooking" feel. |
| **Franklin** (sans-serif) | Utilitarian -- UI labels, body text, functional elements         |
| **Karnak**                | Alternative editorial voice (used cautiously)                    |
| **Imperial**              | Alternative to Cheltenham for readability                        |


**Brand principles:**

- Food photography is the hero -- UI should recede
- "Easy" is a core brand concept but must be expressed through familiar, human terms
- Warmth and approachability over clinical precision
- Editorial sensibility -- thoughtful, specific, occasionally delightful
- Distinct from generic "foodie" or creator-driven aesthetic

---

## Design Process

- VQA/DQA (Visual/Design Quality Assurance) is part of the development process -- design reviews happen before launch
- Design DRIs are assigned per bet (not per track)
- Designers work cross-track when bets span multiple platforms

---

## Design Contacts


| Person            | Title                              | Area                                            |
| ----------------- | ---------------------------------- | ----------------------------------------------- |
| **Aura Weiner**   | Executive Director, Product Design | Design leadership for Cooking                   |
| **Michelle Chiu** | Lead Product Designer              | ADAPT / AI features -- assigned to this project |


---

## Prior Research

### Search & Discovery

- Search is the primary way users discover and return to recipes
- Users try longer queries -- signaling readiness for smarter search
- User feedback: geographic/seasonal mismatch in results
- New search filters launched Dec 2025 based on "Easy research" -- users think about ease through familiar concepts, not abstract difficulty levels

### Recipe Detail Page (RDP) Behavior

- When users land on an RDP, they answer two questions: "Is this recipe right for me?" and "Have I made this before?"
- Cooked status, ratings, and private notes are most useful at the moment of decision (above the fold)

---

## Known Sources


| Type                | Location                                                                                             | Notes                                    |
| ------------------- | ---------------------------------------------------------------------------------------------------- | ---------------------------------------- |
| Design system       | [Pantry Design System (Coda)](https://coda.io/d/_dRwaIeKscIB)                                        | Documentation, type system, components   |
| Type system         | [Pantry Type System](https://coda.io/d/_dRwaIeKscIB/_su1HOiP1)                                       | Font families, type scale                |
| Brand guide         | [NYT Brand Style Guides](https://atthetimes.nyt.net/resource/the-new-york-times-brand-style-guides/) | Wordmark, typography, corporate identity |
| Design explorations | Cooking Figma workspace                                                                              | This project's design work               |
| Slack               | `#pantry`, `#cooking-user-research`                                                                  | Design system + research                 |


---

## Suggested Structure


| Folder      | What goes here                           |
| ----------- | ---------------------------------------- |
| `docs/`     | Design rationale, interaction specs      |
| `research/` | Usability findings, competitive analysis |
| `figma/`    | Figma file links, export notes           |


---

## Project Context

- Full project context: `../product/project.md`
- Scope and user goals: see Discovery and Scope sections in `../product/project.md`
- Constraints (design system, accessibility): `../product/constraints.md`

