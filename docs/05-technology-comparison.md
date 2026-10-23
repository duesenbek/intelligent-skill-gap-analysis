# 05 — Technology Comparison

**Status:** Selected technology stack — agreed by the project team
**Responsible:** Kuanysh Asaubaev
**Project:** CareerLens
**Purpose:** Compare relevant technology alternatives and justify the selected stack for the CareerLens Minimum Viable Product (MVP).

---

## 1. Introduction

CareerLens is a web-based system designed to help university students, recent graduates, and early-career professionals identify skill gaps relative to a selected software-engineering role. The system compares self-assessed skill levels with a curated competency profile, prioritizes missing competencies, and provides personalized learning recommendations.

The system requires a responsive frontend, a maintainable backend API, structured storage for roles and competencies, a reproducible skill-gap analysis process, and a testing strategy that verifies the correctness of its calculations.

The project team has selected the following technology stack for the CareerLens MVP:

- **Frontend:** React + TypeScript + Vite
- **CSS framework:** Tailwind CSS
- **Backend:** Python + FastAPI
- **Database and hosting:** Supabase Managed PostgreSQL
- **ORM and migrations:** SQLAlchemy + Alembic, if adopted by the team
- **Skill-gap analysis:** Python rules-based calculation
- **Testing:** Pytest
- **Version control and task tracking:** GitHub + YouTrack

This document compares alternatives for the main architectural choices, explains the rationale for the selected stack, and identifies relevant limitations and risks.

**Decision status:** The project team has selected the technology stack described in this document for the CareerLens MVP. SQLAlchemy and Alembic remain conditional on the team's decision about ORM usage and database migrations. Technology selection does not mean that implementation or deployment has already been completed.

## 2. Evaluation Criteria

The alternatives are evaluated using consistent criteria.

| **Criterion** | **Description** | **Importance** |
|---|---|---|
| Setup complexity | Effort required to install, configure, and integrate the technology | High |
| Development productivity | How efficiently the technology supports implementation of MVP features | High |
| Security and maintainability | Available security controls, validation, access management, and long-term maintainability | High |
| Testability | How easily functionality can be tested consistently and independently | High |
| Cost | Direct service costs and relevant infrastructure or maintenance costs | High |
| Delivery timeline | Expected setup and implementation effort within the academic project schedule | High |
| Community support and documentation | Availability of official documentation, libraries, and troubleshooting resources | Medium |
| Team familiarity | Existing experience and learning requirements for the project team | High |

The comparison focuses on a small academic MVP rather than hypothetical large-scale production requirements.

The ratings are preliminary qualitative assessments based on the project requirements. They are not results of performance benchmarks, team surveys, or controlled experiments. Team familiarity and actual implementation constraints should be considered when applying the results.

### 2.1 Scoring Method

A five-point scale is used where numerical ratings are appropriate.

| **Score** | **Interpretation** |
|---|---|
| 1 | Poor fit for the project requirements |
| 2 | Limited fit; significant disadvantages |
| 3 | Acceptable fit with relevant trade-offs |
| 4 | Good fit for the expected requirements |
| 5 | Very good fit for the expected requirements |

Scores summarize expected suitability for the CareerLens MVP. They should not be interpreted as measured performance or proof that one technology is universally better than another.

For cost, a higher score means a more favorable expected cost for the academic MVP. For setup complexity, a higher score means less setup effort.

## 3. Frontend Framework and Tooling

The frontend must allow users to select a target role, enter their current proficiency levels, view skill gaps, and explore recommendations.

Three frontend frameworks are considered: React, Vue.js, and Angular. TypeScript and Vite are evaluated as complementary tools for the selected React implementation.

