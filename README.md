# Positioning Grader

A framework-backed analysis tool that scores B2B SaaS homepages against 42 positioning checks drawn from Dunford, Fletch PMM, Moore, MECLABS, and Ries & Trout. Every check includes the full source citation — no opinions, no fluff.

Checks drawn from five proven positioning frameworks, supplemented with common anti-pattern research from consulting practice.

## Purpose

Analyze a B2B SaaS homepage against every check in the positioning playbook. For each check, the output includes what it is, why it matters (the framework rationale), the source citation, a compliance verdict (PASS/FAIL/N/A), the specific observation, and a concrete fix recommendation if failing. The full analysis is exported as a standalone `.md` file.

## How It Works

1. **Crawl** the homepage via WebFetch (text content extraction)
2. **Screenshot the homepage** via browser MCP (full-page capture)
3. **Score every check** — all 42 items, each as PASS, FAIL, or N/A
4. **Export** a comprehensive `.md` report covering every check with full context

Only the homepage is analyzed — positioning is a homepage concern.

## The 42-Check Playbook

### 1. Dunford Canvas (5 checks: DC-1 to DC-5)
Competitive alternatives, unique attributes, value mapping, target customer, market category.
→ See [reference/dunford-canvas.md](skills/positioning-grader/reference/dunford-canvas.md)

### 2. Fletch Questions (4 checks: FQ-1 to FQ-4)
What is it?, Who is it for?, What does it replace?, Why is it better?
→ See [reference/fletch-questions.md](skills/positioning-grader/reference/fletch-questions.md)

### 3. Moore Statement (6 checks: MS-1 to MS-6)
Target customer, need, category, benefit, alternative, differentiator — can every slot be filled?
→ See [reference/moore-statement.md](skills/positioning-grader/reference/moore-statement.md)

### 4. MECLABS Heuristic (4 checks: MH-1 to MH-4)
Appeal, exclusivity, clarity, credibility — the MECLABS conversion heuristic components.
→ See [reference/meclabs-heuristic.md](skills/positioning-grader/reference/meclabs-heuristic.md)

### 5. Competitive Framing (5 checks: CF-1 to CF-5)
Before/after contrast, category ownership, word ownership, repositioning, ladder position.
→ See [reference/competitive-framing.md](skills/positioning-grader/reference/competitive-framing.md)

### 6. Anti-Patterns (18 checks: AP-1 to AP-18)
Default positioning, me-too, wishful thinking, committee-speak, investor language, trend-riding, buzzwords, feature soup, and 10 more.
→ See [reference/anti-patterns.md](skills/positioning-grader/reference/anti-patterns.md)

## Scoring

Each section receives a letter grade (A+ through F) based on the percentage of applicable items that pass. Items marked N/A are excluded from the denominator.

| Grade | Pass Rate |
|-------|-----------|
| A+    | 100%      |
| A     | 90-99%    |
| A-    | 85-89%    |
| B+    | 80-84%    |
| B     | 75-79%    |
| B-    | 70-74%    |
| C+    | 65-69%    |
| C     | 60-64%    |
| C-    | 55-59%    |
| D+    | 50-54%    |
| D     | 45-49%    |
| D-    | 40-44%    |
| F     | Below 40% |

## Output Format

For each of the 42 checks, the `.md` report includes:
- **What it is** — description of the check (from the reference)
- **Why it matters** — the framework rationale (from the reference)
- **Source** — full citation with author, book/methodology, year
- **Compliance** — PASS, FAIL, or N/A
- **Observation** — what was specifically observed on the site
- **How to fix** — concrete, actionable recommendation (only if FAIL)

## Available Commands

1. **analyze** — Full analysis exported as `.md` file with every check evaluated
2. **report** — Generate a polished PDF summary report from the analysis

## Frameworks

All checks are drawn from:
- Dunford, A. *Obviously Awesome: How to Nail Product Positioning so Customers Get It, Buy It, Love It* (2019)
- Pierri, A. & Fralic, R. Fletch PMM — "The Homepage Teardown" methodology (2020–2024)
- Moore, G. A. *Crossing the Chasm: Marketing and Selling Disruptive Products to Mainstream Customers* (1991, 3rd ed. 2014)
- Flint McGlaughlin, M. *The Marketer as Philosopher* — MECLABS Institute (2020)
- Ries, A. & Trout, J. *Positioning: The Battle for Your Mind* (1981, 20th anniversary ed. 2001)
- Ries, A. & Trout, J. *The 22 Immutable Laws of Marketing* (1993)

## License

MIT
