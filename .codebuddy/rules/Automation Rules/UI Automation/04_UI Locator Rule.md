---
description: Appium UI元素定位与Locator管理规则。
alwaysApply: false
---

# UI Locator Rule

## Locator Principle

定位器必须集中管理，不得散落在测试函数中。

优先选择稳定、语义明确、唯一性高的定位方式。
避免依赖易变化的：
- 坐标
- 动态文本
- 层级过深 XPath
- 自动生成的随机属性

## Evidence First

定位器必须来自真实页面证据。
如果没有 XML/Inspector/用户明确提供的 locator：
- 不得编造
- 标记 locator 待补充

## Locator Fallback

只有存在明确失败风险时才设计 fallback。
fallback 必须有顺序和失败日志。

示例策略：
1. resource-id / accessibility id
2. 稳定 text
3. 合理 XPath
4. 坐标点击仅作为明确必要的兜底

## Centralization

```python
class LoginLocator:
    USERNAME = "..."
    PASSWORD = "..."
    LOGIN_BUTTON = "..."
```

测试代码不直接保存 locator 字符串。
