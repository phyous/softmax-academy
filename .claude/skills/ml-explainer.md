# ML/LLM Concept Explainer

## Purpose
Generate visual-first, progressive HTML explainers for ML and LLM concepts. Each explainer is a self-contained HTML file that can be opened in any browser.

## When to use
Use this skill when asked to explain an ML/LLM concept, create a study resource, or generate an explainer for a topic from reference materials.

## Output format
Each explainer is a single `.html` file saved to `docs/explainers/<chapter-folder>/`. The file follows a strict progressive structure:

### Structure (in order)
1. **Quick Take** — 2-3 sentence plain-language explanation. No jargon. Get the idea across fast.
2. **Interactive Visual** — An HTML/CSS/JS visualization that makes the concept tangible. Use canvas, SVG, or DOM-based animations. Make it interactive where possible (hover, click, drag, sliders). This is the centerpiece.
3. **Deep Dive** — 1-3 short paragraphs. Punchy, progressive. Build from intuition to technical detail. Explain *why* this matters in practice.
4. **Code** (if applicable) — A Python snippet that demonstrates the concept. Keep it runnable and minimal. Use syntax-highlighted `<pre><code>` blocks.

### Design principles
- Dark theme (bg: `#0f172a`, text: `#e2e8f0`, accents: `#38bdf8` / `#818cf8` / `#f472b6`)
- Clean typography: system font stack, generous spacing
- Mobile-friendly, max-width 800px centered
- No external dependencies — everything inline (CSS, JS)
- Interactive visuals should respond to user input (hover, click, sliders, animation toggles)
- Section headers use subtle left-border accent bars
- Smooth fade-in animations on scroll

### Naming convention
`QXX-kebab-case-topic.html` (e.g., `Q01-what-is-a-token.html`)

### Chapter index
Also generate/update an `index.html` in the chapter folder that links to all explainers with the chapter title and a card-based layout.
