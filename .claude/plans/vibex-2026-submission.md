# VibeX 2026 Submission Plan: Mise en Place for Agentic Coding

> **DEADLINE: March 8, 2026 (AoE) — 5 days from today**

## Decision: Submission Type

### Recommendation: **Positioning Paper** (5 pages incl. references)

**Why not Experience Report:**
- Experience reports risk being dismissed as "just a blog post" — and we literally already published the blog post
- Our material has theoretical depth (backward design, tacit knowledge, context fluency as a new construct) that belongs in a positioning/vision paper
- The user explicitly expressed interest in the more academic framing
- Positioning papers can propose research questions and future work, which is where our strongest contribution lies

**Why not Full Research Paper:**
- 10 pages requires empirical rigor we can't achieve in 5 days (controlled comparison, statistical analysis)
- Single case study doesn't support "completed research" framing
- Overkill for the insight; dilutes impact with padding

**Why Positioning Paper works:**
- "Preliminary results, conceptual explorations, methodological reflections, or visionary ideas that stimulate discussion"
- We have ALL of these: preliminary results (hackathon), conceptual exploration (context fluency), methodological reflection (3-phase mise en place), visionary ideas (context fluency as emerging skill)
- 5 pages is achievable in 5 days
- Positions us as *defining a new concept*, not just reporting an experience
- First-edition workshop = novel framing wins

---

## Proposed Paper

### Title Options (ranked)

1. **"Mise en Place for Agentic Coding: Deliberate Preparation as Context Engineering Methodology"**
2. "Beyond Vibe Coding: A Preparation-First Methodology for AI Agent Orchestration"
3. "Context Fluency: Formalizing the Preparation Phase of AI-Assisted Software Development"

### Abstract (Draft)

> The rapid adoption of AI coding agents has produced a dominant workflow pattern — often called "vibe coding" — that prioritizes speed of implementation over deliberate preparation. We argue that this approach creates a systematic alignment problem: agents that lack sufficient context produce code requiring extensive debugging and refactoring, consuming 70% or more of total development time. Drawing on the culinary concept of *mise en place* (everything in its place), we propose a three-phase preparation methodology for agentic coding: (1) contextual grounding, where domain expertise and tacit knowledge are externalized into structured documents; (2) collaborative specification, where human-agent dialogue produces detailed design artifacts; and (3) task decomposition, where specifications are converted into structured, dependency-aware task records. We report on the application of this methodology during a competitive hackathon, where two hours of preparation enabled a near-one-shot implementation of a full-stack educational platform by parallel AI agents. We introduce the concept of *context fluency* as an emerging developer skill — the ability to create rich, structured context that agents can act on — and connect it to established frameworks in backward design and tacit knowledge externalization. We conclude with a research agenda for empirically validating preparation-phase methodologies in AI-assisted software development.

### Paper Structure (5 pages, ~3,800 words + references)

#### 1. Introduction (0.5 pages, ~400 words)
- The alignment problem in agentic coding
- Vibe coding as dominant but insufficient pattern
- Mise en place as a metaphor and methodology
- Paper contributions: (1) 3-phase methodology, (2) case study, (3) "context fluency" construct, (4) research agenda

#### 2. Background and Related Work (0.75 pages, ~600 words)
- **AI-assisted coding workflows:** Copilot studies, productivity gains, security concerns (Veracode 45% flaw rate)
- **Emerging preparation methodologies:** RPI (Horthy), Spec-Driven Development (GitHub Spec Kit), Context Engineering (Anthropic/Gartner)
- **Practitioner innovations:** Ralph Loop (Huntley), Beads (Yegge), beads_rust (Emanuel)
- **Theoretical foundations:** Backward design (Wiggins & McTighe), tacit knowledge (Polanyi)
- **Gap:** No formalized, theoretically-grounded methodology for preparation-phase work

#### 3. The Mise en Place Methodology (1.25 pages, ~1,000 words)
Core contribution. Formalize the three phases:

