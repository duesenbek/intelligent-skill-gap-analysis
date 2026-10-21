# 08 — Verification and Evaluation Plan: CareerLens

**Document Version:** 1.0  
**Date:** October 2026  
**Status:** Complete Plan (Provisional Acceptance Targets)  
**Lead Author:** Asylbek Agabekuly (Evaluation Support & Usability)  
**Co-Authors:** Bekzat Duisenbek (Architecture & Performance Testing), Kuanysh Assaubayev (Algorithm Evaluation)  
**Academic Supervisor:** Praveen Kumar (Astana IT University)  

---

## 1. Purpose

This plan defines how CareerLens will be systematically verified and evaluated. The evaluation focuses on:
- Functional correctness across all core user workflows,
- Quality and consistency of skill-gap identification,
- Relevance, clarity, and actionability of personalized career recommendations,
- User experience and system usability,
- Backend API response latency and throughput under realistic test conditions.

> [!IMPORTANT]
> All target metrics stated in this document are **provisional acceptance targets**. They must not be interpreted or reported as achieved results until the empirical experiments, benchmarking, and user studies have been completed.

---

## 2. Evaluation Questions (Research Questions)

The evaluation is structured around four primary research questions:

- **RQ1 (Algorithm Correctness):** Does the system correctly identify skill gaps between a user's declared competencies and the defined requirements of a selected professional role?
- **RQ2 (Recommendation Quality):** Do the generated personalized recommendations accurately address the identified skill gaps and reflect their relative priority?
- **RQ3 (Usability & Autonomy):** Can intended target users (students and early-career engineers) navigate the interface, configure their profile, and comprehend the resulting diagnostic reports without external assistance?
- **RQ4 (Performance Baseline):** Does the gap analysis and recommendation endpoint satisfy the proposed response-time target under specified test conditions and concurrent loads?

---

## 3. Verification & Evaluation Methods

### 3.1 Functional Testing
- **Scope:** Verifies profile creation/input, role selection, competency delta computation, priority sorting, recommendation rendering, edge-case validation, and error messaging.
- **Methodology:** Automated unit and end-to-end integration test suites targeting business logic and REST endpoints.
- **Responsible:** Bekzat Duisenbek.

### 3.2 Algorithm Testing & Benchmark Comparison
- **Scope:** Evaluates the deterministic gap identification heuristic:
  $$\text{gap}_i = \max(0, \text{required}_i - \text{current}_i)$$
  $$\text{priority}_i = \text{gap}_i \times \text{importance}_i$$
- **Methodology:** Execution against a curated test dataset containing 25+ benchmark profiles with manually verified ground truth labels. Evaluates precision, recall, and rank correlation against reference orders.
- **Responsible:** Kuanysh Assaubayev.

### 3.3 Expert Review
- **Scope:** Independent qualitative evaluation of generated skill gap diagnoses and learning roadmaps.
- **Methodology:** A sample of 15 generated profile reports will be blinded and evaluated by 3 industry software engineers / tech leads against a structured evaluation rubric (relevance, priority accuracy, resource suitability). Inter-rater agreement will be calculated.
- **Responsible:** Kuanysh Assaubayev & Asylbek Agabekuly.

### 3.4 Usability Testing (System Usability Scale — SUS)
- **Scope:** Assessment of UI/UX clarity, visual gap charts, and task efficiency with real target users.
- **Methodology:** 
  - Standard 10-item System Usability Scale (SUS) questionnaire (Brooke, 1996; Lewis, 2018) administered immediately after task completion.
  - Participant cohort: Minimum of 15 university students from Astana IT University (SE-2417, SE-2409, SE-2422).
  - Test scenario: Select target role (e.g., Junior Backend Developer) $\rightarrow$ complete skill inventory $\rightarrow$ review gap diagnosis $\rightarrow$ identify next concrete learning action.
- **Responsible:** Asylbek Agabekuly.

### 3.5 Performance & Load Testing
- **Scope:** Analysis endpoint latency and stability.
- **Methodology:** Automated benchmarking (k6 / Locust) measuring median, 90th, and 95th percentile response times across 100 repeated requests under single-user and concurrent load (10 virtual users). Documented testing hardware and network latency parameters.
- **Responsible:** Bekzat Duisenbek.

---

## 4. Proposed Evaluation Metrics

