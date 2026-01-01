# RelayNet Protocol Status

**Current Protocol Version**: v0.1  
**Status**: Frozen  
**Scope**: RelayNet Core Protocol Documents  

This document defines the **official status and change policy**
for the RelayNet protocol documents under this directory.

本文档用于声明本目录下 RelayNet 协议文档的
**当前状态与变更规则**。

---

## 1. Protocol status

The RelayNet protocol version **v0.1** is declared as **Frozen**.

This means:

- Protocol semantics are considered stable
- The protocol is suitable for reference, implementation, and citation
- No silent or ad-hoc changes are permitted

---

## 2. Frozen meaning

When a protocol version is marked as **Frozen**:

- All documents under this directory form a **logical whole**
- The following documents are frozen together:
  - PROTOCOL_v0.1.md
  - STATE_MACHINES_v0.1.md
  - REJECTED_TRANSITIONS_v0.1.md
  - CONFORMANCE_RULES_v0.1.md
  - GLOSSARY.md (referenced)

---

## 3. Allowed changes

The following changes are permitted without a version bump:

- Typographical corrections
- Language clarifications that do **not** change meaning
- Formatting or layout improvements
- Cross-reference fixes

Such changes MUST NOT alter protocol semantics.

---

## 4. Disallowed changes

The following changes are **explicitly forbidden** under v0.1:

- Adding or removing protocol states
- Modifying allowed or rejected state transitions
- Changing responsibility semantics
- Introducing new protocol concepts
- Altering conformance or compliance rules

Any such change requires a **new protocol version**.

---

## 5. Version evolution policy

- Any semantic change requires a new protocol version (e.g. v0.2, v1.0)
- New versions MUST be documented as separate protocol sets
- Older frozen versions MUST remain accessible and unmodified

---

## 6. Governance

This protocol status is governed by the RelayNet Project Constitution.

In case of conflict, the constitution prevails.

---

End of RelayNet Protocol Status
