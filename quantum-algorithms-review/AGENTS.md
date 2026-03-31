# AGENTS.md
## Mission
The goal of this project is to produce a high-quality review article on **research progress in quantum algorithms**.

All agents working in this project must prioritize the writing of a rigorous, well-structured, evidence-aware scholarly review. The primary objective is not to generate code, but to support literature synthesis, conceptual organization, academic drafting, section development, figure and table planning, and citation-aware revision.

This project follows a **document-first**, **evidence-based**, **traceable**, and **scientifically cautious** workflow.

---

## Scope of Work
Agents in this project are expected to help with the following tasks:

1. Design the overall structure of the review article
2. Organize the historical development of quantum algorithms
3. Classify and compare major quantum algorithm families
4. Draft the abstract, introduction, body sections, conclusion, and outlook
5. Propose tables, figures, timelines, and taxonomy diagrams
6. Improve academic style and review-style synthesis
7. Flag unsupported claims and insert citation placeholders
8. Distinguish established results from speculative future directions

---

## Core Writing Goal
The final output should read like a serious scholarly review article rather than a collection of disconnected notes or paper summaries.

The manuscript should aim to be:

- structurally coherent
- conceptually organized
- analytically balanced
- academically written
- citation-aware
- cautious in claims
- clear about both progress and limitations

---

## Preferred Topic Framing
Unless the user specifies otherwise, the review on quantum algorithms should be organized around the following layers:

### Level 1: Foundations
- basic principles of quantum computation relevant to algorithms
- superposition, interference, entanglement
- the circuit model
- complexity-theoretic perspectives
- quantum advantage under explicit assumptions

### Level 2: Major Quantum Algorithm Families
- search algorithms
- amplitude amplification and estimation
- factoring and hidden subgroup problem algorithms
- quantum simulation algorithms
- phase estimation and related subroutines
- quantum linear algebra algorithms
- quantum walk algorithms
- variational and hybrid algorithms
- quantum optimization algorithms
- quantum algorithms related to machine learning
- other emerging algorithmic directions

### Level 3: Practical Constraints and Current Reality
- NISQ-era limitations
- error correction and fault tolerance
- hardware constraints
- resource estimation
- data access assumptions
- the difference between theoretical and practical advantage

### Level 4: Open Problems and Future Directions
- scalability
- noise robustness
- realistic benchmarking
- fair comparison against classical methods
- domain-specific applicability
- conditions for practical quantum advantage

---

## Document-First Policy
Agents should prioritize producing the following materials before writing code:

1. review outline
2. section-by-section writing plan
3. literature classification notes
4. figure and table concepts
5. abstract and conclusion drafts
6. citation placeholder maps
7. final revision checklists
8. section restructuring proposals

Do not generate unnecessary code.

Code should only be proposed when it clearly supports the writing process, such as:

- organizing bibliographic metadata
- cleaning literature notes
- generating tables
- drafting timelines
- supporting figure preparation

Even when code is needed, it should be minimal, reproducible, and directly in service of the manuscript.

---

## Rules for Scientific Writing

### 1. Separate fact from interpretation
Agents must clearly distinguish:
- established results
- review-level interpretation
- forward-looking speculation

Do not present speculation as settled fact.

### 2. Avoid exaggerated language
Avoid expressions such as:
- revolutionary
- definitive
- solves all limitations
- proves broad superiority
- game-changing

Prefer language such as:
- shows promise
- demonstrates theoretical advantages under specific assumptions
- remains challenging in practice
- may be useful in selected settings
- is still under active investigation

### 3. Prefer precise claims
Do not write:
“Quantum algorithms are much better than classical algorithms.”

Prefer:
“Some quantum algorithms provide provable theoretical speedups for specific problem classes under explicit computational assumptions, although their practical utility depends on hardware scale, input models, and resource constraints.”

### 4. Always include limitations
For each major algorithm family, try to discuss:
- what problem it addresses
- how it works at a high level
- why it matters
- what its limitations are
- what remains unresolved

### 5. Maintain academic tone
The style should be:
- restrained
- analytical
- formal
- concise
- non-promotional

---

## Expected Article Structure
Unless the user requests a different structure, default to the following review format:

1. Title  
2. Abstract  
3. Keywords  
4. Introduction  
5. Foundations of Quantum Computation Relevant to Algorithms  
6. Historical Development of Quantum Algorithms  
7. Major Classes of Quantum Algorithms  
   - 7.1 Search and amplitude amplification
   - 7.2 Factoring and hidden subgroup problems
   - 7.3 Quantum simulation
   - 7.4 Quantum linear algebra methods
   - 7.5 Variational and hybrid quantum algorithms
   - 7.6 Quantum optimization approaches
   - 7.7 Other emerging directions
8. Practical Challenges in Realizing Quantum Algorithmic Advantage  
9. Comparison with Classical Algorithms  
10. Open Problems and Future Perspectives  
11. Conclusion  
12. References  

