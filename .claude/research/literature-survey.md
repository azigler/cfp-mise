# Literature Survey: Agentic Coding Methodologies
**Bead:** bd-2kr | **Date:** 2026-03-03

## Executive Summary

The field has bifurcated into **vibe coding** (minimal prep, trust the model) and **structured preparation** (context curation, specs, planning before execution). Our paper enters a landscape with significant academic research on LLM-assisted coding productivity but a critical gap: **no formalized methodology for preparation-phase work as a distinct engineering discipline.**

---

## 1. Academic Literature

### AI Pair Programming & Productivity
- Productivity gains: 21-55% across tasks (GitHub Copilot studies, 2023-2025)
- 60-75% of developers report more fulfillment with AI assistants
- Real metrics: 10.6% increase in PRs, 3.5hr reduction in cycle time
- **Gap:** No studies examine the preparation phase before agent execution

### Security & Reliability Concerns
- Veracode 2025: 45% of AI-generated code contains security flaws
- 10x spike in security findings from AI code (June 2025)
- Productivity paradox: 3-4x more commits but 15-25% rework rate
- **Implication:** Speed without preparation creates a false productivity narrative

### Developer Mental Models
- Critical mismatches between developer expectations and AI behavior (ScienceDirect, 2025)
- Trust requires context-aware explanations (FACCT 2024)
- **Implication:** Validates importance of explicit preparation and clear specifications

---

## 2. Practitioner Methodologies

### Geoffrey Huntley — Ralph Loop (2024-2025)
- Bash loop repeatedly feeding AI agent a prompt file for iterative improvement
- "Deterministically bad in an undeterministic world" — persistence despite setbacks
- **Relation:** Reactive iteration, not preparation-driven. Complementary.
- Sources: ghuntley.com/ralph/, goose docs

### Steve Yegge — Beads & Gas Town (2025-2026)
- Beads: External agent memory with dependency tracking, Git+SQLite backend
- Gas Town: Multi-agent orchestration with persistent work tracking
- **Relation:** Solves memory/orchestration but assumes agents have good specs already
- Sources: github.com/steveyegge/beads, steveyegge/gastown

### Dex Horthy — RPI Methodology (2024-2025)
- Research → Plan → Implement (three-phase approach)
- Forces intermediate design artifacts before code
- **Relation:** RPI IS essentially mise en place formalized. Most direct predecessor.
- Sources: HumanLayer.dev, Dev Interrupted podcast

### Jeffrey Emanuel — beads_rust (2025-2026)
- High-performance Rust reimplementation of Beads (~20K lines vs ~276K)
- beads_viewer (bv): dependency-aware triage with graph metrics
- **Relation:** Infrastructure for tracking prepared work
- Sources: github.com/Dicklesworthstone/beads_rust

### Andrej Karpathy — Vibe Coding (Feb 2025)
- "Fully give in to the vibes, embrace exponentials, forget code exists"
- Entered Merriam-Webster and Collins Dictionary 2025
- Explicitly for "throwaway weekend projects"
- **Relation:** The anti-pattern our methodology opposes

---

## 3. Emerging Formal Methodologies

### Specification-Driven Development (SDD)
- Specs as primary artifact, code as generated output
- Four-phase: Specification → Plan → Tasks → Implementation
- GitHub released "Spec Kit" (open source)
- Gartner 2025: "Context engineering is in, prompt engineering is out"
- Sources: O'Reilly, Thoughtworks, TheNewStack, InfoQ

### Context Engineering (2025-2026)
- Shift from prompt optimization to managing complete informational system around LLM
- Strategies: writing (external memory), selecting (retrieval), compressing, isolating
- Anthropic: "Effective Context Engineering for AI Agents"
- **Relation:** Context engineering IS mise en place at the token level

### Promptware Engineering
- Formal SE principles applied to prompt development
- arXiv:2503.02400
- Recognizes prompts as engineered artifacts

---

## 4. Theoretical Frameworks

### Backward Design (Wiggins & McTighe, 1998)
- Start with desired outcomes → design assessments → plan instruction
- Direct analog: specify agent outputs → define success criteria → design context
- ASCD whitepaper, widely cited in education

### Tacit Knowledge (Polanyi, 1958, 1966)
- "We can know more than we can tell"
- 70-80% of organizational knowledge is tacit/undocumented
- **Implication:** Preparation work makes tacit knowledge explicit for agents

### Human-AI Collaboration Frameworks
- 11 distinct interaction types identified (arXiv 2501.08774, 2025)
- Co-creation model: humans and AI alternate contributions
- Preparation phase = where humans define the collaboration contract

---

## 5. The Gap Our Paper Fills

1. **Preparation phase has no formalized methodology** — Academic lit focuses on real-time coding; practitioner work (RPI, SDD) exists but isn't unified
2. **Speed-reliability tradeoff is undertheorized** — Literature documents gains AND vulnerabilities but doesn't connect them to preparation
3. **Alignment as upstream engineering** — Few papers treat "did the agent build what I intended?" as a preparation-phase problem
4. **No unified framework** — Ralph Loop, RPI, SDD, Beads, Context Engineering all solve parts; integration is missing
5. **Tacit knowledge externalization** — Not addressed in AI-assisted development context

---

## 6. Key References for Paper

### Must-Cite Academic
- Wiggins & McTighe (1998) — Understanding by Design
- Polanyi (1958, 1966) — Tacit Knowledge
- arXiv 2501.08774 (2025) — Human-AI Collaboration Taxonomy
- arXiv 2503.02400 — Promptware Engineering
- FACCT 2024 — Trust in AI Code Generation

### Must-Cite Practitioner
- Huntley — Ralph Loop (ghuntley.com/ralph/)
- Yegge — Beads and Gas Town
- Horthy — RPI Methodology (HumanLayer)
- Emanuel — beads_rust
- Karpathy — Vibe Coding
- GitHub — Spec Kit / SDD

### Must-Cite Industry
- Veracode 2025 — AI code security report
- Gartner 2025 — Context engineering
- Anthropic — Context engineering for agents
