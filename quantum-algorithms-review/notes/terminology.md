# Terminology Notes

## Goal
Keep terminology consistent across the manuscript.

This file focuses on **preferred wording and usage consistency**, not full conceptual definitions.  
For concept-level distinctions and working definitions, see `concepts.md`.

---

## Preferred Terms
Use these terms consistently unless a specific section requires narrower wording:

- quantum algorithm
- quantum advantage
- theoretical speedup
- practical feasibility
- practical utility
- fault-tolerant quantum computing
- noisy intermediate-scale quantum (NISQ)
- variational quantum algorithm
- quantum-classical hybrid method
- resource estimation
- classical baseline
- algorithm family
- computational model
- input model
- oracle model
- heuristic method
- rigorous result

---

## Terms to Use Carefully
These terms are not forbidden, but they should be used only when the context is precise:

- quantum supremacy
- exponential advantage
- practical speedup
- transformative impact
- real-world utility
- breakthrough
- scalable advantage
- deployable quantum solution

---

## Avoid or Limit
Avoid these expressions unless they are directly supported and contextually necessary:

- revolutionary
- game-changing
- dramatically superior
- clearly better
- will transform industry
- broadly useful in practice
- already proven in real-world settings

---

## Preferred Usage Notes

### quantum advantage
Use with qualification when needed.  
Do not use it as an automatic synonym for practical usefulness.

Preferred:
- quantum advantage under specific assumptions
- theoretical quantum advantage
- empirically demonstrated advantage in a restricted setting

Avoid:
- quantum advantage, therefore practical superiority

---

### theoretical speedup
Use when referring to formal improvements established within a computational model.

Preferred:
- theoretical speedup
- asymptotic advantage
- formal complexity advantage

Avoid:
- speedup in practice  
unless practical benchmarking is actually being discussed.

---

### practical feasibility
Use when discussing realistic implementation constraints such as:
- hardware scale
- noise
- circuit depth
- state preparation
- readout cost
- classical comparison

Preferred:
- practical feasibility
- implementation feasibility
- hardware-constrained feasibility

---

### NISQ
Use the full form at first mention:
**noisy intermediate-scale quantum (NISQ)**

After first mention, use:
- NISQ
- NISQ-era algorithms
- NISQ-compatible methods

Avoid treating NISQ as a claim of usefulness or maturity.

---

### fault-tolerant quantum computing
Use consistently rather than switching randomly among:
- error-corrected quantum computing
- fully fault-tolerant systems
- scalable corrected quantum hardware

You may vary wording when stylistically necessary, but keep “fault-tolerant quantum computing” as the default term.

---

### variational quantum algorithm
Use as the default umbrella term for methods such as VQE and QAOA when speaking at the family level.

Preferred:
- variational quantum algorithm
- variational approach
- hybrid variational method

Avoid switching inconsistently between:
- variational quantum method
- variational quantum framework
- parameterized quantum routine  
unless the distinction is deliberate.

---

### classical baseline
Use when comparing quantum methods against serious classical alternatives.

Preferred:
- classical baseline
- strong classical baseline
- best available classical method

Avoid weak phrases such as:
- classical competitor  
when what is really meant is the benchmarking baseline.

---

## Important Distinctions to Preserve
Keep these distinctions clear throughout the manuscript:

- quantum advantage ≠ practical utility
- theoretical speedup ≠ end-to-end real-world speedup
- NISQ compatibility ≠ demonstrated usefulness
- rigorous result ≠ heuristic promise
- oracle-model improvement ≠ application-level improvement
- influential idea ≠ deployable method

---

## Style Notes
- Avoid using “revolutionary” without strong evidence
- Avoid treating “quantum advantage” and “practical usefulness” as synonyms
- Distinguish clearly between “provable” and “heuristic”
- Prefer precise claims over broad praise
- Use the same term consistently across sections unless variation improves clarity without changing meaning

---

## First-Mention Conventions
At first mention in the manuscript, spell out these terms:

- noisy intermediate-scale quantum (NISQ)
- variational quantum eigensolver (VQE)
- quantum approximate optimization algorithm (QAOA)
- quantum phase estimation (QPE), if abbreviated later
- hidden subgroup problem (HSP), if abbreviated later

---

## Final Reminder
This file is for wording consistency.

If the question is “What does this concept mean?”, check `concepts.md`.  
If the question is “Which term should be used in the manuscript?”, check this file.
