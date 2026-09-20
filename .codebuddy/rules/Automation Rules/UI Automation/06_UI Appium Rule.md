---
description: Appium驱动、设备和会话管理规则。
alwaysApply: false
---

# UI Appium Rule

## Driver

Capabilities 必须集中配置。
禁止在测试函数中创建 Driver。

推荐：
```text
conftest.py
 ↓
driver_factory.py
 ↓
Appium Driver
 ↓
Page Object
```

## Environment

设备名、平台、automationName、包名、activity、Appium server 地址等统一进入 config。

敏感数据使用环境变量。

## Session Isolation

每个测试会话必须有明确生命周期。
避免测试之间依赖上一个测试留下的页面状态。

## App Launch

启动应用信息必须来自真实项目资料。
没有 package/activity 时不得猜测。

## Failure

失败时应尽可能保留：
- screenshot
- UI hierarchy dump
- log
- pytest failure
