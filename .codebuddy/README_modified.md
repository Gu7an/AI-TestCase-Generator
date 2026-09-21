# AI Test Case & Automation Generator

基于 **AI Agent + Skill + Rules** 架构构建的智能测试分析与 Python 自动化测试生成框架。

项目提供两条严格分离的能力链路：

1. **测试用例生成**
2. **自动化测试脚本生成**

自动化脚本不会因为生成测试用例而自动执行，只有用户明确要求生成、编写、转换或完善自动化脚本时，才进入自动化流程。

---

# 1. 项目目标

项目不是将需求文字直接转换成测试用例或代码。

测试用例生成必须经过完整测试分析：

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
质量检查
↓
覆盖率检查
↓
遗漏补充
↓
去重
↓
优先级
↓
冒烟测试
↓
最终输出
```

当用户明确要求自动化时，在测试用例完成并通过质量检查后继续：

```text
测试用例
↓
自动化可行性分析
↓
AUTO / PARTIAL / MANUAL
↓
UI / API 分类
↓
自动化输入与依赖分析
↓
项目结构设计
↓
自动化脚本生成
↓
自动化质量检查
↓
测试用例 → 自动化脚本追踪
↓
最终输出
```

---

# 2. 核心能力

## 2.1 测试需求分析

支持：

- PRD
- 需求文档
- 功能说明
- 接口文档
- UI 需求
- 业务规则
- 用户故事
- 技术方案
- 原型说明
- 历史缺陷
- 已有测试用例

分析内容包括：

- 业务目标
- 用户角色
- 功能范围
- 业务对象
- 输入与输出
- 前置与后置条件
- 业务规则
- 数据规则
- 状态变化
- 权限关系
- 系统依赖
- 潜在风险

---

## 2.2 测试场景分析

根据实际业务选择适用场景：

- 正常
- 异常
- 边界
- 空值 / 缺失
- 非法数据
- 数据类型异常
- 状态异常
- 状态转换
- 中断 / 恢复
- 失效状态
- 权限
- 并发
- 重复操作
- 幂等性
- 网络异常
- 超时
- 数据一致性
- 依赖服务异常
- 兼容性
- 安全
- 历史缺陷
- 核心业务回归

不机械生成与业务无关的场景。

---

## 2.3 领域风险检查

在测试场景建立后执行领域风险交叉检查，重点发现：

- 典型业务风险遗漏
- 高风险场景遗漏
- 关键状态遗漏
- 关键依赖遗漏
- 数据风险遗漏
- 权限风险遗漏
- 需求未明确但必须确认的风险

发现遗漏后必须补充测试场景并重新检查。

---

## 2.4 测试用例生成

测试用例必须基于已经完成的：

```text
需求分析
+
业务规则
+
场景分析
+
风险分析
```

每条正式测试用例必须具备：

- 测试编号
- 模块
- 测试标题
- 前置条件
- 测试数据
- 测试步骤
- 预期结果
- 优先级
- 冒烟标识
- 测试依据 / 追踪关系

要求：

- 可执行
- 可验证
- 可追踪
- 无语义重复
- 不虚构业务规则

---

## 2.5 测试质量检查

测试用例生成后必须检查：

- 需求覆盖
- 功能覆盖
- 业务规则覆盖
- 场景覆盖
- 边界覆盖
- 异常覆盖
- 数据覆盖
- 状态覆盖
- 权限覆盖
- 依赖覆盖
- 风险覆盖
- 重复用例
- 可执行性
- 预期结果可验证性
- 需求追踪完整性

发现遗漏：

```text
记录遗漏
↓
分析原因
↓
补充场景
↓
新增用例
↓
重新质量检查
```

未完成质量检查不得结束测试用例生成任务。

---

# 3. 自动化测试能力

## 3.1 自动化触发条件

以下请求才进入自动化 Skill：

- 生成自动化脚本
- 编写自动化脚本
- 测试用例转换为自动化脚本
- 生成 Appium 脚本
- 生成 UI 自动化
- 生成 API 自动化
- 生成 Pytest 自动化
- 生成自动化测试项目
- 根据测试用例生成 Python 自动化代码
- 修改 / 优化已有自动化脚本

如果用户只要求测试分析或测试用例：

**只执行测试用例生成流程，不生成自动化代码。**

---

## 3.2 自动化可行性分类

每条需要自动化的测试用例必须分类：

### AUTO

测试步骤、测试数据、执行环境和验证条件均可以稳定自动化。

### PARTIAL

只有部分步骤可以自动化。

必须明确：

- 自动化部分
- 人工部分
- 无法自动化的具体原因

### MANUAL

当前环境下无法可靠自动化。

必须明确原因。

禁止为了生成代码而强行将测试用例转换为自动化脚本。

---

## 3.3 UI 自动化

技术栈：

```text
Python
+
Pytest
+
Appium
```

流程：

```text
测试用例
↓
页面 / 元素分析
↓
定位策略
↓
Page Object
↓
等待策略
↓
操作封装
↓
断言
↓
Pytest 测试脚本
↓
质量检查
```

具体 UI 技术规则由：

```text
Automation Rules / UI Automation
```

负责。

---

## 3.4 API 自动化

技术栈：

```text
Python
+
Pytest
+
requests
```

可使用：

- Swagger / OpenAPI
- API 文档
- Postman
- curl
- 抓包数据
- 请求日志
- 测试用例中的接口信息
- 用户提供的请求信息

流程：

```text
测试用例
↓
API 信息分析
↓
请求参数分析
↓
测试数据
↓
请求封装
↓
响应断言
↓
Pytest 测试脚本
↓
质量检查
```

具体 API 技术规则由：

```text
Automation Rules / API Automation
```

负责。

---

## 3.5 自动化信息真实性

禁止虚构：

- UI 元素
- resource-id
- accessibility id
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

必要信息缺失时：

```text
需求待确认
```

如果缺失信息导致无法可靠生成：

```text
MANUAL / BLOCKED
```

---

## 3.6 自动化项目输出

用户要求完整项目时，生成可执行 Python 项目。

### UI 项目

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

### API 项目

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

根据实际项目规模创建目录，不创建没有实际职责的文件。

---

## 3.7 测试用例与脚本追踪

自动化生成后必须建立：

```text
测试用例 ID → 自动化脚本
```

例如：

```text
TC_LOGIN_001 → test_login_success
TC_LOGIN_002 → test_login_invalid_password
TC_LOGIN_003 → MANUAL
```

测试用例 ID 与 Python 函数名分离。

---

# 4. 项目结构

```text
AI-TestCase-Generator/
│
├── .codebuddy/
│   │
│   ├── agents/
│   │   └── test-analyst.md
│   │
│   ├── commands/
│   │   └── testcase.md
│   │
│   ├── skills/
│   │   ├── test-case-generation/
│   │   │   └── SKILL.md
│   │   │
│   │   └── test-automation-generation/
│   │       └── SKILL.md
│   │
│   └── rules/
│       │
│       ├── 00_AITestCaseGeneration - Main Rule.md
│       ├── 01_RequirementAnalysis_Rule.md
│       ├── 02_ScenarioAnalysis_Rule.md
│       ├── 03_TestCaseGeneration_Rule.md
│       ├── 04_TestCaseQuality_Rule.md
│       ├── 05_Priority&Smoke_Rule.md
│       ├── 06_TestCaseOutput_Rule.md
│       ├── 07_DomainRiskChecklist_Rule.md
│       │
│       └── Automation Rules/
│           │
│           ├── UI Automation/
│           │   ├── 01_UI Automation Trigger Rule.md
│           │   ├── 02_UI Automation Analysis Rule.md
│           │   ├── 03_UI Project Architecture Rule.md
│           │   ├── 04_UI Locator Rule.md
│           │   ├── 05_UI Page Object Rule.md
│           │   ├── 06_UI Appium Rule.md
│           │   ├── 07_UI Wait Stability Rule.md
│           │   ├── 08_UI Assertion Rule.md
│           │   ├── 09_UI Execution Report Rule.md
│           │   └── 10_UI Automation Quality Rule.md
│           │
│           └── API Automation/
│               ├── 01_API Automation Trigger Rule.md
│               ├── 02_API Input Analysis Rule.md
│               ├── 03_API Project Architecture Rule.md
│               ├── 04_API Information Extraction Rule.md
│               ├── 05_API requests Rule.md
│               ├── 06_API Test Data Rule.md
│               ├── 07_API Assertion Rule.md
│               ├── 08_API Dependency Session Rule.md
│               ├── 09_API Execution Report Rule.md
│               └── 10_API Automation Quality Rule.md
│
└── README.md
```

---

# 5. 架构职责

项目采用：

```text
Agent
+
Command
+
Skill
+
Rules
```

进行职责分层。

```text
                         用户
                          │
                          ↓
                    testcase.md
                          │
                          ↓
                  test-analyst Agent
                          │
             ┌────────────┴────────────┐
             ↓                         ↓
   test-case-generation       用户明确要求自动化
             │                         │
             ↓                         ↓
       测试用例流程          test-automation-generation
             │                         │
             ↓                    ┌────┴────┐
       测试用例输出              UI        API
                                  │          │
                               Appium     requests
                                  │          │
                               Pytest     Pytest
                                  └────┬─────┘
                                       ↓
                                 自动化质量检查
                                       ↓
                                  最终输出
