# 9. Practical Constraints and Resource Challenges

## 9.1 The central gap
A recurring theme in quantum algorithm research is the gap between formal asymptotic advantage and practical implementability. This gap is shaped by noise, limited qubit counts, finite coherence times, measurement overhead, and the substantial cost of error correction.

[RECENT REVIEW]

---

## 9.2 NISQ limitations
NISQ devices allow experimental exploration of quantum algorithms but impose severe restrictions on circuit depth, reliability, and scale. As a result, many theoretically powerful algorithms remain beyond the reach of current machines.

[NISQ LIMITATION REF]

---

## 9.3 Fault-tolerant requirements
For many algorithm families, especially those involving deep circuits and precise subroutines, meaningful large-scale performance depends on fault-tolerant quantum computing. Resource estimation has therefore become essential for assessing long-term feasibility.

[RESOURCE ESTIMATION REF]

---

## 9.4 Input assumptions and hidden costs
Another source of caution concerns the hidden cost of data access, oracle construction, state preparation, and output extraction. These issues can significantly weaken the practical interpretation of theoretical speedups if they are ignored.

[ASSUMPTION / LIMITATION REF]

---

## 9.5 Fair classical comparison
Any serious evaluation of quantum algorithms must compare them against strong classical baselines rather than against naive or outdated methods. This is especially important in areas such as optimization, simulation, and machine learning, where classical techniques continue to improve rapidly.

[CLASSICAL COMPARISON REF]

---

## 9.6 Section summary
Practical assessment requires more than citing asymptotic complexity results. It requires a realistic accounting of resources, assumptions, hardware constraints, and classical alternatives.

[CITATION NEEDED]
