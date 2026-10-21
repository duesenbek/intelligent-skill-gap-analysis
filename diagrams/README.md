# CareerLens — System Architecture Diagrams

This directory contains the initial architecture diagrams for CareerLens, designed in alignment with the diploma project proposal and the MVP scope.

---

## 1. Diagrams Overview

| Diagram | Purpose | Editable Source (`src/`) | Vector Export (`exports/`) | Full Specification |
|---|---|---|---|---|
| **System Context Diagram** (C4 Level 1) | Identifies the system boundary, primary users (students, professionals, admins), and external entities (ESCO/O*NET catalog, evaluator). | [system-context.mmd](src/system-context.mmd) | [system-context.svg](exports/system-context.svg) | [docs/07-architecture/system-context.md](../docs/07-architecture/system-context.md) |
| **Use Case Diagram** | Outlines core user scenarios (profiling, role selection, analysis, prioritized gaps, roadmaps), administrative maintenance, and evaluation. | [use-case.mmd](src/use-case.mmd) | [use-case.svg](exports/use-case.svg) | [docs/07-architecture/use-case.md](../docs/07-architecture/use-case.md) |
| **Component Diagram** (Logical Architecture) | Decomposes Web UI, Backend API, Validation, Profile Service, Catalog Service, Gap Analysis Engine, Recommendation Engine, and Storage. | [component-diagram.mmd](src/component-diagram.mmd) | [component-diagram.svg](exports/component-diagram.svg) | [docs/07-architecture/component-diagram.md](../docs/07-architecture/component-diagram.md) |

---

## 2. Directory Layout

```
diagrams/
├── README.md
├── src/
│   ├── system-context.mmd       # Editable Mermaid source
│   ├── use-case.mmd             # Editable Mermaid source
│   └── component-diagram.mmd    # Editable Mermaid source
└── exports/
    ├── system-context.svg       # High-contrast readable vector graphic
    ├── use-case.svg             # High-contrast readable vector graphic
    └── component-diagram.svg    # High-contrast readable vector graphic
```

---

## 3. Rendering in Markdown

All architectural diagrams are authored in standard Mermaid format and render natively in GitHub and markdown viewers:
- [System Architecture Documentation (docs/07-architecture/README.md)](../docs/07-architecture/README.md)