**Phase 1: Contextual Grounding**
- Purpose: Externalize domain expertise, tacit knowledge, and value judgments
- Artifacts: Briefing documents capturing institutional context, domain knowledge, competitive landscape, design philosophy
- Principle: Context that agents cannot generate independently (Polanyi's tacit knowledge)
- Connection to backward design: Start with *why* before *what*

**Phase 2: Collaborative Specification**
- Purpose: Produce detailed design artifacts through human-agent dialogue
- Process: Human proposes intent → agent proposes implementation → human accepts/rejects/modifies
- Key decisions: Scope constraints, quality standards, architectural choices
- Principle: Value judgments as specification constraints (what to exclude is as important as what to include)

**Phase 3: Task Decomposition**
- Purpose: Convert specifications into structured, dependency-aware task records
- Tooling: Beads (structured JSON task records with priorities and dependencies)
- Principle: Fine-grained decomposition enables parallel agent execution without coordination overhead
- Output: Dependency graph where each node is an independently-executable task

**Figure 1:** Methodology overview diagram (3 phases → agent execution → testing loop)

#### 4. Case Study: The Beat (1.0 page, ~800 words)
Application of mise en place in a constrained setting:

- **Setting:** Hackathon (The Atlantic × Infactory × Hacks/Hackers), 5-hour window, ~12 teams
- **Timeline:** 2hr preparation → 5min parallel agent implementation → 1hr testing/deployment
- **Quantitative data:**
  - Preparation artifacts: 5-6 markdown documents, 1 product specification, 42 structured task records
  - Implementation: 4 parallel subagents, 43 TypeScript files, 9 git commits in final 53 min
  - Task completion: 42/63 beads closed (66.7%); 21 remaining were stretch features
  - Outcome: First place, judged by Atlantic CEO Nicholas Thompson
- **Qualitative observations:**
  - Architecture was correct on first pass (no structural refactoring needed)
  - Bugs were integration/styling issues, not architectural misalignment
  - API instability handled by dispatching dedicated polling agents
  - Domain expertise (teaching background) informed design decisions agents couldn't make

**Table 1:** Timeline breakdown with phase durations and artifact counts

#### 5. Context Fluency: An Emerging Skill (0.5 pages, ~400 words)
Propose "context fluency" as a new construct:

- **Definition:** The ability to create rich, structured context that AI agents can act on — capturing domain expertise, value judgments, and design intent in machine-legible form
- **Components:** Decomposition, specification, constraint definition, domain encoding
- **Theoretical grounding:** Maps to backward design (outcome-driven), tacit knowledge externalization (Polanyi), and pedagogical scaffolding (Vygotsky)
- **Distinction from prompt engineering:** Context fluency is upstream of prompting — it creates the informational environment within which prompts operate
- **Observation:** This skill set maps closely to teaching (lesson planning = context engineering for learners)

#### 6. Research Agenda and Conclusion (0.5 pages, ~400 words)
Open questions for the community:

- **RQ1:** Does deliberate preparation reduce agent misalignment compared to iterative development, and at what cost-benefit threshold?
- **RQ2:** What constitutes "sufficient" context for agentic work — can we define stopping criteria?
- **RQ3:** How does context fluency vary across practitioners, domains, and agent models?
- **RQ4:** Can mise en place principles scale beyond prototyping to sustained, multi-month projects?
- **RQ5:** What is the relationship between preparation time and implementation quality across different project complexities?

Conclude: Mise en place is not a finished answer but a starting framework. Invite empirical validation, replication studies, and tool development.

#### References (~0.5 pages, 15-20 citations)
Key citations organized by category:

**Theoretical:**
- Wiggins & McTighe (1998) — Understanding by Design
- Polanyi (1966) — The Tacit Dimension

**AI-Assisted Development:**
- GitHub Copilot productivity studies (2023-2025)
- Veracode (2025) — AI code security report
- arXiv 2501.08774 — Human-AI Collaboration Taxonomy
- arXiv 2503.02400 — Promptware Engineering

**Practitioner Methodologies:**
- Huntley — Ralph Loop
- Yegge — Beads / Gas Town
- Horthy — RPI Methodology
- Emanuel — beads_rust
- Karpathy — Vibe Coding (2025)
- GitHub — Spec Kit / SDD

**Context Engineering:**
- Anthropic — Effective Context Engineering for AI Agents
- Gartner (2025) — Context engineering shift

---

## Content Adaptation Plan

### What can be adapted from the published article:
- Mise en place metaphor and opening framing
- Three-phase methodology description (needs formalization)
- Case study timeline and quantitative data
- Context fluency concept and components
- Teaching/backward design connection

### What needs to be written new:
- **Abstract** — Academic framing with contributions list
- **Related work section** — Formal literature review connecting to existing research
- **Methodology formalization** — Principles, artifacts, decision points (not just narrative)
- **Quantitative evidence table** — Extract precise data from git logs and beads records
- **Research questions** — Formal RQs with theoretical justification
- **Figure 1** — Methodology overview diagram
- **Table 1** — Timeline/artifact breakdown

### What needs to be removed/changed:
- Personal narrative voice → academic third person or modest first person plural
- "I talked to my computer" energy → "The practitioner-researcher applied..."
- Blog section headers → Academic section numbering
- Informal asides → Formal observations with citations
- The word "I" as subject → "We" or passive constructions

---

## Data Extraction Tasks

Before writing, extract these from the project artifacts:

1. **Git timeline:** Exact timestamps of first and last commit, commit frequency distribution
2. **Beads metrics:** Total created, closed, open; priority distribution; dependency graph depth
3. **File count:** Exact number of source files, total lines of code
4. **Context documents:** Word counts of each preparation document
5. **Session log timestamps:** Precise timing of each phase transition

---

## Formatting Requirements

- **Template:** ACM Primary Article Template
- **LaTeX:** `\documentclass[sigconf,review]{acmart}`
- **Conference declaration:** `\acmConference[EASE 2026]{The 30th International Conference on Evaluation and Assessment in Software Engineering}{9–12 June, 2026}{Glasgow, Scotland, United Kingdom}`
- **Page limit:** 5 pages including references
- **Submission:** PDF via https://easychair.org/conferences/?conf=vibex2026
- **Review:** Single-blind (author names visible)

---

## 5-Day Timeline

| Day | Date | Tasks |
|-----|------|-------|
| **Day 1** | Mar 3 (Mon) | Research complete. Extract quantitative data from git/beads. Draft abstract and outline. |
| **Day 2** | Mar 4 (Tue) | Write Introduction + Related Work + Methodology sections. Set up ACM LaTeX template. |
| **Day 3** | Mar 5 (Wed) | Write Case Study + Context Fluency sections. Create Figure 1 and Table 1. |
| **Day 4** | Mar 6 (Thu) | Write Research Agenda + Conclusion. Compile references. First complete draft review. |
| **Day 5** | Mar 7 (Fri) | Revisions, formatting check, PDF generation. Submit to EasyChair by end of day. |
| **Buffer** | Mar 8 (Sat) | Deadline is AoE (UTC-12). Final submission window if needed. |

---

## Risk Assessment

| Risk | Mitigation |
|------|------------|
| 5 pages too tight for all content | Prioritize methodology + case study; compress related work |
| Reviewers see it as "just a blog post" | Lead with theoretical grounding (backward design, Polanyi), formal RQs |
| Prior publication concern (Substack article) | Substack is gray literature, not peer-reviewed. Paper adds formalization, literature review, research agenda. Disclose in submission. |
| Single case study perceived as weak | Frame as positioning paper, not empirical study. Propose replication as future work. |
| ACM template formatting unfamiliar | Use Overleaf with ACM template; many examples available |

---

## Research Files Index

All research supporting this plan is saved in `.claude/research/`:

- `article-assessment.md` — Core claims inventory, methodology gaps, conceptual mapping (bd-2l4)
- `vibex-cfp-analysis.md` — CFP deep analysis, submission type comparison, strategic positioning (bd-a70)
- `literature-survey.md` — 30+ sources across academic, practitioner, and theoretical literature (bd-2kr)
