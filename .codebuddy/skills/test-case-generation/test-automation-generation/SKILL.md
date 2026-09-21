---
name: test-automation-generation
description: 在用户明确要求自动化测试时，将已有测试用例转换为可维护、可执行、可追踪的 Python + Pytest 自动化测试项目；支持 Appium UI 自动化和 requests API 自动化。
---

# Test Automation Generation Skill

## Purpose

本 Skill 只在用户明确要求生成、编写、转换或完善自动化脚本 / 自动化项目时执行。

**不得因生成测试用例而自动触发本 Skill。**

---

# 流程以真源为准

自动化主流程、AUTO / PARTIAL / MANUAL 三态、自动化类型与技术栈、自动化交付物清单，均以 `Automation Rules/00_Automation Main Control Rule.md` 为准，本 Skill 不复述。

---

# 1. 输入资料

优先使用：

- 已生成测试用例 / 用户提供的测试用例
- 需求 / PRD
- UI 页面信息 / Appium Inspector XML
- API 文档 / Swagger / OpenAPI
- Postman / curl / 抓包 / 请求日志
- 用户提供的环境、账号和测试数据

信息缺失时标记 `需求待确认` 或 `MANUAL / BLOCKED`，禁止猜测。

---

# 2. 技术细节路由

| 内容 | 规则 |
|---|---|
| 自动化触发与可行性 | `Automation Rules/00_Automation Main Control Rule.md` |
| UI 技术细节 | `Automation Rules/UI Automation/01~10` |
| API 技术细节 | `Automation Rules/API Automation/01~10` |
| UI 项目质量 | `Automation Rules/UI Automation/10_UI Automation Quality Rule.md` |
| API 项目质量 | `Automation Rules/API Automation/10_API Automation Quality Rule.md` |

本 Skill 负责资料组织与流程控制，具体技术细节以对应规则为准。

---

# 3. 项目目录结构（真源）

## UI

```text
project/
├── config/
├── pages/
├── tests/
├── utils/
├── data/
├── conftest.py
├── pytest.ini
├── requirements.txt
└── README.md
```

## API

```text
project/
├── config/
├── api/
├── tests/
├── utils/
├── data/
├── conftest.py
├── pytest.ini
├── requirements.txt
└── README.md
```

根据实际规模裁剪目录，不创建无意义文件。

---

# 4. 边界

```text
UI 自动化 ≠ API 自动化
AUTO ≠ 必须自动化
代码完整 ≠ 信息真实
```

UI 与 API 自动化必须保持独立，不得混合生成。

---

# Hard Rules

1. 只有用户明确要求自动化时才执行。
2. 不重新发明测试用例；优先转换已有测试用例。
3. 具体技术实现以对应 Automation Rules 为准。
