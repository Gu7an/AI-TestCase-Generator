---
description: 接口依赖、Token、Session和业务链路规则。
alwaysApply: false
---

# API Dependency & Session Rule

## Dependency

识别：
- 登录 → Token
- 创建 → 查询
- 创建 → 修改
- 上游 ID → 下游请求
- 异步任务 → 查询结果

动态数据必须通过 extractor/fixture/client 传递。

## Token

Token 生命周期必须明确：
- 获取
- 保存
- 使用
- 失效
- 刷新

## Async

异步业务不得使用固定 sleep 代替状态轮询，除非需求明确规定。
应采用有限次数、有限时间的轮询，并在超时后保留响应证据。

## Data Cleanup

需要清理测试数据时，清理逻辑必须与测试目标区分，并避免影响其他测试。
