# AGENTS.md

## Purpose
This repository/task produces an **Arabic-only (RTL)** brand kit / mini-site style PDF by ingesting a full source-of-truth text file and merging it into an existing visual page layout. The agent must include **all** source text without summarization and may add **detailed recommendations** as extra pages.

## Source-of-Truth
- `/mnt/data/serve.txt` is the single source-of-truth for required content.
- The final output MUST contain every paragraph, bullet, number, KPI, and any structured data from `serve.txt` in full.

## Visual References
Use these page images as layout references and to keep continuity of style and structure:
- `/mnt/data/serve_brand_kit_pages/page-1.png`
- `/mnt/data/serve_brand_kit_pages/page-2.png`
- `/mnt/data/serve_brand_kit_pages/page-3.png`
- `/mnt/data/serve_brand_kit_pages/page-4.png`
- `/mnt/data/serve_brand_kit_pages/page-5.png`
- `/mnt/data/serve_brand_kit_pages/page-6.png`

Optional structure reference:
- `/mnt/data/actionable_blueprint.html`

## Brand Constraints
### Colors (strict)
Background MUST be white:
- `#FFFFFF`

All other elements MUST use ONLY this palette:
- Primary Navy: `#002855`
- Accent Teal:  `#2BD3C2`
- Deep Navy:    `#010E48`
- Slate:        `#465C71`
- Neutral Gray: `#A9ADB6`
- White:        `#FFFFFF`

No additional colors are allowed (including shadows, overlays, gradients, or icons).

### Language & Direction (strict)
- Final visible content MUST be **Arabic only** (no English words).
- Right-to-left (RTL) everywhere: headings, body, tables, captions.
- Use an Arabic-capable font with reasonable fallbacks.

## Deliverables (exact paths)
1) Updated PDF:
- `/mnt/data/serve_brand_kit_updated.pdf`

2) Page images (PNG), one per page:
- `/mnt/data/serve_brand_kit_updated_pages/page-1.png`, `page-2.png`, ...

3) Editable source file (choose ONE):
- `/mnt/data/serve_brand_kit_updated_source.html` (preferred)
OR
- `/mnt/data/serve_brand_kit_updated_source.docx`

## Non-Negotiable Rules
1) **No summarization, no omission, no truncation** of `serve.txt`.
2) Rewording is allowed only when necessary for layout, without changing meaning and without losing any detail.
3) If content doesn’t fit, add new pages—never shrink content to unreadable sizes.
4) Any structured info must become proper tables (not plain text blocks).

## Expansion Requirement (Added Value)
After placing all required content, the agent MUST add “Recommendations” pages in Arabic (RTL), clearly labeled (e.g., "مقترحات إضافية", "توصيات", "إرشادات تطبيقية"), including:
- Brand story / positioning
- Voice & tone + writing examples
- Logo usage rules (clear space, minimum size, do/don’t)
- Color usage guidance + contrast/accessibility notes
- Typography hierarchy (Arabic-focused)
- UI components/patterns using the palette
- Social templates guidance (safe areas, grid, post types)
- A one-page Arabic “Quick Start” checklist

These additions must not replace or remove any `serve.txt` content.

## Recommended Implementation Approach
Preferred:
- Generate print-ready RTL HTML + CSS page templates
- Export to PDF via Playwright (chromium print) for consistent pagination
- Render PNG per page from the final PDF (or via Playwright screenshots)

Alternative:
- Direct PDF generation (e.g., reportlab) if HTML export is not feasible.

## QA Checklist (must pass before final export)
- [ ] Every line/item from `serve.txt` appears in the output (no missing sections).
- [ ] No ellipses or “etc.” placeholders used.
- [ ] Background is pure white on all pages.
- [ ] Only allowed palette colors appear.
- [ ] All visible text is Arabic only and RTL.
- [ ] Tables are real tables; numbers preserved exactly.
- [ ] Added recommendations are clearly labeled and separated from source-of-truth.

## Output Review Notes
If a conflict occurs between “design elegance” and “completeness”:
- Completeness wins.
- Add pages, do not omit content.
