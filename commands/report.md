# Command: report

Generate a polished PDF report from a positioning analysis.

## Usage
/positioning-grader:report <url>

## What It Does

1. **Run the full analysis** — same steps as `/analyze`: crawl homepage, screenshot, read reference files, score all 42 checks
2. **Read the HTML template** from `assets/report-template.html`
3. **Populate the template** by replacing all `{{PLACEHOLDER}}` tokens with actual data:
   - `{{COMPANY_NAME}}` — extracted from the homepage
   - `{{URL}}` — the analyzed URL
   - `{{DATE}}` — today's date
   - Grade cards: `{{DC_GRADE}}`, `{{FQ_GRADE}}`, `{{MS_GRADE}}`, `{{MH_GRADE}}`, `{{CF_GRADE}}`, `{{AP_GRADE}}`
   - Grade classes: `{{DC_GRADE_CLASS}}`, etc. — use `grade-a` for A+/A/A-, `grade-b` for B+/B/B-, `grade-c` for C+/C/C-, `grade-d` for D+/D/D-, `grade-f` for F
   - Pass counts: `{{DC_PASS}}`, `{{DC_TOTAL}}`, etc.
   - Progress bars: `{{DC_PROGRESS}}`, etc. — generate 12 `<span>` blocks, filled or empty proportional to pass rate
   - `{{WINS}}` — HTML for top win findings (2-4 items)
   - `{{FIXES}}` — HTML for top fix findings (3-6 items)
   - `{{FRAMEWORK_LIST}}` — comma-separated list of all frameworks cited in findings
4. **Write the populated HTML** to a temporary file in the current directory
5. **Open in browser MCP** — navigate to the local HTML file
6. **Generate PDF** using browser_run_code:
   ```javascript
   await page.pdf({ path: '[company-name]-positioning-report.pdf', format: 'A4', printBackground: true })
   ```
7. **Clean up** — delete the temporary HTML file
8. **Report success** — tell the user where the PDF was saved

## Template Placeholder Reference

### Header
- `{{COMPANY_NAME}}` — Company name (e.g., "Acme")
- `{{URL}}` — Full URL analyzed (e.g., "https://example.com")
- `{{DATE}}` — Report date (e.g., "February 18, 2026")

### Grade Cards (repeat for DC, FQ, MS, MH, CF, AP)
- `{{XX_GRADE}}` — Letter grade (e.g., "A-", "B+", "C")
- `{{XX_GRADE_CLASS}}` — CSS class: `grade-a`, `grade-b`, `grade-c`, `grade-d`, or `grade-f`
- `{{XX_PASS}}` — Number of passing items (e.g., "4")
- `{{XX_TOTAL}}` — Total applicable items (e.g., "5")
- `{{XX_PROGRESS}}` — 12 span elements like:
  ```html
  <span class="block block-filled"></span>
  <span class="block block-filled"></span>
  ...
  <span class="block block-empty"></span>
  ```

### Findings
- `{{WINS}}` — HTML blocks for top wins:
  ```html
  <div class="finding finding-pass">
    <span class="marker">&#10003;</span>
    <div class="content">
      <span class="code">DC-1</span>
      <span class="observation">Clear competitive frame — "Replace your spreadsheets"</span>
    </div>
  </div>
  ```

- `{{FIXES}}` — HTML blocks for top fixes:
  ```html
  <div class="finding finding-fail">
    <span class="marker">&#10007;</span>
    <div class="content">
      <span class="code">FQ-1</span>
      <span class="observation">Headline doesn't pass the 5-second test — "Unlock Your Potential"</span>
      <div class="recommendation">Name what the product does in the headline</div>
      <div class="citation">Fletch PMM homepage teardown methodology</div>
    </div>
  </div>
  ```

### Footer
- `{{FRAMEWORK_LIST}}` — All cited frameworks/sources, comma-separated (e.g., "Dunford 'Obviously Awesome', Fletch PMM, Moore 'Crossing the Chasm', MECLABS Institute, Ries & Trout 'Positioning'")

## Progress Bar Generation

For a category with X passing out of Y total:
1. Calculate `filled = Math.round((X / Y) * 12)`
2. Generate `filled` blocks with class `block-filled`
3. Generate `12 - filled` blocks with class `block-empty`

## Notes

- The PDF will be saved to the user's current working directory
- File name format: `[company-name-lowercase]-positioning-report.pdf` (e.g., `acme-positioning-report.pdf`)
- If browser MCP's `page.pdf()` is not available, save the populated HTML file instead and tell the user they can print it to PDF from their browser
- The report is a visual summary — for the full per-check analysis, use `/analyze` to get the comprehensive `.md` export
- Always include the brief terminal summary as well (same as /analyze), then mention the PDF location
- Only the homepage is analyzed — positioning is a homepage concern
