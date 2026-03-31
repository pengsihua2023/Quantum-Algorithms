# Concepts

## Purpose
This file records the core concepts used throughout the review article.

Its purpose is to:
- keep conceptual definitions consistent
- clarify boundaries between related terms
- prevent drift in meaning across sections
- support more precise review-style writing
- provide a shared conceptual reference for drafting and revision

This is not a manuscript section. It is an internal concept guide for the project.

---

## 1. Quantum Algorithm

### Working definition
A quantum algorithm is a computational procedure that uses quantum-mechanical operations, typically within a formal quantum computational model, to solve a problem or estimate a quantity of interest.

### Why it matters in this review
This review is centered on the development, classification, and evaluation of quantum algorithms. A clear working definition helps distinguish genuine algorithmic contributions from broader discussions of quantum hardware, architecture, or quantum information theory.

### Boundary notes
- Not every result in quantum computing is a quantum algorithm
- Hardware demonstrations are not automatically algorithmic advances
- A quantum protocol is not always the same as a quantum algorithm
- Some hybrid methods count as quantum algorithms if the quantum component is essential to the computational procedure

### Caution
Do not use the term so broadly that it includes all quantum-computing-related work.

### Citation status
[CITATION NEEDED]

---

## 2. Quantum Advantage

### Working definition
In this review, “quantum advantage” refers broadly to a situation in which a quantum computational approach outperforms known classical approaches under a specified comparison framework.

### Why it matters in this review
This is one of the most central concepts in the manuscript, but also one of the most easily overstated or used ambiguously.

### Boundary notes
Quantum advantage may refer to different things depending on context:
- formal complexity-theoretic advantage
- query complexity advantage
- asymptotic runtime advantage
- empirical performance advantage
- application-level usefulness

These are not interchangeable.

### Caution
Do not use “quantum advantage” as a synonym for present-day practical superiority.
Always clarify what kind of advantage is meant.

### Citation status
[CITATION NEEDED]

---

## 3. Theoretical Speedup

### Working definition
A theoretical speedup refers to an improvement established within a formal computational model, usually expressed in asymptotic complexity terms.

### Why it matters in this review
Many of the most famous quantum algorithms are important because of formal speedups, not because they have already demonstrated immediate practical value.

### Boundary notes
- A theoretical speedup may depend on oracle assumptions, input structure, or idealized access models
- A theoretical speedup does not automatically imply lower end-to-end real-world cost
- Strong asymptotic scaling may coexist with very large constants or resource overhead

### Caution
When discussing speedup, specify the model and assumptions whenever possible.

### Citation status
[CITATION NEEDED]

---

## 4. Practical Feasibility

### Working definition
Practical feasibility refers to whether an algorithm can be meaningfully implemented under realistic hardware, resource, noise, and workflow constraints.

### Why it matters in this review
A major theme of the review is the gap between formal algorithmic strength and realistic implementation.

### Boundary notes
Practical feasibility depends on:
- hardware scale
- noise levels
- coherence time
- error correction status
- circuit depth
- state preparation
- measurement overhead
- comparison with classical alternatives

### Caution
Do not treat theoretical interest and practical feasibility as equivalent.

### Citation status
[CITATION NEEDED]

---

## 5. NISQ

### Working definition
NISQ stands for noisy intermediate-scale quantum, referring to a regime of quantum computing with limited qubit counts, noise, and restricted circuit depth, without full fault tolerance.

### Why it matters in this review
Many modern algorithmic proposals, especially variational and hybrid methods, are motivated by NISQ-era hardware limitations.

### Boundary notes
- NISQ algorithms are often evaluated differently from long-term fault-tolerant algorithms
- NISQ compatibility does not imply strong formal guarantees
- Some NISQ approaches are heuristic rather than asymptotically superior

### Caution
Do not treat “NISQ algorithm” as a label of proven usefulness; it mainly indicates near-term hardware orientation.

### Citation status
[RECENT REVIEW]

---

## 6. Fault-Tolerant Quantum Computing

### Working definition
Fault-tolerant quantum computing refers to large-scale quantum computation supported by error correction, enabling reliable execution of deep circuits over long computational times.

### Why it matters in this review
Many foundational algorithms, including some of the most theoretically powerful ones, depend on fault-tolerant operation for meaningful realization at scale.

### Boundary notes
- Fault-tolerant feasibility is not the same as current hardware availability
- Resource demands are often extremely large
- Many algorithm families should be interpreted differently depending on whether they are NISQ-oriented or fault-tolerant-oriented

### Caution
Do not casually imply that a theoretically important algorithm is practically realizable without discussing fault-tolerant requirements.

### Citation status
[RESOURCE ESTIMATION REF]

---

## 7. Oracle Model

### Working definition
An oracle model is a formal framework in which part of the problem is accessed through a black-box query operation.

### Why it matters in this review
Several key quantum algorithms, including Grover-type algorithms, are most naturally described and analyzed in oracle or query-complexity terms.

### Boundary notes
- Oracle results can be highly significant theoretically
- The cost of building or implementing an oracle may be ignored in abstract analysis
- Practical interpretation depends on whether oracle access is realistic in a given application

### Caution
Do not present oracle-based speedups as full real-world speedups without qualification.

### Citation status
[CITATION NEEDED]

---

## 8. Resource Estimation

### Working definition
Resource estimation refers to the analysis of what computational resources are required to implement a quantum algorithm, including qubit counts, logical qubits, gate counts, circuit depth, runtime, and error-correction overhead.

### Why it matters in this review
Resource estimation is essential for bridging the gap between abstract algorithms and realistic implementation.

