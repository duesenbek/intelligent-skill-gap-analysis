# 03 — Literature Review: Scientific Foundation for CareerLens

**Document Version:** 1.0  
**Date:** October 2026  
**Status:** In Progress / Annotated Review  
**Lead Author:** Kuanysh Assaubayev (Literature Review & Scientific Foundation)  
**Co-Authors:** Bekzat Duisenbek (Architecture Alignment), Asylbek Agabekuly (UX & Usability Basis)  
**Academic Supervisor:** Praveen Kumar (Astana IT University)  

---

## 1. Search Strategy and Scope

### 1.1 Methodology
To establish a rigorous scientific foundation, publications were queried across major digital libraries and scholarly indexes:
- **Databases:** IEEE Xplore, ACM Digital Library, ScienceDirect (Elsevier), SpringerLink, and Google Scholar.
- **Search Terms:** `"skill gap analysis" AND "career recommendation"`, `"competency model" AND "employability"`, `"course recommender system" AND "ESCO"`, `"system usability scale" AND "software benchmarking"`.
- **Inclusion Criteria:** Peer-reviewed journal articles, conference proceedings from reputable venues (AAAI, IEEE, ACM, Emerald), and official government/international taxonomies. Priority given to publications from 2020–2025.
- **Exclusion Criteria:** Non-refereed blog posts, marketing whitepapers without reproducible methodology, and papers lacking empirical validation.

---

## 2. Structured Taxonomy and Scientific Literature Catalog

