# 01 — Project Proposal: CareerLens

**Document Version:** 1.0  
**Date:** October 2026  
**Status:** Complete Proposal  
**Lead Author:** Bekzat Duisenbek (Technical Coordination, Backend & Architecture)  
**Co-Authors:** Kuanysh Assaubayev (Data Analysis & ML), Asylbek Agabekuly (Frontend & UX)  
**Academic Supervisor:** Praveen Kumar (School of Software Engineering, Astana IT University)  

---

## 1. Official Project Information

- **System Name:** CareerLens
- **Official Diploma Project Title:**  
  *Design and Development of an Intelligent Skill Gap Analysis and Personalized Career Recommendation System*
- **Degree Program:** Bachelor of Software Engineering, School of Software Engineering, Astana IT University
- **Academic Groups:** SE-2417, SE-2409, SE-2422

---

## 2. Problem Statement

### 2.1 Context and Background
The contemporary information technology job market evolves at an unprecedented pace. Advancements in cloud computing, modern frameworks, and artificial intelligence continually reshape employer expectations for junior and mid-level engineering positions. Consequently, higher education curricula frequently experience a temporal lag relative to the rapidly shifting demands of industrial software engineering.

### 2.2 Core Problems Identified
1. **Information Asymmetry and Job Requirement Ambiguity:**  
   Standard job listings are typically composed of exhaustive lists of required qualifications, libraries, and tools. They lack structured indicators of prerequisite dependencies, relative priority, or the depth of proficiency expected for junior roles. Students struggle to discern which skills are essential core competencies versus secondary preferences.
2. **Lack of Objective Self-Assessment Tools:**  
   University students and recent graduates often evaluate their capabilities through academic course grades, which do not directly map to industrial skill taxonomies. Without an objective benchmark, individuals either overestimate their readiness—leading to unsuccessful job applications—or suffer from impostor syndrome, delaying their market entry.
3. **Generic, Disconnected Career Guidance:**  
   Existing career resources and generic learning platforms provide one-size-fits-all roadmaps (e.g., standard syllabi) that fail to account for the user's existing background. A student with strong Python fundamentals does not need an introductory programming course; they require targeted modular bridging toward production API engineering, data pipelines, or systems design.

---

## 3. Assumptions vs. Verified Findings

To ensure scientific rigor and empirical validity, this project strictly distinguishes between verified evidence and working assumptions.

### 3.1 Verified Findings (Empirical & Literature-Backed)
- **Market Demand Dynamic:** Job vacancies for software roles consistently specify multi-disciplinary stacks (combining language fluency, version control, database querying, and CI/CD).
- **Curriculum Gap Reality:** Preliminary surveys and student feedback within Astana IT University demonstrate that junior students experience anxiety regarding industry readiness and demand clearer guidance on industry-standard tooling (Docker, microservices, testing paradigms).
- **Recruitment Bottleneck:** Technical recruiters frequently report receiving high volumes of candidate resumes lacking evidence of core applied skills, resulting in high initial screening drop-off rates.

### 3.2 Working Assumptions (Subject to Empirical Validation During Project)
- **Structured Gap Modeling:** It is assumed that technical competencies for common tech professions (e.g., Backend Developer, Frontend Developer, Data Analyst) can be hierarchically represented as a weighted ontology graph.
- **Actionability of Automated Roadmaps:** It is assumed that providing a student with a sequenced, gap-specific roadmap with direct learning resources will measurably increase their preparation efficiency compared to unguided independent research.
- **Self-Assessment Calibration:** It is assumed that combining self-reported skills with resume parsing or targeted verification checks can produce a sufficiently reliable candidate profile for actionable gap detection.

---

## 4. Target Users and User Needs

### 4.1 Primary Target Groups
1. **Undergraduate Students (3rd & 4th Year):**  
   Preparing for competitive internships and entry-level positions; need clear alignment between university coursework and market job specifications.
2. **Recent Tech Graduates:**  
   Actively interviewing; need diagnostic feedback to explain rejection patterns and prioritize immediate upskilling goals.
3. **Early-Career Professionals (0–2 Years Experience):**  
   Aiming to transition roles (e.g., Junior Frontend to Full-Stack, or Software Engineer to Machine Learning Engineer); need efficient delta-learning plans without redundant study.

### 4.2 User Needs & System Value Proposition

| User Segment | Critical Pain Point | CareerLens Value Proposition |
|---|---|---|
| University Students | Unclear which industry tools to learn alongside university theory | Clear delta analysis against entry-level industry role profiles |
| Recent Graduates | Rejections without constructive technical feedback | Detailed diagnostic breakdown of missing critical vs. secondary skills |
| Career Transitioners | Overwhelmed by endless tutorials and documentation | Ordered, phased roadmap focusing exclusively on genuine skill gaps |

