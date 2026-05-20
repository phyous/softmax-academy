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

3. **Deep Dive** — This is where real teaching happens. Be thorough — explain the concept well enough that someone unfamiliar could understand it. Use whatever format best serves the topic:
   - Bullet points for lists of properties/characteristics
   - Tables for comparisons and tradeoffs
   - Inline mini-charts/diagrams for relationships
   - Narrative paragraphs when building intuition or explaining a process
   - Use more words than the Quick Take — aim for real understanding, not just bullet-point skimming
   - Use bold for key terms, but don't sacrifice explanation depth for brevity
   - Include "why this matters" and "how this connects to other concepts" where relevant

4. **Code** (if applicable) — Python snippet in a `<details>` element, **collapsed by default**. Summary label: "Python Example".
   - **Syntax highlighting is required**: use `<span>` classes for keywords (`.kw`, purple), functions (`.fn`, blue), strings (`.str`, green), numbers (`.num`, pink), comments (`.com`, gray italic)
   - **Heavily commented**: every non-trivial line should have a comment explaining what it does and why. The code should teach, not just demonstrate.
   - Use `<pre><code>` blocks inside the details element

5. **Follow-up Questions** — 3-5 natural follow-up questions that stem from the topic. Displayed as a `<details>` element, **collapsed by default**. Summary label: "Follow-up Questions".
   - Each question is shown with its **full detailed answer** — not just the question text
   - Format: question as a bold heading, then 2-4 sentences answering it thoroughly
   - These are mini-explainers in their own right — someone should learn something new from each one

### Design system — CRITICAL
- Dark theme: bg `#0f172a`, cards/sections `#1e293b`, text `#e2e8f0`
- Accents: `#38bdf8` (blue), `#818cf8` (purple), `#f472b6` (pink)
- System font stack, body text ~0.9rem for density
- Max-width 860px centered, mobile-friendly
- No external dependencies — all CSS and JS inline

**Interactive visual styling (IMPORTANT — must blend with dark theme):**
- Input fields: bg `#0f172a` or `#1e293b`, border `#334155`, text `#e2e8f0`, placeholder `#64748b`
- Buttons: bg transparent or `rgba(56,189,248,0.1)`, border `#475569`, text `#94a3b8`, hover: border `#38bdf8`
- Active/selected buttons: bg `rgba(56,189,248,0.15)`, border `#38bdf8`, text `#38bdf8`
- Token chips / colored elements: use semi-transparent accent colors (`rgba(...)`) that blend with dark bg
- **NEVER use white or light gray backgrounds** for inputs, buttons, or containers inside visuals
- **NEVER use black text on white backgrounds** — everything must feel cohesive with the dark theme
- Charts and canvases: use dark backgrounds matching `#1e293b`, draw with accent colors
- Sliders: style with accent colors, dark track

Other design details:
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
