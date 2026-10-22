# 10 — Supervisor Feedback and Supervision Log

**Document Version:** 1.0  
**Status:** Maintained — Task `CL-11`  
**Academic Supervisor:** Praveen Kumar  
**School:** School of Software Engineering, Astana IT University  
**Student Team:**  
- Duisenbek Bekzat Daniyaruly  
- Asaubaev Kuanysh Serzhanuly  
- Agabekuly Asylbek (Task Maintainer)  

---

## 1. Supervision Framework

Regular supervision ensures that the diploma project maintains academic rigor, sound engineering practices, and adherence to university pre-defense deadlines. This document tracks formal supervision meetings, supervisor directives, team responses, and resulting project improvements.

---

## 2. Meeting and Feedback Log

### Meeting 1: Topic Approval and Scope Formulation
- **Date:** 2 October 2026  
- **Attendees:** Praveen Kumar (Supervisor), Duisenbek Bekzat, Asaubaev Kuanysh, Agabekuly Asylbek  
- **Format:** Formal In-Person Consultation  
- **Context:** Official application submission for thesis topic approval: *«Design and Development of an Intelligent Skill Gap Analysis and Personalized Career Recommendation System»*.

#### Discussion Summary:
The team presented the initial project vision: an intelligent platform to help students understand why they struggle to transition from academic study into junior IT roles. The supervisor evaluated the title, technical feasibility, and academic scope.

#### Supervisor Directives & Actions Taken:

| # | Feedback & Recommendations | Team Decision & Action Taken | Responsible | Status |
|---|---|---|---|---|
| **1.1** | **Avoid generic course aggregator trap:** The project must not become merely another directory of online courses. The core research and engineering focus must be on *skill gap analysis* and *personalized development roadmaps*. | Structured the project around 4 core modules: Profile Entry, Deterministic/Intelligent Gap Computation, Roadmap Dependency Generation, and Progress Tracking. Documented in `01-project-proposal.md`. | All | Completed |
| **1.2** | **Constrain MVP scope:** Do not attempt to cover the entire IT industry. Focus on 1–2 well-defined benchmark roles to validate the algorithmic model. | Anchored the MVP on *Junior Flutter Developer* (and secondary *Junior Backend Developer*). Excluded native apps and wide cross-industry scraping in `06-requirements-specification.md`. | Bekzat, Asylbek | Completed |
| **1.3** | **Anchor requirements in empirical evidence:** Distinguish verified user findings from subjective assumptions through direct user discussions. | Designed a user research plan (`02-relevance-evidence.md`) with 5 targeted interview questions for real students and junior developers. | Asylbek | In Progress |
| **1.4** | **Define an objective evaluation baseline:** Any intelligent or machine learning recommendation approach must be tested against a deterministic rules-based baseline ($gap \times weight$) before claiming accuracy advantages. | Formalized baseline formula and quantitative metrics (p95 latency $\le 2.5\text{ s}$, SUS $\ge 75$, gap agreement $\ge 80\%$) in `08-verification-and-evaluation.md`. | Bekzat | Completed |

---

### Checkpoint 2: Stage 1 / Pre-Defense 1 Deliverables Review
- **Date:** 22–24 October 2026 (Scheduled)  
- **Attendees:** Praveen Kumar, Project Team  
- **Deliverables Submitted for Review:**
  1. Complete Git repository structure and documentation (`docs/01` to `docs/10`).
  2. Literature review table with $\ge 12$ sources (`docs/03-literature-review.md`).
  3. System and technology comparisons (`docs/04`, `docs/05`).
  4. Formal IEEE 830 / ISO 25010 requirements specification with Gherkin acceptance criteria (`docs/06-requirements-specification.md`).
  5. UML Use Case and Component Architecture diagrams (`docs/07-architecture/`).
  6. Verification and evaluation plan with measurable criteria (`docs/08-verification-and-evaluation.md`).
  7. Risk register (`docs/09-risk-register.md`).

#### Current Status:
> **Status Note:** Deliverables have been prepared, internally reviewed across team members, and submitted to the supervisor ahead of the 24 October milestone. Specific feedback and action items resulting from the formal supervisor review will be logged in the table below immediately upon receipt.

| # | Expected Feedback Item | Proposed Action | Responsible | Status |
|---|---|---|---|---|
| **2.1** | Supervisor review of literature coverage and scientific depth. | Incorporate suggested citations and refine critical analysis table. | Kuanysh | Pending Review |
| **2.2** | Supervisor review of architectural component boundaries. | Adjust interface contracts and dependency directions if flagged. | Bekzat | Pending Review |
| **2.3** | Supervisor sign-off on requirements and evaluation methodology. | Finalize test procedures prior to prototype implementation phase. | Asylbek | Pending Review |

---

## 3. Evidence of Meaningful Project Improvements

The engagement with supervisor Praveen Kumar has directly resulted in key architectural and methodology refinements:

1. **Shift to Verifiable Engineering:** Rather than building an unconstrained web application, the project adopted rigorous verification metrics (`08-verification-and-evaluation.md`), establishing a clear baseline ($gap = \max(0, req - curr)$) to ensure scientific validity.
2. **Defensive Scope Management:** The initial ambition to cover multiple unrelated software careers was reduced to an in-depth benchmark profile, preventing scope creep and ensuring prototype feasibility.
3. **Traceability Standards:** Implementation of bidirectional traceability from Use Cases to Requirements to Test Cases, ensuring that all code written in subsequent phases directly satisfies approved specifications.

---

## 4. Outstanding Actions and Next Steps

| # | Action Description | Responsible | Target Deadline | Status |
|---|---|---|---|---|
| **A-01** | Conduct Pre-Defense 1 presentation and record committee feedback. | All Team Members | 24 October 2026 | Scheduled |
| **A-02** | Schedule post-predefense debriefing meeting with supervisor Praveen Kumar. | Duisenbek Bekzat | 26 October 2026 | Scheduled |
| **A-03** | Finalize technology selection based on committee and supervisor recommendations. | Asaubaev Kuanysh | 27 October 2026 | Open |
| **A-04** | Initiate UI wireframing and clickable prototype development based on approved requirements. | Agabekuly Asylbek | 28 October 2026 | Open |
