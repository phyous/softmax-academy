# ML/LLM Concept Explainer

## Purpose
Generate visual-first, progressive HTML explainers for ML and LLM concepts. Output is a single self-contained HTML file per chapter/topic-set that can be opened in any browser.

## When to use
Use this skill when asked to explain an ML/LLM concept, create a study resource, or generate an explainer for a topic from reference materials.

## Output format
One `.html` file per chapter saved to `docs/explainers/`. The file is a single scrollable document containing all topics.

### Document structure
1. **Title & intro** — Chapter name, one-line description, topic count
2. **Chapter intro** — 3-4 sentences framing why this chapter matters and what the reader will understand by the end
3. **Table of Contents** — Sticky sidebar with anchor links. Group labels with short transition sentences between groups.
4. **Progress bar** — Thin gradient bar fixed at top, fills as user scrolls
5. **Topic sections** — Each topic is a section (see format below)

### Topic ordering
Reorder topics to build understanding naturally:
- Start with foundational "what is X" concepts
- Layer in "how it works" mechanics
- Then "why it matters" practical implications
- End with system design / production concerns

Group related topics with brief transition sentences between groups.

### Topic section format

1. **Quick Take** — 2-3 sentences max. Plain language. Callout box with a small "Copy" button (top right, appears on hover) so it's quotable/shareable.

2. **Mental Model** — One-line analogy or metaphor that makes the concept stick. Uses a lightbulb icon. Styled as a subtle purple-tinted box. E.g., "Think of BPE like ZIP compression — for vocabulary."

3. **Interactive Visual** — HTML/CSS/JS visualization. Canvas, SVG, or DOM. Must respond to user input. This is the centerpiece.

4. **Deep Dive** — Thorough explanation. Structure for scannability:
   - Use **h3** section headers to break into logical sub-topics (e.g., "The Algorithm", "Why It Matters", "Practical Implications")
   - Use **h4** for sub-points within sections
   - Keep paragraphs to 2-3 sentences — never a wall of text
   - Use bullet points for lists, tables for comparisons
   - Use `.key-box` callouts for critical insights
   - Use `<code>` inline for technical terms
   - Include **cross-references** to other topics using `<a href="#topic-N" class="xref">Topic N: Title</a>` links
   - Be thorough but scannable — a reader should be able to skim headers and bold terms and get the gist

5. **Key Takeaway** — Single bold sentence after the deep dive, before code. Green-tinted box. The "one thing to remember" closer. Different from Quick Take (opener) — this is the conclusion after the reader has gone deep.

6. **Code** (if applicable) — `<details class="code-block">` collapsed by default. Summary: "Python Example".
   - Syntax highlighting required: `.kw` (purple), `.fn` (blue), `.str` (green), `.num` (pink), `.com` (gray italic)
   - Heavily commented: every non-trivial line explains what AND why

7. **Follow-up Questions** — `<details class="followup">` collapsed by default. 3-5 questions with detailed answers.
   - Question text in purple/indigo (`#a5b4fc`), NOT prefixed with "Q:"
   - Answer in muted gray (`#7f8ea3`), 0.8rem, generous line-height (1.6)
   - Keep answers to 2-4 SHORT sentences — concise, not walls of text
   - Use `<strong>` for key terms in answers (slightly brighter gray `#94a3b8`)
   - Separate items with `<div class="fq-divider"></div>` (thin line), NOT card-style boxes
   - No background color on individual items — keep it clean and airy
   - Bold key terms within answers to aid scanning

### Design system
- Dark theme: bg `#0f172a`, cards `#1e293b`, text `#e2e8f0`
- Accents: `#38bdf8` (blue), `#818cf8` (purple), `#f472b6` (pink), `#4ade80` (green)
- System font stack, body ~0.9rem
- Max-width 860px content area, 240px TOC sidebar
- No external dependencies — all inline

**Interactive visuals (CRITICAL):**
- ALL elements must use dark theme — NEVER white/light backgrounds
- Inputs: bg `#0f172a`, border `#334155`, text `#e2e8f0`
- Buttons: bg transparent, border `#475569`, active: `rgba(56,189,248,0.15)`
- Token chips: semi-transparent accent `rgba(...)` backgrounds
- Charts/canvas: dark bg, accent-colored data

**New structural elements:**
- `.mental-model` — purple-tinted analogy box with lightbulb icon
- `.key-takeaway` — green-tinted conclusion box with arrow icon
- `.qt-copy` — copy button on Quick Take (appears on hover)
- `.xref` — cross-reference links between topics (blue, dotted underline)
- `.progress-bar` — fixed top gradient bar
- `.group-intro` — italic transition text under group dividers

### Naming convention
`<source>-<chapter>-<short-description>.html`

Where `<source>` is a short name for the source material:
- Language Model Interview Handbook → `lm-handbook`
- Build a Large Language Model → `build-llm`

Examples:
- `lm-handbook-ch2-tokenization-and-context.html`
- `build-llm-ch5-pretraining.html`

### File location
`docs/explainers/<source>-<chapter>-<short-description>.html`
