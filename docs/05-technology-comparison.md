
# 05 — Technology Comparison

**Status:** Draft — proposed technology choices pending team confirmation
**Responsible:** Kuanysh Asaubaev
**Project:** CareerLens
**Purpose:** Justify the proposed technology stack through a documented comparison of alternatives.

---

## 1. Introduction

CareerLens is a proposed web-based system that helps students, recent graduates, and early-career professionals identify skill gaps relative to a selected software-engineering role. The system compares self-reported skill levels with a curated competency profile, prioritizes missing competencies, and provides explainable learning recommendations.

The technology stack must support an interactive user interface, a maintainable backend API, structured role and skill data, and a reproducible skill-gap analysis process.

This document compares alternative technologies using consistent evaluation criteria and explains their suitability for the CareerLens Minimum Viable Product (MVP).

**Important status note:** The project README and architecture documentation state that the final technology stack remains to be confirmed. The technologies recommended in this document are therefore preliminary proposals, not confirmed implementation decisions. The final selections must be approved by the project team.

## 2. Evaluation Criteria

The alternatives are evaluated using the following criteria.

| Criterion | Description | Importance |
|---|---|---|
| Development productivity | How efficiently the technology supports implementation of the required MVP features | High |
| Performance and scalability | Whether it can handle expected requests and data volumes without unnecessary complexity | Medium |
| Community support and documentation | Availability of official documentation, tutorials, libraries, and troubleshooting resources | High |
| Team familiarity | How easily the project team can learn, use, and maintain the technology | High |
| Security and maintainability | Support for secure development, modular architecture, validation, testing, and future changes | High |
| Deployment simplicity | How easily the technology can be configured, tested, and deployed for an academic project | Medium |

The comparison focuses on the needs of the initial MVP rather than hypothetical large-scale production requirements.

The team should prioritize technologies that are sufficiently capable, understandable, testable, and practical within the project timeline.

### 2.1 Scoring Method

A qualitative five-point scale is used to organize the comparison.

| Score | Interpretation |
|---|---|
| 1 | Poor fit for the project requirements |
| 2 | Limited fit; significant disadvantages |
| 3 | Acceptable fit with relevant trade-offs |
| 4 | Good fit for the expected requirements |
| 5 | Very good fit for the expected requirements |

Scores represent preliminary assessments based on the project requirements and documented technology capabilities. They are not results of performance benchmarks, team surveys, or practical experiments.

Team familiarity must be verified with the team before finalizing the scores. The scores should be revised if the team has substantially more experience with a different technology.

## 3. Frontend Framework

The frontend must provide a responsive interface for entering skill levels, selecting a target role, viewing prioritized gaps, and exploring personalized learning recommendations.

Three alternatives are considered: React, Vue.js, and Angular.

| Criterion | React | Vue.js | Angular |
|---|---|---|---|
| Development productivity | 4 — reusable components and a flexible ecosystem | 5 — approachable component model and relatively simple entry point | 3 — comprehensive framework with more conventions |
| Performance and scalability | 4 — suitable for interactive web applications | 4 — suitable for the planned interface | 4 — suitable for structured applications |
| Community support and documentation | 5 — extensive ecosystem and documentation | 4 — strong documentation and community | 5 — extensive documentation and tooling |
| Team familiarity | 3 — must be confirmed | 3 — must be confirmed | 3 — must be confirmed |
| Security and maintainability | 4 — supports modular components and testing practices | 4 — supports modular components and testing practices | 4 — structured conventions support maintainability |
| Deployment simplicity | 4 — straightforward production build and static asset deployment | 5 — straightforward development and build workflow | 3 — more framework configuration and tooling |
| **Preliminary total** | **24/30** | **25/30** | **22/30** |

*Note: Scores are preliminary judgments, not measured results. Team familiarity is provisionally scored equally because the available project documentation does not establish the team's relative experience with these frameworks.*

### 3.1 Proposed Selection: React

