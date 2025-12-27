# AI-SDLC v1.0 Spec

**Full Specification (Single Document)**

---

## 1. Scope and intent

This document is the **normative specification** for **AI-SDLC v1.0**.

It defines:

* what AI-SDLC is,
* what it replaces,
* what artefacts are required,
* what stages exist,
* what rules must be enforced,
* what constitutes progress and completion.

This is **not** a blog post, philosophy paper, or marketing document.
It is written to be used as an **operational SDLC spec**.

---

## 2. Definitions

**AI executor**
A non-human system that generates, modifies, or removes implementation artefacts.

**Human owner**
A named individual accountable for intent, constraints, decisions, and outcomes.

**Intent**
A concise statement of purpose, outcome, constraints, assumptions, and stop conditions.

**Specification**
A machine-readable description of expected behaviour, interfaces, data, non-functional requirements, and observability.

**Evidence**
Observed runtime behaviour produced by a deployed system.

**Decision**
A recorded human judgement based on evidence that determines the next action.

---

## 3. Core premise

AI-SDLC v1.0 is based on the following premises:

1. Implementation cost is low.
2. Change is continuous and expected.
3. Poor decisions dominate failure modes.
4. Execution can be automated.
5. Accountability cannot be automated.

Any process that optimises primarily for human execution speed is out of scope.

---

## 4. What AI-SDLC replaces

AI-SDLC v1.0 explicitly replaces SDLC constructs whose primary purpose is to manage human execution and coordination:

* task backlogs as the unit of progress,
* sprint cycles as a reporting mechanism,
* role hand-offs between product, design, and engineering,
* status reporting based on activity,
* delivery milestones detached from runtime behaviour.

These constructs may exist locally but **MUST NOT** define progress.

---

## 5. What AI-SDLC retains

AI-SDLC v1.0 retains and enforces:

* explicit intent and constraints,
* architectural decisions where consequences exist,
* automated quality verification,
* security, privacy, and compliance controls,
* observability and rollback,
* auditability of decisions.

---

## 6. Design principles (normative)

Implementations of AI-SDLC **MUST** follow these principles:

1. **Intent precedes execution**
   No implementation begins without explicit intent.

2. **Constraints are enforceable**
   Constraints are expressed in a form that automation can block.

3. **Implementation is replaceable**
   Code is an output, not a long-term asset.

4. **Quality gates are automatic**
   Human approval cannot bypass enforcement.

5. **Evidence drives decisions**
   Decisions are based on observed behaviour, not plans.

6. **Humans remain accountable**
   Every decision has a named owner.

---

## 7. Required artefacts

An AI-SDLC v1.0 system **MUST** maintain the following artefacts.

### 7.1 Intent record

**Required fields:**

* Problem statement
* Affected user or system
* Desired outcome
* Non-negotiable constraints
* Explicit assumptions
* Stop or change conditions
* Named intent owner

The intent record **MUST** be concise and versioned.

---

### 7.2 Formal specification

The specification **MUST** describe:

* Behaviour and interfaces
* Inputs and outputs
* Data and state
* Error conditions
* Non-functional requirements
* Acceptance scenarios
* Required observability

The specification **MUST** be machine-readable.

---

### 7.3 Decision log

Each decision **MUST** record:

* Decision date
* Decision owner
* Evidence reviewed
* Decision taken
* Rationale
* Resulting action

---

## 8. Lifecycle stages

AI-SDLC v1.0 defines a **closed decision loop**.

### Stage 1: Intent definition

A human owner defines intent.

**Exit condition:**
Intent record exists and is approved by the intent owner.

---

### Stage 2: Specification

Intent is translated into a formal specification.

**Exit condition:**
Specification is complete, consistent, and machine-readable.

---

### Stage 3: Automated implementation

AI generates:

* application code,
* tests,
* infrastructure,
* instrumentation,
* supporting artefacts.

Human review is permitted but not required for generation.

**Exit condition:**
All required artefacts exist.

---

### Stage 4: Automated enforcement

The system enforces:

* correctness,
* security,
* performance,
* cost limits,
* deployment safety.

Failures **MUST** block progression automatically.

**Exit condition:**
All enforcement checks pass.

---

### Stage 5: Deployment

Deployment **MUST** be:

* incremental,
* reversible,
* observable.

Deployment is not completion.

**Exit condition:**
System is running and observable.