| # | Reference / Authors | Year | Type & Publisher | Method / Approach | Key Findings & Specific Role in CareerLens | DOI / URL |
|---|---|---|---|---|---|---|
| 1 | **ESCO** (European Commission) | 2023 | Official Classification Standard | Multilingual taxonomy of 3,000+ occupations and 13,800+ skills | Provides the standardized European catalog of IT roles and associated skill hierarchies, avoiding ad-hoc manual definitions. | [ESCO Portal](https://esco.ec.europa.eu/en/about-esco) |
| 2 | **O*NET** (U.S. Dept. of Labor) | 2024 | Occupational Database | Standard Occupational Classification (SOC) | Used as a benchmark comparison against ESCO for structuring competency levels (1–5) and task importance weights. | [O*NET Online](https://www.onetonline.org/help/onet/) |
| 3 | **CARIA** (Al-Otaibi et al.) | 2024 | Journal Article (IJICTE / IGI Global) | Competency-based personalized career recommendation | Examines multi-criteria recommendation methods and evaluation metrics for skill-to-role matching; guides CareerLens ranking logic. | [10.4018/IJICTE.356499](https://doi.org/10.4018/IJICTE.356499) |
| 4 | **Scandurra et al.** | 2024 | Systematic Review (Studies in Higher Education) | Meta-analysis of youth employability interventions | Proves the necessity of targeted, actionable skill intervention vs. general career coaching; supports CareerLens problem statement. | [10.1080/03075079.2023.2265425](https://doi.org/10.1080/03075079.2023.2265425) |
| 5 | **Beutling & Spahic-Bogdanovic** | 2024 | AAAI Symposium Series | Hybrid ESCO taxonomy + LLM course recommendations | Demonstrates how bridging formal career taxonomies with recommendation pipelines yields high recommendation coherence. | [10.1609/aaaiss.v3i1.31185](https://doi.org/10.1609/aaaiss.v3i1.31185) |
| 6 | **Gupta et al.** | 2025 | Journal Article (Kybernetes / Emerald) | ML-based skillset extraction and gap analysis | Compares algorithmic delta extraction between curricula and employer job ads; validates our deterministic gap formula baseline. | [10.1108/K-01-2024-0053](https://doi.org/10.1108/K-01-2024-0053) |
| 7 | **Gugnani & Misra (PCRS)** | 2020 | IEEE Access | Personalized Career-Path Recommender System (Markov Models) | Analyzes sequential career progression and identifies data sparsity limitations in complex models, justifying CareerLens explainable heuristic. | [10.1109/ACCESS.2020.3040338](https://doi.org/10.1109/ACCESS.2020.3040338) |
| 8 | **Brooke, J.** | 1996 | Book Chapter / Methodological Standard | System Usability Scale (SUS) | The foundational 10-item instrument for quantifying perceived software usability; adopted as our core UX evaluation metric. | [ResearchGate](https://www.researchgate.net/publication/319394819_SUS_--_a_quick_and_dirty_usability_scale) |
| 9 | **Lewis, J. R.** | 2018 | Journal of Usability Studies | Benchmark and psychometric analysis of SUS | Establishes statistical benchmarks for interpreting SUS scores (70 = acceptable, 75+ = good, 85+ = excellent) to validate our target of $\ge 75$. | [JUS](https://uxpajournal.org/system-usability-scale-past-present-future/) |
| 10 | **Blasco-Arcas et al.** | 2022 | Comput. in Human Behavior | SUS Benchmarking in educational platforms | Documents that interactive visual dashboards significantly improve student engagement and perceived clarity in self-assessment. | [10.1016/j.chb.2022.107293](https://doi.org/10.1016/j.chb.2022.107293) |
| 11 | **Kivunja, C.** | 2021 | Int. J. of Higher Education | 21st century software engineering competencies | Formulates structured rubrics for dividing technical skills into foundational, intermediate, and advanced operational proficiency. | [10.5430/ijhe.v10n1p1](https://doi.org/10.5430/ijhe.v10n1p1) |
| 12 | **Kessler et al.** | 2023 | IEEE Trans. on Learning Tech. | Explainability in automated educational roadmapping | Emphasizes that students reject "black-box" recommendations; rule-based explainability ($gap \times importance$) fosters trust and compliance. | [10.1109/TLT.2023.3288190](https://doi.org/10.1109/TLT.2023.3288190) |

---

## 3. Thematic Analysis and Findings

### 3.1 Taxonomy-Driven vs. Unsupervised Skill Modeling
Prior research highlights a clear dichotomy in skill gap literature:
- **Unsupervised Vector/Embedding Models:** Directly cluster vacancy text using deep embeddings (Word2Vec, BERT). While flexible, they suffer from high noise, hallucinatory skill equivalence, and non-explainable distance metrics (Gupta et al., 2025).
- **Taxonomy-Grounded Models (ESCO/O\*NET):** Mapping vacancies to standardized competency profiles enables exact, transparent comparisons (Beutling & Spahic-Bogdanovic, 2024).  
*CareerLens Decision:* Adopt a structured catalog mapped to ESCO/O*NET competencies for the MVP, ensuring verifiable correctness and regulatory grounding.

### 3.2 Explainable Heuristics vs. Black-Box Recommenders
Complex collaborative filtering and Markov chain career models (Gugnani & Misra, 2020) suffer heavily from the **cold-start problem** for university students who lack extensive professional histories. Furthermore, Kessler et al. (2023) demonstrated that learners require transparent explanations for *why* a particular topic is recommended next.
*CareerLens Decision:* Employ an explainable priority function:
$$\text{Priority}_i = (\max(0, \text{Required}_i - \text{Current}_i)) \times \text{Importance}_i$$
This ensures that every recommendation is directly interpretable by the student (e.g., *"PostgreSQL is recommended with priority 9 because your current level is 1, required is 4, and role importance is 3"*).

---

## 4. Identified Research Gap

While existing tools (LinkedIn Career Insights, Coursera Career Academy) offer coarse skill lists, they have two fundamental weaknesses:
1. **Commercial Bias:** They prioritize selling proprietary platform courses rather than providing vendor-neutral, objective roadmap prioritization.
2. **Binary vs. Granular Measurement:** Existing platforms mark a skill as either "present" or "absent", failing to capture the gap between superficial theoretical familiarity and production-ready applied depth.

**CareerLens Contribution:** An open, explainable, taxonomy-grounded web system providing granular proficiency comparison (Levels 1–5), prioritized delta calculations, and structured open learning milestones.
