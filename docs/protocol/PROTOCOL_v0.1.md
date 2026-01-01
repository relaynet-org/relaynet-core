# RelayNet Protocol Specification

**Version**: v0.1  
**Status**: Draft  
**Scope**: RelayNet Core  

This document specifies the **core protocol semantics** of RelayNet.
It defines the minimal, canonical rules for responsibility handoff
across organizations.

本文档定义 RelayNet 的**核心协议语义**，
用于规范跨组织物流协作中的责任接力规则。

All terms used in this document are defined in:
`docs/GLOSSARY.md`

Any interpretation inconsistent with the glossary is invalid.

---

## 1. Protocol scope and non-goals

### 1.1 In scope

The RelayNet protocol defines:

- Responsibility modeling
- Relay Task structure
- Relay Stage boundaries
- State models and state transitions
- Auditable events and their semantics

---

### 1.2 Explicit non-goals

The protocol does **not** define:

- Transport, routing, or dispatch logic
- User interfaces or workflows
- Business or industry-specific rules
- Identity, authentication, or authorization mechanisms
- Data storage, APIs, or deployment models

Implementations must not infer or extend protocol semantics
beyond what is explicitly defined here.

---

## 2. Core protocol objects

### 2.1 Relay Task

A **Relay Task** represents a complete, end-to-end responsibility chain.

#### Properties (conceptual)

- A Relay Task MUST consist of one or more Relay Stages.
- A Relay Task MUST have a clearly defined start and terminal condition.
- At any point in time, a Relay Task MUST have a well-defined State.

A Relay Task is **not** equivalent to an order, job, or shipment,
even if implementations map it to such concepts.

---

### 2.2 Relay Stage

A **Relay Stage** is a bounded responsibility interval within a Relay Task.

#### Properties (conceptual)

- A Relay Stage MUST be associated with exactly one Participant.
- A Relay Stage MUST have explicit entry and exit conditions.
- Responsibility during a Relay Stage is exclusive.

Relay Stages MUST NOT overlap in responsibility ownership.

---

### 2.3 Participant

A **Participant** is an identifiable entity capable of holding responsibility.

The protocol assumes Participants exist but does not define:

- How they are identified
- How they are authenticated
- How trust is established

These concerns are intentionally left to implementations.

---

## 3. State model

### 3.1 Relay Task states

A Relay Task MUST be in exactly one of the following states:

- **Initialized**  
  The task has been defined but responsibility has not yet begun.

- **Active**  
  Responsibility is currently held by a Participant via a Relay Stage.

- **Completed**  
  The task has reached its terminal condition successfully.

- **Failed**  
  The task has reached a terminal condition unsuccessfully.

No other states are valid at protocol level.

---

### 3.2 Relay Stage states

A Relay Stage MUST be in exactly one of the following states:

- **Pending**  
  The stage is defined but responsibility has not yet been accepted.

- **InProgress**  
  Responsibility has been accepted and is actively held.

- **Released**  
  Responsibility has been formally released.

---

## 4. State transitions

### 4.1 General rules

- All state transitions MUST be explicit.
- Implicit or inferred transitions are invalid.
- Transitions MUST follow protocol-defined rules.
- Invalid transitions MUST be rejected.

---

### 4.2 Relay Task transitions

Valid Relay Task transitions:

- Initialized → Active
- Active → Completed
- Active → Failed

No other transitions are permitted.

---

### 4.3 Relay Stage transitions

Valid Relay Stage transitions:

- Pending → InProgress
- InProgress → Released

Once a Relay Stage is Released, it MUST NOT transition again.

---

## 5. Responsibility handoff rules

### 5.1 Acceptance of responsibility

Responsibility is considered accepted only when:

- A Relay Stage transitions from **Pending** to **InProgress**
- An Auditable Event records this transition

---

### 5.2 Release of responsibility

Responsibility is considered released only when:

- A Relay Stage transitions from **InProgress** to **Released**
- An Auditable Event records this transition

---

### 5.3 Exclusivity

At any point in time:

- Responsibility MUST be held by at most one Participant.
- Shared or ambiguous responsibility is not permitted at protocol level.

---

## 6. Auditable events

### 6.1 Definition

An **Auditable Event** records a responsibility-related fact or state transition.

Events MUST be:

- Immutable
- Time-ordered
- Referenced to a specific Relay Task or Relay Stage

---

### 6.2 Required event categories

At minimum, the following event categories MUST exist:

- TaskInitialized
- StageAccepted
- StageReleased
- TaskCompleted
- TaskFailed

Event payloads are implementation-defined but semantics are fixed.

---

## 7. Protocol compliance

An implementation is considered **RelayNet-compliant** if and only if:

- All protocol states are respected
- All transitions are explicitly recorded
- All terms are used according to the glossary
- No additional protocol semantics are introduced

---

## 8. Governance

This protocol is governed by the RelayNet Project Constitution.

- The constitution overrides this document in case of conflict.
- Changes to protocol semantics require versioned updates.
- Backward compatibility considerations are mandatory.

---

## 9. Versioning

- v0.1 defines the minimal viable protocol semantics.
- Minor revisions may clarify language without changing meaning.
- Breaking changes require a major version increment.

---

End of RelayNet Protocol Specification v0.1
