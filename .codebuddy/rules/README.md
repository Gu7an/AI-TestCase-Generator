# Test Case Rules

本目录负责**测试用例生成层**（需求分析 → 场景 → 用例 → 质量检查 → 优先级/冒烟 → 输出）。
自动化脚本生成层位于 `Automation Rules/`。

---

## Relationship

```text
需求 / PRD / 接口文档 / 原型
    ↓
Test Case Rules（本目录）
    ↓
生成测试用例
    ↓
用户明确要求自动化
    ↓
Automation Rules
    ↓
┌──────────────┬──────────────┐
│ UI           │ API          │
│ Appium       │ requests     │
│ Pytest       │ Pytest       │
└──────────────┴──────────────┘
```

---

## Single Source of Truth

以下内容全体系只允许有一份正文，其他位置（`commands/`、`skills/`、`agents/`）必须引用而非复述：

| 内容 | 唯一真源 |
|---|---|
| 测试分析流程（18 步） | `00_AITestCaseGeneration - Main Rule.md` |
| 需求分析 | `01_RequirementAnalysis_Rule.md` |
| 场景分析 | `02_ScenarioAnalysis_Rule.md` |
| 用例生成（含字段规范） | `03_TestCaseGeneration_Rule.md` |
| 质量检查（含异常/业务规则拦截判定） | `04_TestCaseQuality_Rule.md` |
| 优先级与冒烟 | `05_Priority&Smoke_Rule.md`（P0/P1/P2） |
| 输出格式与表格 | `06_TestCaseOutput_Rule.md` |
| 领域风险清单 | `07_DomainRiskChecklist_Rule.md` |
| 自动化主流程 + 交付物清单 | `Automation Rules/00_Automation Main Control Rule.md` |
| UI 定位策略 | `Automation Rules/UI Automation/04_UI Locator Rule.md` |
| API 必填信息 | `Automation Rules/API Automation/04_API Information Extraction Rule.md` |
| UI / API 其他技术细节 | `Automation Rules/UI Automation/01~03、05~10`、`API Automation/01~03、05~10` |

---

## Important Rules

1. 测试用例生成与自动化脚本生成严格分离。
2. 领域风险清单必须在场景矩阵完成后交叉校验（`00_Main` STEP 10.1）。
3. 优先级只有 P0/P1/P2 三档，P0 占比控制在 20%~35%。
4. 用例字段以 `03` + `06` 为准，执行层不得自定义字段。
5. 输出格式以 `06` 的十段顺序为准。
6. 异常场景与业务规则拦截分开统计（`04` 第 2.1 节）。
7. 禁止虚构需求、业务规则、接口与测试数据。

---

## Modification Discipline

改动任一流程或规则前，必须先确认该内容是否已在 `commands/`、`skills/`、`agents/` 中被复述；若已复述，必须同步改为引用。

权威声明以 `00_AITestCaseGeneration - Main Rule.md` 的 `# Rule Loading` 为准，本文件为可读入口。

---

## Existing Automation Rules

自动化层继续由 `Automation Rules/` 负责，不需要迁移到本目录。
