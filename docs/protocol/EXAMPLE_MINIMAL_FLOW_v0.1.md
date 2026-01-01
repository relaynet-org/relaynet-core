# RelayNet Protocol – Minimal Reference Flow Example

**Version**: v0.1  
**Status**: Informative  
**Scope**: RelayNet Core  

This document provides a **minimal, illustrative reference flow**
demonstrating correct usage of the RelayNet protocol.

本文档通过一个最小示例流程，
帮助理解 RelayNet 协议在现实场景中的正确使用方式。

This example is **non-normative**.
All protocol rules are defined in the protocol specification documents.

All terms used in this document are defined in:  
`docs/GLOSSARY.md`

---

## 1. Scenario overview

This example models a simple logistics responsibility handoff
across three participants.

Participants:

- Participant A: Origin operator
- Participant B: Transport provider
- Participant C: Destination operator

The goal is to demonstrate:

- Relay Task lifecycle
- Relay Stage sequencing
- Responsibility acceptance and release
- Auditable event generation

---

## 2. Relay Task initialization

### 2.1 Task creation

A new Relay Task is defined.

- Relay Task State: `Initialized`
- No responsibility is held at this point

**Interpretation**

At this stage, the task exists conceptually,
but no participant has accepted responsibility.

---

## 3. Relay Stage 1 – Participant A

### 3.1 Stage definition

A Relay Stage is defined for Participant A.

- Relay Stage State: `Pending`
- Assigned Participant: A

---

### 3.2 Responsibility acceptance

Participant A explicitly accepts responsibility.

- Relay Stage State transitions: `Pending → InProgress`
- Relay Task State transitions: `Initialized → Active`
- Auditable Event emitted: `StageAccepted`

**Interpretation**

Responsibility becomes active and exclusive.
The Relay Task is now in an active state.

---

### 3.3 Responsibility release

Participant A completes its responsibility
and explicitly releases it.

- Relay Stage State transitions: `InProgress → Released`
- Auditable Event emitted: `StageReleased`

---

## 4. Relay Stage 2 – Participant B

### 4.1 Stage definition

A new Relay Stage is defined for Participant B.

- Relay Stage State: `Pending`
- Assigned Participant: B

---

### 4.2 Responsibility acceptance

Participant B accepts responsibility.

- Relay Stage State transitions: `Pending → InProgress`
- Auditable Event emitted: `StageAccepted`

---

### 4.3 Responsibility release

Participant B releases responsibility.

- Relay Stage State transitions: `InProgress → Released`
- Auditable Event emitted: `StageReleased`

---

## 5. Relay Stage 3 – Participant C

### 5.1 Stage definition

A Relay Stage is defined for Participant C.

- Relay Stage State: `Pending`
- Assigned Participant: C

---

### 5.2 Responsibility acceptance

Participant C accepts responsibility.

- Relay Stage State transitions: `Pending → InProgress`
- Auditable Event emitted: `StageAccepted`

---

### 5.3 Responsibility release and task completion

Participant C releases responsibility,
and the Relay Task reaches its terminal condition.

- Relay Stage State transitions: `InProgress → Released`
- Relay Task State transitions: `Active → Completed`
- Auditable Event emitted: `StageReleased`
- Auditable Event emitted: `TaskCompleted`

---

## 6. Event sequence summary

The resulting Auditable Event sequence is:

TaskInitialized  
StageAccepted (Stage 1, Participant A)  
StageReleased (Stage 1, Participant A)  
StageAccepted (Stage 2, Participant B)  
StageReleased (Stage 2, Participant B)  
StageAccepted (Stage 3, Participant C)  
StageReleased (Stage 3, Participant C)  
TaskCompleted  


---

## 7. Key protocol guarantees demonstrated

This example demonstrates that:

- Responsibility is always exclusive
- Responsibility handoff occurs only at stage boundaries
- All state transitions are explicit
- All protocol-relevant facts are auditable
- The protocol can be fully reconstructed from events

---

## 8. What this example does NOT define

This example intentionally does not define:

- APIs or data models
- Error handling strategies
- Business-specific rules
- Timing constraints
- Implementation details

Such concerns are outside the scope of the RelayNet protocol.

---

End of Minimal Reference Flow Example v0.1
