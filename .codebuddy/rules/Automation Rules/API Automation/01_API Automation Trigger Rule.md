---
description: 接口自动化触发与可行性判断规则。
alwaysApply: false
---

# API Automation Trigger Rule

仅当用户明确要求接口自动化、API pytest、requests 自动化或将测试用例转换为接口脚本时启用。

## No API Documentation Requirement

接口文档不是强制前置条件。

可接受输入：
1. Swagger/OpenAPI
2. Postman
3. curl
4. 抓包
5. 请求日志
6. 测试用例中的接口信息
7. 用户直接提供的 URL、Method、Headers、Body、Response

## No Guessing

如果没有任何可靠接口信息：
- 不生成猜测的 URL
- 不猜 HTTP Method
- 不猜 Headers
- 不猜鉴权
- 不猜 Body
- 不猜 Response

应标记：
`MANUAL / API_INFORMATION_MISSING`

并列出缺失信息。

## Status
- AUTO
- PARTIAL
- MANUAL