---

## Section-Level Guidance

### Abstract
The abstract should include:
- background
- scope
- classification logic
- major conclusions
- practical challenges
- future outlook

It should not read like a list of papers.

### Introduction
The introduction should explain:
- why quantum algorithms matter
- why the field deserves a review
- why theoretical progress and practical feasibility must be discussed together
- how the review is organized

### Main Body
The main body should avoid a paper-by-paper summary style.

Prefer:
- classification by problem type
- classification by algorithmic mechanism
- historical development with interpretation
- comparison across families
- explicit discussion of assumptions and limitations

### Conclusion and Outlook
The conclusion should:
- summarize the main developments
- identify mature and influential directions
- highlight practical barriers
- offer a cautious future outlook

---

## Literature Handling Policy
When working with literature, agents must:

1. identify foundational, representative, and recent review references
2. explain how each reference fits into the development of the field
3. avoid excessive citation stacking without synthesis
4. use citation placeholders when the exact source is not yet available
5. never fabricate references

Recommended placeholders:
- [CITATION NEEDED]
- [FOUNDATIONAL REF]
- [RECENT REVIEW]
- [RESOURCE ESTIMATION REF]
- [CLASSICAL COMPARISON REF]

---

## Citation and Traceability Rules
Strong factual statements should be traceable to literature whenever possible.

Examples of claims that usually require citation:
- first introduction of a major algorithm
- claims about formal complexity advantage
- claims about cryptographic significance
- claims about hardware feasibility or resource demands
- claims about current research trends

If a reliable source is not yet available, insert a citation placeholder instead of inventing one.

---

## Comparison Rules
When comparing different quantum algorithms, prefer the following dimensions:

- problem class
- high-level mechanism
- type of theoretical advantage
- assumptions on input or access model
- circuit depth and qubit requirements
- suitability for NISQ devices
- dependence on fault tolerance
- strength of classical baselines
- practical applicability
- key limitations

Do not use vague language such as “better” or “more advanced” without specifying in what sense.

---

## Preferred Output Style
Default output style should be:

- academic
- concise
- clearly structured
- paragraph-based
- cautious in claims
- suitable for review writing

When producing English prose, aim for a journal-style review tone.

When producing shorter materials such as outlines or notes, keep them clear and organized, but still consistent with scholarly writing.

---

## What Agents Should Do
Agents should prioritize the following:

- build the review structure
- synthesize literature into categories and trajectories
- improve draft sections into review-style prose
- compress repetitive writing
- identify missing limitations or missing comparisons
- insert citation placeholders where needed
- propose figures and tables that clarify the argument
- improve transitions and section logic
- strengthen analytical framing

---

## What Agents Should Not Do
Agents must not:

- fabricate citations
- fabricate results
- overstate practical quantum advantage
- ignore strong classical baselines
- write promotional or hype-driven language
- confuse theoretical speedup with real-world usability
- generate large unrelated code blocks
- reduce the manuscript to a sequence of paper summaries

---

## Figure and Table Guidance

### Figures
Preferred figures include:
- timeline of quantum algorithm development
- taxonomy of algorithm families
- theoretical advantage vs practical feasibility diagram
- NISQ vs fault-tolerant landscape
- evaluation framework for quantum algorithm claims

### Tables
Preferred tables include:
- representative algorithms and problem classes
- assumptions and limitations across algorithm families
- NISQ suitability vs fault-tolerant requirements
- milestone references and their significance
- comparison with classical methods

Figures and tables must support the review’s analytical structure rather than serve as decoration.

---

## Review Quality Checklist
Before delivering any section draft, agents should check:

- Does this section synthesize rather than merely list?
- Does it explain why the topic matters?
- Does it include limitations?
- Does it avoid exaggerated claims?
- Does it identify places that need citations?
- Is the terminology consistent with the rest of the manuscript?
- Does it read like a review article?

---

## Default Working Mode
If the user simply asks for help writing the review, default to the following order:

1. propose title options
2. generate a detailed outline
3. define section goals
4. draft sections one by one
5. revise the manuscript for consistency and review style
6. insert citation placeholders
7. propose figures and tables
8. perform final review-quality checks

---

## Title Preferences
Preferred title style:

- A Review of Recent Progress in Quantum Algorithms
- Quantum Algorithms: Foundations, Advances, and Challenges
- Research Progress in Quantum Algorithms: From Theoretical Speedups to Practical Constraints
- Quantum Algorithms in Review: Major Developments, Applications, and Open Challenges

Titles should be clear, scholarly, and not overly broad or promotional.

---

## Final Principle
All agents must remember the following:

This project is centered on producing a credible, rigorous, well-structured review article on quantum algorithms.

The task is not to advertise quantum computing, but to explain the field with analytical balance, conceptual clarity, and scientific caution.
