# DOE Genesis Mission Phase I Proposal
## DE-FOA-0003612 | Topic 7 – Discovering Quantum Algorithms with AI
### Focus Area C – Hybrid Quantum-Classical Optimization Algorithms (BES)

---

## COVER PAGE

| Field | Entry |
|---|---|
| **Project Title** | Agentic AI for Hybrid Quantum-Classical Optimization of Electrode Materials Discovery for Contaminant Removal |
| **FOA Number** | DE-FOA-0003612 |
| **Topic** | 7 – Discovering Quantum Algorithms with AI |
| **Focus Area** | C – Hybrid Quantum-Classical Optimization Algorithms (BES) |
| **Phase** | Phase I |
| **Project Period** | 9 months |
| **Requested Budget** | [TBD within $500,000–$750,000] |
| **Lead Institution** | [University / IHE — to be confirmed] |
| **Principal Investigator** | [PI Name, Title, Department] |
| **Co-Investigator(s)** | [Co-PI 1 – Quantum Chemistry / Materials, Co-PI 2 – Hybrid QC Methods] |
| **Partner Institutions** | [DOE National Laboratory or Scientific User Facility]; [Industry Partner] |
| **Submission Date** | On or before April 28, 2026 |

---

## ABSTRACT

We propose to design, implement, and benchmark a reproducible AI-guided hybrid quantum-classical workflow for electrode material discovery targeting electrochemical contaminant removal. An agentic orchestration layer will route computational tasks—across classical electronic-structure methods, hybrid quantum-classical routines, and uncertainty-aware surrogate models—under a constrained compute budget. Rather than treating quantum-classical solvers as isolated demonstrations, the workflow treats **the campaign-level policy itself** as the object of AI optimization: deciding what to compute, at what fidelity, and on which platform. Phase I will deliver a benchmarked prototype workflow, a quantitative ablation study measuring AI advantage relative to strong baselines, a prioritized candidate set for follow-up validation, and a Phase II scaling roadmap. This work directly addresses Topic 7C requirements for agentic AI workflows in quantum chemistry and materials science, AI-driven surrogate models for many-body simulation acceleration, and distributed execution across application-relevant platforms.

---

## PROJECT NARRATIVE

*(5 pages of technical information; figures, tables, and charts count toward this limit.)*

---

### 1. Background and Significance

#### 1.1 Scientific Motivation and National Need

Persistent chemical contaminants—including PFAS compounds, nitrates, heavy-metal complexes, and halogenated organics—present a sustained challenge to water quality and environmental remediation at DOE and national-interest sites. Electrochemical destruction and capture using tailored electrode materials offer a pathway to selective, energy-efficient treatment, but progress is bottlenecked by the slow pace at which candidate electrode materials can be identified, screened, and prioritized for experimental validation. The relevant performance descriptors—adsorption free energy, redox potential, electrochemical stability window, reaction-pathway selectivity, and surface-interaction specificity—depend on coupled electronic-structure and surface-reaction behavior that cannot be reliably captured by empirical rules or low-fidelity heuristics alone.

The design space is combinatorial. Transition-metal oxides, nitrides, carbides, and functionalized two-dimensional materials each present a large composition-and-structure space, and performance is highly sensitive to surface termination, adsorbate configuration, and operating conditions. Exhaustive high-fidelity quantum chemistry across this space is computationally intractable. Static screening hierarchies—applying cheap filters first, expensive validation last—are widely used but suffer from early rejection of promising but computationally challenging candidates, and from excessive resource expenditure on low-value candidates that pass coarse filters.

#### 1.2 The Computational Bottleneck

The core limitation is not merely computational cost, but the **absence of adaptive decision logic** that integrates prior simulation evidence, uncertainty estimates, and application objectives to guide where scarce computational resources are directed. Current workflows treat solver selection as a fixed protocol rather than as a policy learned from the evolving campaign state. High-fidelity methods—density functional theory with hybrid functionals, many-body perturbation theory (GW/BSE), quantum Monte Carlo, or embedded correlated wavefunction methods—are invoked according to pre-specified schedules rather than in response to what the campaign actually needs to resolve. Hybrid quantum-classical methods, including variational quantum eigensolvers (VQE) and quantum approximate optimization algorithms (QAOA) adapted to reduced active-space problems, represent an emerging class of tools that may provide useful computational leverage on selected many-body subproblems, but are currently deployed as isolated benchmarking demonstrations rather than as integral, selectively invoked components of a materials-discovery workflow.

#### 1.3 Alignment with DOE Genesis Mission Topic 7C

The DOE Genesis Mission Topic 7, Focus Area C, calls for: *(i)* agentic AI workflows in quantum chemistry and materials science **beyond iterative parameter-space searches** for variational solvers; *(ii)* execution **across platforms, including distributed deployment**; and *(iii)* **AI-driven surrogate models that accelerate quantum time evolution and many-body simulations by learning efficient representations.** Our proposed work addresses all three requirements directly. The workflow moves beyond parameter optimization by placing AI at the level of **campaign-level orchestration**: deciding which candidates warrant evaluation, at which fidelity level, through which solver, and when accumulated evidence is sufficient to update the surrogate. This is qualitatively distinct from tuning the parameters of a single variational circuit.

#### 1.4 Innovation and Positioning

The novelty of the proposed work lies in four aspects that collectively distinguish it from prior art:

