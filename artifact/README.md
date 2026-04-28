# Mise en Place for Agentic Coding — Research Artifact Bundle

This is the research artifact accompanying the paper:

> **Mise en Place for Agentic Coding: Deliberate Preparation as Context
> Engineering Methodology.** Andrew Zigler. *VibeX 2026* (1st International
> Workshop on Vibe Coding and Vibe Researching), co-located with EASE
> 2026, Glasgow, June 2026.

It is published as a separate deliverable alongside the camera-ready
paper to satisfy the SIGSOFT Open Science Policy. It contains the
quantitative data, hackathon prompts, and agent-harness documentation
referenced in the paper, in a form a third party can read, audit, and
extend.

## What this artifact is — and is not

**It is** a curated bundle of the case-study materials: timing data,
git/beads records, the planning corpus produced during the preparation
phase, and the procedural documentation of the agent harness. The
contents are intended to support reproduction of the methodology
(not the specific product built during the hackathon), to enable
re-analysis of the timing claims, and to make the variation-across-teams
discussion auditable.

**It is not** a software release. The hackathon source code (≈8,500 lines
of TypeScript) is intentionally excluded; the paper's claim is about
*preparation* rather than *implementation*, and reproducing the code
would obscure that. Credentials, secrets, and per-message session
transcripts are also excluded.

## Inventory

```
artifact/
├── README.md                      this file
├── LICENSE-CC-BY-4.0              license for the data and prose
├── LICENSE-MIT                    license for the harness configs
├── data/
│   ├── git-timeline.md            commit-by-commit deployment timeline
│   ├── beads-metrics.md           bead closure metrics (68 beads, 47 closed)
│   ├── bead-timestamps.md         per-bead timing (used in Figure 2)
│   ├── session-analysis.md        Claude Code session aggregate metrics
│   └── beads-jsonl.gz             gzipped raw beads JSONL (full task records)
├── prompts/
│   ├── README.md                  reading order and per-file annotation
│   ├── claude-md.md               the agent contract
│   ├── plans/                     11 planning documents (~11,000 words)
│   └── refs/                      4 curated reference documents
└── agent-harness/
    ├── README.md                  what the harness is and what it isn't
    ├── workflow.md                three-phase methodology as procedure
    └── beads-schema.md            bead record format and lifecycle
```

A reading order for the `prompts/` directory is provided in
`prompts/README.md`. The `agent-harness/` directory is the portable
distillation: it documents the parts of the harness that any
practitioner could adopt without reproducing the specific hackathon
project.

## Licensing

This artifact uses a dual-license model.

- **Data and prose** (everything in `data/`, `prompts/`, `agent-harness/`,
  and this README) are licensed under the **Creative Commons Attribution
  4.0 International License** (CC-BY 4.0). See `LICENSE-CC-BY-4.0`.
- **Harness configurations and code-shaped scaffolds** (specifically
  `prompts/claude-md.md` and any code excerpts within
  `agent-harness/`) are additionally available under the **MIT License**.
  See `LICENSE-MIT`.

In practice this means: cite the artifact when you use the data or
prose; copy the agent contract or scaffolding into your own project
freely.

## Citation

This artifact is archived on Zenodo at
[`10.5281/zenodo.19868258`](https://doi.org/10.5281/zenodo.19868258).
The canonical citation is:

```bibtex
@misc{zigler2026miseartifact,
  author       = {Zigler, Andrew},
  title        = {Mise en Place for Agentic Coding — Research Artifact Bundle},
  year         = {2026},
  howpublished = {Zenodo},
  doi          = {10.5281/zenodo.19868258},
  url          = {https://doi.org/10.5281/zenodo.19868258}
}
```

The DOI above is the canonical citation for this artifact bundle.

## How this artifact was published

This bundle was published via the GitHub-Zenodo integration on
2026-04-28. The flow:

1. `.zenodo.json` at the repo root supplied metadata (title, creator
   with ORCID, keywords, CC-BY 4.0 license, dataset upload type).
2. A GitHub release tagged `artifact-v1.0` was cut from the
   `camera-ready` branch at
   <https://github.com/azigler/cfp-mise/releases/tag/artifact-v1.0>.
3. Zenodo received the GitHub release event and minted DOI
   `10.5281/zenodo.19868258` for this version.
4. The DOI was inserted into `paper/sections/research-agenda.tex`
   (Artifact Availability subsection) and into this README's BibTeX
   block above, then the PDF was rebuilt.

If a future revision of this artifact is needed, cut a new GitHub
release tag (`artifact-v1.1`, etc.); Zenodo will mint a new version
DOI under the same parent record.

## Provenance

This artifact was assembled in April 2026 during the camera-ready
revision of the paper, in response to Reviewer 2's request for
SIGSOFT Open Science Policy compliance. The data files were extracted
during the original research phase (March 2026); the prompts and
references were copied verbatim from the hackathon repository
(`~/hackathon-infactory/`); the harness documentation was newly
written for this artifact.