---

### Stage 6: Observation

The system produces evidence including:

* behaviour,
* reliability,
* performance,
* cost,
* failure modes.

Evidence **MUST** be collected continuously.

---

### Stage 7: Decision

A named decision owner selects one action:

* continue,
* adjust,
* stop,
* pivot.

The decision **MUST** be recorded.

**Exit condition:**
Decision log entry exists.

The loop then repeats.

---

## 9. Unit of progress

The **only recognised unit of progress** in AI-SDLC v1.0 is a **decision informed by evidence**.

Task completion, feature delivery, or code volume **MUST NOT** be treated as progress.

---

## 10. Roles and accountability

AI-SDLC v1.0 requires the following functions:

* **Intent owner**
* **Decision owner**
* **System steward**
* **AI executor**

One person may perform multiple functions.
Every function **MUST** have a named human owner.

---

## 11. Metrics and measurement

AI-SDLC v1.0 **SHOULD** measure:

* time from intent to evidence,
* number of assumptions tested,
* decision latency,
* recovery time from failure,
* cost of change.

It **MUST NOT** optimise for activity metrics.

---

## 12. Failure modes (non-compliance)

An implementation is **non-compliant** if:

* code is built without intent,
* constraints are documented but not enforced,
* deployment occurs without observability,
* decisions lack evidence,
* accountability is unclear.

---

## 13. Versioning and evolution

AI-SDLC versions **MUST** be:

* explicitly numbered,
* backwards aware,
* revised only with documented rationale.

AI-SDLC v1.0 is intentionally minimal.

---

## 14. Summary definition

**AI-SDLC v1.0 is a decision-driven software development lifecycle in which humans define intent and constraints, AI performs implementation, automated systems enforce quality and safety, and runtime evidence determines what happens next.**

---

## 15. Entry and Exit Criteria

This section defines the **mandatory conditions** under which work may enter the AI-SDLC loop, progress between stages, and exit a loop iteration.

These criteria are **normative** and enforceable.

### 15.1 Entry criteria (start of work)

A change, feature, experiment, or system **MUST NOT** enter the AI-SDLC lifecycle unless **all** of the following conditions are met:

1. An **intent record exists** in `intent/intent.md`.
2. The intent record includes:

   * a clear problem statement,
   * a desired outcome,
   * non-negotiable constraints,
   * explicit assumptions,
   * stop or change conditions,
   * a named intent owner.
3. The intent owner has explicitly approved the intent record.

If any condition is not met, **no implementation work is permitted**, including AI-generated work.

### 15.2 Entry criteria for specification

A system **MUST NOT** move from intent definition to specification unless:

1. The intent record is complete and internally consistent.
2. All assumptions are explicitly documented in `intent/assumptions.md`.
3. Constraints are stated in a form that can be enforced by automation.

If constraints cannot be enforced, the intent **MUST** be revised before proceeding.

### 15.3 Entry criteria for automated implementation

Automated implementation **MUST NOT** begin unless:

1. A formal specification exists in `spec/`.
2. All required spec files are present, even if minimal.
3. Acceptance scenarios are defined.
4. Required observability is specified.

Speculative or exploratory implementation without a specification is **non-compliant**.

### 15.4 Entry criteria for deployment

A system **MUST NOT** be deployed unless:

1. All automated enforcement gates pass.
2. Observability is implemented as specified.
3. Rollback mechanisms are available and tested.
4. A decision owner is assigned for post-deployment review.

Deployment without observability is **explicitly forbidden**.

### 15.5 Exit criteria (completion of a loop iteration)

A single AI-SDLC loop iteration is considered **complete** only when:

1. The system has been deployed and observed, **or**
2. A conscious decision has been made not to deploy, **and**
3. A decision record exists in `decisions/` documenting:

   * the evidence reviewed,
   * the decision taken,
   * the rationale.

Without a recorded decision, **no progress has occurred**, regardless of implementation activity.

### 15.6 Stop conditions (mandatory)

Every intent record **MUST** define stop or change conditions.

Work **MUST STOP immediately** when any stop condition is met.

Examples include, but are not limited to:

* evidence contradicts a core assumption,
* constraints are violated beyond acceptable limits,
* cost exceeds defined budgets,
* risk exceeds acceptable thresholds.

Stopping is treated as a **successful outcome** when driven by evidence.

### 15.7 Prohibited states

