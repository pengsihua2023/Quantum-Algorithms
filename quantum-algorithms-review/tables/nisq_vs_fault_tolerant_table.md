# Table: NISQ-Era Algorithms vs Fault-Tolerant Quantum Algorithms

## Purpose
This table clarifies the difference between algorithm classes that are mainly discussed in near-term noisy hardware settings and those that depend on large-scale fault-tolerant quantum computing.

---

| Dimension | NISQ-Oriented Algorithms | Fault-Tolerant-Oriented Algorithms |
|---|---|---|
| Typical examples | VQE, QAOA, shallow variational circuits | Shor, large-scale phase estimation, deep simulation algorithms |
| Hardware assumptions | Noisy, limited qubits, short coherence time | Error-corrected logical qubits, scalable quantum hardware |
| Circuit depth | Typically shallow to moderate | Often deep |
| Goal | Near-term heuristic usefulness | Long-term rigorous large-scale quantum computation |
| Error tolerance | Must cope directly with noise | Built on formal error correction |
| Theoretical guarantees | Often weaker or heuristic | Often stronger in formal complexity terms |
| Benchmarking challenge | Strong classical baselines, noisy output | Resource estimation, implementation cost |
| Main strength | Hardware accessibility | Stronger theoretical computational power |
| Main weakness | Uncertain scalability and advantage | Extremely high resource requirements |
| Typical evaluation style | Empirical / benchmark-driven | Complexity-theoretic + resource-estimation-driven |

---

## Interpretation Notes
- The distinction is not absolute; some methods may sit between these categories
- Some NISQ approaches may evolve into more scalable versions
- Some fault-tolerant algorithms may inspire approximate near-term variants

---

## Draft Paragraph Use
This table can support the section discussing:
- practical constraints
- the theory-practice gap
- why different quantum algorithm families are evaluated differently
