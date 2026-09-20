---
description: 从测试用例、接口资料和请求样例中提取接口实现信息。
alwaysApply: false
---

# API Information Extraction Rule

## Required for Reliable Script

至少需要足以构造真实请求的信息：
- URL
- HTTP Method
- 必要参数
- 必要 Header/Auth
- 可验证的响应或业务断言

## Body

根据真实请求格式判断：
- JSON
- form-data
- x-www-form-urlencoded
- raw
- 其他明确格式

禁止凭经验改变 Content-Type。

## Authentication

Token、Cookie、签名、AES、MD5等必须以实际资料为依据。
如果规则不完整，标记缺失。

## Response

优先根据真实响应结构设计断言。
禁止只断言 HTTP 200 就认定业务成功，除非需求明确如此。