The following states are **explicitly prohibited** under AI-SDLC v1.0:

* implementation without intent,
* deployment without observability,
* iteration without decisions,
* continued work after stop conditions are met,
* unowned systems with no decision owner.

Any occurrence places the system in **non-compliant status**.

### 15.8 Summary

AI-SDLC v1.0 enforces disciplined flow by defining when work may begin, proceed, and stop.

Speed is permitted.
Speculation is not.
Progress requires decisions.

---

## 16. Compliance Levels and Exceptions

This section defines how compliance with AI-SDLC v1.0 is assessed, how exceptions are handled, and how non-compliance is treated.

Compliance is **explicit**, **auditable**, and **decision-owned**.

### 16.1 Compliance levels

Every system operating under AI-SDLC v1.0 **MUST** be in exactly one of the following compliance states at any time.

#### 16.1.1 Fully compliant

A system is **fully compliant** when:

* all mandatory sections of the AI-SDLC v1.0 specification are satisfied,
* all required artefacts exist and are up to date,
* all enforcement gates are active and passing,
* all decisions are recorded and owned.

Fully compliant systems may proceed through the lifecycle without restriction.

#### 16.1.2 Conditionally compliant

A system is **conditionally compliant** when:

* one or more AI-SDLC requirements are intentionally unmet,
* the deviation is explicitly documented,
* a decision owner has approved the deviation,
* the deviation is time-bounded or scope-bounded.

Conditional compliance **MUST** be recorded as a decision in `decisions/`.

Conditional compliance is an exception, not a default state.

#### 16.1.3 Non-compliant

A system is **non-compliant** when:

* mandatory requirements are unmet without an approved exception,
* enforcement gates are bypassed,
* decisions lack evidence or ownership,
* prohibited states defined in Section 15.7 occur.

Non-compliant systems **MUST NOT** be deployed or progressed.

### 16.2 Exception handling

Exceptions are permitted only under controlled conditions.

An exception **MUST**:

1. be explicitly requested,
2. be reviewed by a named decision owner,
3. be approved or rejected explicitly,
4. be recorded in the decision log,
5. define scope, duration, and review conditions.

Silent or implicit exceptions are **forbidden**.

### 16.3 Exception record requirements

An exception decision record **MUST** include:

* the requirement being excepted,
* the reason for the exception,
* the risk introduced,
* mitigation measures,
* the duration or condition for expiry,
* the decision owner.

Exceptions without an expiry condition are **non-compliant**.

### 16.4 Expiry and review of exceptions

All exceptions **MUST** be reviewed:

* at the next decision point, or
* when defined expiry conditions are met, whichever occurs first.

Expired exceptions **MUST** either:

* be removed, restoring full compliance, or
* be explicitly renewed via a new decision.

Automatic or indefinite rollover of exceptions is **not permitted**.

### 16.5 Enforcement of compliance

Compliance status **MUST** be visible and machine-checkable.

Automation **SHOULD**:

* block deployment of non-compliant systems,
* warn on conditional compliance nearing expiry,
* surface compliance status alongside runtime evidence.

Human approval **MUST NOT** override automated blocking of non-compliant states.

### 16.6 Summary

AI-SDLC v1.0 treats compliance as a first-class system property.

Rules may be bent deliberately.
They may not be bent silently.
Accountability is explicit.

---

## 17. Risk Classification

This section defines how systems are classified by risk under AI-SDLC v1.0 and how risk affects enforcement, review, and decision-making.

Risk classification is **mandatory**.
All systems **MUST** be assigned a risk level before automated implementation begins.

### 17.1 Purpose of risk classification

Risk classification exists to ensure that:

* higher-risk systems receive stronger controls,
* low-risk systems are not burdened by unnecessary process,
* enforcement scales with potential impact.

Risk is assessed based on **impact**, not effort.

### 17.2 Risk levels

AI-SDLC v1.0 defines three risk levels.

Each system **MUST** be classified into exactly one level.

#### 17.2.1 Low risk

A system is **low risk** if failure would result in:

* no material user harm,
* no regulatory or legal impact,
* no financial loss beyond defined tolerance,
* no exposure of sensitive data.

Examples include:

* internal tools,
* prototypes,
* experiments with limited scope.

Low-risk systems may operate with minimal enforcement, provided all core AI-SDLC rules are satisfied.

#### 17.2.2 Medium risk

