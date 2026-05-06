# Slide Builder — Workflow Reference

## Library
- **Package:** pptxgenjs `^3.12.0`
- **Install:** `npm install pptxgenjs`
- **Docs:** https://gitbrent.github.io/PptxGenJS/

## NYT Styles

### Fonts
| Role | Font |
|---|---|
| Title / Heading | Georgia |
| Body / Caption | Arial |

### Colors
| Name | Hex |
|---|---|
| Black | `#121212` |
| Dark gray | `#333333` |
| Medium gray | `#666666` |
| Light gray | `#EBEBEB` |
| White | `#FFFFFF` |
| NYT blue (accent) | `#326891` |
| NYT blue (secondary) | `#567B95` |

## Slide Layouts

### Title Slide
Opening slide with project/presentation title and subtitle.
- Title: Georgia 36pt bold, `#121212`, position `{x:0.8, y:2.0, w:8.4, h:1.5}`
- Subtitle: Arial 18pt, `#666666`, position `{x:0.8, y:3.6, w:8.4, h:0.8}`
- Accent rule: `#326891` line, 2pt, position `{x:0.8, y:3.4, w:3.0}`

### Section Divider
Clean break between major sections.
- Section title: Georgia 30pt bold, `#121212`, position `{x:0.8, y:2.5, w:8.4, h:1.2}`
- Accent bar: `#326891` filled shape, position `{x:0, y:0, w:0.3, h:7.5}`

### Content Slide
Standard slide with heading and bullet points.
- Heading: Georgia 24pt bold, `#121212`, position `{x:0.8, y:0.5, w:8.4, h:0.8}`
- Body: Arial 16pt, `#333333`, line spacing 24, position `{x:0.8, y:1.5, w:8.4, h:5.0}`

### Two Column
Side-by-side content for comparisons or related points.
- Heading: Georgia 24pt bold, `#121212`, position `{x:0.8, y:0.5, w:8.4, h:0.8}`
- Left column: Arial 14pt, `#333333`, position `{x:0.8, y:1.5, w:4.0, h:5.0}`
- Right column: Arial 14pt, `#333333`, position `{x:5.2, y:1.5, w:4.0, h:5.0}`

### Quote / Callout
Feature a key quote, insight, or stat.
- Quote: Georgia 24pt italic, `#326891`, position `{x:1.5, y:2.0, w:7.0, h:2.5}`
- Attribution: Arial 14pt, `#666666`, position `{x:1.5, y:4.5, w:7.0, h:0.5}`
- Accent rule: `#326891` line, 3pt vertical, position `{x:1.2, y:2.0, w:0, h:2.5}`

## Workflow

1. Ask what the presentation is about — topic, audience, and purpose
2. Ask for content — an outline, bullets, narrative, or raw material
3. Propose a slide outline (title, sections, content slides) and confirm with the user
4. Write a Node.js script using pptxgenjs that generates the deck with NYT styles above
5. Run the script to produce the PPTX file
6. Tell the user where the file is and offer to adjust any slides

## Output

Write `{presentation-name}.pptx` to `./product/deliverables/`, `./deliverables/`, or `./` — use the first path that exists as a directory.
