# The Three-Phase Workflow as Operational Practice

The paper presents *mise en place* (MEP) as a three-phase methodology.
This file restates those three phases as an **operational procedure** —
what the practitioner actually does, in what order, and what artifacts
each phase produces. It is the harness viewed from the outside, intended
to be reproducible by another practitioner without reading the paper's
narrative framing.

## Overview

| Phase | Activity | Output |
|---|---|---|
| 1. Contextual Grounding | Gather and curate domain context | A briefing packet (markdown documents) |
| 2. Collaborative Specification | Refine product spec with the agent | An agent contract (`CLAUDE.md`) + structured plans |
| 3. Task Decomposition | Convert spec into atomic, dispatchable units | A populated bead store (`issues.jsonl`) |

The phases are sequential **for any given product idea**, but in
practice phases 1 and 2 interleave (returning to phase 1 to fill a gap
identified in phase 2 is normal). Phase 3 is a one-way gate: once
beads are dispatched to parallel agents, returning to phases 1–2
mid-stream creates rework.

The hackathon allocated roughly:

- Phase 1: 60–75 minutes
- Phase 2: 30–45 minutes
- Phase 3: 5–10 minutes (the orchestrator agent decomposed the spec
  into ≈42 initial beads in a single dispatch)
- Implementation: ~3 hours

The 5.7:1 prep-to-execution ratio is what the paper argues is doing
the work.

## Phase 1: Contextual Grounding

**Goal:** capture every piece of context the agent will need but cannot
generate for itself — domain expertise, value judgments, lived
experience, situational specifics.

**Inputs:** the human practitioner's tacit knowledge, plus any external
artifacts (briefs, articles, transcripts) relevant to the domain.

**Outputs:** a directory of markdown documents, each focused on one
slice of context. The hackathon produced eleven of these (see
`../prompts/plans/` and `../prompts/refs/`).

### Procedure