A system is **medium risk** if failure could result in:

* user-facing disruption,
* moderate financial impact,
* operational instability,
* handling of non-sensitive customer data.

Examples include:

* customer-facing applications,
* internal systems supporting revenue,
* systems with availability or performance commitments.

Medium-risk systems require full enforcement of AI-SDLC artefacts and gates.

#### 17.2.3 High risk

A system is **high risk** if failure could result in:

* significant financial loss,
* regulatory or legal exposure,
* safety or security incidents,
* handling of sensitive or regulated data.

Examples include:

* financial systems,
* regulated platforms,
* security-critical infrastructure.

High-risk systems require enhanced controls and stricter decision review.

### 17.3 Risk declaration requirements

Risk classification **MUST** be declared in the intent record.

The declaration **MUST** include:

* assigned risk level,
* justification for the classification,
* named decision owner responsible for the classification.

Risk classification **MUST** be reviewed whenever system scope or impact changes.

### 17.4 Impact on enforcement

Risk level directly affects enforcement.

At minimum:

* **Low risk**

  * Standard AI-SDLC lifecycle
  * Minimal review overhead

* **Medium risk**

  * Full enforcement of all AI-SDLC requirements
  * Mandatory observability and rollback

* **High risk**

  * Full enforcement plus:

    * stricter acceptance criteria,
    * enhanced observability,
    * explicit decision review before deployment,
    * tighter exception controls.

Risk level **MUST NOT** be used to bypass core AI-SDLC principles.

### 17.5 Misclassification

Intentional or negligent misclassification of risk is treated as **non-compliance**.

If observed impact exceeds declared risk level:

* work **MUST** pause,
* risk classification **MUST** be reassessed,
* a decision record **MUST** document corrective action.

### 17.6 Summary

AI-SDLC v1.0 scales discipline with impact.

Low-risk systems move fast.
High-risk systems move carefully.
All systems remain accountable.

---

## 18. Non-Goals

This section defines what **AI-SDLC v1.0 explicitly does not attempt to define or solve**.

These non-goals are intentional.
They protect the specification from scope creep, misinterpretation, and misuse.

### 18.1 Team structure and roles

AI-SDLC v1.0 does **not** define:

* team sizes or compositions,
* job titles or reporting lines,
* organisational design or management structure.

The SDLC defines **accountability and function**, not organisational charts.

### 18.2 Tooling and vendor selection

AI-SDLC v1.0 does **not** mandate:

* specific AI models or providers,
* programming languages or frameworks,
* CI/CD platforms,
* observability tools,
* infrastructure vendors.

Tool choice is an implementation concern and is intentionally left open.

### 18.3 Business governance and approval processes

AI-SDLC v1.0 does **not** replace:

* business case approval,
* budget approval,
* legal or regulatory sign-off,
* executive governance processes.

It assumes these exist externally and integrates with them via intent, constraints, and decisions.

### 18.4 Human performance management

AI-SDLC v1.0 does **not**:

* measure individual productivity,
* evaluate human performance,
* define incentives or compensation,
* optimise for utilisation metrics.

The SDLC governs systems and decisions, not people management.

### 18.5 Velocity optimisation

AI-SDLC v1.0 does **not** optimise for:

* speed of delivery as an end in itself,
* volume of output,
* number of features shipped.

Speed is a byproduct of clarity and automation, not a primary goal.

### 18.6 AI autonomy beyond execution

AI-SDLC v1.0 does **not** grant AI authority to:

* define intent,
* change constraints,
* approve exceptions,
* make final decisions,
* assume accountability.

AI executes. Humans decide.

### 18.7 Universal applicability

AI-SDLC v1.0 does **not** claim to be suitable for:

* every organisation,
* every regulatory environment,
* every system type.

Adoption requires judgement and may require adaptation beyond v1.0.

### 18.8 Summary

AI-SDLC v1.0 is deliberately narrow.

It defines **how systems are built and evolved** when AI performs execution and humans retain responsibility.

Anything outside that boundary is explicitly out of scope.

---

# Appendix A: File and Folder Standard

## A.1 Purpose

This appendix defines the **mandatory file and folder structure** for systems operating under **AI-SDLC v1.0**.

The structure is designed to:

* make intent, decisions, and constraints first-class,
* separate human judgement from AI execution,
* support automation and enforcement,
* ensure auditability and traceability.

