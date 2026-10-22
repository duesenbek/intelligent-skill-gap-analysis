# 06 — Requirements Specification

**Document Version:** 1.0  
**Status:** In Review — Task `CL-9`  
**Author:** Asylbek Agabekuly (SE-2422, `240612@astanait.edu.kz`)  
**Project:** CareerLens — Intelligent Skill Gap Analysis and Personalized Career Recommendation System  
**Traceable Artifacts:** Traced to `01-project-proposal.md`, `07-architecture/`, and `08-verification-and-evaluation.md`

---

## 1. Purpose and Scope

### 1.1 Purpose
This document provides a formal specification of the functional and non-functional requirements for the **CareerLens** web application. It defines the operational capabilities, architectural constraints, quality attributes, and measurable acceptance criteria necessary to verify that the system satisfies the diploma project aims and user needs.

### 1.2 System Scope
CareerLens is designed to assist university students, recent graduates, and early-career software engineering professionals in bridging the gap between academic/self-taught knowledge and industry expectations. The system evaluates the user's technical competencies against curated role profiles, computes prioritized skill gaps, and generates a structured, actionable development roadmap.

### 1.3 Standards Compliance
The requirements in this specification follow the structural guidelines of **IEEE Std 830-1998 / ISO/IEC/IEEE 29148:2018** (Systems and software engineering — Life cycle processes — Requirements engineering) and classify non-functional quality attributes in accordance with the **ISO/IEC 25010:2011** System and Software Quality Model.

---

## 2. Stakeholders and User Personas

| Stakeholder / Persona | Role Description | Key Motivations and Needs |
|---|---|---|
| **Student / Graduate (Primary User)** | A student or recent graduate seeking entry-level software engineering positions (e.g., Junior Flutter Developer, Junior Backend Developer). | Needs to understand why they are not passing interviews, which exact skills are missing, and which skills to learn first. |
| **Early-Career Professional** | A junior software engineer aiming to transition into a new technical stack or level up. | Needs an objective assessment of prerequisites and an efficient learning sequence. |
| **System Administrator / Curriculum Maintainer** | Project maintainer or faculty administrator responsible for maintaining benchmark role profiles. | Needs an extensible mechanism to add or update role competency profiles without code redeployment. |
| **Academic Supervisor / Evaluation Committee** | Praveen Kumar and academic evaluators at Astana IT University. | Requires traceable evidence, verifiable acceptance criteria, and adherence to sound engineering principles. |

---

## 3. Prioritization Framework (MoSCoW)

All requirements in this specification are prioritized using the **MoSCoW** convention:

- **Must Have (M):** Critical core capabilities mandatory for the MVP release candidate. Non-delivery means system failure.
- **Should Have (S):** High-priority features that significantly improve utility and user experience, planned for delivery immediately following MVP stabilization.
- **Could Have (C):** Desirable enhancements that will be considered only if time, evaluation, and compute resources permit.
- **Won't Have (W):** Features explicitly designated outside the scope of the current diploma project milestone.

---

## 4. Functional Requirements (FR)

### FR-01: Target Professional Role Selection
- **Description:** The system shall allow the user to browse and select a target professional role from a curated competency catalogue.
- **User Story:** *As a student, I want to select a target software role (e.g., Junior Flutter Developer), so that I can evaluate my skills against verified market expectations.*
- **Priority:** Must Have (M)
- **Traces to:** `UC-02 (Select Target Software Role)`, Test Case `TC-01`.
- **Acceptance Criteria (Gherkin format):**
  ```gherkin
  Scenario: Successful role selection from catalogue
    Given the CareerLens web application is loaded and the role catalogue contains valid profiles
    When the user navigates to the role selection interface
    Then the system shall display a searchable list of available roles with clear descriptions
    And when the user selects "Junior Flutter Developer", the system shall persist this selection for the active session.

  Scenario: Handling unavailable or invalid role request
    Given the user attempts to load a non-existent or corrupted role profile ID
    When the request is processed by the application
    Then the system shall display an informative error notification
    And fallback to the default catalogue view without crashing.
  ```

