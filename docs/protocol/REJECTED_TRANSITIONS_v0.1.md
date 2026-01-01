# RelayNet Protocol – Rejected State Transitions

**Version**: v0.1  
**Status**: Normative  
**Scope**: RelayNet Core  

This document defines **explicitly forbidden state transitions**
in the RelayNet protocol.

Any implementation that allows or infers the transitions listed below
is **non-compliant** with the RelayNet protocol.

本文档明确列出 RelayNet 协议中 **非法 / 被拒绝的状态转移**。
任何允许或隐式推导下述转移的实现，
均视为 **不符合协议**。

All terms used in this document are defined in:  
`docs/GLOSSARY.md`

This document is normative and MUST be enforced.

---

## 1. Rejected Relay Task State Transitions

The following state transitions for **Relay Task** are explicitly forbidden.

### 1.1 Rejected transitions table

| From State   | To State      | Reason |
|-------------|---------------|--------|
| Initialized | Completed     | A task cannot complete without becoming active |
| Initialized | Failed        | Failure requires an active responsibility stage |
| Active      | Initialized   | State regression is not permitted |
| Completed   | Active        | Terminal state cannot transition further |
| Completed   | Initialized   | Terminal state cannot regress |
| Completed   | Failed        | Terminal state cannot change outcome |
| Failed      | Active        | Terminal state cannot transition further |
| Failed      | Initialized   | Terminal state cannot regress |
| Failed      | Completed     | Terminal state cannot change outcome |

---

### 1.2 Interpretation notes

- Relay Task states are **strictly forward-only**.
- Exactly one terminal state MUST be reached.
- Once a terminal state is entered, the task is immutable.

---

## 2. Rejected Relay Stage State Transitions

The following state transitions for **Relay Stage** are explicitly forbidden.

### 2.1 Rejected transitions table

| From State   | To State      | Reason |
|-------------|---------------|--------|
| Pending     | Released      | Responsibility cannot be released before acceptance |
| InProgress  | Pending       | State regression is not permitted |
| Released    | Pending       | Terminal state cannot regress |
| Released    | InProgress    | Terminal state cannot re-enter responsibility |
| Released    | Released      | Duplicate release is not permitted |

---

### 2.2 Interpretation notes

- Responsibility exists **only** during `InProgress`.
- `Released` is a terminal state.
- Any attempt to bypass `InProgress` invalidates responsibility semantics.

---

## 3. Cross-object invalid transitions

The following transitions are invalid due to **cross-object inconsistency**.

### 3.1 Invalid combinations

| Condition | Reason |
|----------|--------|
| Relay Task is `Initialized` while any Relay Stage is `InProgress` | A task cannot hold responsibility before activation |
| Relay Task is `Completed` while any Relay Stage is not `Released` | All responsibility must be released before completion |
| Relay Task is `Failed` while any Relay Stage is not `Released` | All responsibility must be released before failure |
| Multiple Relay Stages are `InProgress` simultaneously | Responsibility exclusivity violation |

---

## 4. Implementation requirements

An implementation MUST:

- Reject all transitions listed in this document
- Record an error or violation when such transitions are attempted
- Prevent state mutation after terminal states

Silent acceptance or correction of invalid transitions is prohibited.

---

## 5. Relationship to protocol specification

- This document supplements `PROTOCOL_v0.1.md`
- All allowed transitions are defined in the protocol specification
- Any transition not explicitly allowed is implicitly rejected

In case of conflict, the protocol specification prevails.

---

End of Rejected State Transitions v0.1
