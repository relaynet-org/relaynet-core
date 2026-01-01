# RelayNet Glossary（术语表）

**Version**: v0.1  
**Status**: Active  
**Scope**: RelayNet Core (canonical terminology)  

This document defines the **canonical terminology** used in the RelayNet project.  
All protocol documents, implementations, SDKs, and discussions MUST conform to
the definitions in this glossary.

本文档定义 RelayNet 项目中的**规范术语与唯一语义**。  
所有协议文档、实现、SDK 及讨论，均必须遵循本术语表中的定义。

When ambiguity or conflict arises, this glossary takes precedence over
general language usage or contextual interpretation.  
当出现歧义或冲突时，应以本术语表为最终语义依据。

---

## RelayNet

**English definition**  
RelayNet is a protocol-first infrastructure for modeling and governing
responsibility handoff across organizations in logistics workflows.

**中文定义**  
RelayNet 是一个用于建模和治理跨组织物流协作中
**责任接力（responsibility handoff）**的协议型基础设施。

**Notes**  
- RelayNet is a protocol and rule system, not an application.
- RelayNet does not imply a specific deployment or product form.

---

## Responsibility

**English definition**  
Responsibility refers to the explicitly defined obligation held by a participant
to ensure the correctness, completion, or custody of a specific scope
within a relay task.

**中文定义**  
责任是指在接力任务中，由某一参与方在特定范围内
**明确承担的义务与责任边界**。

**Notes**  
- Responsibility is explicit and protocol-defined.
- Responsibility is not inferred implicitly from operations or data.

---

## Relay Task

**English definition**  
A Relay Task is a complete, end-to-end responsibility chain that spans
multiple participants and relay stages.

**中文定义**  
接力任务是一个完整的、跨多个参与方的
**端到端责任接力链**。

**Notes**  
- A Relay Task represents the full lifecycle of responsibility handoff.
- It is not equivalent to an order, job, or workflow instance.

---

## Relay Stage

**English definition**  
A Relay Stage is a bounded interval within a relay task during which
a single participant holds responsibility.

**中文定义**  
接力阶段是接力任务中的一个**有明确边界的责任区间**，
在该区间内责任仅由某一参与方承担。

**Notes**  
- A Relay Stage is defined by responsibility boundaries, not by UI steps.
- A Relay Stage is not a generic process node or activity.

---

## Participant

**English definition**  
A Participant is an identifiable entity that can hold responsibility
within a relay task or relay stage.

**中文定义**  
参与方是指在接力任务或接力阶段中
**能够承担责任的可识别实体**。

**Notes**  
- A participant may represent an organization, system, or legal entity.
- RelayNet does not define participant identity management.

---

## State

**English definition**  
State represents the protocol-defined status of a relay task or relay stage
at a specific point in time.

**中文定义**  
状态是指在某一时间点，
接力任务或接力阶段在协议层面所处的确定状态。

**Notes**  
- State is a protocol concept, not an implementation detail.
- State must be explicitly represented and auditable.

---

## State Transition

**English definition**  
A State Transition is a protocol-governed change from one valid state
to another, subject to defined rules and conditions.

**中文定义**  
状态转移是指在协议规则约束下，
从一个合法状态迁移到另一个合法状态的过程。

**Notes**  
- State transitions are rule-based and deterministic.
- Transitions must not be inferred or implicitly assumed.

---

## Auditable Event

**English definition**  
An Auditable Event is an immutable, protocol-defined record that captures
a responsibility-related fact or state transition.

**中文定义**  
可审计事件是指用于记录责任变化或状态转移的
**不可变协议级事实记录**。

**Notes**  
- Auditable Events form the audit trail of a relay task.
- Events are facts, not interpretations.

---

## Protocol

**English definition**  
Protocol refers to the formal specification of concepts, rules,
state machines, and semantics defined by RelayNet Core.

**中文定义**  
协议是指由 RelayNet Core 定义的
**概念、规则、状态机与语义的正式规范集合**。

**Notes**  
- The protocol precedes implementation.
- Implementations must conform to the protocol, not redefine it.

---

## SDK (Software Development Kit)

**English definition**  
An SDK is a set of integration tools that facilitate interaction
with the RelayNet protocol without embedding protocol rules.

**中文定义**  
SDK 是用于简化与 RelayNet 协议交互的接入工具集合，
**不包含任何协议规则或决策逻辑**。

**Notes**  
- SDKs must not implement or reinterpret protocol semantics.
- SDKs are convenience layers only.

---

## Enterprise Distribution

**English definition**  
An Enterprise Distribution is a commercial or private deployment
that extends RelayNet usage without altering core protocol semantics.

**中文定义**  
企业发行版是指在不改变核心协议语义的前提下，
用于商业或私有化部署的扩展形态。

**Notes**  
- Enterprise distributions must not redefine protocol rules.
- Core protocol neutrality must be preserved.

---

## Glossary governance

This glossary is governed by the RelayNet Project Constitution.

- New terms must be explicitly defined here before being used in protocols.
- Changes to existing definitions require careful review.
- Ambiguous or overloaded terms are intentionally excluded.

本术语表受《RelayNet 项目宪法》约束：

- 新术语必须先在此定义，方可进入协议正文。
- 已有术语的修改需审慎评估。
- 有歧义或多义风险的术语将被刻意排除。
