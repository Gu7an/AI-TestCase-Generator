---
name: test-automation-generation
description: 在用户明确要求自动化测试时，将已有测试用例转换为可维护、可执行、可追踪的 Python + Pytest 自动化测试项目；支持 Appium UI 自动化和 requests API 自动化。
---

# Test Automation Generation Skill

## Purpose

本 Skill 只在用户明确要求生成、编写、转换或完善自动化脚本 / 自动化项目时执行。

核心流程：

测试用例 → 自动化分析 → 可行性分类 → UI/API 分类 → 项目设计 → 脚本生成 → 质量检查 → 用例与脚本追踪 → 输出

**不得因生成测试用例而自动触发本 Skill。**

---

# 1. Input

优先使用：

- 已生成测试用例
- 用户提供的测试用例
- 需求 / PRD
- UI 页面信息 / Appium Inspector XML
- API 文档 / Swagger / OpenAPI
- Postman / curl / 抓包 / 请求日志
- 用户提供的环境、账号和测试数据

如果自动化所需信息缺失：

`需求待确认` 或 `MANUAL / BLOCKED`

禁止猜测。

---

# 2. Automation Feasibility

逐条判断测试用例：

### AUTO

可稳定自动执行和验证。

### PARTIAL

部分可自动化。

必须说明：

- 自动化部分
- 人工部分
- 原因

### MANUAL

当前条件下无法可靠自动化。

必须说明原因，不得为了生成代码而强行自动化。

---

# 3. Automation Type

根据测试对象分开处理：

## UI Automation

技术栈：

`Python + Pytest + Appium`

流程：

测试用例
→ 页面 / 元素分析
→ 定位策略
→ Page Object
→ 等待策略
→ 操作封装
→ 断言
→ Pytest 测试

## API Automation

技术栈：

`Python + Pytest + requests`

流程：

测试用例
→ API 信息分析
→ 请求参数
→ 测试数据
→ 请求封装
→ 响应断言
→ Pytest 测试

**UI 与 API 自动化必须保持独立。**

---

# 4. Automation Rules Routing

具体实现必须使用对应 Automation Rules。

## UI

依次参考：

- `01_UI Automation Trigger Rule.md`
- `02_UI Automation Analysis Rule.md`
- `03_UI Project Architecture Rule.md`
- `04_UI Locator Rule.md`
- `05_UI Page Object Rule.md`
- `06_UI Appium Rule.md`
- `07_UI Wait Stability Rule.md`
- `08_UI Assertion Rule.md`
- `09_UI Execution Report Rule.md`
- `10_UI Automation Quality Rule.md`

## API

依次参考：

- `01_API Automation Trigger Rule.md`
- `02_API Input Analysis Rule.md`
- `03_API Project Architecture Rule.md`
- `04_API Information Extraction Rule.md`
- `05_API requests Rule.md`
- `06_API Test Data Rule.md`
- `07_API Assertion Rule.md`
- `08_API Dependency Session Rule.md`
- `09_API Execution Report Rule.md`
- `10_API Automation Quality Rule.md`

本 Skill 负责流程控制，具体技术细节以 Automation Rules 为准。

---

# 5. Information Integrity

禁止虚构：

- UI 元素
- resource-id
- XPath
- URL
- HTTP Method
- Header
- Token / Auth
- Request Body
- Response
- 账号
- 测试数据
- 环境信息

如果缺少必要信息：

1. 明确缺失项
2. 判断是否阻塞
3. 非阻塞则继续可确定部分
4. 阻塞则标记 `MANUAL / BLOCKED`

---

# 6. Project Generation

用户要求完整项目时，根据实际类型生成：

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

# 7. Script Quality

生成后必须检查：

- 项目结构
- UI / API 分离
- 定位稳定性
- 等待策略
- 断言完整性
- 测试数据
- Fixture
- 异常处理
- 重复代码
- 硬编码
- Pytest 测试发现
- Case ID 追踪
- 环境依赖
- 执行方式

优先保证：

**稳定、可维护、可执行、可追踪。**

---

# 8. Traceability

必须建立：

`测试用例 ID → 自动化脚本`

例如：

```text
TC_LOGIN_001 → test_login_success
TC_LOGIN_002 → test_login_invalid_password
TC_LOGIN_003 → MANUAL
```

测试用例 ID 与 Python 函数名分离。

---

# 9. Output

自动化任务至少输出：

1. 自动化类型
2. AUTO / PARTIAL / MANUAL 分类
3. 测试用例 → 脚本映射
4. 项目结构
5. 自动化代码
6. 依赖与环境要求
7. 执行方式
8. 无法自动化项及原因

用户只要求代码时，不强制输出完整项目。

---

# Hard Rules

1. 只有用户明确要求自动化时才执行。
2. 不重新发明测试用例；优先转换已有测试用例。
3. 不虚构 UI、API、数据或环境信息。
4. UI 与 API 自动化分离。
5. AUTO、PARTIAL、MANUAL 必须明确。
6. 不为追求代码完整而猜测缺失信息。
7. 自动化脚本必须可追踪到测试用例。
8. 具体实现以对应 Automation Rules 为准。