```

---

## 5.1 Agent

文件：

```text
.codebuddy/agents/test-analyst.md
```

职责：

- 定义测试分析角色
- 判断任务类型
- 控制分析流程
- 控制测试用例与自动化脚本边界
- 路由到对应 Skill
- 执行最终质量门禁

解决：

> **谁负责测试分析，以及什么时候进入哪个能力流程？**

---

## 5.2 Command

文件：

```text
.codebuddy/commands/testcase.md
```

职责：

- 提供用户入口
- 调用 `test-analyst`
- 指定测试用例生成流程
- 根据用户明确要求进入自动化 Skill

解决：

> **用户如何启动测试分析和自动化任务？**

---

## 5.3 Test Case Skill

文件：

```text
.codebuddy/skills/test-case-generation/SKILL.md
```

职责：

- 需求分析
- 场景分析
- 风险分析
- 测试用例生成
- 覆盖率检查
- 遗漏补充
- 去重
- 优先级
- 冒烟
- 最终测试用例输出

解决：

> **测试用例应该如何生成？**

---

## 5.4 Automation Skill

文件：

```text
.codebuddy/skills/test-automation-generation/SKILL.md
```

职责：

- 自动化触发
- 自动化可行性分析
- AUTO / PARTIAL / MANUAL 分类
- UI / API 分类
- 自动化项目设计
- 脚本生成
- 自动化质量检查
- 测试用例与脚本追踪

解决：

> **用户明确要求自动化后，如何将测试用例转换为可执行的自动化测试？**

---

## 5.5 Rules

测试用例 Rules：

```text
.codebuddy/rules/
```

自动化 Rules：

```text
.codebuddy/rules/Automation Rules/
```

Rules 负责定义具体的：

- 分析规范
- 技术规范
- 约束
- 输出规范
- 质量检查

Skill 负责流程控制，Rules 负责专业细节。

---

# 6. Rule 说明

## 6.1 Test Case Rules

| Rule | 职责 |
|---|---|
| `00_AITestCaseGeneration - Main Rule.md` | 测试用例生成总控、质量门禁和总体约束 |
| `01_RequirementAnalysis_Rule.md` | 需求结构化分析 |
| `02_ScenarioAnalysis_Rule.md` | 测试场景分析 |
| `03_TestCaseGeneration_Rule.md` | 测试用例生成 |
| `04_TestCaseQuality_Rule.md` | 测试用例质量检查 |
| `05_Priority&Smoke_Rule.md` | 优先级和冒烟测试 |
| `06_TestCaseOutput_Rule.md` | 最终测试用例输出 |
| `07_DomainRiskChecklist_Rule.md` | 领域风险交叉检查 |

## 6.2 UI Automation Rules

| Rule | 职责 |
|---|---|
| `01_UI Automation Trigger Rule.md` | UI 自动化触发条件 |
| `02_UI Automation Analysis Rule.md` | UI 自动化可行性和测试分析 |
| `03_UI Project Architecture Rule.md` | UI 自动化项目结构 |
| `04_UI Locator Rule.md` | 元素定位策略 |
| `05_UI Page Object Rule.md` | Page Object 设计 |
| `06_UI Appium Rule.md` | Appium 实现规范 |
| `07_UI Wait Stability Rule.md` | 等待与稳定性 |
| `08_UI Assertion Rule.md` | UI 断言 |
| `09_UI Execution Report Rule.md` | 执行与报告 |
| `10_UI Automation Quality Rule.md` | UI 自动化质量检查 |

## 6.3 API Automation Rules

| Rule | 职责 |
|---|---|
| `01_API Automation Trigger Rule.md` | API 自动化触发条件 |
| `02_API Input Analysis Rule.md` | API 输入和自动化分析 |
| `03_API Project Architecture Rule.md` | API 自动化项目结构 |
| `04_API Information Extraction Rule.md` | API 信息提取 |
| `05_API requests Rule.md` | requests 实现规范 |
| `06_API Test Data Rule.md` | API 测试数据 |
| `07_API Assertion Rule.md` | API 响应断言 |
| `08_API Dependency Session Rule.md` | Session / Token / 接口依赖 |
| `09_API Execution Report Rule.md` | 执行与报告 |
| `10_API Automation Quality Rule.md` | API 自动化质量检查 |

---

# 7. 使用方式

## 7.1 只生成测试用例

输入：

```text
请根据 login-prd.md 进行完整测试分析并生成测试用例。
```

执行：

```text
test-analyst
↓
test-case-generation
```

不会生成自动化脚本。

---

## 7.2 根据测试用例生成 UI 自动化

输入：

```text
请将刚才生成的登录测试用例转换成 Appium + Pytest 自动化脚本。
```

执行：

```text
test-analyst
↓
test-case-generation
↓
test-automation-generation
↓
UI Automation Rules
```

---

## 7.3 根据测试用例生成 API 自动化

输入：

```text
请将这些 API 测试用例转换成 requests + Pytest 自动化脚本。
```

执行：

```text
test-analyst
↓
test-case-generation
↓
test-automation-generation
↓
API Automation Rules
```

---

## 7.4 生成完整自动化项目

输入：

```text
请根据这些测试用例生成完整的 Appium + Pytest 自动化项目。
```

除测试脚本外，还应输出：

- 项目目录
- 配置文件
- 公共封装
- 测试数据
- Fixture
- requirements.txt
- pytest.ini
- README
- 执行方式
- 测试用例 → 脚本映射
- MANUAL / PARTIAL 用例及原因

---

# 8. 核心边界

必须严格遵守：

```text
测试用例生成 ≠ 自动化脚本生成
```

测试用例任务：

```text
需求
↓
测试分析
↓
测试用例
↓
结束
```

自动化任务：

```text
测试用例
↓
自动化分析
↓
脚本生成
```

并且：

```text
UI Automation ≠ API Automation
```

两类自动化分别使用独立的 Rules 和项目结构。

另外：

```text
风险 ≠ 业务规则
假设 ≠ 事实
AUTO ≠ 必须自动化
代码完整 ≠ 信息真实
```

任何缺失但会影响结论或代码正确性的信息，都必须明确提出，不得使用模糊描述或自行编造。

---

# 9. 质量原则

项目最终目标不是：

> 生成最多的测试用例或最多的自动化代码。

而是：

> **基于真实测试依据建立完整测试覆盖，并在用户明确要求自动化时，将可自动化的测试用例转换为稳定、可维护、可执行、可追踪的 Python + Pytest 自动化测试。**
