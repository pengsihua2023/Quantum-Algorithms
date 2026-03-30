# Figure Ideas

## Figure 1. Timeline of Major Quantum Algorithm Milestones
### Purpose
Show the historical evolution of major quantum algorithmic ideas.

### Possible contents
- Deutsch-Jozsa
- Simon
- Shor
- Grover
- Phase estimation
- Amplitude amplification
- Quantum walks
- Hamiltonian simulation
- HHL
- VQE
- QAOA
- Recent resource-estimation / benchmarking era

### Why useful
This figure helps readers quickly understand that the field did not emerge all at once but expanded through multiple conceptual phases.

---

## Figure 2. Taxonomy of Quantum Algorithm Families
### Purpose
Present a classification map of major algorithm families.

### Possible branches
- Search and query algorithms
- Algebraic / hidden subgroup algorithms
- Simulation algorithms
- Linear algebra algorithms
- Quantum walk algorithms
- Variational / hybrid algorithms
- Optimization algorithms
- Machine-learning-related algorithms
- Other emerging directions

### Why useful
This figure provides structural clarity and makes the review easier to navigate.

---

## Figure 3. Theoretical Advantage vs Practical Feasibility
### Purpose
Visually separate strong asymptotic results from near-term implementability.

### Suggested axes
- X-axis: practical feasibility / hardware accessibility
- Y-axis: strength of theoretical advantage

### Possible placement examples
- Shor: high theoretical significance, low current feasibility
- Grover: clear theory, moderate practical dependence on oracle model
- VQE/QAOA: higher near-term feasibility, weaker formal guarantees
- Quantum simulation: strong long-term application promise, mixed near-term feasibility

### Why useful
This figure helps the paper maintain a balanced tone and avoids treating all algorithm families as equivalent.

---

## Figure 4. NISQ vs Fault-Tolerant Algorithm Landscape
### Purpose
Show the separation between near-term and long-term algorithmic paradigms.

### Possible contents
Left side:
- variational methods
- shallow hybrid circuits
- heuristic near-term approaches

Right side:
- Shor
- deep phase-estimation-based algorithms
- large-scale simulation
- precise algebraic algorithms

Center band:
- approaches that may partially bridge both worlds

### Why useful
This figure supports discussion of practical constraints and strategic research directions.

---

## Figure 5. Evaluation Framework for Quantum Algorithm Claims
### Purpose
Show how to evaluate a quantum algorithm claim in a disciplined way.

### Possible flow
Claimed speedup  
→ assumptions  
→ input model  
→ circuit depth / qubit cost  
→ noise / error tolerance  
→ classical baseline comparison  
→ realistic applicability

### Why useful
This figure can reinforce the review’s methodological stance and improve analytical depth.

---

## Optional Figure 6. Relationship Among Core Algorithmic Building Blocks
### Purpose
Show how key subroutines connect to broader algorithm families.

### Possible links
- Phase estimation → factoring, simulation, eigenvalue tasks
- Amplitude amplification → search, estimation, success boosting
- Hamiltonian simulation → physics and chemistry applications
- Variational loops → optimization and near-term chemistry tasks

### Why useful
This figure helps readers see that some techniques are reusable primitives, not isolated results.