| Metric | Proposed Target | Measurement Methodology |
|---|---:|---|
| **Functional Test Pass Rate** | 100% of mandatory tests | $\frac{\text{Passed mandatory tests}}{\text{Total mandatory tests}} \times 100\%$ |
| **Skill-Gap Agreement** | $\ge 80\%$ | Element-wise agreement (F1-score / Cohen's $\kappa$) between system output and independent expert reference labels |
| **Recommendation Relevance** | $\ge 4.0 \,/\, 5.0$ | Mean Likert score from participant evaluation rubric across 3 dimensions: relevance, feasibility, clarity |
| **Analysis Response Time ($P_{95}$)** | $\le 2.5$ seconds | 95th percentile response latency under documented local/staging deployment |
| **Core Algorithm Test Coverage** | $\ge 75\%$ | Line and branch coverage reported by automated test runner (`pytest-cov` / `c8`) |
| **System Usability Scale (SUS)** | $\ge 75 \,/\, 100$ | Standardized SUS score calculation across all completed participant surveys |

> [!NOTE]
> These targets are provisional. The final evaluation report will document the actual sample sizes, environmental parameters, observed empirical distributions, and statistical confidence intervals.

---

## 5. Dataset and Reference Labels

### 5.1 Dataset Composition
The evaluation benchmark consists of:
1. **Role Requirement Baselines:** Formal competency models for 3 initial target roles:
   - Junior Backend Developer (Python / Node.js)
   - Junior Frontend Developer (JavaScript / TypeScript / React)
   - Junior Data Analyst / ML Assistant
2. **User Profiles ($N = 25$):**
   - 10 typical university student profiles (based on actual curriculum coursework),
   - 5 boundary/edge-case profiles (zero experience, fully mastered senior level, contradictory skill inputs),
   - 5 career-switcher profiles (e.g., QA transitioning to Backend),
   - 5 incomplete/minimal input profiles to evaluate graceful degradation.

### 5.2 Reference Labeling Procedure
- Reference labels (expected gaps and expected priority ordering) are established independently of the algorithmic implementation by manual consensus between two evaluators.
- Ambiguities and disagreements are recorded in an evaluation audit log.
- Synthetic profiles are utilized strictly for algorithmic validation and never presented as claims of organic market adoption.

---

## 6. Acceptance Criteria

The system will be verified against the following non-negotiable criteria:
1. **Input Validation:** Incomplete, out-of-range, or malicious inputs must be rejected with informative, human-readable validation errors.
2. **Deterministic Gap Identification:** For every test profile in the benchmark suite, the gap engine must correctly flag all missing or below-threshold skills according to the defined threshold criteria.
3. **Actionable Rationale:** Every recommendation item must explicitly state the underlying gap reason (e.g., *"Required: Level 3 (Intermediate) · Current: Level 1 (Novice) · Gap: 2"*).
4. **Reproducible Test Suite:** All functional and unit test cases must run to completion in automated CI environments without manual intervention.
5. **Transparency in Reporting:** Any failed test cases, anomalous edge behaviors, or algorithmic limitations must be fully documented in the final thesis report rather than omitted.

---

## 7. Threats to Validity and Limitations

- **Small Sample Size:** The usability cohort ($N \ge 15$) is limited to Astana IT University students and may not fully represent all global self-taught developers.
- **Subjective Self-Assessment:** Users may exhibit cognitive bias (overconfidence or modesty) during skill input. Rubrics and behavioral descriptors are introduced to minimize variance.
- **Static Taxonomy Coverage:** The initial catalog is constrained to selected roles based on ESCO and O*NET taxonomies and may not reflect hyper-recent framework releases without periodic data updates.
- **No Direct Employment Claims:** The evaluation measures educational alignment and recommendation utility; it does **not** assert that following recommendations guarantees employment or predicts interview outcomes.

---

## 8. Reporting Format

The post-evaluation report (to be added to Section 9 of the final diploma documentation) will comprehensively detail:
- Complete hardware, software, and container runtime specifications,
- Anonymized demographic summary of test participants,
- Raw evaluation scores, median values, standard deviations, and confusion matrices,
- Qualitative user feedback transcripts and identified UX bottlenecks,
- Documented discrepancies between expected and observed results, along with proposed algorithmic enhancements.