React is proposed as the frontend framework because CareerLens requires a component-based interface with multiple related views and interactive analysis results.

Potential advantages include:

- Reusable interface components for skill inputs, gap summaries, charts, and recommendations.
- Flexibility when organizing screens and application state.
- Extensive documentation and a large ecosystem of supporting libraries.
- The ability to develop the frontend separately from the backend API.

Vue.js is also a strong alternative, particularly if the team prefers its integrated approach and simpler initial learning experience. Angular provides a more comprehensive framework but may introduce additional structure and tooling that are unnecessary for the initial MVP.

**Decision status:** React is the preliminary recommendation. The team must confirm its familiarity with React and approve the final frontend choice.

**Reference:** [S1]

## 4. Backend Platform

The backend must validate user input, coordinate application services, retrieve role and skill requirements, execute the analysis algorithm, and return structured results to the frontend.

The alternatives are FastAPI (Python), Node.js with Express, and Django REST Framework.

| Criterion | FastAPI (Python) | Node.js / Express | Django REST Framework |
|---|---|---|---|
| Development productivity | 5 — type hints, request validation, and automatic API documentation | 4 — flexible and lightweight, with more choices to configure | 4 — integrated tools for common web application requirements |
| Performance and scalability | 4 — suitable for the expected API workload | 4 — suitable for asynchronous request handling | 4 — suitable for typical API workloads |
| Community support and documentation | 4 — established documentation and Python ecosystem | 5 — extensive JavaScript ecosystem and community | 5 — mature Django ecosystem and documentation |
| Team familiarity | 3 — must be confirmed | 3 — must be confirmed | 3 — must be confirmed |
| Security and maintainability | 4 — supports validation and modular API design; additional security controls remain necessary | 4 — supports modular design; security depends on implementation and middleware | 5 — provides integrated features for common security and application concerns |
| Deployment simplicity | 4 — straightforward for a small Python API | 4 — straightforward for a small Node.js service | 3 — additional framework conventions and configuration may be required |
| **Preliminary total** | **24/30** | **24/30** | **24/30** |

*Note: Equal preliminary totals do not imply that the platforms are interchangeable in every situation. Team experience, implementation requirements, and deployment constraints may change the preferred option.*

### 4.1 Proposed Selection: FastAPI (Python)

FastAPI is proposed because CareerLens includes a skill-gap analysis process that may benefit from Python's data-processing and machine-learning ecosystem.

Potential advantages include:

- Request validation using typed data models.
- Automatically generated interactive API documentation.
- A modular structure for separating profile management, role catalogues, analysis, and recommendations.
- Access to Python libraries if semantic similarity or other analytical methods are evaluated later.

Node.js with Express would be a reasonable alternative if the team prefers JavaScript across the frontend and backend. Django REST Framework would be appropriate if the project needs more of Django's integrated application functionality.

The initial architecture does not require a machine-learning model. Therefore, Python's machine-learning ecosystem is a potential advantage rather than proof that FastAPI is the only suitable backend.

**Decision status:** FastAPI is the preliminary recommendation. The team must confirm the backend framework based on experience, integration needs, and deployment constraints.

**References:** [S4], [S5], [S6]

## 5. Database

CareerLens may need to store role definitions, required competencies, skill levels, importance weights, learning resource references, and evaluation results.

The architecture identifies an application database but also permits a small prototype to begin with version-controlled JSON. PostgreSQL, MongoDB, and SQLite are compared as potential database technologies.

