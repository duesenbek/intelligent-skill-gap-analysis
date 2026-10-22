# 09 — Risk Register

**Document Version:** 1.0  
**Status:** Maintained — Task `CL-11`  
**Primary Maintainer:** Asylbek Agabekuly  
**Contributors:** Bekzat Duisenbek, Kuanysh Asaubaev  
**Project:** CareerLens — Intelligent Skill Gap Analysis and Personalized Career Recommendation System  

---

## 1. Risk Management Framework

The risk management process for CareerLens follows standard software engineering risk management practices (ISO/IEC 16085 / PMBOK). Risks are identified across four core dimensions:
1. **Technical & Algorithmic Risks (TR):** System architecture, algorithm precision, data schemas, and performance.
2. **Product & Scope Risks (PR):** Scope boundaries, feature inflation, and alignment with target user needs.
3. **Operational & Schedule Risks (OR):** Task delivery schedules, repository/YouTrack tracking, and team member availability.
4. **Ethical & Data Protection Risks (ER):** Participant privacy, assessment subjectivity, and career guidance liabilities.

### Risk Scoring Matrix

| Likelihood \ Impact | Low (L) | Medium (M) | High (H) |
|---|---|---|---|
| **High (H)** | Moderate (Yellow) | Major (Orange) | Critical (Red) |
| **Medium (M)** | Low (Green) | Moderate (Yellow) | Major (Orange) |
| **Low (L)** | Low (Green) | Low (Green) | Moderate (Yellow) |

---

## 2. Comprehensive Risk Register

| ID | Category | Risk Description | Likelihood | Impact | Severity | Mitigation Strategy & Contingency Plan | Owner | Status |
|---|---|---|---|---|---|---|---|---|
| **R-01** | Scope | **Scope Creep beyond MVP**<br>Attempting to cover excessive professions, build mobile apps, or integrate live web scrapers before the pre-defense. | M | H | **Major** | Strictly enforce MoSCoW prioritization defined in `06-requirements-specification.md`. Anchor MVP exclusively to 1–2 benchmark roles (Junior Flutter, Junior Backend). Exclude native apps and live scraping from initial release. | Bekzat | Mitigated |
| **R-02** | Technical | **Subjective Self-Assessment Bias**<br>Users over- or under-estimating their skill levels on the 1–5 scale, leading to skewed gap outputs. | H | M | **Major** | Provide explicit anchor rubrics for each level (e.g., Level 1 = Novice/Theory, Level 3 = Autonomous implementation, Level 5 = Expert/Architect). In subsequent milestones, integrate evidence-based verification tasks for critical skills. | Asylbek | Open |
| **R-03** | Technical | **Curated Role Ontology Cold-Start**<br>Benchmark role competency profiles are incomplete or poorly calibrated against current industry expectations. | M | M | **Moderate** | Standardize competency profiles against verified professional frameworks (SFIA 8, European e-Competence Framework) and cross-validate against published entry-level vacancy criteria. | Kuanysh | Open |
| **R-04** | Operational | **Schedule and Milestone Slippage**<br>Key pre-defense deliverables delayed due to uneven task progress or academic workload. | M | H | **Major** | Decompose work into fine-grained tasks in YouTrack with internal deadlines 24–48 hours before official university submissions. Maintain daily asynchronous standups and Git pull request reviews. | Bekzat | Mitigated |
| **R-05** | Technical | **Roadmap Dependency Graph Cycles**<br>Circular dependencies or illogical sequencing in the personalized learning roadmap generator (e.g., framework before language). | L | H | **Moderate** | Formulate prerequisite relationships as a Directed Acyclic Graph (DAG) with automated topological sorting and cycle-detection unit tests during build. | Bekzat | Open |
| **R-06** | Data/Ethics | **Unauthorized Collection of Identifiable Data**<br>Student interview transcripts or user profiles inadvertently disclosing personal contact details or private academic records. | L | H | **Moderate** | Enforce data anonymization at collection. Store zero personal identifiers in the repository. Use placeholder mock data in automated testing and configuration files. | Asylbek | Mitigated |
| **R-07** | Operational | **Technology Comparison & Selection Delay**<br>Prolonged debates on framework or database stack delaying prototype implementation. | L | M | **Low** | Establish formal multi-criteria decision analysis (MCDA) in `05-technology-comparison.md` with weighted criteria and strict approval deadline. | Kuanysh | Mitigated |
| **R-08** | Technical | **Algorithm Response Time Exceeding SLA**<br>Complex gap calculations and graph traversals breaching the $p95 \le 2.5\text{ s}$ target (`NFR-01`). | L | M | **Low** | Precompute role competency profiles in memory or cached read-models. Use deterministic $gap \times weight$ calculation before considering heavier ML models. | Bekzat | Open |
| **R-09** | Product | **Unsubstantiated AI Superiority Claims**<br>Asserting that complex models outperform baselines without empirical comparative evidence. | M | H | **Major** | Follow the evaluation plan in `08-verification-and-evaluation.md`: evaluate any advanced model strictly against the rule-based baseline using identical reference test profiles. | All | Open |

---

## 3. Status Definitions and Contingency Triggers

- **Open:** The risk is active and under ongoing monitoring.
- **Mitigated:** Preventative measures are actively implemented, reducing residual likelihood or impact.
- **Closed:** The milestone has passed or the risk condition is no longer applicable.

### Immediate Contingency Triggers
1. **If user interview responses are insufficient by the internal deadline:** Fall back to structured secondary data analysis from public developer surveys (Stack Overflow 2024 Developer Survey, JetBrains State of Developer Ecosystem) as specified in `08-verification-and-evaluation.md`.
2. **If complex matching models cannot be calibrated before pre-defense:** Deploy the verified deterministic rules-based baseline ($gap \times weight$) as the primary demonstrator, documenting advanced models as planned future work.

---

## 4. Risk Review and Audit Log

| Date | Reviewer | Changes / Findings |
|---|---|---|
| 2026-10-15 | Bekzat Duisenbek | Initial baseline risk register skeleton created (`R-01` to `R-06`). |
| 2026-10-22 | Asylbek Agabekuly | Formalized complete risk management framework for `CL-11`. Added scoring matrix, expanded technical risks (`R-07` to `R-09`), defined DAG cycle risks, and documented contingency triggers. |