This is a **normative standard**, not a suggestion.

---

## A.2 Root structure (canonical)

Every AI-SDLC–compliant repository **MUST** follow this structure:

```text
/
├─ intent/
├─ spec/
├─ decisions/
├─ src/
├─ tests/
├─ infra/
├─ observability/
├─ compliance/
├─ runbooks/
├─ ai/
└─ README.md
```

No directory may be omitted unless explicitly stated.

---

## A.3 intent/ — human purpose and constraints

### Purpose

Holds **human-authored intent records**.

### Rules

* Written by humans only.
* Small, explicit, and versioned.
* No implementation detail.

### Required files

```text
intent/
├─ intent.md
└─ assumptions.md
```

#### intent/intent.md (required)

Must include:

* Problem statement
* Affected user or system
* Desired outcome
* Non-negotiable constraints
* Stop / change conditions
* Intent owner

#### intent/assumptions.md (required)

* Explicit list of assumptions
* Each assumption must be testable
* Each assumption must link to evidence later

---

## A.4 spec/ — executable system definition

### Purpose

Holds **machine-readable specifications** used by AI executors.

### Rules

* Source of truth for behaviour.
* No narrative prose.
* Must be consumable by automation.

### Required structure

```text
spec/
├─ system.yaml
├─ interfaces.yaml
├─ data.yaml
├─ nfr.yaml
├─ acceptance.yaml
└─ observability.yaml
```

Each file **MUST** exist, even if minimal.

---

## A.5 decisions/ — accountability and evidence

### Purpose

Records **human decisions** made using runtime evidence.

### Rules

* Append-only.
* One decision per file.
* Decisions are immutable once recorded.

### Structure

```text
decisions/
├─ 0001-initial-scope.md
├─ 0002-adjust-constraint.md
└─ 0003-pivot.md
```

Each decision file **MUST** include:

* Date
* Decision owner
* Evidence reviewed (links)
* Decision taken
* Rationale
* Resulting action

---

## A.6 src/ — AI-generated implementation

### Purpose

Holds **implementation artefacts**.

### Rules

* Primarily AI-generated.
* Replaceable at any time.
* No business intent defined here.

### Notes

* Humans may edit, but code is not authoritative.
* Spec and intent override code.

---

## A.7 tests/ — automated verification

### Purpose

Holds tests enforcing correctness and constraints.

### Rules

* Tests are mandatory.
* Generated by AI, reviewed by humans.
* Blocking in CI.

### Typical contents

```text
tests/
├─ unit/
├─ integration/
├─ contract/
└─ security/
```

---

## A.8 infra/ — deployment and environment

### Purpose

Defines infrastructure and deployment behaviour.

### Rules

* Must support rollback.
* Must support staged deployment.
* Must expose observability hooks.

### Typical contents

```text
infra/
├─ environments/
├─ pipelines/
└─ policies/
```

---

## A.9 observability/ — evidence production

### Purpose

Defines how **runtime evidence** is produced and collected.

### Rules

* Required before deployment.
* Enforced automatically.

### Typical contents

```text
observability/
├─ metrics.yaml
├─ logs.yaml
├─ alerts.yaml
└─ dashboards.yaml
```

---

## A.10 compliance/ — enforced constraints

### Purpose

Captures **formal constraints** that automation must enforce.

### Rules

* Constraints must be machine-checkable.
* Documentation alone is insufficient.

### Typical contents

```text
compliance/
├─ security.md
├─ privacy.md
├─ cost-limits.yaml
└─ performance-budgets.yaml
```

---

## A.11 runbooks/ — operational response

### Purpose

Defines how humans respond to failures.

### Rules

* Short and explicit.
* No architecture descriptions.

### Typical contents

```text
runbooks/
├─ rollback.md
├─ incident-response.md
└─ escalation.md
```

---

## A.12 ai/ — AI execution configuration

### Purpose

Defines how AI systems operate within the SDLC.

### Rules

* Controls AI behaviour.
* Never contains intent.

### Typical contents

```text
ai/
├─ prompts/
├─ policies.yaml
├─ guardrails.yaml
└─ memory.md
```

---

## A.13 README.md — orientation only

### Purpose

Human-readable overview.

### Rules

* Points to intent, spec, and decisions.
* No duplication of authoritative content.

---

## A.14 Authority order (critical)

