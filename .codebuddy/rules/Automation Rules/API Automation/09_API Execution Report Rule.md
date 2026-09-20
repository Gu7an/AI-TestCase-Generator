---
description: API Pytest执行、标记和报告规则。
alwaysApply: false
---

# API Execution & Report Rule

## Discovery

测试文件：
`test_*.py`

测试函数：
`test_*`

Case ID 使用 marker/映射，不负责 pytest discovery。

## Markers

至少：
- case_id
- priority
- smoke

## Execution

提供：
```bash
pytest
pytest -m smoke
```

按 Case ID 执行时必须提供真实可执行的 pytest nodeid/筛选机制。

## Failure Evidence

失败时保留：
- Case ID
- URL/Method（敏感信息脱敏）
- status code
- response body（敏感信息脱敏）
- exception
- log

禁止把 Token、密码、Secret 写入报告。
