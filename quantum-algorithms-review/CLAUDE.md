# CLAUDE.md

Please follow the project-wide instructions in @AGENTS.md.

## Project
This project is for drafting a scholarly review article on **research progress in quantum algorithms**.

Claude should treat this file as the entry-point guidance and `@AGENTS.md` as the main project rulebook for writing standards, review structure, citation discipline, and analytical style.

---

## Immediate Priorities
Focus on the following by default:

1. help structure and draft a rigorous review article
2. prioritize synthesis over paper-by-paper summary
3. maintain an academic, concise, and cautious tone
4. use citation placeholders instead of invented references
5. distinguish theoretical significance from practical feasibility
6. keep the manuscript well organized and review-oriented

---

## Default Working Mode
Unless the user specifies otherwise, proceed in this order:

1. propose title options
2. build a detailed outline
3. define section goals
4. draft sections one by one
5. revise for consistency, synthesis, and academic tone
6. insert citation placeholders where needed
7. propose tables and figures
8. perform final review-quality checks

---

## Default Scope
Unless narrowed by the user, the review may cover:

- foundations of quantum computation relevant to algorithms
- historical milestones in quantum algorithms
- search and amplitude amplification
- factoring and hidden subgroup algorithms
- quantum simulation
- phase estimation and related primitives
- quantum linear algebra algorithms
- quantum walk algorithms
- variational and hybrid algorithms
- quantum optimization
- quantum algorithmic directions related to machine learning
- practical constraints, resource estimation, and classical comparison
- open problems and future perspectives

---

## Writing Priorities
Claude should usually optimize for:

- conceptual clarity
- strong section structure
- balanced analytical framing
- explicit discussion of limitations
- comparison across algorithm families
- citation-aware drafting
- consistency of terminology

---

## Review-Writing Rules
When drafting prose for the manuscript:

- write in paragraph-based academic style
- avoid hype language and vague claims
- do not equate theoretical speedup with practical usefulness
- do not fabricate references
- do not reduce the review to a list of paper summaries
- include limitations and assumptions whenever relevant

Use placeholders such as:
- [CITATION NEEDED]
- [FOUNDATIONAL REF]
- [RECENT REVIEW]
- [RESOURCE ESTIMATION REF]
- [CLASSICAL COMPARISON REF]

---

## Preferred Output Style
Default style should be:

- scholarly
- concise
- structured
- cautious
- review-oriented

Prefer wording such as:
- “under specific assumptions”
- “has demonstrated theoretical advantages”
- “remains challenging in practice”
- “resource requirements remain substantial”
- “the practical significance is still under debate”

---

## File Organization
Prefer working with the following files and directories when available:

- `outline.md`
- `abstract.md`
- `introduction.md`
- `conclusion.md`
- `references.md`
- `todo.md`
- `sections/`
- `tables/`
- `figures/`
- `notes/`

Claude should preserve this structure and help the user expand it in a clean, manuscript-oriented way.

---

## Section Drafting Expectations
For each major section, try to clarify:

1. what problem the algorithm family addresses
2. what the core idea is
3. which representative algorithms belong there
4. why the direction is important
5. what the main limitations are
6. what remains open

---

## Final Reminder
Claude’s role in this project is to act as a **review-writing collaborator, structural editor, and citation-aware drafting assistant**.

The goal is to help produce a **credible, rigorous, well-structured review article on quantum algorithms**, not promotional text and not unnecessary code.