---

### FR-02: Current Skill Profile Inventory and Input
- **Description:** The system shall enable the user to input their self-declared technical proficiency across competency domains on a validated 1 to 5 Likert scale.
- **User Story:** *As an applicant, I want to record my current skill levels (e.g., Dart: 3/5, State Management: 2/5), so that the system knows my baseline knowledge.*
- **Priority:** Must Have (M)
- **Traces to:** `UC-01 (Enter / Update Skill Profile)`, Test Case `TC-02`.
- **Acceptance Criteria:**
  ```gherkin
  Scenario: Valid skill entry and persistence
    Given the user has selected a target role
    When the user enters integer skill levels between 1 and 5 for the listed competencies
    And clicks "Save Skill Profile"
    Then the system shall accept and store the inputs in the application state
    And display a visual summary confirming the submitted ratings.

  Scenario: Out-of-bounds or non-numeric input validation
    Given the skill input form is open
    When the user enters a non-integer, negative value, or number greater than 5 (e.g., 6 or "expert")
    Then the system shall flag the field with an inline validation error: "Values must be an integer between 1 and 5"
    And prevent calculation until all invalid fields are corrected.
  ```

---

### FR-03: Algorithmic Skill-Gap Computation
- **Description:** The system shall compute quantitative skill gaps by comparing the user's declared proficiency with benchmark competency thresholds defined in the target role profile.
- **User Story:** *As an engineer, I want the system to calculate the exact difference between what I know and what the industry requires, so that I have an objective assessment.*
- **Priority:** Must Have (M)
- **Traces to:** `UC-03 (Run Skill-Gap Analysis)`, Test Case `TC-03`.
- **Baseline Formula:**
  $$\text{gap}_i = \max\left(0, \text{required\_level}_i - \text{current\_level}_i\right)$$
- **Acceptance Criteria:**
  ```gherkin
  Scenario: Correct gap calculation against reference threshold
    Given a target competency requires level 4
    When a user inputs current proficiency level 2
    Then the system shall compute a skill gap of exactly 2.0.

  Scenario: No gap when user meets or exceeds requirement
    Given a target competency requires level 3
    When a user inputs current proficiency level 4 or 5
    Then the computed skill gap shall be 0.0
    And the skill shall be marked as "Satisfied".
  ```

---

### FR-04: Skill Gap Prioritization and Ranking
- **Description:** The system shall order identified skill gaps by a composite priority score incorporating gap magnitude and market importance weight.
- **User Story:** *As a student with limited study time, I want to see which gaps are most critical to fix first, so that I do not waste time on low-priority topics.*
- **Priority:** Must Have (M)
- **Traces to:** `UC-04 (View Prioritized Skill Gaps)`, Test Case `TC-04`.
- **Baseline Priority Scoring:**
  $$\text{priority\_score}_i = \text{gap}_i \times \text{importance\_weight}_i$$
- **Acceptance Criteria:**
  ```gherkin
  Scenario: Ranking gaps in descending priority order
    Given the user has computed gaps for multiple competencies:
      | Skill | Gap | Importance Weight |
      | State Management (Bloc) | 2.0 | 0.9 |
      | CI/CD Pipeline Basics   | 2.0 | 0.4 |
      | Widget Lifecycle        | 1.0 | 0.8 |
    When the prioritization engine executes
    Then the system shall order the gaps as:
      1. State Management (Score: 1.80)
      2. CI/CD Pipeline Basics (Score: 0.80)
      3. Widget Lifecycle (Score: 0.80)
    And resolve tie scores deterministically based on prerequisite hierarchy.
  ```

---

### FR-05: Personalized Learning Roadmap Generation
- **Description:** The system shall generate a structured learning path consisting of sequential milestones and curated learning objectives linked directly to the prioritized skill gaps.
- **User Story:** *As a learner, I want a step-by-step roadmap indicating prerequisites and study topics, so that I can systematically acquire the missing skills.*
- **Priority:** Must Have (M)
- **Traces to:** `UC-05 (View Personalized Learning Recommendations)`, Test Case `TC-05`.
- **Acceptance Criteria:**
  ```gherkin
  Scenario: Roadmap dependency ordering
    Given a user has identified gaps in both "Dart Asynchronous Programming" and "Flutter Riverpod State Management"
    When the roadmap is generated
    Then "Dart Asynchronous Programming" must be placed before "Riverpod State Management" in the roadmap sequence
    Because foundational language concepts are designated prerequisites for framework-level state management.
  ```

