# 06 — Requirements Specification

**Status:** Draft — to be completed by Asylbek Agabekuly

**Purpose:** Define what the system must do and how success will be measured.

---

## Functional Requirements

| ID | Requirement | Priority | Acceptance Criteria |
|---|---|---|---|
| FR-01 | The user shall be able to select a target professional role | Must | Role list displayed; selection saved |
| FR-02 | The user shall be able to input their current skills | Must | Skills recorded and displayed back |
| FR-03 | The system shall compare user skills to the role competency profile | Must | Comparison result produced within 5 s |
| FR-04 | The system shall identify and prioritise skill gaps | Must | Gaps listed with priority level |
| FR-05 | The system shall generate a personalised development roadmap | Must | Roadmap presented with ordered steps |
| FR-06 | The system shall present results through a web interface | Must | Interface accessible in a modern browser |
| FR-07 | The user shall be able to save and retrieve their analysis | Should | Results persist across sessions |

*Add or revise requirements as analysis progresses.*

---

## Non-Functional Requirements

| ID | Category | Requirement | Acceptance Criteria |
|---|---|---|---|
| NFR-01 | Performance | Analysis completes within 5 seconds | Measured under normal test conditions |
| NFR-02 | Usability | A target user completes a full analysis without assistance | Verified in usability test |
| NFR-03 | Security | No credentials stored in plain text | Code review and config audit |
| NFR-04 | Maintainability | New role profile added without code changes | Demonstrated in evaluation |

---

## Out of Scope

> See README §6 — Outside the Initial Scope.

---

## Open Questions

> List unresolved questions that affect requirements.
