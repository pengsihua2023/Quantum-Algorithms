# Table: Representative Quantum Algorithms and Their Core Characteristics

## Purpose
This table provides a structured overview of major quantum algorithm families, their target problems, core ideas, theoretical advantages, assumptions, and practical limitations.

---

| Algorithm / Family | Representative Problem | Core Idea | Claimed Theoretical Advantage | Key Assumptions | Practical Limitations | NISQ Suitability | Fault-Tolerant Requirement |
|---|---|---|---|---|---|---|---|
| Deutsch-Jozsa | Oracle-based decision problem | Quantum interference for global property testing | Separation in oracle setting | Oracle access | Limited practical relevance | Low | No |
| Simon’s algorithm | Hidden XOR mask problem | Periodicity / structure extraction | Exponential oracle separation | Structured oracle model | Mostly conceptual importance | Low | Likely yes for scale |
| Shor’s algorithm | Integer factorization, discrete logarithm | Period finding via QFT | Strong asymptotic speedup | Efficient modular arithmetic, fault tolerance | Very high resource demands | No | Yes |
| Grover’s algorithm | Unstructured search | Amplitude amplification | Quadratic speedup | Oracle model | Oracle construction cost | Limited | Often yes for large-scale use |
| Amplitude amplification | Success boosting | Iterative amplification of target amplitude | Quadratic improvement in success scaling | Reusable quantum procedure | Depends on procedure structure | Limited | Often yes |
| Quantum phase estimation | Eigenvalue estimation | Phase extraction from controlled evolution | Core subroutine with broad impact | Controlled unitary evolution, coherence | Deep circuits, precision cost | Poor | Yes |
| Hamiltonian simulation | Quantum system evolution | Approximate time evolution under Hamiltonian | Potential efficiency for specific systems | Efficient Hamiltonian encoding | State prep, measurement, hardware scale | Limited | Often yes |
| HHL / linear system algorithms | Solving linear systems | Quantum state encoding of solutions | Strong under specific assumptions | Sparsity, condition number, data access assumptions | Input/output bottlenecks | Poor | Often yes |
| Quantum walks | Search, graph problems | Quantum analogue of random walks | Speedups for structured problems | Problem-specific graph structure | Limited broad practicality | Limited | Often yes |
| VQE | Ground-state estimation | Variational circuit + classical optimizer | Heuristic, not universal asymptotic | Ansätze quality, optimizer behavior | Noise, barren plateaus, scaling | Yes | No |
| QAOA | Approximate combinatorial optimization | Alternating problem and mixer unitaries | Problem-dependent / heuristic | Suitable encoding, trainability | Benchmark uncertainty, scaling | Yes | No |
| Quantum optimization methods | Combinatorial optimization | Diverse, exact or heuristic methods | Varies by method | Model-dependent | Strong classical competition | Mixed | Mixed |
| Quantum machine learning-related algorithms | Linear algebra / kernels / classification | Quantum subroutines for data tasks | Sometimes strong under ideal assumptions | Efficient data access, output assumptions | Data loading bottleneck, unclear practical advantage | Mixed | Often yes |

---

## Notes to Fill Later
- Add citations for each row where needed
- Decide whether to separate “quantum machine learning” into multiple rows
- Decide whether to split “quantum simulation” into:
  - Hamiltonian simulation
  - digital simulation
  - chemistry-focused simulation
- Decide whether to add a “cryptographic impact” column