---

## 5. Project Aim and Objectives

### 5.1 Project Aim
To design, implement, and evaluate an intelligent, web-based system (**CareerLens**) that analyzes individual software engineering skill profiles against curated market competency benchmarks, identifies technical skill deficiencies, and generates personalized, prioritized development roadmaps.

### 5.2 Project Objectives
To realize this aim, the team will achieve the following research and engineering objectives:

1. **Investigate User Needs & Market Requirements:**  
   Conduct structured user interviews and compile an empirical dataset of technical job postings to identify current market competency demands.
2. **Review Academic Literature & Existing Tools:**  
   Analyze state-of-the-art methods in skill extraction, competency ontologies, gap analysis algorithms, and automated educational recommendation systems.
3. **Compare Technical Alternatives:**  
   Formulate a documented comparison of architectural styles, frontend/backend frameworks, database models, and recommendation algorithms to justify technical decisions.
4. **Define Requirements & Acceptance Criteria:**  
   Formalize functional specifications, non-functional performance baselines, security constraints, and verifiable acceptance metrics.
5. **Architect the System:**  
   Design modular system architecture adhering to clean architecture principles and document it via C4 model diagrams and Architectural Decision Records (ADRs).
6. **Implement the Core Analysis & Recommendation Engines:**  
   Develop algorithms for skill extraction, weighted profile-vacancy matching, gap prioritization, and sequential roadmap compilation.
7. **Develop the User Interface & System Prototype:**  
   Create an intuitive, responsive web application enabling seamless skill profiling, interactive gap visualization, and progress tracking.
8. **Conduct Verification and Empirical Evaluation:**  
   Evaluate recommendation relevance and gap extraction accuracy against predefined expert baselines, followed by user usability testing.

---

## 6. Project Scope and Boundaries

### 6.1 In-Scope (Minimum Viable Product — MVP)
- **Target Role Selection:** Support for core software engineering specializations (Backend Engineer, Frontend Engineer, Full-Stack Developer, Data Analyst/Engineer).
- **Multi-Modal Profile Input:**  
  - Interactive structured self-assessment questionnaire.
  - Plain-text resume upload and keyword extraction.
- **Competency Gap Analyzer:**  
  - Direct comparison of user capabilities against benchmark role requirements.
  - Classification into **Missing (Critical)**, **Developing (Moderate)**, and **Proficient (Met)**.
- **Personalized Learning Roadmap Generator:**  
  - Phased learning paths structured into logical stages (Foundations, Core, Applied).
  - Recommended free/open learning resources, documentation, and practical project tasks for each identified gap.
- **User Dashboard & Progress Visualization:**  
  - Radar charts, progress indicators, and visual comparison graphs.
- **Secure Web Application:**  
  - User authentication, saved profiles, and safe configuration management.

### 6.2 Out-of-Scope (Explicit MVP Exclusions)
- **Universal Industry Coverage:** The MVP will intentionally focus exclusively on software engineering and data science roles, excluding non-IT professions.
- **Direct Employment or Hiring Guarantees:** CareerLens is an educational guidance and advisory tool, not an employment agency or automated job placement portal.
- **Full Automated Live Web Scraping at Scale:** To prevent IP blocking and legal compliance issues, the MVP will utilize curated and periodically synchronized vacancy datasets rather than unbounded live web scrapers.
- **Native Mobile Applications:** Desktop and tablet-optimized responsive web interfaces will be prioritized over native iOS/Android development.
- **Automated Code Proctoring:** The system will not include live IDE sandboxes or automated coding assessments in the initial phase.

---

## 7. Expected Outcomes and Measurable Success Criteria

### 7.1 Tangible Deliverables
1. **Software Artifact:** A fully functional, containerized, web-based software application with public web access.
2. **Documentation Package:** Comprehensive documentation covering proposal, literature review, requirements specification, C4 architecture diagrams, ADRs, test reports, and supervisor records.
3. **Evaluation Dataset & Benchmark:** A curated benchmark of role profiles and evaluated test resumes for reproducible accuracy measurement.

### 7.2 Measurable Quality and Performance Metrics

| Metric Dimension | Target Baseline | Verification Method |
|---|---|---|
| **Skill Gap Detection Agreement** | $\ge 80\%$ agreement with expert consensus | Blind review by 3 experienced software engineers across 20 synthetic/anonymized profiles |
| **Roadmap Relevance Rating** | Average score $\ge 4.0 / 5.0$ | Post-evaluation survey across 15+ student test subjects |
| **API Response Latency** | $\le 2.5$ seconds for gap analysis calculation | Automated performance benchmark suite (k6 / Locust) under standard load |
| **Code Reliability & Testing** | $\ge 75\%$ test coverage on core analytical algorithms | Automated CI test suite (Pytest / Jest) |
| **System Usability (SUS)** | SUS Score $\ge 75$ (Good/Excellent usability) | Standard System Usability Scale questionnaire administered to test users |