| **Criterion** | **React** | **Vue.js** | **Angular** |
|---|---|---|---|
| Development productivity | 4 — reusable components and a flexible ecosystem | 5 — approachable component model and relatively simple entry point | 3 — comprehensive framework with more conventions |
| Performance and scalability | 4 — suitable for interactive web applications | 4 — suitable for the planned interface | 4 — suitable for structured applications |
| Community support and documentation | 5 — extensive ecosystem and documentation | 4 — strong documentation and community | 5 — extensive documentation and tooling |
| Team familiarity | 3 — must be confirmed | 3 — must be confirmed | 3 — must be confirmed |
| Maintainability | 4 — supports modular components and testing practices | 4 — supports modular components and testing practices | 4 — structured conventions support maintainability |
| Setup and deployment | 4 — straightforward with common build tools | 5 — straightforward development and build workflow | 3 — more framework conventions and tooling |
| **Preliminary total** | **24/30** | **25/30** | **22/30** |

*Note: These scores are preliminary assessments, not measured results. React is the team's selected choice even though Vue.js receives a slightly higher total in this initial comparison. The rationale and team familiarity should be considered when interpreting the scores.*

### 3.1 Selected Frontend: React + TypeScript + Vite

React is selected because CareerLens requires reusable interface components and interactive views for skill profiles, gap summaries, and recommendations.

Potential advantages include:

- Reusable components for skill inputs, gap summaries, charts, and recommendations.
- Flexibility when organizing screens and application state.
- A large ecosystem of supporting libraries and learning resources.
- Separation of frontend responsibilities from backend API logic.

TypeScript adds static type checking to JavaScript, helping identify certain errors during development and making component interfaces and API data structures easier to maintain.

Vite provides a development server and build tooling for the frontend. It supports a streamlined development workflow without requiring the team to configure a larger build system from scratch.

Tailwind CSS is selected for styling. Its utility-class approach can help the team implement consistent spacing, typography, layouts, and responsive interface elements.

Vue.js remains a reasonable alternative, particularly if a different team has substantially more experience with it. Angular offers a more comprehensive framework but may introduce additional conventions and tooling that are unnecessary for the initial MVP.

**Decision status:** React + TypeScript + Vite and Tailwind CSS are selected by the project team.

**References:** [S1], [S2], [S3], [S16], [S17], [S18]

## 4. Backend Platform

The backend must validate requests, retrieve role and skill requirements, execute the skill-gap calculation, and return structured results to the frontend.

The alternatives are FastAPI with Python, Node.js with Express, and Django REST Framework.

| **Criterion** | **FastAPI (Python)** | **Node.js / Express** | **Django REST Framework** |
|---|---|---|---|
| Development productivity | 5 — type hints, request validation, and automatic API documentation | 4 — flexible and lightweight, with more choices to configure | 4 — integrated tools for common web application requirements |
| Performance and scalability | 4 — suitable for the expected API workload | 4 — suitable for asynchronous request handling | 4 — suitable for typical API workloads |
| Community support and documentation | 4 — established documentation and Python ecosystem | 5 — extensive JavaScript ecosystem and community | 5 — mature Django ecosystem and documentation |
| Team familiarity | 3 — must be confirmed | 3 — must be confirmed | 3 — must be confirmed |
| Security and maintainability | 4 — supports validation and modular API design; additional security controls remain necessary | 4 — supports modular design; security depends on implementation and middleware | 5 — integrated features for common security and application concerns |
| Setup and deployment | 4 — suitable for a small Python API | 4 — suitable for a small Node.js service | 3 — additional framework conventions may be required |
| **Preliminary total** | **24/30** | **24/30** | **24/30** |

*Note: Equal preliminary totals do not mean that the frameworks are interchangeable in every situation. Team experience, integration requirements, and deployment constraints may change their suitability.*

### 4.1 Selected Backend: Python + FastAPI

FastAPI is selected because CareerLens uses Python for its rules-based skill-gap analysis and may later require additional data-processing libraries.

Potential advantages include:

- Request validation using typed data models.
- Automatically generated interactive API documentation.
- A modular structure for separating role catalogues, analysis, and recommendations.
- Access to Python testing and database libraries.
- A consistent language for backend services and skill-gap calculations.