| Criterion | PostgreSQL | MongoDB | SQLite |
|---|---|---|---|
| Development productivity | 4 — relational schema and SQL support structured data management | 4 — flexible document model for evolving records | 5 — minimal setup for a local prototype |
| Performance and scalability | 5 — suitable for relational queries and concurrent application workloads | 4 — suitable for document-oriented workloads | 3 — effective for small deployments, with write-concurrency limitations |
| Community support and documentation | 5 — mature documentation and ecosystem | 5 — extensive documentation and ecosystem | 5 — widely documented and broadly supported |
| Team familiarity | 3 — must be confirmed | 3 — must be confirmed | 3 — must be confirmed |
| Security and maintainability | 5 — constraints, transactions, and access-control capabilities | 4 — flexible schema, with integrity rules requiring careful design | 4 — simple storage with application and deployment constraints |
| Deployment simplicity | 3 — requires a database service or managed instance | 3 — typically requires a database service or managed instance | 5 — file-based database with minimal setup |
| **Preliminary total** | **25/30** | **23/30** | **25/30** |

*Note: The scores reflect different project trade-offs. PostgreSQL is favored for relational integrity, while SQLite is especially simple for a local prototype. Team familiarity remains unverified.*

### 5.1 Proposed Selection: PostgreSQL

PostgreSQL is proposed for a persistent version of CareerLens because the planned domain contains related entities, including roles, skills, competency requirements, and learning recommendations.

Potential advantages include:

- Relational tables and foreign keys for representing relationships between roles and skills.
- Constraints and transactions for maintaining data integrity.
- SQL support for retrieving and aggregating structured competency data.
- A mature ecosystem for application integration and deployment.

MongoDB may be appropriate if the data model becomes primarily document-oriented. SQLite may be sufficient for an early local prototype or a demonstration that does not require a separate database service.

The repository's `config/.env.example` currently contains a PostgreSQL-style `DATABASE_URL`. This indicates that PostgreSQL is represented in the configuration example, but it does not prove that the database has been implemented or formally approved.

**Decision status:** PostgreSQL is the preliminary recommendation. The team must confirm whether persistent database storage is required for the assessed MVP and whether PostgreSQL is the approved choice.

**References:** [S7], [S8], [S9]

## 6. Skill Gap Analysis Method

The analysis method must compare a user's declared skills with the requirements of a selected professional role.

The architecture already proposes an explainable, deterministic baseline:

\[
gap_i = \max(0, required_i - current_i)
\]

\[
priority_i = gap_i \times importance_i
\]

Here, `required_i` is the target proficiency level, `current_i` is the user-declared proficiency level, and `importance_i` is the importance assigned to the skill for the selected role.

This method provides a transparent basis for identifying missing competencies and prioritizing development needs. It does not, by itself, require a machine-learning model.

Three approaches to matching skill descriptions are considered: keyword matching, cosine similarity using TF-IDF, and sentence embeddings using SBERT.

| Criterion | Keyword Matching | Cosine Similarity (TF-IDF) | Sentence Embeddings (SBERT) |
|---|---|---|---|
| Development productivity | 5 — simple to implement | 4 — requires text vectorization and similarity calculation | 3 — requires model selection and inference integration |
| Performance and scalability | 5 — low computational cost for small catalogues | 4 — efficient for many sparse-text comparisons | 3 — model inference may require more resources |
| Community support and documentation | 4 — common technique with broad support | 5 — supported by established text-processing libraries | 4 — established documentation and pretrained models |
| Team familiarity | 3 — must be confirmed | 3 — must be confirmed | 3 — must be confirmed |
| Security and maintainability | 4 — easy to inspect, but rules may need maintenance | 4 — reproducible and inspectable, but vocabulary choices matter | 3 — model dependencies and model behavior require additional management |
| Deployment simplicity | 5 — minimal additional dependencies | 4 — moderate library requirements | 3 — model downloads, storage, and inference setup may be required |
| **Preliminary total** | **26/30** | **24/30** | **19/30** |

*Note: These scores describe implementation trade-offs for the proposed MVP. They do not establish the predictive accuracy of any method. Accuracy must be assessed experimentally using representative skill descriptions and reference judgments.*

### 6.1 Keyword Matching

Keyword matching checks whether skill names or terms appear in both a user's skill profile and a target-role description.

Advantages:

- Simple to implement and explain.
- Low computational cost.
- Easy to debug and reproduce.
- Suitable for a small curated catalogue with standardized skill names.

Limitations:

