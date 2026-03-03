# Review Notes: Mise en Place for Agentic Coding

> Generated 2026-03-03. Paper is at `paper/main.pdf` (5 pages, ACM sigconf format).

## Build

```bash
cd ~/cfp/mise/paper && latexmk -pdf main.tex
```

PDF is already built. Re-run after any edits.

## Decisions Made

1. **Submission type:** Positioning paper (5 pages incl. references) — strongest fit per CFP analysis. Allows methodology proposal + case study + research agenda format.

2. **Title:** "Mise en Place for Agentic Coding: Deliberate Preparation as Context Engineering Methodology" — positions us at the intersection of preparation and context engineering, which is where the CFP interest is strongest.

3. **Structure:** 6 sections (Intro → Related Work → Methodology → Case Study → Context Fluency → Research Agenda/Conclusion). Context fluency gets its own section because it's the paper's most novel intellectual contribution.

4. **Theoretical framing:** Backward design (Wiggins & McTighe) + tacit knowledge (Polanyi) as the two pillars. These are well-established frameworks that give the methodology academic legitimacy.

5. **Trimming for page count:** Cut ~600 words from first draft (6→5 pages). Cuts prioritized narrative redundancy over quantitative data. All key numbers preserved.

## Owner Judgment Needed

### 1. Author Information (REQUIRED)
`paper/main.tex` lines 26-32 have placeholder author info:
```latex
\author{[Author Name]}
\email{[author@example.com]}
\affiliation{%
  \institution{[Institution]}
  \city{[City]}
  \country{[Country]}
}
```
Fill in before submission. Single-blind review means names are visible to reviewers.

### 2. Timing Claims — "Two Hours" vs. Session Data
The abstract and case study say "two hours of preparation." The extracted session data shows the primary Claude session started at 02:40 UTC with the first bead created at 19:41 UTC — a ~17-hour span. The "two hours" reflects the author's subjective experience of concentrated preparation during the hackathon event window, not the full session timeline.

**Decision needed:** Is "two hours" the right framing? Options:
- Keep "two hours" — this is the hackathon preparation window as experienced
- Change to reflect the broader session timeline (would strengthen the preparation investment narrative but complicate the "hackathon constraint" framing)
- Add a footnote clarifying that earlier exploration preceded the focused preparation phase

### 3. Claims Strength
The paper hedges appropriately ("suggests," "consistent with," "illustrative rather than definitive"), but reviewers may still push back on:
- **"70% rework time" claim** (Introduction, line 16): Currently attributed to practitioners [huntley2025ralph, yegge2025beads]. This is anecdotal — no formal citation supports this specific number. Consider softening to "substantial" or finding a citation.
- **Context fluency as "novel construct"**: Reviewers may argue this is just "specification writing" by another name. The pedagogical connection (lesson planning) is the strongest differentiator — make sure this comes through.

### 4. Prior Publication Disclosure
The published Substack article covers the same case study. EasyChair may ask about prior publication. The paper adds formalization, literature review, theoretical grounding, and research agenda — substantial new contribution. But you should disclose the Substack article in the submission form if asked.

### 5. Tone Check
The paper aims for "academic but accessible." Read the full PDF and verify:
- Does it capture your voice as formalized for an academic audience?
- Is the culinary analogy effective or does it feel forced?
- Does the conclusion land? ("The code, increasingly, is the easy part.")

## Potential Reviewer Concerns

| Concern | Our Defense |
|---------|-------------|
| Single case study, no controls | Explicitly framed as positioning paper; Section 6 proposes controlled experiments as RQ1 |
| "Just a blog post" | Adds formalization (three phases with defined artifacts), theoretical grounding (backward design, Polanyi), and research agenda with 5 RQs |
| Context fluency is vague | Defined with four concrete components + theoretical grounding; analogized to lesson planning |
| Preparation time impractical | 5.7:1 ratio is for a hackathon; paper acknowledges scaling question as RQ4 |
| Not generalizable | Acknowledged in Limitations subsection; generalization is explicitly future work |

## Submission Checklist

- [ ] Fill in author name, email, affiliation in `main.tex`
- [ ] Read full PDF for tone and accuracy
- [ ] Resolve "two hours" timing question (see §2 above)
- [ ] Check the "70% rework" claim (see §3 above)
- [ ] Build final PDF: `cd paper && latexmk -pdf main.tex`
- [ ] Submit via https://easychair.org/conferences/?conf=vibex2026
  - Title: "Mise en Place for Agentic Coding: Deliberate Preparation as Context Engineering Methodology"
  - Keywords: agentic coding, mise en place, context engineering, vibe coding, context fluency
  - Track: Positioning Paper / Ongoing Research / Vision Paper
  - If asked about prior publication: disclose Substack article as gray literature

## File Inventory

| File | Purpose |
|------|---------|
| `paper/main.tex` | Main document — abstract, metadata, section includes |
| `paper/sections/introduction.tex` | Section 1: Introduction (~350 words) |
| `paper/sections/related-work.tex` | Section 2: Background and Related Work (~490 words) |
| `paper/sections/methodology.tex` | Section 3: The Mise en Place Methodology (~750 words, includes Figure 1) |
| `paper/sections/case-study.tex` | Section 4: Case Study (~700 words, includes Table 1) |
| `paper/sections/context-fluency.tex` | Section 5: Context Fluency (~400 words) |
| `paper/sections/research-agenda.tex` | Section 6: Research Agenda and Conclusion (~370 words) |
| `paper/references.bib` | 16 BibTeX entries |
| `paper/acmart.cls` | ACM document class (local copy) |
| `paper/ACM-Reference-Format.bst` | ACM bibliography style |
| `data/git-timeline.md` | Extracted git commit data |
| `data/beads-metrics.md` | Extracted beads task tracking data |
| `data/session-analysis.md` | Extracted session log analysis |
