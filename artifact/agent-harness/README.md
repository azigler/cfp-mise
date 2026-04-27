# Agent Harness

The case-study workflow ran on a deliberately minimal toolchain: a
terminal over SSH, voice-to-text dictation for prompts, Claude Code as
the agent runtime, and the **beads** issue tracker as the coordination
layer between the human orchestrator and parallel sub-agents. There was
no IDE, no agent dashboard, no custom orchestration framework.

This directory documents the parts of that harness that are **portable**
— the conventions and primitives that any practitioner could adopt
without reproducing the specific hackathon project. The hackathon-specific
content (product idea, API exploration, demo flow) lives in
`../prompts/`.

## What's in this directory

- **`workflow.md`** — the three-phase methodology (Contextual Grounding,
  Collaborative Specification, Task Decomposition) reformulated as
  operational practice rather than narrative. This is the harness as a
  reproducible procedure.
- **`beads-schema.md`** — the structure of a beads issue, the lifecycle
  states, the dependency model, and the discipline that makes beads
  useful as an agent-coordination layer rather than a glorified TODO
  list.

## What's deliberately omitted

- **The Claude Code product itself.** Claude Code is Anthropic's
  commercial agent runtime; reproducing it is out of scope. The artifact
  bundle is about how to *use* an agent runtime, not how to build one.
- **Voice-to-text tooling.** The practitioner used Wispr Flow; the
  practice — dictating long associative thoughts rather than typing
  tight self-edited ones — is portable across any speech-to-text tool.
- **Project-specific scaffolding.** The Bun/Vite/React/TypeScript stack
  used for the hackathon is incidental. The harness is stack-agnostic.

## Relationship to the paper

The paper's three-phase methodology (Section 3) is a generalization of
this harness. The harness documents here ground the methodology in
concrete artifacts:

| Paper phase | Harness artifact | Where to look |
|---|---|---|
| Phase 1: Contextual Grounding | Curated reference docs + dictated domain notes | `../prompts/refs/`, `../prompts/plans/conversation-log.md`, `../prompts/plans/idea.md` |
| Phase 2: Collaborative Specification | The agent contract (CLAUDE.md) + structured plans | `../prompts/claude-md.md`, `../prompts/plans/ui-explainer.md`, `../prompts/plans/simulated-progress.md` |
| Phase 3: Task Decomposition | Beads issues with priorities, dependencies, acceptance criteria | `../data/beads-jsonl.gz`, `beads-schema.md` |

## Beads, in one sentence

A bead is a JSON record (`{id, title, description, priority, status,
dependencies, ...}`) appended to a single git-tracked JSONL file
(`.beads/issues.jsonl`), readable by both humans and agents, with a CLI
(`br`) that provides atomic operations (claim, close, dependency add)
and a "ready" view that filters to unblocked, unclaimed work. That is
the entire harness.

## Beads, slightly more

Two properties of beads matter for the methodology:

1. **Structured but lightweight.** A bead has fields (priority, type,
   acceptance criteria, dependencies) but no schema enforcement layer
   beyond what the CLI gives you. This is the right tradeoff for an
   agent-coordination layer: enough structure to query and filter,
   little enough overhead that creating a bead is cheap.
2. **Single source of truth, git-tracked.** The JSONL file is the
   authoritative state. Every commit can include a `Bead: <id>` trailer
   linking the change to the originating task. This makes the project's
   history a graph of *intent* (beads) connected to *execution* (commits).
   The hackathon produced 68 beads and 10 commits; the asymmetry (6.8
   beads per commit) reflects the fact that beads tracked planning,
   bug filing, and feature decomposition, while commits tracked
   deployment milestones.

See `beads-schema.md` for the full record format and lifecycle.

## Practitioner credit

The beads tool was originally conceived by Steve Yegge ("Beads") and
implemented as a Rust binary by Jeffrey Emanuel (`beads_rust` /
`br`). The convergence on this kind of structured task-decomposition
layer — Geoffrey Huntley's "Ralph Loop," Yegge's Beads/Gas Town,
Emanuel's lightweight Rust port — is one of the data points the paper
uses to argue that *mise en place* (MEP) is an emerging practice rather
than an idiosyncratic preference.
