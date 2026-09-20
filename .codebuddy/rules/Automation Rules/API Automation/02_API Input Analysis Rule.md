---
description: 接口自动化输入资料分析规则。
alwaysApply: false
---

# API Input Analysis Rule

## Extract

尽可能提取：
- Case ID
- Method
- URL
- Headers
- Query Params
- Path Params
- Request Body
- Authentication
- Cookies/Token
- Response
- Business assertion
- Dependencies
- Test data

## Source Priority

优先使用用户提供的真实资料。
多个来源冲突时：
1. 用户当前明确说明
2. 当前接口请求样例/抓包
3. API文档
4. 测试用例
5. 其他历史资料

无法确认时标记待确认，不擅自选择。

## Missing Information

输出明确缺口，不用占位符伪装成完成脚本。
