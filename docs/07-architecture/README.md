# 07 — System Architecture & Design: CareerLens

**Document Version:** 1.0  
**Date:** October 2026  
**Status:** Architectural Baseline (MVP Scope)  
**Lead Author:** Bekzat Duisenbek (System Architecture & Backend)  
**Co-Authors:** Kuanysh Assaubayev (Analytical Modules), Asylbek Agabekuly (Frontend Interfaces)  
**Academic Supervisor:** Praveen Kumar (Astana IT University)  

---

## 1. Architectural Philosophy and Scope

CareerLens prioritizes a modular, maintainable, and explainable software architecture over complex, opaque "black-box" models. For the diploma MVP, the core analytical decisions rely on deterministic heuristics grounded in standardized skill taxonomies (ESCO / O*NET), guaranteeing verifiable correctness, low runtime latency, and full transparency for academic evaluation.

---

## 2. System Context Diagram (C4 Level 1)

The C4 Context diagram illustrates how CareerLens interacts with primary users and external systems.

```mermaid
C4Context
    title System Context Diagram (C4 Level 1) — CareerLens

    Person(student, "Student / Job Seeker", "University student or early-career professional seeking skill gap insights.")
    Person(supervisor, "Academic Supervisor", "Reviews student evaluation data and research metrics.")

    System(careerlens, "CareerLens Platform", "Provides skill self-assessment, gap identification, and personalized learning roadmaps.")

    System_Ext(esco, "ESCO / O*NET Standards", "Standardized occupational profiles and skill hierarchies.")
    System_Ext(open_resources, "Curated Open Learning Repositories", "Public documentation, GitHub tutorials, and MOOCs (Coursera, edX, MDN).")

    Rel(student, careerlens, "Inputs skills, selects target role, views roadmaps", "HTTPS / Web Browser")
    Rel(careerlens, esco, "References standardized role competencies", "Taxonomy Baseline")
    Rel(careerlens, open_resources, "Links actionable learning resources", "Curated Metadata")
    Rel(supervisor, careerlens, "Inspects evaluation benchmarks & test reports", "Audit / Evaluation")
```

---

## 3. Use Case Diagram

The core user workflows of CareerLens cover authentication, profiling, analysis, and roadmap tracking:

```mermaid
flowchart LR
    subgraph Users
        U((Student / Graduate))
        A((Academic Evaluator))
    end

    subgraph CareerLens Platform
        UC1([Register & Authenticate])
        UC2([Select Target Career Role])
        UC3([Input Current Skill Profile])
        UC4([Upload & Parse Resume Text])
        UC5([Execute Skill Gap Analysis])
        UC6([Inspect Visual Gap Breakdown])
        UC7([View & Follow Personalized Roadmap])
        UC8([Run Automated Evaluation & Benchmarks])
        UC9([Review SUS Usability Survey])
    end

    U --> UC1
    U --> UC2
    U --> UC3
    U -. optional .-> UC4
    UC2 & UC3 --> UC5
    UC5 --> UC6
    UC5 --> UC7

    A --> UC8
    A --> UC9
```

---

## 4. Component Diagram (C4 Level 3 — Backend API & Engine)

The internal decomposition of the system emphasizes modular decoupling between data ingestion, computation, and presentation:

```mermaid
graph TD
    subgraph Client Tier [Web Client - Single Page Application]
        UI_Auth[Auth & Profile Views]
        UI_Select[Role & Skill Input Matrix]
        UI_Viz[Interactive Radar & Gap Charts]
        UI_Roadmap[Roadmap Milestone Dashboard]
    end

    subgraph Application Tier [Backend API Service]
        API_GW[API Gateway & Router]
        Auth_Mgr[Auth & Session Manager]
        Catalog_Svc[Skill & Role Catalog Service]
        
        subgraph Analytical Engine [Core Business Logic]
            Gap_Engine[Gap Analysis Engine]
            Rec_Engine[Recommendation Engine]
            Eval_Module[Evaluation & Benchmark Runner]
        end
    end

    subgraph Data Tier [Persistence Layer]
        DB[(Relational Database)]
        Taxonomy_Store[(Taxonomy & Role Baseline JSON/DB)]
        Bench_Store[(Evaluation Benchmark Dataset)]
    end

    UI_Auth --> API_GW
    UI_Select --> API_GW
    UI_Viz --> API_GW
    UI_Roadmap --> API_GW

    API_GW --> Auth_Mgr
    API_GW --> Catalog_Svc
    API_GW --> Gap_Engine
    API_GW --> Rec_Engine
    API_GW --> Eval_Module

    Catalog_Svc --> Taxonomy_Store
    Gap_Engine --> Catalog_Svc
    Gap_Engine --> DB
    Rec_Engine --> Gap_Engine
    Rec_Engine --> DB
    Eval_Module --> Gap_Engine
    Eval_Module --> Bench_Store
```