1. **Identify the situation.** What triggered the work? In the
   hackathon case: a published challenge prompt ("How might we make
   The Atlantic accessible to high school and college students and
   teachers?"). Capture this verbatim as a reference document.
2. **Gather external context.** Any document, interview, dataset, or
   API description that shapes the problem space. Convert to markdown
   if needed. Place in a known location the agent will read.
3. **Dictate domain context.** Use voice-to-text to produce
   long-form, associative narrative about the practitioner's
   relevant experience. Do not edit. The artifact is the texture
   of the thinking, including false starts.
4. **Note constraints.** Time-box (e.g., 3-hour build window),
   evaluation criteria (e.g., judges' preferences), competitive
   landscape (e.g., what other teams are doing).

### What "good" looks like

- The directory contains 5–10 markdown files
- Total length is in the range of 5,000–15,000 words
- An external reader who has not seen the practitioner's project could
  understand, from these documents alone, **why** the project exists
  and what would make it succeed
- At least one document captures the practitioner's domain expertise
  in a form an agent can reference

### Anti-patterns

- **Bullet-point summaries instead of narrative.** Bullet points lose
  the texture of expert reasoning. Voice-dictated paragraphs with
  occasional digressions are more useful to the agent than tight
  outlines.
- **Stopping at "the data."** External documents are necessary but not
  sufficient. The practitioner's own reasoning *about* the data is
  the part the agent can't generate.
- **Premature filtering.** Capture the false starts. The agent will
  read what's there.

## Phase 2: Collaborative Specification

**Goal:** convert the contextual grounding into an actionable product
specification that an agent could implement without asking clarifying
questions.

**Inputs:** Phase 1 artifacts + the practitioner's ongoing dialogue
with the agent.

**Outputs:**
1. An **agent contract** (`CLAUDE.md`) committed to the project root.
   This is the single document the agent loads on every session as
   system context. It must include:
   - Tech stack and architectural conventions
   - Project structure
   - Coding conventions (style, naming, patterns)
   - Demo flow / acceptance scenarios
   - Design principles (what to optimize for, what to refuse)
   - Any tooling-specific protocols (e.g., beads workflow, build
     commands)
2. **Structured plans** for each major aspect of the product:
   - UI architecture (`ui-explainer.md`)
   - Demo states (`simulated-progress.md`)
   - API surface (`api-exploration.md`, `api-info.md`)
   - Content selection (`topic-research.md`, `selected-data.md`)

### Procedure

1. **Draft the agent contract.** Start from a minimal template and
   accrete sections as decisions emerge from dialogue with the agent.
2. **Run dialogues with the agent on specific subsystems.** For each
   major component (UI, API, demo, state), have the agent propose an
   approach. Disagree explicitly when the proposal misaligns with
   intent. Capture the dialogue's outcome as a plan document.
3. **Make value judgments visible.** When you reject an agent's
   proposal, write down *why* in the plan. This is the externalized
   tacit knowledge the next agent will need.
4. **Defer scope aggressively.** A specification that says "support
   one assignment type" is more useful than one that says "support
   all assignment types eventually." The plan should reflect what
   the agents will actually build, not what would be ideal.

### What "good" looks like

- A `CLAUDE.md` that an agent can read in 2–3 minutes and have a
  concrete-enough mental model of the project to start work
- Plan documents that bound the work to a specific scope
- Visible disagreement traces — places where "the agent suggested X
  and I overrode to Y because Z"

### Anti-patterns

- **Specification as wishlist.** "Eventually we want…" content does
  not constrain implementation; it inflates it.
- **Hidden value judgments.** Decisions made silently in dialogue
  but not captured in the plan are decisions the next agent cannot
  re-derive.
- **Skipping the agent contract.** A project without `CLAUDE.md`
  forces the agent to infer conventions every session, which causes
  drift.

## Phase 3: Task Decomposition

**Goal:** convert the specification into atomic, dispatchable work
units with explicit priorities, dependencies, and acceptance criteria.

**Inputs:** Phase 2 artifacts.

**Outputs:** a populated bead store (`issues.jsonl`) — see
`beads-schema.md`.

### Procedure

1. **Dispatch an orchestrator agent** with the task: "Read CLAUDE.md
   and the planning documents in `.claude/plans/`. Produce a complete
   set of beads covering every screen, feature, and integration point.
   Each bead must have: priority, type, acceptance criteria, and any
   blocking dependencies."
2. **Review the output.** The orchestrator's first pass will be
   mostly correct but will miss things or over-decompose. Add, edit,
   delete beads as needed. Common adjustments:
   - Splitting a bead that's actually two pieces of work
   - Merging beads that share state and can't be parallelized
   - Adding `blocks` edges between beads that share data structures
3. **Verify atomicity.** A bead is atomic if a single sub-agent can
   complete it in one session (≈10 minutes). The hackathon's median
   closure time was 5.9 min, mean 7.6 min — under the atomicity
   bound.
4. **Then, and only then, dispatch.** Sub-agents pull from
   `br ready` (open + unblocked + unclaimed) and execute against the
   acceptance criteria.

### What "good" looks like

- 30–80 beads for a hackathon-scale project
- Most beads (≥50%) close in under 10 minutes
- Bug beads close fastest (median ≈1.2 min in the case study) because
  they are the most narrowly-scoped
- Parallel batches: 5–10 beads closing within seconds of each other,
  indicating the spec was decomposable

### Anti-patterns

- **Beads as TODO list.** Without acceptance criteria, beads degrade
  into prose tasks the agent can't verify against.
- **Decomposing during implementation.** Creating beads while agents
  are running causes the orchestrator to thrash. Decompose first,
  dispatch once, observe results, decompose again as a discrete next
  cycle.
- **Skipping the dependency graph.** Without `blocks` edges,
  parallel agents will race on shared state. Two beads that touch
  the same store should be sequential, not parallel.

## After implementation: the "small" final phase

The paper does not call this a fourth phase, but the hackathon data
shows a recognizable post-implementation cycle:

- **Test, observe, file bugs as beads.** The hackathon filed 6 bugs
  during the build; all closed within 3 minutes each.
- **Hotfix late.** The final bug (bd-htl, "Articles showing
  truncated content") was filed and closed in the same minute,
  during the live demo.
- **Stretch beads stay open.** 21 beads remained open at time
  expiration. The discipline of not chasing them is itself part of
  the methodology.

## Reproducing this workflow

To run this on a new project:

1. Create `<project>/CLAUDE.md` with at minimum: tech stack,
   project structure, agent protocol section.
2. Create `<project>/.claude/plans/` and dictate context into it.
3. Initialize beads: `br init --prefix <2-letter-prefix>`.
4. Dispatch an orchestrator: "Read CLAUDE.md and .claude/plans/.
   Produce beads covering all work. Use atomic sizing."
5. Then start dispatching sub-agents against `br ready`.

That is the harness. The rest is judgment about what to build.
