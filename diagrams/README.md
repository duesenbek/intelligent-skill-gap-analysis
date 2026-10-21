# CareerLens — System Architecture Diagrams

This directory organizes the architectural, structural, and behavioral diagrams for the CareerLens system.

## 1. Primary Architecture Specifications

Detailed architecture diagrams rendered in Mermaid format are integrated directly into the architecture documentation:
- [System Architecture & Design Document (docs/07-architecture/README.md)](../docs/07-architecture/README.md)

### Available Diagrams:
1. **System Context Diagram (C4 Level 1):** Defines system boundaries, primary human actors (Students, Evaluators), and external taxonomy references (ESCO / O*NET).
2. **Use Case Diagram:** Maps out the primary user interactions (role selection, skill profile assessment, gap diagnostics, and roadmap tracking).
3. **Component Diagram (C4 Level 3):** Illustrates the internal decomposition of the Backend API, the analytical engines (`Gap Analysis Engine`, `Recommendation Engine`), the database persistence layer, and the Single Page Application client.
4. **Algorithmic Flow:** Outlines the deterministic gap calculation pipeline:
   $$\text{gap}_i = \max(0, \text{required}_i - \text{current}_i), \quad \text{priority}_i = \text{gap}_i \times \text{importance}_i$$

---

## 2. Directory Layout for External Exports

- `src/` — Editable diagram source files (`.drawio`, `.puml`, `.mmd`).
- `exports/` — High-resolution exported images (`.svg`, `.png`) prepared for inclusion in the formal diploma thesis report.
