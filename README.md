# Positioning Diagnostic

Analyze any homepage's positioning using frameworks from April Dunford, Fletch PMM, Geoffrey Moore, and Al Ries & Jack Trout. Get a score, find what's broken, and know what to fix first.

This is a **diagnostic tool** — it tells you what's wrong with your positioning and why. It does not rewrite your copy or make decisions for you.

## Install

### Option 1: Via And/or Labs Marketplace (Recommended)

```bash
/plugin marketplace add eclecticv/positioning-diagnostic
/plugin install positioning-diagnostic
```

This adds the And/or Labs marketplace to Claude Code and installs the positioning-diagnostic plugin. You'll get automatic updates when new versions are released.

### Option 2: Direct Git Clone

```bash
git clone https://github.com/eclecticv/positioning-diagnostic.git ~/.claude/skills/positioning-diagnostic
```

That's it. The skill is available immediately in your next Claude Code session.

### Option 3: Manual Install

Download the ZIP from this repo and copy the `.md` files into `~/.claude/skills/positioning-diagnostic/`.

## Commands

| Command | What It Does |
|---------|-------------|
| `/diagnose <url>` | Quick 5-second test + MECLABS score (out of 20) |
| `/audit <url>` | Full 100-point positioning audit |
| `/alignment` | Generate survey to test if your team agrees on positioning |
| `/antipatterns <url>` | Scan for specific positioning mistakes |
| `/compare <url> <url>` | Side-by-side competitive comparison |
| `/export <url>` | Generate a shareable markdown report |

## Quick Start

```
/diagnose https://yourcompany.com
```

You'll get:
- **5-second test** — Can visitors tell what you do, who it's for, and why to choose you?
- **MECLABS score** — Appeal, Exclusivity, Clarity, Credibility (each out of 5)
- **Top 3 red flags** — Specific findings with evidence from your homepage
- **Recommended fix** — The single highest-priority improvement

## Frameworks

- **April Dunford** — "Obviously Awesome" 5-component canvas (competitive alternatives, unique attributes, value, target customers, market category)
- **Fletch PMM** — 4 positioning questions every homepage must answer (what is it, who's it for, what does it replace, why is it better)
- **Geoffrey Moore** — "Crossing the Chasm" positioning statement template with slot-filling test
- **Al Ries & Jack Trout** — Competitive framing principles from "Positioning: The Battle for Your Mind"

## Scoring (100-point scale)

| Dimension | Points | What It Measures |
|-----------|--------|-----------------|
| Clarity | 25 | Can someone understand what you do in 5 seconds? |
| Differentiation | 25 | Is your "why better" specific and provable? |
| Value Proposition | 25 | Appeal, exclusivity, clarity, credibility (MECLABS) |
| Execution | 25 | Above-the-fold completeness, CTAs, social proof |

**80-100:** Strong — minor optimization needed
**60-79:** Adequate — significant improvement opportunities
**40-59:** Weak — requires strategic rework
**Below 40:** Critical — full repositioning required

## Example Workflow

```
/diagnose https://mycompany.com                            # Quick check
/audit https://mycompany.com                               # Deep analysis
/alignment                                                 # Team agreement test
/antipatterns https://mycompany.com                        # Mistake scan
/compare https://mycompany.com https://competitor.com      # Competitive view
/export https://mycompany.com                              # Stakeholder report
```

## And/or Labs Marketplace

This repository serves as both a Claude Code skill and the And/or Labs marketplace. Future And/or Labs tools for B2B SaaS marketing and growth will be available here.

To add the marketplace:
```bash
/plugin marketplace add eclecticv/positioning-diagnostic
```

Then browse and install plugins:
```bash
/plugin list
/plugin install positioning-diagnostic
```

## Compatibility

This skill follows the open [Agent Skills standard](https://github.com/anthropics/skills) (SKILL.md). It works with:
- **Claude Code** (primary)
- **Codex CLI** and other tools that support SKILL.md

## License

MIT
