---
description: Python requests接口实现规则。
alwaysApply: false
---

# API requests Rule

## Implementation

统一使用 requests 或项目明确要求的 HTTP 客户端。

请求应封装在 client/service 层，测试层负责调用和断言。

## Timeout

必须设置合理 timeout，禁止无限等待。

## Headers

使用真实接口要求。
不要自动添加未经证实的 Header。

## Error Handling

保留 HTTP 状态码、响应体和异常信息。
不要吞掉 requests 异常。

## Session

需要 Cookie/Token/session 时通过 fixture 或 client session 管理。
不得把一次测试运行中的动态 Token 硬编码到源码。

## Retries

仅对明确可安全重试的场景使用有限重试。
涉及创建、支付、扣费等非幂等操作时禁止无条件重试。
