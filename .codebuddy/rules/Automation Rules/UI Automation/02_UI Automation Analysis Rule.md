---
description: UI测试用例到Appium自动化实现的分析规则。
alwaysApply: false
---

# UI Automation Analysis Rule

## Analysis

对每条测试用例提取：
- Case ID
- 模块
- 页面
- 前置条件
- 测试数据
- UI操作
- 页面状态变化
- 断言
- 外部依赖
- 自动化状态

## Mapping

```text
测试用例步骤
 ↓
页面
 ↓
Page Object方法
 ↓
Locator
 ↓
测试函数
```

测试用例中的业务语义必须保留到自动化代码中。

## Atomicity
一个 pytest 测试函数对应一个明确测试目标。
不得把多个无关测试目标合并成一个测试函数。

## Unsupported
对真实验证码、无法控制的第三方页面、不可控支付、人工审批等步骤：
- 标记阻塞
- 不编造绕过方案
- 必要时输出 PARTIAL
