---
name: test-case-generation
description: 根据需求、PRD、接口文档、原型和业务规则，执行系统化测试分析并生成完整、可执行、可追踪的测试用例。
---

# Test Case Generation Skill

## Purpose

本 Skill 负责测试分析与测试用例生成。

适用于：

- 产品需求 / PRD
- 功能说明
- 接口需求
- UI 需求
- 业务规则
- 用户故事
- 技术方案

---

# 流程以真源为准

执行流程以 `00_AITestCaseGeneration - Main Rule.md` 的 18 步为准，本 Skill 不复述流程细节。

各阶段的专项规则：

| 阶段 | 专项规则 |
|---|---|
| 需求分析 | `01_RequirementAnalysis_Rule.md` |
| 场景分析 | `02_ScenarioAnalysis_Rule.md` |
| 用例生成 | `03_TestCaseGeneration_Rule.md` |
| 质量检查 | `04_TestCaseQuality_Rule.md` |
| 优先级 / 冒烟 | `05_Priority&Smoke_Rule.md` |
| 最终输出 | `06_TestCaseOutput_Rule.md` |
| 领域风险清单 | `07_DomainRiskChecklist_Rule.md`（场景矩阵完成后交叉校验） |

---

# 关键口径

```text
用例字段 ：以 03 + 06 为准（9 列：用例ID / 一级模块 / 二级模块 / 前置步骤 /
           用例名称 / 测试点 / 优先级 / 操作步骤 / 预期结果）
优先级   ：P0 / P1 / P2，以 05 为准
输出格式 ：以 06 的十段顺序为准
领域校验 ：场景矩阵完成后、用例生成之前，按 07 交叉校验
异常统计 ：业务规则拦截不计入异常，判定标准见 04 第 2.1 节
```

---

# 边界

```text
测试用例 ≠ 自动化脚本
```

本 Skill 只负责测试分析与测试用例，不触发自动化脚本生成。

其余约束（禁止虚构需求与业务规则、必须完成质量检查、信息不足标记 `需求待确认` 等）以 `00_Main` 的 Core Principles 与 Forbidden 为准。
