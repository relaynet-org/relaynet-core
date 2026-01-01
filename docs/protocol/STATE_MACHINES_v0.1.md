# RelayNet Protocol – State Machine Diagrams

**Version**: v0.1  
**Status**: Informative  
**Scope**: RelayNet Core  

This document provides **illustrative state machine diagrams** for the
RelayNet protocol defined in `PROTOCOL_v0.1.md`.

本文档以**示意性状态机图（文字化）**的形式，帮助理解 RelayNet
协议中的状态与状态转移，不引入任何新的协议语义。

All terms used in this document are defined in:  
`docs/GLOSSARY.md`

---

## 1. Relay Task State Machine

### 1.1 States

A Relay Task MUST be in exactly one of the following states:

- Initialized  
- Active  
- Completed  
- Failed  

---

### 1.2 State diagram (illustrative)

        +----------------+
        |  Initialized   |
        +----------------+
                 |
                 | (task starts)
                 v
        +----------------+
        |     Active     |
        +----------------+
           |          |
           |          |
(successful) | | (failure)completion | |
             v v
+-------------+ +-----------+
| Completed | | Failed |
+-------------+ +-----------+


---

### 1.3 Interpretation notes

- A Relay Task **cannot** skip states.
- A Relay Task **cannot** return to `Initialized` once it becomes `Active`.
- `Completed` and `Failed` are **terminal states**.
- Exactly one terminal state MUST be reached.

---

## 2. Relay Stage State Machine

### 2.1 States

A Relay Stage MUST be in exactly one of the following states:

- Pending  
- InProgress  
- Released  

---

### 2.2 State diagram (illustrative)

    +------------+
    |   Pending  |
    +------------+
           |
           | (responsibility accepted)
           v
    +---------------+
    |  InProgress  |
    +---------------+
           |
           | (responsibility released)
           v
    +-------------+
    |  Released   |
    +-------------+

---

### 2.3 Interpretation notes

- A Relay Stage **cannot** transition directly from `Pending` to `Released`.
- Once a Relay Stage reaches `Released`, it is **final**.
- Responsibility is held **only** during the `InProgress` state.

---

## 3. Responsibility handoff timing (conceptual)

The following diagram illustrates responsibility ownership across
sequential Relay Stages within a Relay Task.

Time ─────────────────────────────────────────────>

Participant A: [==== Stage 1 (InProgress) ====]  
Participant B: [==== Stage 2 (InProgress) ====]  
Participant C: [==== Stage 3 (InProgress) ====]  


---

### Interpretation

- Responsibility is **exclusive** at any point in time.
- Responsibility handoff occurs only at explicit Relay Stage boundaries.
- Overlapping responsibility ownership is not permitted by the protocol.

---

## 4. Events and state transitions

Every state transition defined by the RelayNet protocol
MUST be accompanied by an **Auditable Event**.

### Conceptual mapping

StageAccepted : Pending → InProgress  
StageReleased : InProgress → Released  
TaskCompleted : Active → Completed  
TaskFailed : Active → Failed


Auditable Events record **facts**, not interpretations.

---

## 5. Relationship to protocol rules

- This document is **illustrative only**.
- All **normative rules** are defined in `PROTOCOL_v0.1.md`.
- In case of any inconsistency, the protocol specification prevails.

---

End of RelayNet State Machine Diagrams v0.1
