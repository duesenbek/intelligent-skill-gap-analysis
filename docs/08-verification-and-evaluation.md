# Verification and Evaluation Plan — CareerLens

## 1. Purpose

This plan defines how CareerLens will be verified and evaluated. It focuses on functional correctness, skill-gap identification, recommendation relevance, usability, and response time.

All values below are **proposed targets**, not achieved results. They must be reviewed before testing and reported only after measurements have been collected.

## 2. Evaluation Questions

- **RQ1:** Does CareerLens identify skill gaps correctly against independently prepared reference labels?
- **RQ2:** Are recommendations relevant to the identified gaps and their priorities?
- **RQ3:** Can intended users complete the core workflow and understand the results?
- **RQ4:** Does the analysis endpoint meet the response-time target under documented conditions?

## 3. Verification Strategy

### 3.1 Functional tests

Test profile entry, input validation, target-role selection, analysis execution, gap ordering, recommendation generation, explanation display, and error handling.

### 3.2 Algorithm tests

Prepare a fixed set of test profiles and role requirements with expected results. Include cases with no gaps, several gaps, missing skills, invalid values, and equal priority scores. Compare actual outputs against reference outputs.

### 3.3 Expert review

Ask qualified reviewers to assess a predefined sample of gaps and recommendations using a rubric written before the evaluation. Record reviewer qualifications, sample size, disagreements, and the method used to calculate agreement.

### 3.4 Usability testing

Ask representative students, graduates, or early-career professionals to complete a realistic workflow: enter skills, choose a target role, interpret the gap report, and identify a next action. Record completion, errors, feedback, and questionnaire results.

### 3.5 Performance testing

Use a documented hardware/software environment and fixed test dataset. Run repeated requests and report median and 95th-percentile response times. State whether the measurement includes network latency and database access.

## 4. Metrics and Proposed Success Criteria

| Metric | Proposed target | Measurement conditions |
|---|---:|---|
| Mandatory functional acceptance tests | 100% pass | Run documented test cases against the release candidate |
| Skill-gap agreement | ≥ 80% | Compare system labels with independently reviewed reference labels; define the unit of agreement before testing |
| Recommendation relevance | ≥ 4.0/5.0 | Mean participant rating using a fixed rubric and disclosed sample size |
| Analysis response time | ≤ 2.5 seconds at p95 | Repeated analysis requests in a documented environment |
| Algorithm-core test coverage | ≥ 75% | Automated coverage report for the defined algorithm module |
| SUS usability score | ≥ 75/100 | Standard SUS questionnaire after participants complete the core workflow |

These are provisional targets. If the team cannot justify or measure a target, it must revise the target and explain why rather than claim success without evidence.

## 5. Baseline and Comparison

The primary baseline is a deterministic, rules-based comparison:

`gap = max(0, required_level - current_level)`

A proposed priority score is:

`priority = gap × importance_weight`

The baseline will be evaluated on the same fixed test profiles and role catalogue as any alternative method. If an advanced method is implemented, compare methods using the same reference labels, dataset, and metrics. If no alternative method is implemented, report the rules-based baseline without claiming comparative superiority.

## 6. Dataset and Reference Labels

Create a documented dataset of profiles, role requirements, expected gaps, and expected priority order. Reference results should be reviewed independently of the implementation. Record the rubric, reviewer disagreements, and any changes to the dataset.

Synthetic profiles are useful for repeatable functional testing but do not demonstrate real-world user demand. User interviews and usability testing must be reported separately.

## 7. Requirement-to-Test Traceability

| Requirement ID | Requirement Description | Test Scenario / Procedure | Verifiable Evidence |
|---|---|---|---|
| **FR-01** | User can select a target professional role | TC-01: Valid role selection from catalog and invalid/unknown role handling | Test execution log, UI selection state |
| **FR-02** | User can input current technical skills | TC-02: Boundary checks, numeric range validation (1–5), missing input rejection | Validation error log, state persistence |
| **FR-03** | System compares skills to role profile | TC-03: Execution against fixed benchmark profiles with expected delta labels | Expected-vs-actual comparison matrix |
| **FR-04** | System identifies and prioritizes skill gaps | TC-04: Priority scoring verification ($gap \times importance$) including score ties | Priority rank correlation report |
| **FR-05** | System generates personalized roadmap | TC-05: Verify recommendation-to-gap traceability and learning action linkage | Recommendation audit checklist |
| **FR-06** | System presents results via web interface | TC-06: Cross-browser rendering and interactive gap visualization display | UI test suite, visual inspection |
| **FR-07** | User can save and retrieve analysis | TC-07: Persistence and session retrieval across reloads | Database query logs, API test results |
| **NFR-01** | Analysis response time meets target ($\le 2.5$ s) | TC-08: Repeated requests under documented local/staging test conditions | Latency distribution report (p50, p95) |
| **NFR-02** | Target user completes analysis without assistance (SUS $\ge 75$) | TC-09: Usability test with $\ge 15$ participants and standardized SUS survey | Task observation logs, SUS score dataset |
| **NFR-03** | Security: no credentials stored in plain text | TC-10: Configuration and environment audit against secrets | Security review checklist, `.env.example` audit |
| **NFR-04** | Maintainability: new role profile added without code changes | TC-11: Load new JSON/DB occupational profile and verify analysis execution | Automated catalog integration test |

## 8. Acceptance Criteria

- Mandatory functional tests pass.
- Gap calculations match the defined reference cases.
- Each recommendation maps to one or more identified gaps and includes a rationale.
- Evaluation metrics are calculated using documented formulas and conditions.
- Dataset, sample size, test environment, results, deviations, and limitations are recorded.
- Results that have not been measured are labelled as planned or pending.

## 9. Threats to Validity and Ethics

Results may be affected by small participant samples, subjective self-assessment, incomplete role requirements, reviewer disagreement, and limited role coverage. Report these limitations explicitly.

Collect only the information necessary for evaluation, obtain participant consent, avoid publishing identifiable interview data, and do not claim that CareerLens guarantees employment or independently verifies a user's skills.

## 10. Reporting Checklist

The final report should include:
- system version and test environment;
- dataset description and reference-label procedure;
- test cases and pass/fail outcomes;
- reviewer and participant counts;
- metric formulas and observed values;
- deviations from planned targets;
- limitations and next steps.