---

## 5. Algorithmic Foundation: Gap Computation and Prioritization

The core analytical pipeline executes deterministically in six clear steps:

1. **Role Requirement Retrieval:**  
   The user selects a target role $R$ (e.g., *Junior Backend Developer*). The system retrieves the required skills $\mathcal{S}_R = \{s_1, s_2, \dots, s_n\}$ along with their minimum required proficiency levels $\text{required}_i \in [1, 5]$ and role importance weights $\text{importance}_i \in [1, 5]$.
2. **Current Competency Mapping:**  
   The user declares their current proficiency $\text{current}_i \in [0, 5]$ for each skill (where $0$ indicates absence of knowledge).
3. **Gap Model:**  
   The skill deficiency $\text{gap}_i$ for each skill $s_i$ is computed as:
   $$\text{gap}_i = \max(0, \, \text{required}_i - \text{current}_i)$$
4. **Priority Ranking Function:**  
   To prioritize which gap should be addressed first, each gap is weighted by the importance of that skill in the target role:
   $$\text{priority}_i = \text{gap}_i \times \text{importance}_i$$
   *Example:* If SQL has $\text{current} = 1$, $\text{required} = 4$ ($\text{gap} = 3$), and $\text{importance} = 3$, its calculated priority is $3 \times 3 = 9$.
5. **Categorization:**  
   - **Critical / Missing:** $\text{gap}_i \ge 3$ or $\text{priority}_i \ge 9$.
   - **Developing / Moderate:** $1 \le \text{gap}_i \le 2$.
   - **Proficient / Met:** $\text{gap}_i = 0$.
6. **Explainable Roadmap Compilation:**  
   For each skill with $\text{gap}_i > 0$, the system attaches a curated learning action, estimated hours of study, and a direct open resource reference, ordered descending by $\text{priority}_i$.

---

## 6. Architectural Decision Records (ADRs)

### ADR-01: Explainable Rule-Based Analytical Engine for MVP
- **Status:** Accepted
- **Context:** The project requires a reliable, transparent, and verifiable method to identify skill gaps without unpredictable hallucinations or the cold-start data scarcity typical of pure collaborative filtering.
- **Decision:** Implement a deterministic mathematical heuristic ($\text{gap} \times \text{importance}$) grounded in standardized role competency matrices.
- **Consequences:** Low computational overhead, sub-second latency, deterministic testability, and full transparency during academic thesis defense.

### ADR-02: Decoupled Web Client & RESTful Backend Architecture
- **Status:** Accepted
- **Context:** Individual responsibilities divide frontend (Asylbek) and backend/data (Bekzat, Kuanysh).
- **Decision:** Adopt a decoupled architecture communicating over well-documented OpenAPI / REST endpoints with JSON payloads.
- **Consequences:** Independent development velocity, isolated testing, clear interface contracts, and reproducible API benchmarking.

### ADR-03: Grounding in International Taxonomies (ESCO & O*NET)
- **Status:** Accepted
- **Context:** Manually inventing skill lists risks personal bias and non-standard terminology.
- **Decision:** Align the role catalog with the European Commission's ESCO classification and US O*NET competency dimensions.
- **Consequences:** Scientifically defensible skill hierarchies and direct cross-referencing in academic literature.

### ADR-04: Relational Data Persistence with Migration Versioning
- **Status:** Accepted
- **Context:** The system manages structured entity relationships between Users, Roles, Skills, Assessments, and Recommendations.
- **Decision:** Utilize a relational schema (PostgreSQL / SQLite for local development) with structured schema migrations.
- **Consequences:** ACID guarantees, data integrity, and strict typing of assessment records.