- May miss synonyms and semantically equivalent expressions.
- Depends on consistent terminology.
- May treat similar words as equivalent even when their meanings differ.

Keyword matching is a reasonable baseline for a small, controlled skill catalogue.

### 6.2 Cosine Similarity Using TF-IDF

TF-IDF represents text using weighted term vectors. Cosine similarity measures the similarity between those vectors.

Advantages:

- Considers the relative importance of terms within the available text.
- Provides a reproducible numerical similarity score.
- Can identify some textual relationships that exact keyword matching misses.
- Can be implemented using established text-processing libraries.

Limitations:

- Relies primarily on vocabulary overlap.
- Does not reliably understand meaning when descriptions use different words.
- Requires decisions about text preprocessing, vocabulary, and similarity thresholds.

TF-IDF is a suitable intermediate baseline if skill descriptions contain enough text to make vectorization useful.

### 6.3 Sentence Embeddings Using SBERT

Sentence-BERT-style models generate vector representations intended to capture semantic information from text. Similarity between skill descriptions can then be estimated using a measure such as cosine similarity.

Advantages:

- Can identify some semantically similar descriptions despite different wording.
- May help match skill descriptions written with synonyms or alternative expressions.
- Provides a possible extension beyond exact terms and sparse text vectors.

Limitations:

- Requires model selection and additional dependencies.
- Adds inference, resource, and deployment considerations.
- Similarity scores do not automatically represent proficiency levels or prove that a user possesses a skill.
- Results depend on the chosen model, input descriptions, and evaluation data.

SBERT is therefore a candidate for experimental evaluation rather than an assumed requirement of the initial MVP.

### 6.4 Recommended Approach

The initial MVP should use the deterministic rules-based skill-gap calculation described in the architecture documentation. The system should compare structured proficiency levels against role requirements and rank gaps using the documented importance weights.

Keyword matching or TF-IDF may be used to match alternative skill descriptions if this functionality is required. SBERT should be considered only if the team can evaluate it using representative data and a documented comparison.

The methods solve related but different problems:

- **Gap calculation** determines how far a declared proficiency level is below a target level.
- **Priority calculation** determines the relative importance of the gap.
- **Text matching** helps identify whether differently worded skill descriptions refer to similar competencies.
- **Recommendations** map identified gaps to curated learning actions.

Text similarity alone should not be treated as a measure of a user's actual proficiency.

**Decision status:** Rules-based gap calculation is the proposed baseline in the architecture. The final text-matching method remains open pending implementation requirements and evaluation.

**References:** [S10], [S11], [S12]

## 7. Proposed Technology Stack

Based on the preliminary comparison, the following stack is recommended for further team review.

| Component | Proposed Technology | Justification | Status |
|---|---|---|---|
| Frontend | React | Reusable components and a flexible approach to the interactive web interface | Proposed |
| Backend | FastAPI (Python) | Typed request validation, API documentation, and access to Python analytical libraries | Proposed |
| Database | PostgreSQL | Relational structure and integrity constraints for roles, skills, and related records | Proposed |
| Skill-gap calculation | Deterministic rules-based method | Transparent and reproducible calculation based on required and current proficiency | Proposed baseline in architecture |
| Skill-description matching | Keyword matching or TF-IDF baseline; SBERT evaluated only if justified | Allows comparison of simpler methods before adding model complexity | Pending evaluation |
| API communication | HTTPS requests between the frontend and backend | Consistent with the proposed web architecture | Proposed architectural approach |
| Testing | Automated tests and controlled evaluation cases | Supports reproducible verification of calculations and recommendations | Required project activity; tools to be selected |

These recommendations are intended to provide a practical starting point, not to claim that the application has already been implemented using these technologies.

The final stack should be confirmed against team familiarity, implementation feasibility, the assessed MVP scope, and the actual architecture approved by the team.

## 8. Decision Record

The following record distinguishes architectural guidance from decisions that still require team confirmation.

