# VibeX 2026 Paper: Mise en Place for Agentic Coding

> Academic paper submission for the 1st International Workshop on Vibe Coding and Vibe Researching (VibeX 2026), co-located with EASE 2026, Glasgow, June 9-12, 2026.

## DEADLINE: March 8, 2026 (AoE)

## Status & Timeline

Research phase is complete (4 beads closed). The project is now in **Phase 1: Infrastructure** per the plan.

| Day | Date | Phase | Status |
|-----|------|-------|--------|
| 1 | Mar 3 (Mon) | Research + data extraction + template setup | Research DONE. Data extraction & template next. |
| 2 | Mar 4 (Tue) | Write Introduction + Related Work + Methodology | |
| 3 | Mar 5 (Wed) | Write Case Study + Context Fluency + figures/tables | |
| 4 | Mar 6 (Thu) | Write Research Agenda + Conclusion + references + first draft review | |
| 5 | Mar 7 (Fri) | Revisions, formatting, PDF generation, submit | |
| Buffer | Mar 8 (Sat) | Deadline AoE (UTC-12). Final window if needed. | |

**Next steps:** Create beads for Phase 1 tasks, deploy data extraction agent into `~/hackathon-infactory/` (read-only) and template setup agent here. See `.claude/plans/vibex-2026-submission.md` for full plan.

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