---

### FR-06: Interactive Web Interface and Visual Reports
- **Description:** The system shall present analysis results through an accessible, responsive web interface including gap summary cards, radar/bar comparison charts, and milestone checklists.
- **User Story:** *As a visual learner, I want clear graphical representations of my skill profile versus the target profile, so that I can quickly interpret my progress.*
- **Priority:** Must Have (M)
- **Traces to:** `UC-04`, `UC-06`, Test Case `TC-06`.
- **Acceptance Criteria:**
  ```gherkin
  Scenario: Interactive visualization rendering
    Given the gap analysis has completed successfully
    When the results dashboard loads in a modern web browser
    Then the interface shall display:
      1. A visual comparison chart (target vs. current profile)
      2. A prioritized table of missing competencies
      3. An actionable roadmap checklist.
  ```

---

### FR-07: Analysis Session Persistence and Retrieval
- **Description:** The system shall allow users to store their evaluation session and retrieve previous analysis results for progress tracking.
- **User Story:** *As a user returning after a week of study, I want to retrieve my previous skill profile, so that I do not have to re-enter all my data from scratch.*
- **Priority:** Should Have (S)
- **Traces to:** `UC-01`, `UC-07`, Test Case `TC-07`.
- **Acceptance Criteria:**
  ```gherkin
  Scenario: Session state restore
    Given the user has completed an analysis session and saved their progress
    When the user reopens the application with a valid session identifier
    Then the system shall restore the previously selected role, skill inputs, and computed roadmap.
  ```

---

### FR-08: Transparent Rationale and Recommendation Explanation
- **Description:** The system shall provide an explicit textual explanation for each recommendation, showing the underlying gap value, weight, and reasoning.
- **User Story:** *As a skeptical student, I want to know why a specific library is recommended to me, so that I can trust the advice.*
- **Priority:** Should Have (S)
- **Traces to:** `UC-06 (Review Analysis Explanation)`, Test Case `TC-05`.
- **Acceptance Criteria:**
  ```gherkin
  Scenario: Displaying computation explanation
    Given a user inspects a prioritized recommendation item
    When the user clicks the "Why this recommendation?" toggle
    Then the system shall display the exact arithmetic breakdown: (Gap: X × Market Weight: Y = Priority Z)
    And display the competency description justifying its relevance.
  ```

---

## 5. Non-Functional Requirements (NFR)

In accordance with **ISO/IEC 25010:2011**, non-functional requirements are categorized as follows:

| ID | Quality Category | Requirement Statement | Target Metric & Measurement Condition | Verification Method |
|---|---|---|---|---|
| **NFR-01** | **Performance Efficiency** | The skill gap analysis and roadmap generation endpoint shall respond within acceptable human interaction thresholds. | Latency $\le 2.5\text{ s}$ at the 95th percentile (p95) under a simulated load of 20 concurrent requests on local/staging environment. | Automated load testing (`TC-08`) |
| **NFR-02** | **Usability (Learnability)** | A target user shall be able to complete the core flow (role selection, skill rating, roadmap viewing) without external training or manual intervention. | System Usability Scale (SUS) score $\ge 75/100$ evaluated across a sample of at least 15 representative students. | Usability evaluation test (`TC-09`) |
| **NFR-03** | **Security & Privacy** | The system shall not store passwords, secret keys, or personally identifiable data (PII) in plaintext or version control. | Zero secret violations on Git commits; configuration parameters isolated in `.env` files conforming to `.env.example`. | Static code analysis & configuration audit (`TC-10`) |
| **NFR-04** | **Maintainability & Extensibility** | A domain expert or administrator shall be able to add a new role competency profile without modifying application source code or triggering rebuilds. | New profile loaded via external JSON configuration/database seed and verified operational within 5 minutes. | Integration test (`TC-11`) |
| **NFR-05** | **Reliability & Fault Tolerance** | The application shall handle network dropouts or backend latency gracefully without loss of user input state. | Client-side input state retained in browser storage (e.g., localStorage/sessionStorage); zero uncaught front-end exceptions. | Fault injection testing |
| **NFR-06** | **Portability & Compatibility** | The web application interface shall render functionally and responsively across contemporary standard browsers. | Certified functional on Chromium-based browsers (Google Chrome $\ge 110$, Edge $\ge 110$), Mozilla Firefox ($\ge 115$), and Safari ($\ge 16$). | Cross-browser compatibility suite |