| Decision ID | Area | Proposed Decision | Reason | Status |
|---|---|---|---|---|
| TD-01 | Frontend | React | Component-based interface and ecosystem suitable for interactive results | Pending team confirmation |
| TD-02 | Backend | FastAPI (Python) | API validation, documentation, and access to Python analytical libraries | Pending team confirmation |
| TD-03 | Database | PostgreSQL, if persistent relational storage is required | Relational data model and integrity constraints | Pending team confirmation |
| TD-04 | Gap calculation | Deterministic rules-based calculation | Transparent and reproducible gap and priority scores | Proposed in architecture |
| TD-05 | Skill-description matching | Begin with a simple baseline; evaluate TF-IDF or SBERT if needed | Avoids unnecessary model complexity before evidence is available | Pending implementation and evaluation |
| TD-06 | Authentication | Defer unless required by the approved MVP | Reduces unnecessary scope and handling of personal data | Proposed in architecture |

### 8.1 Conditions for Final Approval

Before treating this record as final, the team should:

1. Confirm the frontend framework and backend platform based on team experience and integration requirements.
2. Confirm whether the MVP requires persistent storage and approve the database choice.
3. Agree on the proficiency scale, importance weights, and rules used to calculate skill gaps.
4. Decide whether text matching is necessary for the initial catalogue.
5. If an advanced matching method is introduced, define a baseline, representative test cases, and evaluation metrics.
6. Update the README and architecture documentation so they are consistent with the approved stack.
7. Record the final decisions and their rationale in this document.

## 9. Limitations and Risks

The comparison has several limitations.

- The ratings are qualitative assessments rather than benchmark results.
- Team familiarity has not been verified and may change the ranking of technologies.
- The actual deployment environment and expected workload have not yet been established.
- The final persistence and authentication requirements depend on the approved MVP scope.
- No experimental evidence currently establishes that SBERT would outperform keyword matching or TF-IDF for the CareerLens skill catalogue.
- A similarity score between descriptions does not independently validate a user's declared proficiency.
- Recommendations depend on the quality, relevance, and maintenance of the curated role catalogue and learning resources.

These limitations should be considered during implementation and evaluation. The selected approach should remain proportionate to the project scope and available time.

## 10. References

The following official documentation sources support the technology descriptions. They are not evidence that the team has selected or implemented a particular technology.

- [S1] React Documentation. *Describing the UI.* https://react.dev/learn/describing-the-ui
- [S2] Vue.js Documentation. *Introduction.* https://vuejs.org/guide/introduction.html
- [S3] Angular Documentation. https://angular.dev/
- [S4] FastAPI Documentation. https://fastapi.tiangolo.com/
- [S5] Express.js Documentation. https://expressjs.com/
- [S6] Django REST Framework Documentation. https://www.django-rest-framework.org/
- [S7] PostgreSQL Documentation. https://www.postgresql.org/docs/
- [S8] MongoDB Manual. https://www.mongodb.com/docs/manual/
- [S9] SQLite Documentation. https://www.sqlite.org/docs.html
- [S10] scikit-learn Documentation. *Working With Text Data.* https://scikit-learn.org/stable/tutorial/text_analytics/working_with_text_data.html
- [S11] scikit-learn Documentation. *Cosine Similarity.* https://scikit-learn.org/stable/modules/generated/sklearn.metrics.pairwise.cosine_similarity.html
- [S12] Sentence Transformers Documentation. https://sbert.net/

---

## Conclusion

React, FastAPI, and PostgreSQL form a plausible preliminary stack for the CareerLens MVP, subject to team approval. The initial skill-gap analysis should remain deterministic and explainable, using the rules-based calculations already described in the architecture.

Keyword matching and TF-IDF provide simpler options for matching skill descriptions. SBERT may be considered as an extension if an evaluation demonstrates sufficient benefit to justify its additional complexity.

The final technology choices must be approved by the project team and reflected consistently in the project README, architecture diagrams, implementation, and evaluation plan.