1. **Workflow-level optimization.** Hybrid quantum-classical computation is treated as a resource to be selectively deployed by an intelligent planner, not as a universal solver. The AI optimizes the campaign policy, not only a variational circuit.
2. **Agentic task routing.** An orchestration layer interprets project objectives, monitors campaign state, and selects among classical, surrogate, and hybrid quantum-classical pathways in response to uncertainty and decision value.
3. **Learned surrogate representations.** Surrogate models trained on accumulated simulation outputs reduce the burden on expensive evaluations while preserving the ranking quality required for candidate prioritization.
4. **Application-grounded evaluation.** AI advantage is defined operationally and measured against pre-specified baselines, producing a quantitative result that is interpretable without quantum-advantage overclaiming.

**Central hypothesis:** An agentic AI workflow that adaptively routes materials-screening tasks across classical simulation, hybrid quantum-classical routines, and learned surrogate models can reduce the number of expensive high-fidelity calculations required to identify promising electrode-material candidates, while maintaining or improving top-candidate quality relative to strong static and non-agentic baselines under matched resource constraints.

---

### 2. Project Objectives

**Overall Phase I objective:** To design, implement, and benchmark a reproducible AI-guided hybrid quantum-classical workflow that measurably improves the efficiency and candidate-selection quality of electrode-material prioritization for contaminant-removal applications.

The Phase I work is organized around three specific aims:

**Aim 1 — Agentic Orchestration.** Build a workflow orchestration layer that routes chemistry and materials computation tasks across classical, hybrid quantum-classical, and surrogate pathways using a policy driven by campaign state, uncertainty estimates, and objective priorities.
*Success signal:* Policy-driven routing outperforms static workflow execution under matched compute budgets, as measured by campaign efficiency and candidate quality metrics.

**Aim 2 — Surrogate Acceleration.** Develop uncertainty-aware surrogate models that learn efficient representations from accumulated simulation outputs, reducing dependence on repeated expensive quantum chemistry or many-body evaluations while preserving decision quality.
*Success signal:* Surrogate-assisted selection reduces expensive solver calls per validated hit without degrading top-*k* candidate recovery relative to brute-force evaluation.

**Aim 3 — Benchmarking and AI Advantage Quantification.** Conduct a rigorous ablation study comparing the full workflow against three progressively weaker baselines, producing quantitative evidence that the proposed approach is on a credible trajectory toward application-relevant AI advantage.
*Success signal:* Measurable improvements in at least two efficiency or quality metrics under matched resource constraints.

---

### 3. Proposed Research and Methods

#### 3.1 Task Definition and Bounded Phase I Scope

To ensure that Phase I produces measurable, reproducible outcomes within 9 months, we will define a bounded discovery problem: screening a candidate set of transition-metal-based electrode materials for performance in a representative electrochemical contaminant-removal scenario. The candidate pool will be drawn from experimentally reported and computationally tractable material families (e.g., rutile and perovskite oxides, MXene-derived surfaces, metal-nitrogen-carbon composites) and will be sized to allow full classical evaluation as a ground-truth reference alongside adaptive campaign runs. Target properties will include adsorption free energy for a representative contaminant, computed electrochemical stability limits, and a composite screening score encoding multi-criteria performance priorities.

This bounded scope is appropriate for Phase I feasibility: it enables rigorous comparison against a known reference, supports reproducible benchmark execution, and is narrow enough to deliver a complete ablation study within the project period while remaining scientifically representative of the broader discovery challenge.

#### 3.1.1 Data Sources and Candidate Pool Construction

The Phase I workflow will draw on three complementary data sources.

**Existing computational databases.** The initial candidate pool will be constructed from publicly available high-throughput DFT repositories, primarily the **Materials Project** (~150,000 inorganic structures with computed formation energies, band gaps, and electrochemical stability windows) [Jain et al., 2013] and the **Open Quantum Materials Database (OQMD)** (~1,000,000 DFT entries) [Saal et al., 2013]. Candidates will be filtered to the target material families (rutile and perovskite oxides, MXene-derived surfaces, metal-nitrogen-carbon composites) and further screened by computed electrochemical stability and elemental abundance criteria, producing an initial pool of approximately 200–500 tractable candidates for Phase I campaigns.

**Phase I DFT calculations.** For properties not available in existing databases—specifically, contaminant adsorption free energies, surface-termination-dependent redox potentials, and reaction-pathway energetics—the team will generate new DFT calculations (PBE and HSE06 functionals via VASP or Quantum ESPRESSO) on selected candidates during Phase I. These calculations will serve as both training data for surrogate model development and as the ground-truth reference for the ablation benchmark study. We estimate approximately 500–1,000 single-point and geometry-optimization calculations over the project period, sized to fit within the allocated HPC budget.

**Experimental literature anchors.** A small curated set of electrode materials with published experimental contaminant-removal performance data (e.g., Ti₄O₇ Magnéli phase, boron-doped diamond, RuO₂-based anodes) will be included in the candidate pool as known-performance anchors. These anchors serve as validation checkpoints: a workflow that fails to rank experimentally validated high-performers in its top-*k* set provides a clear diagnostic signal for surrogate or routing failures.

**Data management.** All generated DFT outputs, surrogate training sets, and provenance records will be archived in a structured format compatible with the **NOMAD Repository** or **Materials Data Facility**, ensuring FAIR-compliant data sharing at project close. Dataset versioning will be maintained via AiiDA's built-in provenance graph throughout the campaign.

#### 3.2 Workflow Architecture

The proposed workflow integrates four tightly coupled layers, as illustrated in Figure 1:

<img width="939" height="512" alt="image" src="https://github.com/user-attachments/assets/2e91210e-9a2e-4750-a539-55e2661c75ac" />

**Figure 1.** Project workflow overview. The diagram shows the four tightly coupled layers (candidate ingestion and representation, agentic planning and routing, computational back-end with classical and hybrid Q-C paths, and surrogate active-learning loop), the 9-month work package timeline (WP1–WP5), Phase I deliverables, ablation comparison structure (B0–B3), and the multi-institutional team arrangement.

