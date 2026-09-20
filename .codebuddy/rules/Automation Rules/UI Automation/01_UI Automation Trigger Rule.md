---
description: UI自动化触发与可行性判断规则。
alwaysApply: false
---

# UI Automation Trigger Rule

## Trigger
仅当用户明确要求 UI 自动化、Appium 自动化或将测试用例转换为 UI pytest 脚本时启用。

## Preconditions
必须已有测试用例。测试用例生成任务不能被本规则反向触发。

## Feasibility

每条用例判断：
- UI操作是否明确
- 页面/元素是否可识别
- 测试数据是否可获得
- 前置环境是否可建立
- 预期结果是否可通过 UI/业务状态验证
- 是否存在验证码、真实支付、第三方授权等不可控依赖

## Status
- AUTO：所有关键步骤均可自动化
- PARTIAL：部分步骤可自动化
- MANUAL：关键条件无法自动化

MANUAL 不生成伪造 Appium 代码。

## Required Evidence
优先使用：
1. Appium Inspector XML
2. 页面 UI hierarchy
3. 用户提供的截图/定位信息
4. 测试用例中的明确元素信息

没有页面证据时不得凭经验虚构 resource-id、accessibility id、text 或 XPath。
