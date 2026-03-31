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

#### 3.2 Workflow Architecture

The proposed workflow integrates four tightly coupled layers (Figure 1 — *to be provided in submitted version*):

**(a) Candidate Ingestion and Representation.**
Materials candidates are encoded using a combination of compositional descriptors, structural fingerprints (e.g., smooth overlap of atomic positions, crystal graph representations), surface-context features encoding termination and adsorbate configuration, and any partially observed property vectors accumulated during prior campaign iterations. Objective and constraint specifications are encoded at campaign initialization and updated as the workflow evolves.

**(b) Agentic Planning and Routing Layer.**
An agentic controller receives the current campaign state—candidate set, accumulated computation outputs, uncertainty estimates, remaining budget, and objective priorities—and selects the next computational action. Available actions include: *(i)* requesting a low-cost classical pre-screening calculation; *(ii)* invoking surrogate inference with uncertainty quantification; *(iii)* escalating a candidate to higher-fidelity classical validation (DFT with hybrid functional, post-DFT correction); *(iv)* routing a selected subproblem to a hybrid quantum-classical solver; or *(v)* triggering surrogate retraining when accumulated evidence is sufficient to warrant a model update. The planner is implemented as a policy that maps campaign state to action, and is itself updated using active learning or reinforcement-style feedback from campaign outcomes.

This architecture addresses the Topic 7C requirement for workflows **beyond iterative parameter-space searches**: the AI does not merely tune the parameters of a single solver but makes campaign-level decisions about what to compute, when, and how.

**(c) Computational Back-End.**
The back-end integrates three execution paths:
- *Classical path:* periodic DFT (PBE and HSE06 functionals), semiempirical tight-binding, and force-field screening as appropriate for early-stage filtering and high-throughput validation.
- *Hybrid quantum-classical path:* targeted invocation of VQE or related variational algorithms for selected reduced active-space many-body subproblems (e.g., transition-metal *d*-band correlation, strongly correlated surface-adsorption states) where classical approximations are least reliable. Phase I emphasizes **workflow integration and quantitative benchmarking** of when hybrid routines add value, not unsupported claims of quantum speed-up.
- *Provenance and resource logging:* all task submissions, outputs, routing decisions, and resource usage are logged for reproducibility and for downstream analysis of workflow policy quality.

Distributed execution will be supported via a job scheduler abstraction layer enabling deployment across local clusters, national HPC systems (e.g., NERSC, ALCF), and cloud resources, consistent with the Topic 7C requirement for cross-platform execution.

**(d) Surrogate and Active-Learning Loop.**
Surrogate models are trained on the accumulated outputs of prior campaign iterations and are used to predict target properties and composite scoring functions for unvisited candidates. Uncertainty quantification (Bayesian neural networks, deep ensembles, or Gaussian-process-based local surrogates) drives acquisition functions for next-round selection, balancing exploitation of predicted high-value regions with exploration of uncertain areas of candidate space. Surrogates are retrained at campaign checkpoints determined by the agentic planner based on evidence accumulation criteria.

#### 3.3 Why This Is Beyond Iterative Parameter Search

Topic 7C explicitly calls for workflows **beyond iterative parameter-space searches**. The proposed work satisfies this requirement at three levels. First, the object being optimized is the **campaign policy**—the mapping from campaign state to next action—rather than the parameters of a single variational circuit. Second, the workflow manages heterogeneous computation across qualitatively different solver types, not a single parameterized solver. Third, the surrogate models learn **representations of the scientific landscape** (property surfaces, uncertainty maps) rather than representations of a single optimization objective in a fixed parameter space.

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

The workflow will be designed for portability across:
- **National HPC systems** (NERSC Perlmutter, ALCF Polaris, or equivalent) for classical DFT calculations and large surrogate training runs;
- **DOE quantum information platforms** (as available through the DOE lab partner) for hybrid quantum-classical subroutine execution and benchmarking;
- **Local institutional clusters** for development, prototyping, and intermediate-scale runs.

All workflow components will be containerized and documented to support reproducible execution and eventual integration with Genesis Mission shared infrastructure.

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

*(Full reference list to be completed in final submission. Representative citations will include foundational works on agentic AI orchestration, active learning for materials discovery, hybrid quantum-classical algorithms, electrochemical materials for contaminant removal, and relevant DOE computational infrastructure publications.)*

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