**(a) Candidate Ingestion and Representation.**
Materials candidates are encoded using a combination of compositional descriptors, structural fingerprints (e.g., smooth overlap of atomic positions, crystal graph representations), surface-context features encoding termination and adsorbate configuration, and any partially observed property vectors accumulated during prior campaign iterations. Objective and constraint specifications are encoded at campaign initialization and updated as the workflow evolves.

**(b) Agentic Planning and Routing Layer.**
An agentic controller receives the current campaign state—candidate set, accumulated computation outputs, uncertainty estimates, remaining budget, and objective priorities—and selects the next computational action. Available actions include: *(i)* requesting a low-cost classical pre-screening calculation; *(ii)* invoking surrogate inference with uncertainty quantification; *(iii)* escalating a candidate to higher-fidelity classical validation (DFT with hybrid functional, post-DFT correction); *(iv)* routing a selected subproblem to a hybrid quantum-classical solver; or *(v)* triggering surrogate retraining when accumulated evidence is sufficient to warrant a model update. The planner is implemented as a policy that maps campaign state to action, and is itself updated using active learning or reinforcement-style feedback from campaign outcomes.

This architecture addresses the Topic 7C requirement for workflows **beyond iterative parameter-space searches**: the AI does not merely tune the parameters of a single solver but makes campaign-level decisions about what to compute, when, and how.

The agentic orchestration layer will be implemented using **LangGraph** as the stateful graph execution backbone, leveraging its native support for cyclic, condition-branched workflows and persistent campaign state. Scientific computation tasks will be dispatched and tracked via **AiiDA** or **Atomate2**, which provide mature provenance capture, HPC scheduler integration, and workflow reproducibility features well-suited to the DFT and hybrid quantum-classical back-ends. This two-layer software architecture separates AI decision logic from computational execution, improving modularity and enabling independent testing of each component.

**(c) Computational Back-End.**
The back-end integrates three execution paths:
- *Classical path:* periodic DFT (PBE and HSE06 functionals), semiempirical tight-binding, and force-field screening as appropriate for early-stage filtering and high-throughput validation.
- *Hybrid quantum-classical path:* targeted invocation of VQE or related variational algorithms for selected reduced active-space many-body subproblems (e.g., transition-metal *d*-band correlation, strongly correlated surface-adsorption states) where classical approximations are least reliable. Phase I emphasizes **workflow integration and quantitative benchmarking** of when hybrid routines add value, not unsupported claims of quantum speed-up. The migration from classical simulation to real quantum hardware follows the four-stage validation protocol described in Section 3.4.
- *Provenance and resource logging:* all task submissions, outputs, routing decisions, and resource usage are logged for reproducibility and for downstream analysis of workflow policy quality.

Distributed execution will be supported via a job scheduler abstraction layer enabling deployment across local clusters, national HPC systems (e.g., NERSC, ALCF), and cloud resources, consistent with the Topic 7C requirement for cross-platform execution.

**(d) Surrogate and Active-Learning Loop.**
Surrogate models are trained on the accumulated outputs of prior campaign iterations and are used to predict target properties and composite scoring functions for unvisited candidates. Uncertainty quantification (Bayesian neural networks, deep ensembles, or Gaussian-process-based local surrogates) drives acquisition functions for next-round selection, balancing exploitation of predicted high-value regions with exploration of uncertain areas of candidate space. Surrogates are retrained at campaign checkpoints determined by the agentic planner based on evidence accumulation criteria.

#### 3.3 Why This Is Beyond Iterative Parameter Search

Topic 7C explicitly calls for workflows **beyond iterative parameter-space searches**. The proposed work satisfies this requirement at three levels. First, the object being optimized is the **campaign policy**—the mapping from campaign state to next action—rather than the parameters of a single variational circuit. Second, the workflow manages heterogeneous computation across qualitatively different solver types, not a single parameterized solver. Third, the surrogate models learn **representations of the scientific landscape** (property surfaces, uncertainty maps) rather than representations of a single optimization objective in a fixed parameter space.

#### 3.4 Simulation-to-Hardware Migration Protocol for Quantum Components

A credible Phase I plan for hybrid quantum-classical computation must provide a concrete pathway from classical simulation of quantum circuits to validated execution on real quantum processors. We adopt a four-stage migration protocol aligned with the 9-month project timeline (Table 1), designed to ensure that quantum hardware runs are only attempted once circuit designs have been validated and resource requirements are well characterized.

**Table 1.** Simulation-to-hardware migration stages and timeline.

| Stage | Months | Platform | Purpose |
|---|---|---|---|
| S1: Noise-free simulation | 1–3 | CPU/GPU state-vector simulator | Circuit design and ansatz validation |
| S2: Noise-model simulation | 3–5 | GPU noise simulator (device-calibrated) | Error mitigation protocol selection |
| S3: Small-molecule hardware validation | 5–7 | Real quantum processor (8–12 qubits) | End-to-end workflow verification |
| S4: Application-relevant hardware runs | 7–9 | Real quantum processor (12–20 qubits) | Materials subproblem benchmarking |

**Stage 1 — Noise-Free Classical Simulation (Months 1–3).**
All quantum circuit designs will first be developed and validated using exact state-vector simulation on GPU-accelerated classical hardware (Qiskit Aer `statevector_simulator` or PennyLane `default.qubit`, executed on NERSC Perlmutter A100 nodes). This stage serves three purposes: *(i)* confirming that the chosen ansatz (e.g., UCCSD, hardware-efficient variational form, or k-UpCCGSD) converges to the correct ground-state energy for benchmark systems; *(ii)* establishing noise-free reference energies against CASSCF and DMRG classical references for the same reduced active-space problems; and *(iii)* characterizing circuit depth and two-qubit gate count as a function of active-space size, which determines feasibility on near-term hardware. At this stage, systems up to 20 qubits are tractable via GPU state-vector simulation (~2²⁰ amplitudes, ~8 MB memory per shot). Go/no-go criterion: VQE energy error versus CASSCF reference must be below 1 kcal/mol (chemical accuracy) in noise-free simulation before proceeding to Stage 2.

