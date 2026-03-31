
# Quantum Algorithms Review Project

A Claude Code project for drafting a review article on **research progress in quantum algorithms**.

---

## Project Goal
This project is designed to support the writing of a scholarly review article on quantum algorithms, with emphasis on:

- foundational ideas
- landmark algorithms
- major modern algorithm families
- practical limitations in the NISQ era
- fault-tolerant prospects
- open challenges and future directions

The project follows a **document-first** workflow: prioritize outlines, section drafts, synthesis, comparison, and citation-aware writing over unnecessary coding.

---

## Core Files

### `AGENTS.md`
Defines the overall project rules and agent behavior:
- academic tone
- evidence-based writing
- no fabricated citations
- cautious claims
- strong focus on synthesis rather than literature stacking

### `CLAUDE.md`
Defines how Claude should work inside this project:
- preferred workflow
- default review scope
- writing style
- citation placeholders
- output conventions
- quality checks

---

## Suggested Project Structure

```text
your-project/
├─ README.md
├─ AGENTS.md
├─ CLAUDE.md
├─ outline.md
├─ abstract.md
├─ introduction.md
├─ conclusion.md
├─ references.md
├─ todo.md
├─ sections/
│  ├─ 01_foundations.md
│  ├─ 02_historical_milestones.md
│  ├─ 03_search_algorithms.md
│  ├─ 04_factoring_and_hsp.md
│  ├─ 05_quantum_simulation.md
│  ├─ 06_quantum_linear_algebra.md
│  ├─ 07_variational_algorithms.md
│  ├─ 08_quantum_optimization.md
│  ├─ 09_practical_constraints.md
│  ├─ 10_classical_comparison.md
│  └─ 11_future_directions.md
├─ tables/
│  ├─ algorithm_comparison_table.md
│  ├─ milestone_papers_table.md
│  └─ nisq_vs_fault_tolerant_table.md
├─ figures/
│  ├─ figure_ideas.md
│  └─ captions.md
└─ notes/
   ├─ reading_notes.md
   ├─ concepts.md
   └─ terminology.md
````

---

## Recommended Writing Workflow

### Step 1. Define the article title

Start with 3–5 possible review titles and choose one.

### Step 2. Build the outline

Create a detailed outline with section and subsection headings.

### Step 3. Draft section goals

For each section, write:

* what it covers
* why it matters
* what key papers or concepts belong there
* what limitations should be discussed

### Step 4. Draft the paper section by section

Suggested order:

1. Introduction
2. Foundations
3. Historical milestones
4. Major algorithm families
5. Practical constraints
6. Comparison with classical methods
7. Open problems and outlook
8. Conclusion

### Step 5. Add citation placeholders

Where exact sources are not yet inserted, use:

* [CITATION NEEDED]
* [FOUNDATIONAL REF]
* [RECENT REVIEW]
* [RESOURCE ESTIMATION REF]

### Step 6. Unify style

After drafting, revise the whole article to ensure:

* consistent terminology
* balanced tone
* concise academic language
* smooth transitions between sections

---

## Default Review Scope

Unless otherwise specified, the review may include:

### Foundations

* superposition
* entanglement
* interference
* circuit model
* algorithmic complexity perspective

### Landmark algorithms

* Deutsch-Jozsa
* Simon
* Shor
* Grover
* Quantum Phase Estimation
* Amplitude Amplification / Estimation

### Major modern areas

* search algorithms
* hidden subgroup problem
* quantum simulation
* Hamiltonian simulation
* quantum linear system algorithms
* quantum walks
* variational quantum algorithms
* quantum optimization
* quantum algorithmic directions related to machine learning

### Practical reality

* NISQ constraints
* noise and error accumulation
* resource overhead
* classical baselines
* fault-tolerant requirements
* practical quantum advantage vs theoretical speedup

---

## Writing Principles

### 1. Be analytical, not promotional

Do not describe quantum algorithms as universally transformative without qualification.

### 2. Separate theory from practice

A proven theoretical speedup does not automatically imply present-day practical superiority.

### 3. Emphasize comparison

Each major algorithm family should ideally discuss:

* problem type
* key mechanism
* theoretical advantage
* assumptions
* practical limitations
* comparison to classical methods

### 4. Do not fabricate references

If a source is missing, mark the place with a citation placeholder.

### 5. Avoid paper-by-paper listing

The review should synthesize literature into categories, trajectories, and open questions.

---

## Style Preferences

Preferred style:

* scholarly
* clear
* concise
* structured
* cautious in claims

Avoid:

* hype language
* vague claims
* overly casual explanations
* unsupported “breakthrough” statements

Prefer phrases like:

* “under specific assumptions”
* “has demonstrated theoretical advantages”
* “remains challenging in practice”
* “resource requirements remain substantial”
* “the extent of practical benefit is still under active investigation”

---

## Recommended Tables and Figures

### Tables

* representative quantum algorithms and their problem domains
* theoretical speedups and assumptions
* NISQ suitability vs fault-tolerant requirement
* comparison with classical baselines
* milestone papers and their significance

### Figures

* timeline of quantum algorithm development
* taxonomy of algorithm families
* map of theoretical advantage vs practical feasibility
* NISQ vs fault-tolerant landscape

---

## Section Drafting Template

A useful template for each major section:

1. **What problem does this algorithm family address?**
2. **What is the core idea?**
3. **What are the representative algorithms?**
4. **Why was this direction influential?**
5. **What are the main limitations?**
6. **What are the most important recent developments?**
7. **What remains open?**

---

## Quality Checklist

Before considering a section complete, check:

* Does it synthesize rather than merely list?
* Does it explain why this direction matters?
* Does it mention limitations?
* Does it avoid exaggerated claims?
* Does it mark unsupported statements with citation placeholders?
* Is the style consistent with a review article?

---

## Example Tasks for Claude

Good tasks to ask Claude in this project:

* “Draft a detailed outline for this review.”
* “Rewrite this paragraph in a more academic review style.”
* “Summarize the development of Grover-type algorithms.”
* “Compare Shor’s algorithm and variational algorithms in review style.”
* “Write a conclusion section with a cautious outlook.”
* “Find places in this section that need citations.”
* “Turn my rough notes into a polished subsection.”

---

## Final Objective

The final output should read like a serious review article:

* well organized
* literature aware
* conceptually clear
* balanced in judgment
* useful to researchers and advanced students

```


