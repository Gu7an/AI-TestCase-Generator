---

## description: 使用 AI 测试分析 Agent 完成测试用例分析，并在用户明确要求时生成自动化测试脚本

# Test Case Command

使用 `test-analyst` Agent 执行测试分析。

使用：

`test-case-generation` Skill。

---

# 1. 流程以真源为准

本命令不复述流程细节，一律引用唯一真源：

| 内容 | 唯一真源 |
|---|---|
| 测试分析流程（18 步，不得跳步） | `00_AITestCaseGeneration - Main Rule.md` |
| 需求分析 / 场景分析 / 用例生成 / 质量检查 / 优先级冒烟 / 输出格式 / 领域风险清单 | `01`~`07` 对应规则 |
| 领域风险交叉校验时机 | `00_Main` STEP 10.1（场景矩阵完成后、用例生成之前） |
| 用例字段 | `03_TestCaseGeneration_Rule.md` + `06_TestCaseOutput_Rule.md` |
| 优先级 | `05_Priority&Smoke_Rule.md`（P0/P1/P2） |
| 内部分析顺序 | `06_TestCaseOutput_Rule.md`（十段顺序，不进入交付物） |
| 交付物格式与交付范围 | `00_OutputFormat_Rule.md` |
| 自动化主流程 | `Automation Rules/00_Automation Main Control Rule.md` |
| 自动化交付物清单 | `Automation Rules/00_Automation Main Control Rule.md` 的 Final Output |
| UI / API 技术细节 | `Automation Rules/UI Automation/01~10`、`API Automation/01~10` |
| 自动化项目目录结构 | `test-automation-generation` Skill 第 6 节 |

---

# 2. 信息不足处理

指向 `00_Main` Core Principles 1 与 `test-analyst` Agent 第 1.1 节。

---

# 3. 自动化触发

默认不生成自动化脚本。

是否进入自动化流程，以 `Automation Rules/00_Automation Main Control Rule.md` 的 Core Boundary 为准。

---

# 4. 边界

```text
测试用例 ≠ 自动化脚本
UI ≠ API
假设 ≠ 事实
代码完整 ≠ 信息真实
```