**Stage 2 — Device-Calibrated Noise Simulation (Months 3–5).**
Validated circuits are subjected to realistic noise modeling using device-specific noise profiles obtained from the target quantum processor's daily calibration data (available via IBM Quantum or IonQ cloud APIs). Noise models include depolarizing error on single- and two-qubit gates, readout error, and T₁/T₂ decoherence. Three error mitigation strategies will be evaluated: *(i)* **Zero-Noise Extrapolation (ZNE)**, in which circuit noise is intentionally amplified by gate folding and the zero-noise limit is extrapolated; *(ii)* **Symmetry Verification**, exploiting known symmetries of the Hamiltonian (particle number, spin) to detect and post-select against corrupted bitstrings; and *(iii)* **Measurement Error Mitigation** via calibration matrices. The combination yielding the best energy recovery relative to Stage 1 reference values will be adopted for hardware execution. Go/no-go criterion: mitigated energy error versus Stage 1 reference must remain below 2 kcal/mol under the simulated noise model.

**Stage 3 — Small-Molecule Hardware Validation (Months 5–7).**
The validated circuit designs and error mitigation protocols are executed on real quantum hardware using well-characterized small-molecule benchmark systems (H₂, LiH, BeH₂) whose exact energies are known to high precision classically. These systems require 2–6 qubits and serve as end-to-end integration tests of the full workflow path: LangGraph routing decision → AiiDA job submission → Qiskit Runtime circuit execution → result ingestion → campaign state update. Hardware platforms will be accessed via the DOE Quantum User Program or IBM Quantum Network. The primary validation metric is agreement between hardware-executed VQE energies (with error mitigation) and classically exact references within 2 kcal/mol. Secondary metrics include circuit fidelity, shot efficiency, and queue-to-result latency as experienced within the AiiDA workflow layer. This stage also validates the **fallback behavior**: if hardware is unavailable or results fail quality checks, the workflow automatically substitutes a CASSCF classical result and logs the substitution event.

**Stage 4 — Application-Relevant Hardware Benchmarking (Months 7–9).**
With the end-to-end pipeline validated on small molecules, Stage 4 applies the hardware-execution pathway to reduced active-space subproblems derived from the Phase I electrode-material candidate set—specifically, transition-metal *d*-band correlated states (e.g., Ti or Ru active spaces of 8–16 electrons in 8–16 orbitals, requiring 8–20 qubits after active-space reduction via AVAS or DMET embedding). Results from quantum hardware runs are compared against *(i)* Stage 1 noise-free simulation, *(ii)* CASSCF/DMRG classical references, and *(iii)* the B1 static hybrid baseline. This comparison produces the quantitative evidence base for whether selectively deployed quantum routines, as directed by the agentic workflow, yield scientifically meaningful improvements over the classical-only path for this application class. All Stage 4 results—including cases where quantum hardware does not outperform classical solvers—will be reported transparently as part of the Phase I benchmark deliverable.

---

### 4. Evaluation Plan, Baselines, and Definition of AI Advantage

#### 4.1 Baseline Comparison Structure

We will evaluate the proposed workflow against four comparison classes in a fully ablated benchmark study:

| Baseline | Description |
|---|---|
| **B0: Classical-only static** | Sequential classical screening with pre-specified fidelity schedule; no AI routing, no surrogates |
| **B1: Static hybrid** | Pre-scripted inclusion of hybrid Q-C steps at fixed points; no adaptive routing |
| **B2: Agentic without surrogate** | Agentic routing across classical and Q-C paths; surrogate acceleration disabled |
| **B3: Full proposed workflow** | Agentic routing + surrogate acceleration + hybrid Q-C integration |

The ablation structure isolates the contribution of each component: orchestration intelligence (B0 vs. B2), surrogate acceleration (B2 vs. B3), and hybrid solver integration (B1 vs. B3). Resource budgets (CPU-hours, wall-clock time, number of expensive solver calls) are matched across comparison classes for all primary metrics.

#### 4.2 Evaluation Metrics

**Efficiency metrics:**
- Number of expensive (high-fidelity DFT or hybrid Q-C) evaluations per validated top-*k* candidate
- Total wall-clock time per complete campaign run
- Compute resource usage (CPU/GPU hours) per validated hit

**Scientific utility metrics:**
- Top-*k* enrichment ratio: fraction of ground-truth top-*k* candidates recovered by each workflow under matched budgets
- Spearman rank correlation between workflow-recommended ranked list and full-reference ranking
- Recovery rate of expert-supported or experimentally validated candidates present in the candidate pool

**Workflow quality metrics:**
- Reproducibility across repeated independent runs (variance in top-*k* composition and ranking)
- Robustness to simulated task failures (graceful degradation behavior)
- Traceability: fraction of routing decisions with logged rationale

#### 4.3 Operational Definition of AI Advantage

We adopt a conservative, Phase I–appropriate definition:

> **AI advantage** in this project means a measurable improvement in workflow efficiency and/or top-candidate selection quality, produced by AI-guided orchestration and/or surrogate acceleration, relative to the strongest applicable non-agentic baseline under matched resource constraints.

