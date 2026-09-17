---
name: test-case-generation
description: 根据需求、PRD、接口文档、原型和业务规则，执行完整的AI测试分析和测试用例生成流程。
---

# Test Case Generation Skill

## Purpose

本 Skill 用于执行完整的软件测试分析和测试用例生成任务。

适用于：

- 产品需求
- PRD
- 功能需求
- 接口需求
- UI需求
- 业务规则
- 用户故事
- 功能说明
- 技术方案

---

# Workflow

## Phase 1：Requirement Understanding

首先读取用户提供的全部需求资料。

识别：

- 业务目标
- 用户角色
- 功能范围
- 功能模块
- 业务对象
- 输入
- 输出
- 前置条件
- 后置条件
- 状态
- 业务规则
- 数据约束
- 外部依赖

禁止直接生成测试用例。

---

## Phase 2：Requirement Analysis

使用：

`01_RequirementAnalysis_Rule.md`

建立需求模型。

输出：

### 业务目标

### 用户角色

### 功能模块

### 业务流程

### 业务规则

### 数据规则

### 状态变化

### 权限关系

### 系统依赖

### 风险点

---

## Phase 3：Scenario Analysis

使用：

`02_ScenarioAnalysis_Rule.md`

建立完整测试场景。

至少考虑：

### 正常场景

### 异常场景

### 边界场景

### 空值场景

### 非法数据

### 状态场景

### 权限场景

### 重复操作

### 并发场景

### 网络异常

### 超时

### 中断

### 恢复

### 数据一致性

### 兼容性

### 安全性

---

## Phase 4：Domain Risk Analysis

使用：

`07_DomainRiskChecklist_Rule.md`

根据具体业务领域执行风险检查。

例如：

登录类：

- 身份认证
- Token
- Session
- 验证码
- 登录失败
- 锁定
- 多设备

支付类：

- 金额
- 支付状态
- 重复支付
- 回调
- 幂等
- 退款
- 订单状态
- 余额一致性

AI Agent 类：

- 上下文
- 多轮会话
- 流式响应
- SSE
- 超时
- 中断
- 重复提交
- Token限制
- 多模态
- 模型异常

具体检查项以 `07_DomainRiskChecklist_Rule.md` 为准。

---

## Phase 5：Risk Gap Analysis

比较：

需求场景
vs
领域风险场景

识别：

- 缺失场景
- 隐含风险
- 未覆盖业务规则
- 未覆盖边界
- 未覆盖异常

发现遗漏后必须补充场景。

---

## Phase 6：Test Case Generation

使用：

`03_TestCaseGeneration_Rule.md`

将测试场景转换为可执行测试用例。

每条测试用例至少包含：

- 测试编号
- 模块
- 测试标题
- 前置条件
- 测试数据
- 测试步骤
- 预期结果
- 优先级
- 冒烟标识

具体格式以 Rule 03 和 Rule 06 为准。

---

## Phase 7：Quality Check

使用：

`04_TestCaseQuality_Rule.md`

检查：

### Requirement Coverage

需求是否全部覆盖。

### Scenario Coverage

测试场景是否全部覆盖。

### Business Rule Coverage

业务规则是否全部覆盖。

### Boundary Coverage

边界条件是否覆盖。

### Exception Coverage

异常流程是否覆盖。

### Risk Coverage

领域风险是否覆盖。

### Data Coverage

数据类型和数据边界是否覆盖。

### Executability

测试人员是否可以直接执行。

### Duplication

是否存在重复测试。

---

## Phase 8：Gap Supplement

如果质量检查发现遗漏：

1. 记录遗漏项
2. 分析遗漏原因
3. 补充测试场景
4. 生成新增测试用例
5. 再次执行质量检查

不得直接忽略遗漏。

---

## Phase 9：Deduplication

对全部测试用例进行去重。

检查：

- 测试目标
- 测试条件
- 测试步骤
- 预期结果

如果多个用例验证相同测试目标，应考虑合并。

---

## Phase 10：Priority & Smoke

使用：

`05_Priority&Smoke_Rule.md`

进行：

- P0
- P1
- P2
- P3

优先级分析。

同时识别：

- 核心功能
- 核心业务链路
- 阻断性功能
- 冒烟测试

---

## Phase 11：Final Output

使用：

`06_TestCaseOutput_Rule.md`

按照规定格式输出。

---

# Final Validation

输出之前必须执行：

需求
↓
功能
↓
业务规则
↓
场景
↓
领域风险
↓
测试用例
↓
质量检查
↓
遗漏补充
↓
去重
↓
优先级
↓
冒烟
↓
最终输出

如果链路存在断点，必须继续分析。

---

# Important Rules

不要：

- 直接从需求生成用例
- 忽略异常场景
- 忽略边界场景
- 忽略领域风险
- 虚构业务规则
- 生成重复用例
- 输出无法执行的测试步骤
- 未完成质量检查就结束