Node.js with Express would be reasonable if the team preferred JavaScript across the frontend and backend. Django REST Framework would be appropriate if the project needed more of Django's integrated application functionality.

The initial architecture does not require machine learning. Python's analytical ecosystem is therefore a possible future advantage, not a requirement to introduce an ML model.

Security controls such as authentication, authorization, input validation, and secret management must be implemented according to the approved MVP requirements. FastAPI does not provide complete application security automatically.

**Decision status:** Python + FastAPI is selected by the project team.

**References:** [S4], [S5], [S6]

## 5. Database and Managed Database Platform

CareerLens may need to store role definitions, required competencies, proficiency levels, importance weights, learning resource references, and evaluation results.

PostgreSQL is a relational database engine. Supabase is a managed platform that provides hosted PostgreSQL and additional dashboard and platform services. Therefore, choosing Supabase means using PostgreSQL through a managed service rather than operating the database server independently.

Three options are compared:

1. **Supabase Managed PostgreSQL** — hosted PostgreSQL with a dashboard and managed platform services.
2. **Self-managed PostgreSQL** — PostgreSQL installed and operated by the project team on a local machine or server.
3. **MongoDB Atlas Free** — a managed document database representing a non-relational alternative.

### 5.1 Database Comparison

| **Criterion** | **Supabase Managed PostgreSQL** | **Self-managed PostgreSQL** | **MongoDB Atlas Free** |
|---|---|---|---|
| Setup complexity | 5 — hosted project and dashboard reduce infrastructure work | 2 — team configures installation, networking, access, updates, and backups | 4 — hosted cluster is quick to create, but the data model differs |
| Security | 4 — managed infrastructure helps, but credentials, access policies, and application security remain the team's responsibility | 3 — full control, but the team owns hardening, patching, access, and network exposure | 4 — managed infrastructure, but database users, network access, and application security still need configuration |
| Testability | 5 — PostgreSQL-compatible schema and standard SQL tools; local or isolated test databases are possible | 5 — full control over versions and local test instances | 4 — good driver and test support, but tests target different data and query semantics |
| Cost for an academic MVP | 5 — $0 within Free-plan quotas; inactivity pausing and lack of automatic backups are important limitations | 3 — software is free, but hosting, maintenance time, backups, and uptime have costs | 5 — free cluster within documented limits; storage and inactivity restrictions apply |
| Delivery timeline | 5 — less time spent on database infrastructure and dashboard setup | 2 — more time for deployment, monitoring, backups, and hardening | 4 — fast provisioning, but relational integrity may require more application-level work |
| **Preliminary total** | **24/25** | **15/25** | **21/25** |

*Note: These scores are qualitative planning estimates for the CareerLens MVP, not benchmark results. They should be revised if team experience, hosting requirements, or the approved data model differs from the assumptions.*

### 5.2 Selected Database and Hosting: Supabase Managed PostgreSQL

Supabase Managed PostgreSQL is selected because it preserves the relational PostgreSQL model while reducing the infrastructure work required from the student team.

CareerLens contains related entities such as roles, skills, competency requirements, and learning resources. These relationships can be represented using relational tables, foreign keys, and constraints.

Potential advantages include:

- A managed PostgreSQL instance and dashboard reduce initial setup effort.
- Relational tables, SQL, constraints, and transactions support data integrity.
- Standard PostgreSQL tooling and Python database libraries remain available.
- Less time is spent operating the database server than with a self-managed instance.
- The backend can connect through a PostgreSQL-compatible connection using a standard Python database driver.
- SQLAlchemy and Alembic can be added if the team decides to use an ORM and versioned schema migrations.

The managed service reduces infrastructure responsibilities but does not remove the need for secure application design.

The team must:

- Store database credentials in environment variables or an appropriate secret manager.
- Never commit credentials or private keys to GitHub.
- Use appropriately restricted database access.
- Validate and authorize backend requests.
- Avoid exposing privileged database credentials in the React frontend.
- Configure and test Row Level Security (RLS) if frontend access uses Supabase APIs.
- Never place the Supabase service-role key in client-side code.

