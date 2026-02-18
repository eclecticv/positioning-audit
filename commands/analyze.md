# Command: analyze

Analyze a B2B SaaS homepage against 42 positioning checks drawn from Dunford, Fletch PMM, Moore, MECLABS, Ries & Trout, and common anti-pattern research. Export a comprehensive markdown report covering every single check.

## Usage
/positioning-grader:analyze <url>

## What It Does

1. **Crawl the homepage** via WebFetch to extract text content
2. **Screenshot the homepage** via the browser MCP:
   - Navigate to the URL, take a full-page screenshot
3. **Read all 6 reference files** to get the full checklist:
   - `skills/positioning-grader/reference/dunford-canvas.md` (DC-1 to DC-5)
   - `skills/positioning-grader/reference/fletch-questions.md` (FQ-1 to FQ-4)
   - `skills/positioning-grader/reference/moore-statement.md` (MS-1 to MS-6)
   - `skills/positioning-grader/reference/meclabs-heuristic.md` (MH-1 to MH-4)
   - `skills/positioning-grader/reference/competitive-framing.md` (CF-1 to CF-5)
   - `skills/positioning-grader/reference/anti-patterns.md` (AP-1 to AP-18)
4. **Score every single check** as PASS, FAIL, or N/A based on what you observed
5. **Write the full analysis** to a markdown file in the current directory

## Scoring Rules

- Score each applicable item as PASS or FAIL based on the criteria in the reference files
- Mark items as N/A ONLY when they genuinely don't apply (e.g., "Competitive Repositioning" when the product is first in a genuinely new category, "Wrong Champion" when product is self-serve only)
- N/A items are excluded from the pass rate — they don't count against the score
- Be honest and specific — cite what you actually observed on the site
- When uncertain, lean toward FAIL with a note about what you couldn't verify
- For items marked N/A, still include them in the output but note why they don't apply
- For anti-pattern checks (AP-1 to AP-18): PASS means the anti-pattern is NOT detected (good). FAIL means the anti-pattern IS detected (bad positioning).

## Grading Scale

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

## Output

Write a markdown file to the current working directory named `[company-name-lowercase]-positioning-analysis.md`.

The file must follow this EXACT structure:

# Positioning Analysis: [Company Name]

**URL:** [url]
**Date:** [date]
**Overall Score:** [total pass]/[total applicable] ([overall grade])

---

## Summary

| Section | Score | Grade |
|---------|-------|-------|
| Dunford Canvas | X/Y | [grade] |
| Fletch Questions | X/Y | [grade] |
| Moore Statement | X/Y | [grade] |
| MECLABS Heuristic | X/Y | [grade] |
| Competitive Framing | X/Y | [grade] |
| Anti-Patterns | X/Y | [grade] |

---

## 1. Dunford Canvas ([X/Y] — [Grade])

### DC-1: Competitive Alternatives Acknowledged

**What it is:** [Copy the "What it is" text from the reference file — word for word]

**Why it matters:** [Copy the "Why it matters" text from the reference file — word for word]

**Source:** [Copy the full "Source" citation from the reference file — word for word]

**Compliance:** PASS | FAIL | N/A

**Observation:** [What you actually observed on the site — be specific. Quote the actual headline, describe what you saw, cite evidence.]

**How to fix:** [Only if FAIL. Specific, actionable recommendation based on what was observed. Reference the framework. Example: "Name the competitive alternative explicitly — e.g., 'Replace your spreadsheet-based tracking' — so visitors understand the comparison frame (Dunford Step 1)."]

---

[...repeat for every check in the section...]

## 2. Fletch Questions ([X/Y] — [Grade])

[...every FQ check...]

## 3. Moore Statement ([X/Y] — [Grade])

[...every MS check...]

## 4. MECLABS Heuristic ([X/Y] — [Grade])

[...every MH check...]

## 5. Competitive Framing ([X/Y] — [Grade])

[...every CF check...]

## 6. Anti-Patterns ([X/Y] — [Grade])

[...every AP check...]

## Critical Rules for the Output

1. **Every single check gets its own section** — no exceptions, no skipping, no grouping
2. **"What it is" and "Why it matters" are copied word-for-word** from the reference files — this is the educational value of the report
3. **"Source" is the full citation** from the reference files — authors, book/article title, year
4. **"Observation" is specific** — never say "vague headline." Say what the headline actually says. Never say "no social proof." Say what IS on the page and what's missing.
5. **"How to fix" is actionable** — give a concrete alternative. Don't say "improve your headline." Say exactly what the headline should say instead.
6. **N/A checks are still listed** — show the check, mark N/A, and explain why (e.g., "N/A — product is first in a genuinely new category with no established alternatives")
7. **Section grades count only applicable items** — N/A items excluded from denominator
8. **The horizontal rule `---` separates every check** for clean readability

## After Writing the File

After writing the `.md` file, output a brief terminal summary:

ANALYSIS COMPLETE: [Company Name]
File: [filename].md ([total checks] checks evaluated)

  Dunford Canvas        [grade]  (X/Y)
  Fletch Questions      [grade]  (X/Y)
  Moore Statement       [grade]  (X/Y)
  MECLABS Heuristic     [grade]  (X/Y)
  Competitive Framing   [grade]  (X/Y)
  Anti-Patterns         [grade]  (X/Y)

  OVERALL               [grade]  (X/Y passing)

Open [filename].md for the full analysis.

## Notes

- Only the homepage is analyzed — positioning is a homepage concern. Do not look for or crawl pricing pages.
- If the browser MCP is unavailable, proceed with text-only analysis and note that visual checks may be less accurate
- The `.md` file is the primary output — it should be a complete, standalone document that can be shared with a team
- The report should read as an educational document — someone who hasn't read the original frameworks should learn from reading this analysis