We are not claiming fault-tolerant quantum advantage or broad quantum speed-up. The Phase I question is whether AI creates a credible, quantitatively supported trajectory toward transformative discovery capability by reducing expensive computation while preserving scientific utility. A successful result is one where the full workflow (B3) outperforms B0 and B2 on at least two primary metrics without degrading any primary metric.

#### 4.4 Risk Assessment and Mitigations

| Risk | Likelihood | Mitigation |
|---|---|---|
| Hybrid Q-C component yields no measurable benefit for selected tasks | Moderate | Maintain a clearly defined quantum-ready interface; quantify and report the result honestly; shift Phase I emphasis toward agentic orchestration and surrogate contributions |
| Surrogate fidelity insufficient for reliable ranking | Moderate | Use uncertainty-aware acquisition; fall back to local or task-specific surrogates; narrow candidate diversity |
| Candidate scope too broad for 9-month execution | Low–Moderate | Restrict to one material family and one contaminant target; establish go/no-go criterion at Month 2 |
| Access to required HPC or Q-C platforms delayed | Low | Begin benchmark workflow on simulation/emulation; defer hardware-specific integration to Months 5–7 |

#### 4.5 Definition of Phase I Success

A successful 9-month Phase I outcome is defined as:
1. A fully documented, version-controlled, reproducible prototype workflow is delivered and executable by a third party.
2. The ablation benchmark study is complete with quantitative results across all four baseline classes and all primary metrics.
3. The full workflow (B3) shows statistically meaningful improvement over the classical-only static baseline (B0) on at least two efficiency or utility metrics under matched budgets.
4. A curated prioritized candidate set with ranked confidence scores is delivered for potential experimental follow-up.
5. A Phase II roadmap is delivered describing the path to larger-scale chemistry deployment and tighter hardware integration.

---

### 5. Team, Resources, Management, and Expected Impact

#### 5.1 Team Structure

The proposal assembles a small multi-institutional team drawn from at least two of the three DOE-eligible partnership categories, meeting the RFA teaming requirement:

| Partner | Category | Primary Role |
|---|---|---|
| **Lead University** | IHE / Non-profit | PI: AI workflow design, surrogate learning, benchmark orchestration, and overall project integration |
| **DOE National Laboratory / User Facility** | DOE/NNSA Lab | Co-PI: quantum chemistry and materials simulation expertise; access to HPC and quantum information platforms; high-fidelity validation calculations |
| **Industry Partner** | Industry | Co-I / Collaborator: electrochemical contaminant-removal application constraints; materials testing pathway; translation relevance |

All partner institutions will provide letters of commitment. Each partner contributes intellectually to the project, not solely in a resource-providing role.

**PI (Lead University):** Leads overall technical integration, AI workflow design, surrogate model development, and benchmark evaluation. Responsible for Phase I reporting and Phase II planning.

**Co-PI (DOE Lab):** Leads quantum chemistry and hybrid quantum-classical computational components; provides access to high-performance computing resources; coordinates distributed execution across DOE infrastructure.

**Co-I / Collaborator (Industry):** Provides electrochemical application context, material performance constraints, and a translational perspective on prioritized candidates. Contributes to target property specification and evaluation criteria.

#### 5.2 9-Month Milestone Plan

| Work Package | Months | Key Deliverables |
|---|---|---|
| **WP1** — Problem formalization and benchmark setup | 1–2 | Bounded candidate pool finalized; target properties and baseline evaluation framework established; go/no-go criteria defined |
| **WP2** — Agentic workflow prototype | 2–4 | Initial orchestration layer operational; baseline workflow (B0, B1) runs complete; candidate-routing experiments initiated |
| **WP3** — Hybrid Q-C integration and surrogate development | 3–6 | First surrogate model training cycle complete; hybrid Q-C subroutine integrated into workflow back-end; uncertainty-aware acquisition active |
| **WP4** — Benchmarking and ablation study | 6–8 | Full benchmark run set executed across all four comparison classes; ablation analysis and failure review complete; top-candidate validation runs initiated |
| **WP5** — Final evaluation, packaging, Phase II roadmap | 8–9 | Integrated Phase I report submitted; workflow code and data packaged for release; prioritized candidate set delivered; Phase II roadmap finalized |

**Go/no-go checkpoint (Month 2):** The team will confirm that the bounded Phase I scope is tractable (candidate pool size, data availability, platform access), that baseline workflows are running, and that evaluation metrics are finalized. Scope adjustments will be made at this point if needed.

#### 5.3 Computational Resources and Infrastructure

Phase I requires two qualitatively distinct classes of computational resource—conventional HPC and quantum computing hardware—used at different stages of the workflow and integrated through a common orchestration layer.

**5.3.1 Conventional HPC Resources**

Classical electronic-structure calculations and surrogate model training constitute the dominant computational workload of Phase I and will be executed on national HPC systems:

- **NERSC Perlmutter** (LBNL): The primary platform for DFT calculations and GPU-accelerated surrogate training. CPU partition nodes (AMD EPYC, 512 GB RAM) will handle periodic DFT geometry optimizations and single-point energy calculations via VASP or Quantum ESPRESSO. GPU partition nodes (NVIDIA A100, 40 GB HBM2) will support graph neural network surrogate training and batch inference. Estimated usage: ~200,000–400,000 CPU-hours and ~5,000–10,000 GPU-hours over the project period.
- **ALCF Polaris** (ANL): Secondary platform providing additional A100 GPU capacity for large-batch surrogate training runs and distributed benchmark campaign execution. Estimated usage: ~5,000–10,000 GPU-hours.
- **Local institutional clusters**: Used for workflow development, prototyping, and small-scale integration tests prior to full-scale HPC deployment.

