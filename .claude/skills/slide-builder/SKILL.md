---
name: slide-builder
description: >
  Build a PPTX presentation using NYT-inspired styling (Georgia headings,
  clean layout, NYT blue accents) via pptxgenjs. Takes your content —
  an outline, bullet points, narrative, or raw material — and produces
  a polished .pptx saved to the deliverables/ folder.
  Use when someone says "build a deck", "make slides", "create a presentation",
  or "I need a PowerPoint".
---

# Slide Builder Skill

Generates a styled PPTX from whatever content you have.

## What I Need
- Topic, audience, and purpose of the presentation
- Your content: outline, bullets, narrative, or raw text (I'll structure it)

## What I'll Produce
- `deliverables/{presentation-name}.pptx`

## How It Works
1. Ask about topic, audience, and purpose
2. You provide the content
3. I propose a slide outline — you confirm or adjust
4. I generate the PPTX using pptxgenjs with NYT styles
5. File saved to your deliverables/ folder

## NYT Styling Applied
- Georgia for headings
- Clean single-column or two-column layouts
- NYT blue (`#326891`) as accent color
- No decorative clipart or stock photo placeholders
- Section dividers with rule lines

## Full Workflow
See `references/workflow.md` in this skill directory for styles and layout definitions.
