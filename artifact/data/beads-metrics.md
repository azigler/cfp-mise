# Beads Metrics: Hackathon Project

> Extracted from `~/hackathon-infactory/.beads/issues.jsonl` on 2026-03-03.

## Summary

| Metric | Value |
|--------|-------|
| Total beads | 68 |
| Hackathon-day beads (Jan 31) | 64 |
| Post-hackathon beads (Mar 3) | 4 |
| Closed | 47 (69.1%) |
| Open | 21 (30.9%) |
| Bugs filed | 6 (all closed) |
| Bug resolution rate | 100% |

## Status Breakdown

| Status | Count | Percentage |
|--------|-------|------------|
| Closed | 47 | 69.1% |
| Open | 21 | 30.9% |

### Hackathon-Day Only (64 beads)

| Status | Count | Percentage |
|--------|-------|------------|
| Closed | 43 | 67.2% |
| Open | 21 | 32.8% |

## Priority Distribution

| Priority | Count | Percentage | Description |
|----------|-------|------------|-------------|
| P0 (Critical) | 3 | 4.4% | Hotfixes during demo |
| P1 (High) | 38 | 55.9% | Core features and blockers |
| P2 (Medium) | 20 | 29.4% | Demo states, secondary features |
| P3 (Low) | 6 | 8.8% | Stretch goals, polish |
| P4 (Backlog) | 1 | 1.5% | Cleanup tasks |

## Issue Type Distribution

| Type | Count | Percentage |
|------|-------|------------|
| Task | 52 | 76.5% |
| Feature | 10 | 14.7% |
| Bug | 6 | 8.8% |

## Bug Inventory

| ID | Title | Status | Priority |
|----|-------|--------|----------|
| bd-1m4 | Fix View Submitted Essays link redirecting to homepage | Closed | P1 |
| bd-231 | Fix classroom data flow - climate classroom showing space race data | Closed | P1 |
| bd-2lq | Fix ResearchWorkspace API error - articles fail to load | Closed | P1 |
| bd-2zx | New classrooms should start on Day 1, not Day 30 | Closed | P1 |
| bd-htl | Articles showing truncated content in Research View | Closed | P0 |
| bd-ptw | Fix setHasSearched not defined error in ClassroomCustomize | Closed | P0 |

All 6 bugs were filed and closed during the hackathon day.

## Closure Time Analysis (Hackathon-Day Closed Beads)

| Metric | Value |
|--------|-------|
| Beads with closure data | 43 |
| Minimum closure time | < 1 minute |
| Maximum closure time | 32.6 minutes |
| Mean closure time | 7.6 minutes |
| Median closure time | 5.9 minutes |

## Creation Time Distribution (Hackathon Day, UTC)

| Hour (UTC) | Beads Created | Percentage |
|------------|---------------|------------|
| 19:00-19:59 | 20 | 31.3% |
| 20:00-20:59 | 13 | 20.3% |
| 21:00-21:59 | 25 | 39.1% |
| 22:00-22:59 | 6 | 9.4% |

First bead created: 19:41:39 UTC (Jan 31).
Last bead created: 22:45:27 UTC (Jan 31).
Bead creation window: 3 hours 4 minutes.

## Dependency Graph

Three beads declared explicit dependencies:

| Bead | Depends On | Depth |
|------|-----------|-------|
| bd-1vg (Replace teacher review mock data) | bd-37n (Infactory API client) | 1 |
| bd-30h (Classroom code validation) | bd-37n (Infactory API client) | 1 |
| bd-gqm (Submission plan synthesis) | bd-2kr, bd-2l4, bd-a70 (3 research beads) | 1 |

Maximum dependency depth: 1 (no transitive chains).
`bd-37n` is the only shared dependency (2 downstream beads).

## Label Distribution (Top 15)

| Label | Count |
|-------|-------|
| domain:demo | 11 |
| domain:student | 7 |
| domain:teacher | 7 |
| citations | 6 |
| student | 5 |
| store | 3 |
| domain:ai | 2 |
| domain:state | 2 |
| bug | 2 |
| critical | 2 |
| api | 2 |
| page | 2 |
| stretch | 1 |
| data-flow | 1 |
| research | 1 |

## Post-Hackathon Beads (Mar 3)

Four beads were created on 2026-03-03 for academic paper research:

| ID | Title | Status |
|----|-------|--------|
| bd-2kr | Survey related academic work on agentic coding methodologies | Closed |
| bd-2l4 | Assess mise en place article for academic conversion | Closed |
| bd-a70 | Analyze VibeX 2026 CFP and submission requirements | Closed |
| bd-gqm | Propose submission strategy and paper scaffold | Closed |

## Open Beads by Priority

| Priority | Count | Examples |
|----------|-------|---------|
| P0 | 0 | -- |
| P1 | 5 | Atlantic Dashboard sections (4), article engagement |
| P2 | 12 | Demo states (6), Socratic AI, classroom displays |
| P3 | 3 | Visual highlights, text selection, auto-save |
| P4 | 1 | Remove old feature placeholders |

The 21 open beads represent stretch goals and polish work that was deprioritized during the hackathon in favor of shipping core functionality.
