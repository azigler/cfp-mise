# VibeX 2026 Paper: Mise en Place for Agentic Coding

> Academic paper submission for the 1st International Workshop on Vibe Coding and Vibe Researching (VibeX 2026), co-located with EASE 2026, Glasgow, June 9-12, 2026.

## DEADLINE: March 8, 2026 (AoE)

## Status

Research phase is complete (4 beads closed). **Pipeline starts at Phase 1.**

## Pipeline

This project runs as a continuous pipeline. Each phase feeds the next. The orchestrator creates beads, deploys subagents, merges results, and advances to the next phase without stopping. The end result is a complete paper PDF and a production notes file for the owner to review.

### Phase 1: Infrastructure
- Deploy data extraction agent into `~/hackathon-infactory/` (read-only) → saves to `data/`
- Set up ACM LaTeX template in `paper/` with section scaffolding
- Both can run in parallel. Phase 2 depends on data extraction completing.

### Phase 2: Writing
- Write Related Work section (draws from `.claude/research/literature-survey.md`)
- Write Methodology + Case Study sections (draws from published article + extracted data)
- Write Introduction, Context Fluency, Research Agenda, Conclusion
- Parallelizable where sections don't cross-reference each other.

### Phase 3: Assembly
- Merge all sections into `paper/main.tex`
- Compile reference list in `references.bib`
- Create Figure 1 (methodology diagram) and Table 1 (timeline/metrics)
- Verify page count against 5-page limit. Trim if needed.

### Phase 4: Review Package
- Build final PDF
- Write `REVIEW-NOTES.md` at project root with:
  - Decisions made and rationale
  - Areas where owner judgment is needed (tone, claims strength, author info)
  - Any concerns about page count, citation gaps, or framing
  - Instructions for EasyChair submission (author names, affiliations, keywords)
- Owner reviews, approves or requests changes, then submits.

## Submission Details

- **Type:** Positioning Paper (5 pages incl. references)
- **Template:** ACM Primary Article Template (`\documentclass[sigconf,review]{acmart}`)
- **Portal:** https://easychair.org/conferences/?conf=vibex2026
- **Review:** Single-blind
- **Published in:** ACM Digital Library

## Project Structure

```
~/cfp/mise/
├── CLAUDE.md              # This file — project context
├── paper/                 # LaTeX source and built PDF
│   ├── main.tex
│   ├── references.bib
│   └── figures/
├── data/                  # Extracted quantitative data from hackathon
│   ├── git-timeline.md
│   ├── beads-metrics.md
│   └── session-analysis.md
├── .claude/
│   ├── plans/
│   │   └── vibex-2026-submission.md   # Master plan with outline and timeline
│   ├── research/
│   │   ├── article-assessment.md      # Claims inventory, gaps, strengths
│   │   ├── vibex-cfp-analysis.md      # CFP analysis, submission strategy
│   │   └── literature-survey.md       # 30+ sources, gap analysis
│   └── ref/
│       └── published-article.md       # The published Substack article
└── .beads/                # Task tracking (prefix: mp)
```

## Agent Instructions

### Working Style: Split Repo

This paper workspace is SEPARATE from the hackathon project repo at `~/hackathon-infactory/`.

- **This folder (`~/cfp/mise/`):** Paper writing, LaTeX, research accumulation. All writing work happens here.
- **Hackathon folder (`~/hackathon-infactory/`):** READ-ONLY data source. Deploy researcher subagents there to extract git logs, beads records, session transcripts, and code metrics. **Do not modify anything in that repo.**
- Extracted data gets saved to `~/cfp/mise/data/`.

### Subagent Protocol

- Research/data extraction agents: deploy into `~/hackathon-infactory/` as READ-ONLY
- Writing agents: deploy into `~/cfp/mise/` with write access
- All agents use beads (prefix `mp`) for task tracking
- Include `Bead: <id>` in commit trailers

### Writing Standards

- **Voice:** Academic but accessible. First person plural ("we"). Not stilted.
- **Tone:** The published article (`.claude/ref/published-article.md`) captures the author's voice. The paper should formalize that voice for an academic audience without losing its clarity.
- **Citations:** ACM numeric style `[1]`. Use BibTeX.
- **Page budget:** ~3,800 words + references in 5 pages. Every word counts.

## Key References (Read These First)

1. **`.claude/plans/vibex-2026-submission.md`** — Master plan: paper outline, section-by-section structure with word counts, abstract draft, timeline, content adaptation notes
2. **`.claude/ref/published-article.md`** — The published Substack article being adapted
3. **`.claude/research/literature-survey.md`** — 30+ sources for Related Work section
4. **`.claude/research/article-assessment.md`** — Claims inventory and evidence gaps
5. **`.claude/research/vibex-cfp-analysis.md`** — CFP alignment and strategic positioning

## Paper Contributions (from the plan)

1. **Three-phase mise en place methodology** formalized with principles and artifacts
2. **Case study** with quantitative data from a competitive hackathon
3. **"Context fluency"** proposed as a new construct for AI-assisted development
4. **Research agenda** with 5 formal research questions

## Theoretical Grounding

- **Backward design** — Wiggins & McTighe (1998), Understanding by Design
- **Tacit knowledge** — Polanyi (1958, 1966), The Tacit Dimension
- **Context engineering** — Anthropic (2025), Gartner shift from prompt to context engineering
- **Practitioner convergence** — Huntley (Ralph Loop), Yegge (Beads/Gas Town), Horthy (RPI), Emanuel (beads_rust)

## Hackathon Data Source

The hackathon project at `~/hackathon-infactory/` contains:

- **Git history:** 9+ commits with timestamps (Jan 31, 2026)
- **Beads records:** `.beads/issues.jsonl` — 68 beads (42 closed, 21 open, 5 bugs)
- **Session logs:** `~/.claude/projects/-home-ubuntu-hackathon-infactory/*.jsonl` — 4 sessions totaling ~5,500 lines
- **Planning docs:** `.claude/plans/` — idea.md, conversation-log.md, api-info.md, selected-data.md, ui-explainer.md
- **Reference docs:** `.claude/ref/` — event-description.md, competitor-ideas.md, verge-interview.md
- **Source code:** `src/` — 43 TypeScript/TSX files

## Commands

```bash
# Build paper (once LaTeX is set up)
cd ~/cfp/mise/paper && latexmk -pdf main.tex

# Check beads
cd ~/cfp/mise && br ready
cd ~/cfp/mise && br list --status=open

# Sync beads
cd ~/cfp/mise && br sync --flush-only
```
