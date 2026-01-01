# RelayNet Core

This repository follows a **bilingual documentation policy (English / Chinese)**.  
本仓库采用 **中英双语并列文档策略**，作为项目的长期规范。

---

## English

### What is RelayNet Core?

RelayNet Core is the **protocol and rules core** of the RelayNet project.

It defines the **canonical models, state machines, and semantics**
for responsibility handoff across organizations in logistics workflows.

RelayNet Core serves as the **single source of truth** for all relay rules
and protocol-level concepts.

---

### Public project overview

A public, high-level overview of the RelayNet project, its core ideas,
and architectural boundaries is available at:

**https://relaynet.dev**

This site serves as the canonical public description of the project and
is intended for external readers.

---

### Scope and responsibility

RelayNet Core is responsible for:

- Relay task and relay stage models
- Responsibility state machines and transitions
- Auditable event definitions
- Protocol-level data structures and semantics

RelayNet Core explicitly does **NOT** include:

- User interfaces or frontend code
- Business or industry-specific logic
- SDK convenience layers
- Deployment, operations, or enterprise delivery logic

---

### Relationship to other repositories

- **relaynet-core**  
  Defines protocol rules and semantics (open core)

- **relaynet-sdk**  
  Provides client libraries and integration tools  
  (no rules, no state machines)

- **relaynet-enterprise**  
  Hosts commercial and enterprise-only extensions  
  (private, boundary-protected)

All other repositories must conform to the rules and boundaries
defined in RelayNet Core.

---

### Governance

RelayNet Core is governed by the project constitution.

All design and implementation decisions must comply with:

- Project Constitution  
  `docs/PROJECT_CONSTITUTION.md`

When conflicts arise, the constitution takes precedence over
documentation, discussions, and implementation details.

---

## 中文

### 什么是 RelayNet Core？

RelayNet Core 是 **RelayNet 项目的规则与协议内核**。

它定义了跨组织物流协作中，
**责任接力（responsibility handoff）**所需的
核心模型、状态机与语义约定。

RelayNet Core 是整个项目中
**规则与协议的唯一真源（Single Source of Truth）**。

---

### 对外项目说明

RelayNet 项目的对外立项说明、核心思想与架构边界，
统一发布于：

**https://relaynet.dev**

该站点作为项目的官方公开描述入口，
主要面向外部读者与非实现层用户。

---

### 职责与边界

RelayNet Core 负责：

- 接力任务（Relay Task）与接力阶段（Relay Stage）模型
- 责任状态机与状态转移规则
- 可审计事件（Auditable Event）的定义
- 协议级数据结构与语义约定

RelayNet Core **明确不包含**：

- 任何前端或 UI 代码
- 行业或业务逻辑
- SDK 级便利封装
- 部署、运维或企业交付逻辑

---

### 与其他仓库的关系

- **relaynet-core**  
  定义规则与协议语义（开源内核）

- **relaynet-sdk**  
  提供接入与集成工具  
  （不包含规则与状态机）

- **relaynet-enterprise**  
  承载商业与私有化扩展  
  （私有仓库，严格边界）

所有其他仓库，
均必须遵循 RelayNet Core 中定义的规则与边界。

---

### 治理与裁决

RelayNet Core 受《RelayNet 项目宪法》约束。

任何设计、实现或讨论，
一旦与项目宪法冲突，
均以宪法为最终裁决依据。

详见：

- `docs/PROJECT_CONSTITUTION.md`
