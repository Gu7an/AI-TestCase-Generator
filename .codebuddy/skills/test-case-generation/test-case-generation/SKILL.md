---
name: test-case-generation
description: 根据需求、PRD、接口文档、原型和业务规则，执行系统化测试分析并生成完整、可执行、可追踪的测试用例。
---

# Test Case Generation Skill

## Purpose

负责：

需求理解 → 需求分析 → 功能拆解 → 业务规则 → 场景分析 → 风险分析 → 测试用例 → 质量检查 → 覆盖率 → 遗漏补充 → 去重 → 优先级 → 冒烟 → 输出

适用于：

- 产品需求 / PRD
- 功能说明
- 接口需求
- UI 需求
- 业务规则
- 用户故事
- 技术方案

---

# Workflow

### 1. Requirement Analysis

读取全部测试依据，提取：

- 业务目标
- 用户角色
- 功能范围
- 业务对象
- 输入 / 输出
- 前置 / 后置条件
- 业务规则
- 数据约束
- 状态
- 权限
- 外部依赖

**禁止在完成需求分析前直接生成用例。**

使用：

`01_RequirementAnalysis_Rule.md`

### 2. Scenario Analysis

从适用维度建立场景：

- 正常
- 异常
- 边界
- 空值 / 缺失
- 非法数据
- 状态
- 权限
- 重复 / 幂等
- 并发
- 网络 / 超时
- 中断 / 恢复
- 数据一致性
- 兼容性
- 安全性

使用：

`02_ScenarioAnalysis_Rule.md`

### 3. Domain Risk Analysis

根据业务领域检查特殊风险。

使用：

`07_DomainRiskChecklist_Rule.md`

发现遗漏后必须补充场景。

### 4. Test Case Generation

将已分析场景转换为可执行测试用例。

每条用例至少包含：

- 测试编号
- 模块
- 标题
- 前置条件
- 测试数据
- 测试步骤
- 预期结果
- 优先级
- 冒烟标识

使用：

`03_TestCaseGeneration_Rule.md`
`06_TestCaseOutput_Rule.md`

### 5. Quality Check

检查：

- 需求覆盖
- 场景覆盖
- 业务规则覆盖
- 边界 / 异常覆盖
- 数据覆盖
- 风险覆盖
- 可执行性
- 可验证性
- 重复性

使用：

`04_TestCaseQuality_Rule.md`

发现遗漏：

**记录 → 分析 → 补充场景 → 新增用例 → 再次检查。**

### 6. Priority & Smoke

根据业务影响和风险确定：

- P0
- P1
- P2
- P3

识别核心业务链路和冒烟用例。

使用：

`05_Priority&Smoke_Rule.md`

### 7. Final Output

使用：

`06_TestCaseOutput_Rule.md`

按项目规定格式输出最终测试用例。

---

# Hard Rules

1. 不得从需求原文机械转换测试用例。
2. 不得虚构需求、业务规则或测试数据。
3. 不得忽略异常、边界和领域风险。
4. 不得生成重复用例。
5. 用例必须可执行、可验证、可追踪。
6. 信息不足时明确标记 `需求待确认`。
7. 必须完成质量检查后才能结束。
8. 测试用例生成与自动化脚本生成严格分离。

**本 Skill 只负责测试分析和测试用例，不负责生成自动化脚本。**