HPC allocations will be pursued through DOE's **ERCAP** process (NERSC), the **INCITE** and **ALCC** national allocation programs, and institutional allocations held by the lead university and DOE lab partner. The DOE lab co-PI's existing allocation history will provide a fallback resource path if new allocations are pending during early project months.

The HPC resource estimate is sized for the bounded Phase I campaign: approximately 500–1,000 DFT single-point and geometry-optimization calculations on candidate surface slabs (typically 50–200 atoms per cell, ~100–500 CPU-hours each), plus surrogate model training cycles of modest scale (graph neural networks on ~10³ training points, feasible on a single A100 node in hours).

**5.3.2 Quantum Computing Hardware**

Hybrid quantum-classical subroutines will be executed on available NISQ-era quantum processors for targeted many-body subproblems where classical approximations are least reliable, such as strongly correlated transition-metal *d*-band states and reduced active-space electronic structure problems. Phase I usage of quantum hardware is deliberately exploratory and bounded:

- **Target problem size**: Reduced active-space subproblems requiring 8–20 qubits are the primary Phase I scope, compatible with current gate-based devices (50–127+ physical qubits) and near-term error mitigation strategies.
- **Platforms**: Access will be pursued through the **DOE Quantum User Program (QUP)**, DOE national laboratory quantum testbeds (e.g., ORNL quantum computing user program, Sandia QSCOUT), and cloud-accessible devices (IBM Quantum via the IBM Quantum Network, IonQ, or Quantinuum) using Qiskit or PennyLane as the quantum circuit interface. The DOE lab partner's existing quantum program relationships will be the primary access pathway.
- **Estimated usage**: Approximately 50–150 quantum circuit execution batches in Phase I, primarily for benchmarking VQE convergence behavior on reduced subproblems against classical CASSCF/DMRG references. Quantum hardware time is not the rate-limiting resource; the scientific contribution is in the workflow logic that decides *when* to invoke quantum routines and *how* to interpret their results within the campaign.

**5.3.3 Integration Architecture**

The two resource classes are unified through the two-layer software stack described in Section 3.2(b). The **LangGraph** agentic orchestrator issues routing decisions and maintains campaign state. **AiiDA** dispatches HPC jobs to NERSC/ALCF via SLURM scheduler interfaces and tracks their provenance. Quantum circuit jobs are submitted asynchronously via cloud APIs (Qiskit Runtime, PennyLane cloud) and their results are returned to the same AiiDA provenance database upon completion. Both job types report outputs in a common schema, allowing the LangGraph planner to treat HPC and quantum results uniformly when updating campaign state and making the next routing decision.

This architecture ensures that quantum hardware is never a blocking dependency for classical campaign progress: HPC-based calculations and surrogate inference continue while quantum jobs are queued, and quantum results are incorporated into the campaign when available. Fallback behavior—routing a quantum-designated subproblem to a classical correlated solver if quantum hardware is unavailable—is an explicitly handled workflow state.

All workflow components will be containerized (Docker/Singularity) and documented to support reproducible execution and eventual integration with Genesis Mission shared infrastructure.

#### 5.4 Expected Outcomes and Impact

**Immediate Phase I outputs:**
- A reproducible, benchmarked prototype AI-guided workflow for hybrid quantum-classical materials discovery;
- Quantitative evidence that AI-guided orchestration and surrogate acceleration improve discovery efficiency relative to strong baselines;
- A curated set of prioritized electrode-material candidates for contaminant-removal follow-up;
- Open-source code, data artifacts, and benchmark results supporting reproducibility and community reuse.

**Contribution to the Genesis Mission program:**
This project delivers a concrete, evaluated demonstration of agentic AI coordinating hybrid quantum-classical computation in a materials-science application—directly aligned with the Genesis Mission objective of developing AI-enabled workflows that transform scientific discovery. The workflow architecture is designed to generalize: the agentic routing and surrogate acceleration approach is applicable to other quantum chemistry and materials screening challenges beyond the specific electrode materials studied in Phase I.

**Trajectory toward Phase II:**
A successful Phase I will establish the quantitative evidence base, workflow infrastructure, and team coordination needed to pursue Phase II at larger scale: broader material families, higher-fidelity quantum-classical components on more capable hardware, and tighter integration with experimental validation campaigns.

---

## REFERENCES

### A. Electrochemical Contaminant Removal and Electrode Materials

[1] Radjenovic, J.; Sedlak, D. L. Challenges and Opportunities for Electrochemical Processes as Next-Generation Technologies for the Treatment of Contaminated Water. *Environ. Sci. Technol.* **2015**, *49* (19), 11292–11302.

[2] Chaplin, B. P. Critical Review of Electrochemical Advanced Oxidation Processes for Water Treatment Applications. *Environ. Sci.: Processes Impacts* **2014**, *16* (6), 1182–1203.

[3] Suss, M. E.; Porada, S.; Sun, X.; Biesheuvel, P. M.; Yoon, J.; Presser, V. Water Desalination via Capacitive Deionization: What Is It and What Can We Expect from It? *Energy Environ. Sci.* **2015**, *8* (8), 2296–2319.

[4] Gayen, P.; Spataro, J.; Avasarala, S.; Ali, A.-M.; Cerrato, J. M.; Chaplin, B. P. Electrocatalytic Reduction of Nitrate Using Magnéli Phase TiO₂ Reactive Electrochemical Membranes Doped with Pd-Based Catalysts. *Environ. Sci. Technol.* **2018**, *52* (16), 9370–9379.

[5] Maza, W. A.; Breslin, V. M.; Owrutsky, J. C.; Pate, B. B.; Epshteyn, A. Electrochemical Oxidation of PFAS at Ti₄O₇ Magnéli Phase Reactive Electrochemical Membrane. *J. Electrochem. Soc.* **2023**, *170* (4), 043503.