If the backend connects directly to PostgreSQL, the backend must still protect its credentials, restrict database privileges, and validate user requests.

### 5.3 Supabase Free-Plan Constraints

The Supabase Free plan is intended as a possible hosting option for an academic prototype. The team must check the current pricing and documentation before promising a particular deployment date or availability level.

The official Supabase pricing and platform documentation have listed the following Free-plan limits:

- **Price:** $0 per month within the plan's quotas.
- **Database size:** 500 MB per project.
- **Egress:** 5 GB.
- **Cached egress:** 5 GB.
- **Free projects:** two free projects across organizations where the user is an owner or administrator.
- **Automatic database backups:** not included on the Free plan.
- **Project inactivity:** projects may be paused after a week of low activity and can be resumed from the dashboard.

These limits and policies can change. They should be verified directly against the official documentation before deployment.

The Free plan may be sufficient for a small classroom demonstration, depending on the size of the dataset and expected traffic. However, it does not guarantee uninterrupted availability or production-level data recovery.

The team should:

1. Monitor database size and traffic usage.
2. Export database backups regularly.
3. Test connection and schema migration procedures.
4. Verify that exported data can be restored.
5. Check project activity and resume a paused project if necessary.
6. Review paid hosting if continuous availability or managed backups are required.

**Deployment limitation:** Supabase Free is a possible MVP hosting option, not a guarantee of uninterrupted production hosting. Deployment commitments should be made only after verifying current quotas, inactivity policies, backup requirements, and team expectations.

### 5.4 Self-managed PostgreSQL

Self-managed PostgreSQL offers control over database versions, configuration, hosting, and maintenance schedules.

Potential advantages include:

- Full control over the database environment.
- The ability to reproduce a chosen database version locally.
- No dependency on a particular managed database provider.
- Standard PostgreSQL tools and SQL support.

However, the team becomes responsible for installation, network configuration, access control, updates, backups, monitoring, and availability. Hosting may also introduce costs even though PostgreSQL itself is open-source software.

For an academic MVP, these responsibilities may consume time that would otherwise be used to implement and evaluate CareerLens. A local PostgreSQL instance remains useful for development and automated testing even if Supabase is used for the hosted environment.

### 5.5 MongoDB Atlas Free

MongoDB Atlas Free is a managed document-database alternative that can be provisioned without operating a database server directly.

Potential advantages include:

- Managed database infrastructure.
- A document-oriented data model.
- A free cluster for eligible small projects within the plan's limitations.

However, CareerLens has explicit relationships between roles, skills, required proficiency levels, and learning recommendations. These relationships fit a relational data model naturally. MongoDB may still be appropriate if the approved data model changes, but it would introduce different query semantics and testing considerations.

The team should check MongoDB Atlas's current free-cluster limits before relying on it for deployment.

**Database decision status:** Supabase Managed PostgreSQL is selected by the project team as the database and hosting option. PostgreSQL remains the underlying database engine. The Free plan's current constraints must be checked before making deployment commitments.

**References:** [S7], [S8], [S9], [S13], [S14], [S15]

## 6. Skill Gap Analysis Method

The analysis method must compare a user's declared skills with the requirements of a selected professional role.

The selected MVP approach is a deterministic rules-based calculation. This approach is explainable and does not require a machine-learning model.

For each skill \(i\), the gap is:

$$
gap_i = \max(0, required_i - current_i)
$$

The priority of a skill gap is:

$$
priority_i = gap_i \times importance_i
$$

Here:

- `required_i` is the target proficiency level for the selected role.
- `current_i` is the user's declared proficiency level.
- `importance_i` is the importance assigned to the skill for that role.

The proficiency scale and importance weights must be defined consistently. The application should validate that input values are within the allowed range.

Three approaches to matching skill descriptions are considered: keyword matching, cosine similarity using TF-IDF, and sentence embeddings using SBERT.

