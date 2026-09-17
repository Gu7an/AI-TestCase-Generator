# AI Test Case Generation

基于 AI Agent + Skill + Rules 架构构建的智能测试用例生成框架。

用于辅助测试人员对 **PRD、需求文档、接口文档、功能说明、业务规则** 等测试输入进行系统化分析，并生成结构化、可执行、可追踪的测试用例。

---

## 1. 项目目标

本项目不是简单地将需求文字转换成测试用例。

核心目标是建立完整的测试分析链路：

```text
需求理解
    ↓
需求建模
    ↓
功能拆解
    ↓
业务规则分析
    ↓
数据分析
    ↓
状态分析
    ↓
权限分析
    ↓
依赖分析
    ↓
风险分析
    ↓
测试场景设计
    ↓
领域风险交叉检查
    ↓
测试用例生成
    ↓
需求追踪
    ↓
覆盖率检查
    ↓
遗漏补充
    ↓
重复用例处理
    ↓
优先级划分
    ↓
冒烟测试筛选
    ↓
最终输出
```

---

# 2. 核心能力

## 2.1 需求分析

对输入的需求进行结构化分析，包括：

* 需求目标
* 用户角色
* 功能范围
* 业务对象
* 输入与输出
* 前置条件
* 业务规则
* 数据规则
* 状态变化
* 权限关系
* 系统依赖
* 潜在风险

---

## 2.2 测试场景分析

根据需求和业务规则建立测试场景，重点覆盖：

* 正常场景
* 异常场景
* 边界场景
* 空值场景
* 缺失数据
* 非法数据
* 数据类型异常
* 状态异常
* 状态转换
* 中断状态
* 失效状态
* 权限场景
* 并发场景
* 重复操作
* 幂等性
* 网络异常
* 超时
* 中断恢复
* 数据一致性
* 依赖服务异常
* 兼容性
* 安全风险
* 历史缺陷
* 核心业务回归

实际测试场景根据具体业务特征进行选择，不进行无意义的机械扩展。

---

## 2.3 领域风险检查

在测试场景矩阵建立完成后，通过领域风险清单进行交叉检查。

用于发现：

* 典型业务风险遗漏
* 高风险场景遗漏
* 关键状态遗漏
* 关键依赖遗漏
* 数据风险遗漏
* 权限风险遗漏
* 需求未明确但需要确认的风险

---

## 2.4 测试用例生成

根据已经完成的需求分析、业务规则、场景矩阵和风险分析生成测试用例。

测试用例要求：

* 测试目标明确
* 前置条件明确
* 测试步骤可执行
* 测试数据明确
* 预期结果可验证
* 具备需求追踪关系
* 避免语义重复
* 根据风险和业务重要性确定优先级

---

## 2.5 测试质量检查

生成测试用例后进行二次质量检查：

* 需求覆盖率
* 功能覆盖率
* 业务规则覆盖率
* 场景覆盖率
* 边界覆盖率
* 异常覆盖率
* 数据覆盖率
* 状态覆盖率
* 权限覆盖率
* 依赖覆盖率
* 用例重复率
* 用例可执行性
* 预期结果可验证性
* 需求追踪完整性

发现遗漏后继续补充测试用例，而不是直接结束任务。

---

# 3. 项目结构

```text
AI-TestCase-Generator/
│
├── .codebuddy/
│   │
│   ├── agents/
│   │   └── test-analyst.md
│   │
│   ├── skills/
│   │   └── test-case-generation/
│   │       └── SKILL.md
│   │
│   ├── commands/
│   │   └── testcase.md
│   │
│   └── rules/
│       ├── 00_AITestCaseGeneration - Main Rule.md
│       ├── 01_RequirementAnalysis_Rule.md
│       ├── 02_ScenarioAnalysis_Rule.md
│       ├── 03_TestCaseGeneration_Rule.md
│       ├── 04_TestCaseQuality_Rule.md
│       ├── 05_Priority&Smoke_Rule.md
│       ├── 06_TestCaseOutput_Rule.md
│       └── 07_DomainRiskChecklist_Rule.md
│
└── README.md
```

---

# 4. 架构说明

项目采用 Agent + Skill + Rules 的职责分层设计。

```text
                 用户需求
                    │
                    ↓
             test-analyst Agent
                    │
                    ↓
       test-case-generation Skill
                    │
                    ↓
             Main Rule
                    │
       ┌────────────┼────────────┐
       ↓            ↓            ↓
 Requirement    Scenario      Domain Risk
  Analysis      Analysis       Checklist
       │            │            │
       └────────────┼────────────┘
                    ↓
             Test Case Generation
                    ↓
              Quality Check
                    ↓
             Priority & Smoke
                    ↓
               Final Output
```

### Agent

负责定义测试分析角色和职责。

文件：

```text
.codebuddy/agents/test-analyst.md
```

主要解决：

> **谁负责进行测试分析？**

---

### Skill

负责定义完整的测试执行流程。

文件：

```text
.codebuddy/skills/test-case-generation/SKILL.md
```

主要解决：

> **测试分析应该按照什么流程执行？**

---

### Rules

负责定义具体测试规范、约束和质量要求。

目录：

```text
.codebuddy/rules/
```

主要解决：

> **每一个测试分析阶段具体应该遵守什么规则？**

---

# 5. Rule 说明

| Rule                                     | 职责                   |
| ---------------------------------------- | -------------------- |
| `00_AITestCaseGeneration - Main Rule.md` | 测试用例生成总控规则、质量门禁和总体约束 |
| `01_RequirementAnalysis_Rule.md`         | 需求结构化分析              |
| `02_ScenarioAnalysis_Rule.md`            | 测试场景分析               |
| `03_TestCaseGeneration_Rule.md`          | 测试用例生成               |
| `04_TestCaseQuality_Rule.md`             | 测试用例质量检查             |
| `05_Priority&Smoke_Rule.md`              | 优先级和冒烟测试             |
| `06_TestCaseOutput_Rule.md`              | 最终测试用例输出             |
| `07_DomainRiskChecklist_Rule.md`         | 领域风险交叉检查             |

---

# 6. 使用方式

## 6.1 准备测试需求

可以使用以下类型的输入：

```text
PRD
需求文档
功能说明
接口文档
业务规则
原型说明
历史缺陷
已有测试用例
```

---

## 6.2 使用 Test Analyst

打开包含本项目 `.codebuddy` 配置的项目后，使用：

```text
test-analyst
```

进行测试分析。

例如：

```text
请根据 login-prd.md 进行完整测试分析，并生成测试用例。
```

或者：

```text
请根据当前需求生成完整测试用例，
要求执行完整的需求分析、场景分析、
风险检查、覆盖率检查和遗漏补充。
```

---

## 6.3 使用测试用例命令

如果项目配置了：

```text
.codebuddy/commands/testcase.md
```

可以使用项目提供
