# ML/LLM Concept Explainer

## Purpose
Generate visual-first, progressive HTML explainers for ML and LLM concepts. Output is a single self-contained HTML file per chapter/topic-set that can be opened in any browser.

## When to use
Use this skill when asked to explain an ML/LLM concept, create a study resource, or generate an explainer for a topic from reference materials.

## Output format
One `.html` file per chapter saved to `docs/explainers/`. The file is a single scrollable document containing all topics.

### Document structure
1. **Title & intro** — Chapter name, one-line description, topic count
2. **Table of Contents** — Sticky/fixed sidebar or top nav with anchor links to each topic. Show topic numbers and short titles. Highlight active section on scroll.
3. **Topic sections** — Each topic is a section in the document (see Topic format below)

### Topic ordering
Don't just follow the source numbering blindly. Reorder topics to build understanding naturally:
- Start with foundational "what is X" concepts
- Layer in "how it works" mechanics
- Then "why it matters" practical implications
- End with system design / production concerns

Group related topics and add brief transition sentences between groups.

### Topic section format
Each topic section is compact and glanceable:

1. **Quick Take** — 2-3 sentences max. Plain language. Displayed prominently but not oversized — think callout box, not hero banner.

2. **Interactive Visual** — HTML/CSS/JS visualization. Canvas, SVG, or DOM-based. Must respond to user input (hover, click, drag, sliders). This is the centerpiece of each topic.

3. **Deep Dive** — This is where real explanation happens. Use whatever format best serves the topic:
   - Bullet points for lists of properties/characteristics
   - Tables for comparisons and tradeoffs
   - Inline mini-charts/diagrams for relationships
   - Short paragraphs only when narrative flow is needed
   - Can be longer than the Quick Take — aim for thoroughness while staying scannable
   - Use bold for key terms, keep paragraphs to 2-3 sentences max when using prose

4. **Code** (if applicable) — Python snippet in a `<details>` element, **collapsed by default**. Summary label: "Python Example". Syntax-highlighted `<pre><code>` block inside.

5. **Follow-up Questions** — 3-5 natural follow-up questions that stem from the topic. Displayed as a `<details>` element, **collapsed by default**. Summary label: "Follow-up Questions". Each question is just the question text (no answers), styled as a clickable-looking list.

### Design system
- Dark theme: bg `#0f172a`, cards/sections `#1e293b`, text `#e2e8f0`
- Accents: `#38bdf8` (blue), `#818cf8` (purple), `#f472b6` (pink)
- System font stack, body text ~0.9rem for density
- Max-width 860px centered, mobile-friendly
- No external dependencies — all CSS and JS inline
- Section headers: compact, with colored left-border accent bars (3px)
- Quick Take: styled as a subtle callout box (slightly lighter bg, left accent)
- Spacing: tighter than typical — optimize for glanceability over airiness
- Smooth scroll between TOC links
- IntersectionObserver to highlight active TOC item
- `<details>` elements styled to match theme (custom arrow, padding)

### Naming convention
`ch{NN}-kebab-case-title.html` (e.g., `ch02-tokens-tokenization-context-windows.html`)

### File location
`docs/explainers/ch{NN}-kebab-case-title.html`