| **Criterion** | **Keyword Matching** | **Cosine Similarity (TF-IDF)** | **Sentence Embeddings (SBERT)** |
|---|---|---|---|
| Development productivity | 5 — simple to implement | 4 — requires text vectorization and similarity calculation | 3 — requires model selection and inference integration |
| Performance and scalability | 5 — low computational cost for small catalogues | 4 — efficient for many sparse-text comparisons | 3 — model inference may require more resources |
| Community support and documentation | 4 — common technique with broad support | 5 — supported by established text-processing libraries | 4 — established documentation and pretrained models |
| Team familiarity | 3 — must be confirmed | 3 — must be confirmed | 3 — must be confirmed |
| Maintainability | 4 — easy to inspect, but rules may need maintenance | 4 — reproducible and inspectable, but vocabulary choices matter | 3 — model dependencies and behavior require additional management |
| Deployment simplicity | 5 — minimal additional dependencies | 4 — moderate library requirements | 3 — model downloads, storage, and inference setup may be required |
| **Preliminary total** | **26/30** | **24/30** | **19/30** |

*Note: These scores describe implementation trade-offs for the proposed MVP. They do not establish predictive accuracy. Accuracy must be evaluated experimentally using representative skill descriptions and reference judgments.*

### 6.1 Keyword Matching

Keyword matching checks whether skill names or terms appear in both a user's skill profile and a target-role description.

**Advantages:**

- Simple to implement and explain.
- Low computational cost.
- Easy to debug and reproduce.
- Suitable for a small curated catalogue with standardized skill names.

**Limitations:**

- May miss synonyms and semantically equivalent expressions.
- Depends on consistent terminology.
- May treat similar words as equivalent even when their meanings differ.

Keyword matching is a reasonable baseline for a small, controlled skill catalogue.

### 6.2 Cosine Similarity Using TF-IDF

TF-IDF represents text using weighted term vectors. Cosine similarity measures the similarity between those vectors.

**Advantages:**

- Considers the relative importance of terms within the available text.
- Provides a reproducible numerical similarity score.
- Can identify some textual relationships that exact keyword matching misses.
- Can be implemented using established text-processing libraries.

**Limitations:**

- Relies primarily on vocabulary overlap.
- Does not reliably understand meaning when descriptions use different words.
- Requires decisions about text preprocessing, vocabulary, and similarity thresholds.

TF-IDF is a suitable intermediate option if skill descriptions contain enough text to make vectorization useful.

### 6.3 Sentence Embeddings Using SBERT

Sentence-BERT-style models generate vector representations intended to capture semantic information from text. Similarity between skill descriptions can then be estimated using a measure such as cosine similarity.

**Advantages:**

- Can identify some semantically similar descriptions despite different wording.
- May help match descriptions that use synonyms or alternative expressions.
- Provides a possible extension beyond exact terms and sparse text vectors.

**Limitations:**

- Requires model selection and additional dependencies.
- Adds inference, resource, and deployment considerations.
- Similarity scores do not automatically represent proficiency levels or prove that a user possesses a skill.
- Results depend on the chosen model, input descriptions, and evaluation data.

SBERT is a candidate for future experimental evaluation, not a requirement of the initial MVP.

### 6.4 Selected Approach

The MVP uses the deterministic rules-based skill-gap calculation described above. It compares structured proficiency levels against role requirements and ranks gaps using documented importance weights.

Keyword matching or TF-IDF may be introduced if matching alternative skill descriptions becomes necessary. SBERT should be considered only if the team can evaluate it using representative data and a documented comparison.

These methods solve related but different problems:

- **Gap calculation** determines how far a declared proficiency level is below a target level.
- **Priority calculation** determines the relative importance of the gap.
- **Text matching** helps identify whether differently worded skill descriptions refer to similar competencies.
- **Recommendations** map identified gaps to curated learning actions.

Text similarity alone should not be treated as a measure of a user's actual proficiency.

**Decision status:** Python rules-based skill-gap analysis is selected for the MVP. The final text-matching method remains dependent on implementation requirements and evaluation.