[6] Jing, Y.; Chaplin, B. P. Mechanistic Study of the Validity of Using Hydroxyl Radical Probes to Characterize Electrochemical Advanced Oxidation Processes. *Environ. Sci. Technol.* **2017**, *51* (4), 2355–2365.

### B. Density Functional Theory and High-Fidelity Electronic Structure Methods

[7] Kohn, W.; Sham, L. J. Self-Consistent Equations Including Exchange and Correlation Effects. *Phys. Rev.* **1965**, *140* (4A), A1133–A1138.

[8] Heyd, J.; Scuseria, G. E.; Ernzerhof, M. Hybrid Functionals Based on a Screened Coulomb Potential. *J. Chem. Phys.* **2003**, *118* (18), 8207–8215.

[9] Kresse, G.; Furthmüller, J. Efficient Iterative Schemes for Ab Initio Total-Energy Calculations Using a Plane-Wave Basis Set. *Phys. Rev. B* **1996**, *54* (16), 11169–11186.

[10] Giannozzi, P. et al. QUANTUM ESPRESSO: A Modular and Open-Source Software Project for Quantum Simulations of Materials. *J. Phys.: Condens. Matter* **2009**, *21* (39), 395502.

[11] Himmetoglu, B.; Floris, A.; de Gironcoli, S.; Cococcioni, M. Hubbard-Corrected DFT Energy Functionals: The LDA+U Description of Correlated Systems. *Int. J. Quantum Chem.* **2014**, *114* (1), 14–49.

### C. Hybrid Quantum-Classical Algorithms

[12] Peruzzo, A.; McClean, J.; Shadbolt, P.; Yung, M.-H.; Zhou, X.-Q.; Love, P. J.; Aspuru-Guzik, A.; O'Brien, J. L. A Variational Eigenvalue Solver on a Photonic Chip. *Nat. Commun.* **2014**, *5*, 4213.

[13] Farhi, E.; Goldstone, J.; Gutmann, S. A Quantum Approximate Optimization Algorithm. *arXiv:1411.4028* **2014**.

[14] McClean, J. R.; Romero, J.; Babbush, R.; Aspuru-Guzik, A. The Theory of Variational Hybrid Quantum-Classical Algorithms. *New J. Phys.* **2016**, *18* (2), 023023.

[15] Cao, Y. et al. Quantum Chemistry in the Age of Quantum Computing. *Chem. Rev.* **2019**, *119* (19), 10856–10915.

[16] Bauer, B.; Bravyi, S.; Motta, M.; Chan, G. K.-L. Quantum Algorithms for Quantum Chemistry and Quantum Materials Science. *Chem. Rev.* **2020**, *120* (22), 12685–12717.

[17] Cerezo, M. et al. Variational Quantum Algorithms. *Nat. Rev. Phys.* **2021**, *3* (9), 625–644.

[18] Motta, M.; Rice, J. E. Emerging Quantum Computing Algorithms for Quantum Chemistry. *WIREs Comput. Mol. Sci.* **2022**, *12* (3), e1580.

### D. Agentic AI, Scientific Workflow Orchestration, and Autonomous Discovery

[19] Jablonka, K. M.; Schwaller, P.; Ortega-Guerrero, A.; Smit, B. Leveraging Large Language Models for Hypothesis Generation in the Chemical Sciences. *Chem. Sci.* **2024**, *15* (15), 5473–5482.

[20] Boiko, D. A.; MacKnight, R.; Kline, B.; Gomes, G. Autonomous Chemical Research with Large Language Models. *Nature* **2023**, *624* (7992), 570–578.

[21] Bran, A. M.; Cox, S.; Schilter, O.; Baldassari, C.; White, A. D.; Schwaller, P. ChemCrow: Augmenting Large-Language Models with Chemistry Tools. *Nat. Mach. Intell.* **2024**, *6*, 525–535.

[22] Jain, A.; Ong, S. P.; Hautier, G.; Chen, W.; Richards, W. D.; Dacek, S.; Cholia, S.; Gunter, D.; Skinner, D.; Ceder, G.; Persson, K. A. Commentary: The Materials Project: A Materials Genome Approach to Accelerating Materials Innovation. *APL Mater.* **2013**, *1* (1), 011002.

[23] Curtarolo, S. et al. AFLOW: An Automatic Framework for High-Throughput Materials Discovery. *Comput. Mater. Sci.* **2012**, *58*, 218–226.

[24] Mathew, K.; Montoya, J. H.; Faghaninia, A.; Dwarakanath, S.; Aykol, M.; Tang, H.; Chu, I.-H.; Smidt, T.; Bocklund, B.; Horton, M.; Dagdelen, J.; Wood, B.; Liu, Z.-K.; Neaton, J.; Ong, S. P.; Persson, K.; Jain, A. Atomate: A High-Level Interface to Generate, Execute, and Analyze Computational Materials Science Workflows. *Comput. Mater. Sci.* **2017**, *139*, 140–152.

### E. Surrogate Modeling, Active Learning, and Machine Learning for Materials Discovery

[25] Schütt, K. T.; Kindermans, P.-J.; Sauceda, H. E.; Chmiela, S.; Tkatchenko, A.; Müller, K.-R. SchNet: A Continuous-Filter Convolutional Neural Network for Modeling Quantum Interactions. *Adv. Neural Inf. Process. Syst.* **2017**, *30*.

[26] Chen, C.; Ye, W.; Zuo, Y.; Zheng, C.; Ong, S. P. Graph Networks as a Universal Machine Learning Framework for Molecules and Crystals. *Chem. Mater.* **2019**, *31* (9), 3564–3572.

