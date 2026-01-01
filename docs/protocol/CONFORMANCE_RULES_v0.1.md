# RelayNet Protocol – Conformance and Compliance Rules

**Version**: v0.1  
**Status**: Normative  
**Scope**: RelayNet Core  

This document defines the **mandatory conformance and compliance rules**
for any implementation claiming compatibility with the RelayNet protocol.

Any implementation that violates these rules MUST NOT claim
RelayNet protocol compliance.

本文档定义任何声称“支持 RelayNet 协议”的实现
**必须满足的协议一致性与合规性规则**。
违反本规则的实现，不得宣称其符合 RelayNet 协议。

All terms used in this document are defined in:  
`docs/GLOSSARY.md`

This document is normative and enforceable.

---

## 1. Conformance levels

RelayNet defines a **single conformance level** for protocol compliance.

There are no partial, optional, or subset compliance levels in v0.1.

An implementation is either:

- **Compliant**, or
- **Non-compliant**

---

## 2. General compliance requirements

An implementation MUST:

1. Use all protocol terms strictly according to `GLOSSARY.md`
2. Implement all protocol-defined states
3. Enforce all allowed state transitions
4. Reject all forbidden state transitions
5. Preserve protocol-defined semantics without reinterpretation

An implementation MUST NOT:

- Redefine protocol terms
- Introduce additional protocol states
- Infer implicit state transitions
- Auto-correct invalid protocol behavior silently

---

## 3. State model compliance

### 3.1 Relay Task compliance

A compliant implementation MUST:

- Represent all Relay Task states defined in `PROTOCOL_v0.1.md`
- Allow only the explicitly permitted Relay Task transitions
- Enforce terminal state immutability
- Ensure exactly one terminal state is reached

A non-compliant implementation includes, but is not limited to:

- Allowing state regression
- Allowing multiple terminal states
- Skipping required states

---

### 3.2 Relay Stage compliance

A compliant implementation MUST:

- Represent all Relay Stage states defined in `PROTOCOL_v0.1.md`
- Allow only the explicitly permitted Relay Stage transitions
- Enforce responsibility exclusivity
- Prevent re-entry into responsibility after release

A non-compliant implementation includes, but is not limited to:

- Bypassing the `InProgress` state
- Allowing overlapping responsibility ownership
- Allowing duplicate or implicit releases

---

## 4. Rejected transition enforcement

A compliant implementation MUST:

- Explicitly reject all transitions listed in
  `REJECTED_TRANSITIONS_v0.1.md`
- Surface such rejections as errors or violations
- Prevent any state mutation resulting from rejected transitions

Silent acceptance, normalization, or correction of rejected transitions
is strictly prohibited.

---

## 5. Auditable event compliance

A compliant implementation MUST:

- Emit an Auditable Event for every protocol state transition
- Preserve the immutability of Auditable Events
- Maintain a complete, time-ordered event history

Auditable Events MUST:

- Represent protocol facts, not interpretations
- Reference the relevant Relay Task or Relay Stage
- Accurately reflect the associated state transition

Failure to record an event for a state transition
constitutes non-compliance.

---

## 6. Responsibility consistency rules

A compliant implementation MUST ensure that:

- Responsibility is held by **at most one Participant** at any time
- Responsibility exists **only** during `Relay Stage = InProgress`
- Responsibility handoff occurs **only** via explicit state transitions

Any ambiguity, overlap, or inferred responsibility ownership
constitutes a protocol violation.

---

## 7. Error handling and violations

A compliant implementation MUST:

- Detect protocol violations deterministically
- Reject invalid operations before state mutation
- Preserve protocol integrity in the presence of errors

A compliant implementation MUST NOT:

- Mask protocol violations
- Repair invalid state by implicit transitions
- Continue execution after unrecoverable protocol violations

---

## 8. Claiming protocol compliance

An implementation MAY claim **RelayNet protocol compliance** if and only if:

- All rules in this document are enforced
- All protocol documents are respected:
  - `PROTOCOL_v0.1.md`
  - `STATE_MACHINES_v0.1.md`
  - `REJECTED_TRANSITIONS_v0.1.md`
  - `GLOSSARY.md`
- No additional protocol semantics are introduced

False or misleading compliance claims are prohibited.

---

## 9. Governance and versioning

This document is governed by the RelayNet Project Constitution.

- Changes to compliance rules require a protocol version update
- Breaking changes require a major version increment
- Compliance is always evaluated against a specific protocol version

---

End of RelayNet Conformance and Compliance Rules v0.1
