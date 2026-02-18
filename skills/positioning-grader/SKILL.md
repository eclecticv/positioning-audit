# Positioning Grader

Score any B2B SaaS homepage against 42 positioning checks drawn from five proven frameworks: April Dunford's *Obviously Awesome*, Fletch PMM's homepage teardown methodology, Geoffrey Moore's *Crossing the Chasm*, the MECLABS conversion heuristic, and Ries & Trout's *Positioning: The Battle for Your Mind*.

Every check includes the full source citation. No opinions, no best-practice hand-waving — just the frameworks and a PASS/FAIL verdict.

## Installation

```bash
# Load the plugin from its directory
claude --plugin-dir /path/to/positioning-diagnostic
```

Or add to your Claude Code settings for persistent loading.

## Commands

### `/analyze <url>`

Analyzes a B2B SaaS homepage against all 42 checks and exports a comprehensive markdown report.

/positioning-grader:analyze https://example.com

**Output:** A standalone `.md` file (`example-positioning-analysis.md`) covering every check with:
- What the check is and why it matters (from frameworks)
- Full source citation (author, book/methodology, year)
- PASS/FAIL/N/A compliance verdict
- Specific observation from the site
- Concrete fix recommendation (if failing)

### `/report <url>`

Runs the same analysis and generates a polished PDF summary report.

/positioning-grader:report https://example.com

**Output:** A designed A4 PDF saved to your current directory.

## What It Checks (42 Checks)

| # | Category | Checks | Framework | Examples |
|---|----------|--------|-----------|----------|
| 1 | Dunford Canvas | DC-1 to DC-5 | Dunford | Competitive alternatives, unique attributes, value mapping, target customer, market category |
| 2 | Fletch Questions | FQ-1 to FQ-4 | Fletch PMM | What is it?, Who is it for?, What does it replace?, Why is it better? |
| 3 | Moore Statement | MS-1 to MS-6 | Moore | Target customer, need, category, benefit, alternative, differentiator |
| 4 | MECLABS Heuristic | MH-1 to MH-4 | MECLABS | Appeal, exclusivity, clarity, credibility |
| 5 | Competitive Framing | CF-1 to CF-5 | Ries & Trout | Before/after contrast, category ownership, word ownership, repositioning, ladder position |
| 6 | Anti-Patterns | AP-1 to AP-18 | Multiple | Default positioning, me-too, wishful thinking, committee-speak, investor language, buzzwords, feature soup, and 12 more |

## Requirements

- Claude Code CLI
- Browser MCP (for screenshots and PDF generation)
- WebFetch capability (for page content extraction)

## File Structure

```
positioning-diagnostic/
├── .claude-plugin/
│   └── marketplace.json
├── commands/
│   ├── analyze.md
│   └── report.md
├── skills/
│   └── positioning-grader/
│       ├── SKILL.md
│       └── reference/
│           ├── dunford-canvas.md
│           ├── fletch-questions.md
│           ├── moore-statement.md
│           ├── meclabs-heuristic.md
│           ├── competitive-framing.md
│           └── anti-patterns.md
├── assets/
│   └── report-template.html
└── README.md
```