[27] Batzner, S. et al. E(3)-Equivariant Graph Neural Networks for Data-Efficient and Accurate Interatomic Potentials. *Nat. Commun.* **2022**, *13*, 2453.

[28] Lookman, T.; Balachandran, P. V.; Xue, D.; Yuan, R. Active Learning in Materials Science with Emphasis on Adaptive Sampling in Experimental Design: Survey and Review. *npj Comput. Mater.* **2019**, *5*, 21.

[29] Deringer, V. L.; Caro, M. A.; Csányi, G. Machine Learning Interatomic Potentials as Emerging Tools for Materials Science. *Adv. Mater.* **2019**, *31* (46), 1902765.

[30] Reker, D.; Bernardes, G. J. L.; Rodrigues, T. Computational Advances in Combating Colloidal Aggregation in Drug Discovery. *Nat. Chem.* **2019**, *11* (5), 402–418.

[31] Zuo, Y.; Chen, C.; Li, X.; Deng, Z.; Chen, Y.; Brorsson, J.; Hellman, O.; Rulis, P.; Ramprasad, R.; Ong, S. P. Performance and Cost Assessment of Machine Learning Interatomic Potentials. *J. Phys. Chem. A* **2020**, *124* (4), 731–745.

### F. DOE Computational Infrastructure and Genesis Mission Context

[32] U.S. Department of Energy, Office of Science. *Funding Opportunity Announcement: The Genesis Mission: Transforming Science and Energy with AI*, DE-FOA-0003612. 2025.

[33] Bard, A.; Faulkner, L. R. *Electrochemical Methods: Fundamentals and Applications*, 2nd ed.; Wiley: New York, 2001.

[34] National Energy Research Scientific Computing Center (NERSC). NERSC Strategic Plan 2023–2028. Lawrence Berkeley National Laboratory, 2023.

[35] Dongarra, J. et al. The International Exascale Software Project Roadmap. *Int. J. High Perform. Comput. Appl.* **2011**, *25* (1), 3–60.

---

## BUDGET NARRATIVE

*(Detailed budget to be submitted on required DOE forms. Narrative summary follows.)*

**Total Phase I request:** [within $500,000–$750,000 range]

**Personnel (~60–65% of total):** Salaries and fringe benefits for PI, Co-PI(s), graduate research assistants, and a postdoctoral researcher directly conducting the research. Effort is distributed to reflect the workflow design, computational chemistry, and benchmarking workstreams.

**Computational resources (~15–20%):** Allocation purchase or cloud compute costs for HPC campaign runs, surrogate model training, and benchmark execution. Supplemented by national allocation awards where available (e.g., INCITE, ALCC).

**Subcontract / partner allocations (~10–15%):** Support for DOE lab and industry partner intellectual contributions. Combined industry partner budget is targeted at ≤20% of total requested funds, consistent with Genesis Mission guidance.

**Travel (~3–5%):** Site visits for team coordination, Genesis Mission program meetings, and relevant scientific conferences.

**Other direct costs (~3–5%):** Software licensing, data storage, open-source publication costs, workshop participation.

**Budget rationale:** The budget is calibrated for a 9-month proof-of-workflow effort. Personnel are the dominant cost driver, reflecting the research-intensive nature of workflow design, model development, and benchmarking. Computational resource costs are sized to support the bounded Phase I campaign runs and ablation benchmark study without over-provisioning for Phase II-scale deployment.

---

## TEAM BIOGRAPHICAL SKETCHES

*(DOE-format biosketches for PI, Co-PI(s), and senior personnel to be appended per RFA requirements. Not counted toward 5-page narrative limit.)*

---

## FACILITIES AND OTHER RESOURCES

*(Institutional facility statements for all participating organizations to be appended per RFA requirements.)*

---

## LETTERS OF COMMITMENT

*(Letters of commitment from all partner institutions — DOE National Laboratory / User Facility and Industry Partner — to be included as required appendices. Letters must confirm intellectual contribution, not merely resource provision.)*

---

## DATA MANAGEMENT PLAN

All computational workflows, surrogate model weights and training data, benchmark results, and provenance logs will be versioned and archived in a publicly accessible repository (e.g., Materials Data Facility, Zenodo, or equivalent DOE-endorsed repository) at project close. Data will be formatted and documented to meet FAIR principles (Findable, Accessible, Interoperable, Reusable). Software will be released under an OSI-approved open-source license. Sensitive or export-controlled materials will be handled per institutional and DOE requirements.

---

## APPENDIX: COMPLIANCE SUMMARY

| Requirement | Status | Notes |
|---|---|---|
| FOA: DE-FOA-0003612 | Targeted | Genesis Mission Phase I |
| Topic 7, Focus Area C | Addressed | Agentic AI + hybrid Q-C + surrogate models in quantum chemistry and materials science |
| Phase I period ≤ 9 months | Compliant | 9-month project period |
| Phase I budget $500K–$750K | Compliant | Budget within range |
| Multi-institutional team | Compliant | IHE lead + DOE Lab + Industry (≥2 categories) |
| Letters of commitment | Required | To be obtained from all partners |
| Project Narrative ≤ 5 pages | Compliant | Technical narrative scoped to 5 pages |
| LOI | Not required | Phase I LOI not required per RFA |
| "Beyond parameter search" criterion | Addressed | Campaign-level policy optimization, not variational parameter tuning |
| AI advantage evaluation plan | Addressed | Four baselines, three metric families, operational definition |
| No Phase II overclaiming in Phase I | Addressed | Phase II vision clearly separated from Phase I deliverables |

---

*Draft version — for internal review and revision before submission.*
*Proposal due: April 28, 2026, 11:59 PM Eastern.*