---

## 6. Traceability Matrix

This matrix establishes bidirectional traceability between business requirements, use cases, architectural components, and verification test cases.

| Requirement ID | Use Case ID | Architecture Component | Verification Test Case |
|---|---|---|---|
| **FR-01** | `UC-02` | `RoleCatalogueService` / Web UI | `TC-01` |
| **FR-02** | `UC-01` | `ProfileController` / `InputValidator` | `TC-02` |
| **FR-03** | `UC-03` | `SkillGapEngine` | `TC-03` |
| **FR-04** | `UC-04` | `PrioritizationEngine` | `TC-04` |
| **FR-05** | `UC-05` | `RoadmapGenerator` | `TC-05` |
| **FR-06** | `UC-04`, `UC-06` | `WebClient (UI Dashboard)` | `TC-06` |
| **FR-07** | `UC-01`, `UC-07` | `PersistenceAdapter` / Storage | `TC-07` |
| **FR-08** | `UC-06` | `ExplanationFormatter` | `TC-05` |
| **NFR-01** | `UC-03` | Core API & Engine Services | `TC-08` |
| **NFR-02** | `UC-01` – `UC-06` | Web Client UX Flow | `TC-09` |
| **NFR-03** | All | Application Configuration & Auth | `TC-10` |
| **NFR-04** | `UC-07` | `RoleCatalogueRepository` | `TC-11` |

---

## 7. Project Boundaries and Out-of-Scope Items

To prevent scope creep and ensure rigorous execution within the diploma timeline, the following capabilities are explicitly designated as **Won't Have (Out of Scope)** for the MVP:

1. **Broad Occupational Coverage:** The MVP will not attempt to model every IT specialization; it focuses strictly on benchmark software engineering roles (e.g., Junior Flutter Developer, Junior Backend Developer).
2. **Guaranteed Employment / Hiring Predictions:** The system will not guarantee employment or claim automated recruitment matching.
3. **Live Job Portal Scraping at Runtime:** The MVP will utilize curated, verified competency datasets rather than real-time web scraping of unstable job boards.
4. **Native Mobile Clients:** The platform is engineered strictly as a responsive web application; standalone iOS/Android native applications are excluded.
5. **Unvalidated Autonomous AI Claims:** No claims of black-box LLM superiority will be asserted without empirical validation against the deterministic benchmark defined in `08-verification-and-evaluation.md`.

---

## 8. Open Questions and Revision History

### 8.1 Open Questions
- **Q-01:** Should the Likert scale for user proficiency retain 5 levels or be reduced to 4 levels to eliminate the neutral midpoint? *(Current consensus: Retain 1–5 scale consistent with European e-Competence Framework).*
- **Q-02:** Will external course links be static curated resources or dynamically queried? *(Current consensus: Curated static references for the MVP to guarantee link validity).*

### 8.2 Revision History
| Version | Date | Author | Description of Changes |
|---|---|---|---|
| 0.1 | 2026-10-15 | Bekzat Duisenbek | Initial skeleton and high-level requirement list |
| 1.0 | 2026-10-22 | Asylbek Agabekuly | Formalized complete IEEE 830 / ISO 25010 specification, Gherkin acceptance criteria, MoSCoW prioritization, and traceability matrix for task `CL-9`. |