When conflicts exist, authority is resolved in this order:

1. intent/
2. spec/
3. decisions/
4. compliance/
5. observability/
6. infra/
7. tests/
8. src/

Code **never overrides intent or decisions**.

---

## A.15 Compliance rule

A repository is **AI-SDLC v1.0 compliant** only if:

* all required directories exist,
* required files are present,
* decisions are logged,
* constraints are enforceable,
* observability exists before deployment.

---

## A.16 Summary

This file and folder standard ensures that:

* humans control purpose and judgement,
* AI controls execution,
* automation enforces safety,
* evidence drives change,
* accountability is explicit.

It is intentionally strict.

---

# Appendix B: YAML Specification Schemas

This appendix defines the normative YAML schemas used by AI-SDLC v1.0.
These schemas are machine-checkable and enforceable.

---

## B.1 spec/system.yaml

Defines system identity, ownership, and scope.

```yaml
system:
  name: string
  version: string
  description: string

ownership:
  intent_owner: string
  decision_owner: string
  system_steward: string

scope:
  in_scope:
    - string
  out_of_scope:
    - string
```

Rules:

* system.name, ownership.intent_owner, and ownership.decision_owner are required.
* Version changes require a recorded decision in decisions/.

---

## B.2 spec/interfaces.yaml

Defines externally visible behaviour.

```yaml
interfaces:
  - name: string
    type: api | event | job
    description: string

    endpoint:
      method: GET | POST | PUT | PATCH | DELETE
      path: string

    input:
      schema_ref: string

    output:
      schema_ref: string

    errors:
      - code: string
        description: string

    auth:
      type: none | api_key | oauth2 | jwt
```

Rules:

* Every interface MUST define errors.
* Authentication MUST be explicit (none is allowed, but must be stated).

---

## B.3 spec/data.yaml

Defines persistent and transient state.

```yaml
data:
  stores:
    - name: string
      type: postgres | mysql | dynamodb | redis | filesystem
      purpose: string

      entities:
        - name: string
          fields:
            - name: string
              type: string
              nullable: boolean
              primary_key: boolean
```

Rules:

* Every store MUST declare purpose.
* Data creation MUST be explicit (no implicit entities).

---

## B.4 spec/nfr.yaml

Defines enforceable non-functional requirements.

```yaml
nfr:
  availability:
    target_percentage: number

  performance:
    latency_p95_ms: number
    throughput_rps: number

  reliability:
    error_rate_percentage: number

  cost:
    monthly_budget_limit: number
    currency: string

  scalability:
    max_users: number
```

Rules:

* At least one NFR section MUST be present.
* NFRs MUST be measurable at runtime.

---

## B.5 spec/acceptance.yaml

Defines correctness via scenarios.

```yaml
acceptance:
  - scenario: string
    given:
      - string
    when:
      - string
    then:
      - string
```

Rules:

* Each interface MUST have at least one acceptance scenario.
* Scenarios MUST be testable.

---

## B.6 spec/observability.yaml

Defines required runtime evidence.

```yaml
observability:
  metrics:
    - name: string
      type: counter | gauge | histogram
      description: string

  logs:
    - name: string
      level: info | warn | error
      description: string

  alerts:
    - name: string
      condition: string
      severity: low | medium | high | critical
```

Rules:

* Observability MUST exist before deployment.
* Alerts MUST map to NFR breaches or constraint violations.

---

## B.7 spec/security.yaml (optional but recommended)

Defines security posture.

```yaml
security:
  data_classification: public | internal | confidential | restricted

  controls:
    - name: string
      enforced: boolean

  secrets:
    storage: vault | env | kms
```

Rules:

* If data_classification is not public, at least one controls entry MUST be present.
* Secrets MUST NOT be stored in code or committed to the repo.

---

## B.8 Cross-schema invariants

Automation MUST enforce all of the following:

* Every item in interfaces has at least one matching acceptance scenario in acceptance.
* Every NFR defined in nfr.yaml has at least one corresponding metric in observability.metrics.
* Every alert corresponds to a constraint breach (NFR or security control).
* No production deployment is allowed without observability.

If any invariant fails, the pipeline MUST block deployment.

---

## B.9 Authority order reminder

When conflicts exist, resolve them in this order:

1. intent/
2. spec/
3. decisions/
4. compliance/
5. implementation (src/)

Code MUST NOT override intent or decisions.
