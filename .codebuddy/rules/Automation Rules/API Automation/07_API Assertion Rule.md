---
description: 接口自动化断言与响应验证规则。
alwaysApply: false
---

# API Assertion Rule

## Assertions

根据测试用例预期结果验证：
- HTTP status
- business code
- message
- response fields
- data type
- value
- business state
- related data

## Layered Assertion

必要时：
```text
HTTP层
 ↓
协议/结构层
 ↓
业务层
 ↓
数据关联层
```

## No Weak Assertions

禁止只验证：
```python
assert response is not None
```
来替代真实业务断言。

## Unclear Response

如果没有真实响应结构且需求也无法确定断言：
- 不编造字段
- 标记断言待补充
- 必要时 PARTIAL/MANUAL
