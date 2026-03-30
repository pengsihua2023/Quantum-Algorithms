# Table: Common Assumptions and Limitations in Quantum Algorithm Claims

## Purpose
This table helps keep the review balanced by explicitly listing the assumptions and hidden costs that often underlie claimed speedups.

---

| Algorithm Area | Common Assumption | Why It Matters | Limitation or Risk | Citation Needed |
|---|---|---|---|---|
| Search algorithms | Efficient oracle access | Speedup is defined in oracle/query model | Oracle construction may be costly or unrealistic | [CLASSICAL COMPARISON REF] |
| Factoring / algebraic algorithms | Scalable fault-tolerant quantum hardware | Theoretical advantage depends on large reliable circuits | Current hardware is far from required scale | [RESOURCE ESTIMATION REF] |
| Simulation algorithms | Efficient state preparation and measurement | End-to-end usefulness depends on full workflow | Measurement and readout cost may be substantial | [APPLICATION REF] |
| Linear algebra algorithms | Efficient input encoding | Claimed speedups often depend on data access model | Data loading can erase advantage | [ASSUMPTION / LIMITATION REF] |
| Quantum machine learning | Efficient QRAM-like access or favorable encoding | Many speedup claims rely on idealized assumptions | Practical data pipelines may be bottlenecks | [CRITICAL ASSESSMENT REF] |
| Variational methods | Trainable circuits and good optimization landscapes | Empirical success depends on trainability | Barren plateaus and noise can degrade performance | [TRAINABILITY REF] |
| Optimization algorithms | Problem instances favorable to quantum heuristics | Performance is often instance-dependent | Strong classical heuristics may remain competitive | [CLASSICAL COMPARISON REF] |
| General complexity claims | Asymptotic runtime dominates total cost | Theoretical results often ignore engineering constraints | Constants and hidden overhead may be large | [CITATION NEEDED] |

---

## Notes
Use this table to prevent the manuscript from overstating results.
It is especially useful when revising sections that sound too optimistic.
