---
description: Appium等待、重试、状态恢复和稳定性规则。
alwaysApply: false
---

# UI Wait & Stability Rule

## Wait

优先显式等待，不使用大量固定 sleep。

等待对象包括：
- 元素出现
- 元素可点击
- 页面状态
- 加载完成
- 文案出现
- 页面切换完成

固定 sleep 只能用于明确存在的系统/动画时序问题，并说明原因。

## Retry

仅对可恢复的瞬态失败进行有限重试。
禁止无限重试。

失败后应记录：
- locator
- 当前页面
- 异常
- 重试次数

## State Reset

每条用例必须尽量独立。
需要登录、清理数据、返回首页等操作时，通过 fixture 或公共方法实现。

## Failure Evidence

UI失败至少尽量保存：
- 截图
- UI dump
- 日志

## Stability Gate

不得通过无限等待、无限重试或吞掉异常来制造“通过”。
