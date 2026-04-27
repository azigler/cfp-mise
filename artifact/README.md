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

When the artifact is published to Zenodo, a DOI will be issued. The
canonical citation is:

```bibtex
@misc{zigler2026miseartifact,
  author       = {Zigler, Andrew},
  title        = {Mise en Place for Agentic Coding — Research Artifact Bundle},
  year         = {2026},
  howpublished = {Zenodo},
  doi          = {10.5281/zenodo.[TBD]},
  url          = {https://doi.org/10.5281/zenodo.[TBD]}
}
```

Replace `[TBD]` with the issued DOI after upload (see Upload Steps).

## Upload steps (for the paper author)

1. **Verify contents.** From the repo root: `find artifact -type f
   | sort` and confirm everything in the inventory above is present.
2. **Create a release archive.** `tar czf
   mise-en-place-artifact.tar.gz artifact/` (or zip equivalent).
3. **Upload to Zenodo.** Visit https://zenodo.org/uploads/new (sign in
   with GitHub or ORCID).
   - Upload type: *Dataset* (or *Other*, if you prefer to flag it as a
     mixed-content artifact).
   - Title: *Mise en Place for Agentic Coding — Research Artifact Bundle*.
   - Authors: Andrew Zigler (LinearB, ORCID 0009-0001-8073-5917).
   - Description: copy the "What this artifact is" paragraphs above.
   - Keywords: `agentic coding`, `mise en place`, `context engineering`,
     `vibe coding`, `context fluency`, `SIGSOFT Open Science`.
   - License: *Creative Commons Attribution 4.0 International*.
   - Related identifier: link to the published paper DOI (when available).
   - Funding: none.
4. **Publish.** Zenodo will issue a DOI in the form
   `10.5281/zenodo.NNNNNNN`.
5. **Replace the placeholder.** In the paper source
   (`paper/sections/research-agenda.tex`, "Artifact Availability"
   subsection), replace `https://zenodo.org/[TBD]` with
   `https://doi.org/10.5281/zenodo.NNNNNNN`. Rebuild the PDF.
6. **Optional.** Mirror the bundle to a GitHub release on the same
   repo (`github.com/azigler/cfp-mise/releases`) for redundancy.

## Provenance

This artifact was assembled in April 2026 during the camera-ready
revision of the paper, in response to Reviewer 2's request for
SIGSOFT Open Science Policy compliance. The data files were extracted
during the original research phase (March 2026); the prompts and
references were copied verbatim from the hackathon repository
(`~/hackathon-infactory/`); the harness documentation was newly
written for this artifact.