**References:** [S10], [S11], [S12]

## 7. Selected Technology Stack

The following technology stack has been selected by the project team for the CareerLens MVP.

| **Component** | **Selected Technology** | **Justification** | **Status** |
|---|---|---|---|
| Frontend | React + TypeScript + Vite | Reusable components, static typing, and a streamlined development/build workflow | Selected by team |
| CSS framework | Tailwind CSS | Utility classes support consistent styling and rapid UI iteration | Selected by team |
| Backend | Python + FastAPI | Typed request validation, API documentation, and access to Python analytical libraries | Selected by team |
| Database and hosting | Supabase Managed PostgreSQL | Managed PostgreSQL and dashboard reduce infrastructure work; Free-plan limitations apply | Selected by team; verify quotas |
| ORM and migrations | SQLAlchemy + Alembic, if adopted | Python ORM and versioned schema migrations; adds dependencies and setup | Optional; pending team decision |
| Skill-gap calculation | Python deterministic rules-based method | Transparent and reproducible calculation based on required and current proficiency | Selected by team |
| Skill-description matching | Keyword matching or TF-IDF baseline; SBERT only if justified | Allows comparison of simpler methods before adding model complexity | Depends on implementation requirements |
| API communication | HTTPS requests between frontend and backend | Consistent with the proposed web architecture | Architectural approach |
| Testing | Pytest | Tests rules-based calculations, API endpoints, validation, and regressions | Selected by team |
| Version control and task tracking | GitHub + YouTrack | Version control, code review, task ownership, and project progress tracking | Selected by team |

The selected technologies define the intended implementation direction. They do not claim that the application has already been implemented or deployed.

SQLAlchemy and Alembic remain optional until the team confirms the need for an ORM and schema migration workflow.

## 8. Decision Record

This record documents the selected stack and distinguishes it from conditional implementation details.

| **Decision ID** | **Area** | **Selected Decision** | **Reason** | **Status** |
|---|---|---|---|---|
| TD-01 | Frontend | React + TypeScript + Vite | Component-based UI, static typing, and a streamlined development workflow | Selected by team |
| TD-02 | CSS framework | Tailwind CSS | Rapid and consistent interface styling | Selected by team |
| TD-03 | Backend | Python + FastAPI | API validation, documentation, and compatibility with Python analysis code | Selected by team |
| TD-04 | Database and hosting | Supabase Managed PostgreSQL | Relational data integrity with less self-managed infrastructure | Selected by team; verify Free-plan constraints |
| TD-05 | ORM and migrations | SQLAlchemy + Alembic | ORM and versioned schema migrations if required | Optional; pending team decision |
| TD-06 | Skill-gap calculation | Deterministic rules-based calculation | Transparent and reproducible gap and priority scores | Selected by team |
| TD-07 | Skill-description matching | Begin with a simple baseline; evaluate TF-IDF or SBERT if needed | Avoids unnecessary model complexity before evidence is available | Depends on implementation requirements |
| TD-08 | Testing | Pytest | Automated testing of calculations and API behavior | Selected by team |
| TD-09 | Collaboration and tracking | GitHub + YouTrack | Code review, version control, task ownership, and progress tracking | Selected by team |
| TD-10 | Authentication | Defer unless required by the approved MVP | Reduces unnecessary scope and handling of personal data | Depends on MVP requirements |

### 8.1 Implementation Conditions

The team should:

1. Keep the implementation consistent with the selected frontend and backend technologies.
2. Verify the current Supabase Free-plan limits before committing to deployment.
3. Decide whether SQLAlchemy and Alembic are needed for the MVP.
4. Define the proficiency scale and importance weights used in skill-gap calculations.
5. Decide whether text matching is necessary for the initial skill catalogue.
6. If an advanced matching method is introduced, define a baseline, representative test cases, and evaluation metrics.
7. Establish a database export and recovery procedure.
8. Update the README and architecture documentation to match the selected stack.
9. Record any changes to these decisions and their rationale.