### Boundary notes
- A strong algorithmic result may still be impractical if resource requirements are prohibitive
- Resource estimates often change as hardware assumptions and error-correction schemes evolve
- Resource estimation is especially important for fault-tolerant algorithms

### Caution
Do not discuss long-term practical relevance without considering resource cost.

### Citation status
[RESOURCE ESTIMATION REF]

---

## 9. Classical Baseline

### Working definition
A classical baseline is the strongest relevant classical method used for comparison when evaluating the significance of a quantum algorithm.

### Why it matters in this review
Quantum algorithms should not be evaluated against weak, naive, or outdated classical methods.

### Boundary notes
- Fair comparison requires identifying serious classical competitors
- Practical quantum relevance depends heavily on baseline strength
- In some areas, modern classical heuristics are extremely strong

### Caution
Do not discuss quantum improvement in isolation from the best available classical alternatives.

### Citation status
[CLASSICAL COMPARISON REF]

---

## 10. Variational Quantum Algorithm

### Working definition
A variational quantum algorithm is a hybrid quantum-classical method that uses a parameterized quantum circuit and a classical optimization loop.

### Why it matters in this review
Variational algorithms are among the most visible NISQ-era quantum algorithm families.

### Boundary notes
- They are often practically motivated rather than supported by strong asymptotic guarantees
- Performance depends on ansatz design, optimization behavior, and noise robustness
- VQE and QAOA are representative but not exhaustive examples

### Caution
Do not present variational methods as already validated sources of broad practical advantage.

### Citation status
[RECENT REVIEW]

---

## 11. Quantum Simulation

### Working definition
Quantum simulation refers to the use of quantum computation to model the behavior or evolution of quantum systems.

### Why it matters in this review
Quantum simulation is widely regarded as one of the most compelling long-term applications of quantum algorithms.

### Boundary notes
- Quantum simulation may refer to Hamiltonian simulation, digital simulation, chemistry simulation, or broader modeling tasks
- It is one of the most application-oriented algorithmic areas
- Practical usefulness still depends on hardware and measurement constraints

### Caution
Do not treat all simulation claims as equally mature or experimentally accessible.

### Citation status
[FOUNDATIONAL REF]

---

## 12. Quantum Optimization

### Working definition
Quantum optimization refers to algorithmic approaches that use quantum computation to solve or approximate optimization problems.

### Why it matters in this review
Optimization is a major claimed application area, but one in which the difference between promise and demonstrated advantage remains especially important.

### Boundary notes
- Some optimization algorithms are rigorous, others heuristic
- Optimization claims are highly sensitive to benchmarking choices
- Strong classical heuristics often make fair comparison difficult

### Caution
Do not describe optimization-oriented quantum algorithms as broadly superior without strong evidence.

### Citation status
[CITATION NEEDED]

---

## 13. Quantum Machine Learning-Related Algorithms

### Working definition
This term refers to quantum algorithms proposed for tasks related to data analysis, learning, classification, feature mapping, optimization, or related machine learning workflows.

### Why it matters in this review
This is a highly visible area, but also one in which claims of speedup or usefulness are often sensitive to assumptions.

### Boundary notes
- Some proposals rely heavily on idealized data-loading assumptions
- Some are better understood as quantum linear algebra or kernel methods
- Practical significance remains debated in many cases

### Caution
Avoid broad claims that quantum machine learning has already established general practical superiority.

### Citation status
[CRITICAL ASSESSMENT REF]

---

## 14. Heuristic vs Rigorous Quantum Algorithms

### Working definition
A rigorous quantum algorithm comes with formal guarantees under an explicit model, while a heuristic quantum algorithm is motivated by empirical promise or intuitive reasoning without equally strong guarantees.

### Why it matters in this review
A major analytical distinction in the paper is the difference between provable algorithmic results and practically motivated but less formally grounded methods.

### Boundary notes
- This distinction is especially important for variational and optimization-oriented methods
- Heuristic does not mean unimportant
- Rigorous does not mean practically realizable

### Caution
Do not collapse these categories into a single notion of “progress.”

### Citation status
[CITATION NEEDED]

---

## 15. Working Conceptual Distinctions Used in This Review

### Distinction A
**Quantum advantage** is not the same as **practical utility**

### Distinction B
**Theoretical speedup** is not the same as **end-to-end real-world speedup**

### Distinction C
**NISQ compatibility** is not the same as **demonstrated usefulness**

### Distinction D
**Rigorous algorithmic result** is not the same as **heuristic promise**

### Distinction E
**Oracle-model improvement** is not automatically **application-level improvement**

### Distinction F
**Influential algorithmic idea** is not the same as **currently deployable technology**

These distinctions should remain visible throughout the manuscript.

---

## 16. Project-Level Usage Notes

### Preferred use of “quantum advantage”
Use with qualification unless the context is already precise.

### Preferred use of “practical”
Use only when hardware, workflow, or benchmark realism is actually relevant.

### Preferred use of “important”
Whenever possible, explain *why* a result is important:
- foundational significance
- cryptographic relevance
- methodological influence
- application potential
- benchmarking implications

### Preferred use of “recent progress”
Do not treat all new work as equal progress; distinguish:
- conceptual breakthroughs
- refinements
- resource-aware improvements
- critical reassessments
- application-driven developments

---

## 17. Concepts That May Need Expansion Later
- BQP
- query complexity
- amplitude estimation
- Hamiltonian simulation
- quantum walk
- QRAM assumptions
- trainability
- barren plateaus
- logical vs physical qubits
- utility-scale quantum computing

---

## 18. Final Reminder
This file is meant to stabilize the conceptual language of the review.

When drafting sections, prefer these definitions and distinctions unless there is a clear reason to narrow or modify them in context.