---

## 8. Limitations and Risk Mitigation

### 8.1 Technical and Domain Limitations
- **Self-Reported Bias:** Users may unintentionally misjudge their own skill levels.  
  *Mitigation:* Provide concrete behavioral rubrics for proficiency levels (e.g., "Beginner: knows syntax; Intermediate: has deployed to production; Advanced: understands internals").
- **Dynamic Job Market Trends:** Job descriptions frequently introduce new framework names.  
  *Mitigation:* Implement alias mappings and flexible keyword ontologies that associate specialized tools with fundamental principles.
- **Cold-Start for Emerging Roles:** Specialized niche roles may have insufficient benchmark vacancies.  
  *Mitigation:* Restrict MVP to well-established, highly populated job tracks with abundant data points.

---

## 9. Team Structure and Responsibilities

The project is developed by a balanced three-person engineering team, with clearly delineated responsibilities aligned with the academic justification approved by the Dean's office:

```
                          ┌────────────────────────┐
                          │     Praveen Kumar      │
                          │   Academic Supervisor  │
                          └───────────┬────────────┘
                                      │
         ┌────────────────────────────┼────────────────────────────┐
         │                            │                            │
┌────────┴─────────────┐   ┌──────────┴───────────┐   ┌────────────┴───────────┐
│  Bekzat Duisenbek    │   │  Kuanysh Assaubayev  │   │   Asylbek Agabekuly    │
│  Lead Backend / Arch │   │  ML & Data Analysis  │   │   Frontend / UX / UI   │
│       SE-2417        │   │       SE-2409        │   │        SE-2422         │
└──────────────────────┘   └──────────────────────┘   └────────────────────────┘
```

### 9.1 Individual Allocation of Responsibilities

1. **Bekzat Duisenbek (Group SE-2417) — Technical Lead, Backend & Architecture:**
   - Architecture definition, system integration, and C4 diagram authoring.
   - Database schema design, relational modeling, migrations, and data consistency.
   - RESTful API development, user authentication (JWT), profile persistence, and vacancy storage.
   - Interface contracts between the analytical service and frontend application.
   - DevOps: repository governance, CI/CD pipeline, and containerization.

2. **Kuanysh Assaubayev (Group SE-2409) — Data Analysis & Machine Learning:**
   - Vacancy dataset acquisition, cleaning, preprocessing, and exploratory data analysis.
   - Skill taxonomy formulation, entity extraction, and normalization algorithms.
   - Design and implementation of the skill gap calculation and weighting algorithm.
   - Development of the personalized recommendation logic and roadmap ranking models.
   - Quantitative evaluation of model accuracy and benchmark comparative testing.

3. **Asylbek Agabekuly (Group SE-2422) — Frontend Engineering & User Experience:**
   - User research, persona creation, and interactive Figma UI/UX prototyping.
   - Responsive web client implementation using modern frontend component architecture.
   - Development of interactive data visualizers (skill gap radars, competency matrices, visual roadmaps).
   - Integration with backend REST endpoints and state management.
   - Usability testing, user acceptance testing (UAT), and UI evaluation reporting.

---

## 10. Preliminary Implementation Schedule

| Phase | Milestone | Period | Key Deliverables |
|---|---|---|---|
| **Phase 1** | Problem Discovery & Analysis | Weeks 1–3 | Project proposal, user interviews, literature review, requirements specification |
| **Phase 2** | Architecture & UI Prototype | Weeks 4–6 | C4 architecture diagrams, ADRs, database design, interactive Figma prototype |
| **Phase 3** | Core Engine & Backend API | Weeks 7–10 | Database migrations, REST API, vacancy dataset processing, skill gap algorithm |
| **Phase 4** | Frontend Integration & MVP | Weeks 11–13 | Interactive frontend, dashboard visualization, full end-to-end user journey |
| **Phase 5** | Verification & Evaluation | Weeks 14–16 | Accuracy evaluation, usability testing, performance benchmarks, final thesis report |

---

## 11. References and Bibliography

1. Lightcast (formerly Emsi Burning Glass). (2023). *Skills Taxonomy and Market Demand Reports*.
2. European Commission. (2022). *European Skills, Competences, Qualifications and Occupations (ESCO) Taxonomy*.
3. ACM/IEEE-CS Joint Task Force on Computing Curricula. (2020). *Computing Curricula 2020: Paradigms for Future Computing Curricula*.
4. World Economic Forum. (2023). *The Future of Jobs Report 2023*. World Economic Forum, Geneva, Switzerland.
5. Brown, S. (2018). *The C4 Model for Visualising Software Architecture*. Leanpub.
