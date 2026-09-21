---
description: 测试用例生成完成后的统一输出格式和结果展示规则。
globs:
  - "**/*.md"
  - "**/*.txt"
  - "**/*.json"
alwaysApply: false
---

# Test Case Output Rule

## Final Output Order

最终输出必须按照以下顺序：

```text
一、需求分析摘要

二、功能拆解

三、业务规则

四、测试场景矩阵

五、测试用例

六、需求覆盖检查

七、遗漏补充

八、重复/无效用例处理

九、需求待确认

十、冒烟测试用例
```

---

# Test Case Table

测试用例必须使用：

| 用例ID | 一级模块 | 二级模块 | 前置步骤 | 用例名称 | 测试点 | 优先级 | 操作步骤 | 预期结果 |
|---|---|---|---|---|---|---|---|---|

字段口径以 `03_TestCaseGeneration_Rule.md` 的 Required Fields 为准。

---

# Coverage Report

输出：

```text
需求覆盖：
X/X

业务规则覆盖：
X/X

正常场景：
X

异常场景：
X（按 04_TestCaseQuality_Rule 第 2.1 节判定标准统计，不含业务规则拦截）

业务规则场景：
X（单独统计，不得与异常场景混计）

依赖覆盖：
X/X（对照 01_RequirementAnalysis_Rule 第 8 节依赖清单）

状态转换覆盖：
X/X（对照 01_RequirementAnalysis_Rule 第 5 节生命周期状态机）

领域清单覆盖：
X/X（对照 07_DomainRiskChecklist_Rule）

边界场景：
X

数据场景：
X

状态场景：
X

权限场景：
X

网络场景：
X

兼容性场景：
X

历史回归：
X
```

禁止在未完成维度判定的情况下输出覆盖率数字。

禁止手填覆盖率细分数字。

所有维度数量必须由用例数据实测得出，并满足：

```text
各维度之和 = 用例总数（或明确标注维度可重叠）
细分之和 ≤ 总数 + 说明
```

若出现「手填 65 条、实测 42 条」这类自相矛盾，判定为覆盖率报告无效。

---

# Missing Coverage

如果发现遗漏：

```text
遗漏维度：
遗漏场景：
遗漏原因：
补充用例：
```

---

# Requirement Questions

需求不明确时：

```text
需求待确认：

1. 问题：
   影响：

2. 问题：
   影响：
```

不得自行补充需求规则。

---

# Output Principles

最终输出必须：

```text
准确
完整
可执行
可验证
可追溯
无明显重复
```

不要为了展示AI分析过程输出大量无关内容。

测试用例最终应该能够直接复制到：

- Excel
- 测试管理平台
- CSV
- Word
- XMind
- 飞书
- HTML