## 9. Limitations and Risks

The comparison has several limitations and risks.

- The ratings are qualitative assessments rather than benchmark results.
- Team familiarity has not been independently verified and may affect the relative suitability of technologies.
- The actual deployment environment and expected workload have not yet been established.
- The final persistence and authentication requirements depend on the MVP scope.
- Supabase Free-plan quotas and policies may change and should be checked before deployment.
- The Free plan does not include automatic database backups, so a separate export and recovery procedure is necessary.
- A paused or unavailable managed database can affect a demonstration.
- Self-managed PostgreSQL requires additional work for deployment, security, updates, backups, and monitoring.
- MongoDB Atlas uses a different data model and query semantics from PostgreSQL.
- No experimental evidence currently establishes that SBERT would outperform keyword matching or TF-IDF for the CareerLens skill catalogue.
- Similarity between skill descriptions does not independently validate a user's declared proficiency.
- Recommendations depend on the quality, relevance, and maintenance of the curated role catalogue and learning resources.
- SQLAlchemy and Alembic add dependencies and workflow decisions; they should be adopted only if their benefits justify the additional setup.

These risks should be considered during implementation and evaluation. The selected approach should remain proportionate to the project scope and available time.

## 10. References

The following official documentation sources support the technology descriptions.

- [S1] React Documentation. *Describing the UI.* https://react.dev/learn/describing-the-ui
- [S2] Vue.js Documentation. *Introduction.* https://vuejs.org/guide/introduction.html
- [S3] Angular Documentation. https://angular.dev/
- [S4] FastAPI Documentation. https://fastapi.tiangolo.com/
- [S5] Express.js Documentation. https://expressjs.com/
- [S6] Django REST Framework Documentation. https://www.django-rest-framework.org/
- [S7] Supabase Pricing. Free-plan quotas and features. https://supabase.com/pricing
- [S8] Supabase Documentation. Project pausing on the Free plan. https://supabase.com/docs/guides/platform/free-project-pausing
- [S9] MongoDB Atlas Documentation. Free cluster limitations. https://www.mongodb.com/docs/atlas/reference/free-shared-limitations/
- [S10] scikit-learn Documentation. *Working With Text Data.* https://scikit-learn.org/stable/tutorial/text_analytics/working_with_text_data.html
- [S11] scikit-learn Documentation. *Cosine Similarity.* https://scikit-learn.org/stable/modules/generated/sklearn.metrics.pairwise.cosine_similarity.html
- [S12] Sentence Transformers Documentation. https://sbert.net/
- [S13] Supabase Documentation. Database backups. https://supabase.com/docs/guides/platform/backups
- [S14] Supabase Documentation. Row Level Security. https://supabase.com/docs/guides/database/postgres/row-level-security
- [S15] PostgreSQL Documentation. https://www.postgresql.org/docs/
- [S16] TypeScript Documentation. https://www.typescriptlang.org/docs/
- [S17] Vite Documentation. https://vite.dev/guide/
- [S18] Tailwind CSS Documentation. https://tailwindcss.com/docs

---

## Conclusion

The project team has selected React + TypeScript + Vite, Tailwind CSS, Python + FastAPI, Supabase Managed PostgreSQL, Python rules-based skill-gap analysis, Pytest, and GitHub + YouTrack for the CareerLens MVP. SQLAlchemy and Alembic remain optional pending the team's decision about ORM and migration requirements.

Supabase Managed PostgreSQL reduces database setup and maintenance effort compared with operating a database server independently, while retaining PostgreSQL's relational capabilities. The Free plan may be sufficient for an academic prototype, but its quotas, inactivity policies, and lack of automatic database backups must be considered before committing to deployment.

The initial skill-gap analysis remains deterministic and explainable. Keyword matching and TF-IDF provide simpler options for matching skill descriptions, while SBERT may be evaluated later if evidence justifies its additional complexity.

The implementation should remain consistent with the selected stack and include testing and recovery procedures appropriate to the MVP.