---
description: UI自动化断言规则。
alwaysApply: false
---

# UI Assertion Rule

## Principle

断言必须来自测试用例预期结果。

禁止：
```python
assert True
```

禁止为了让脚本通过而弱化断言。

## Assertion Types

可根据实际需求使用：
- 文本
- 元素状态
- 页面状态
- 业务状态
- 数量
- 可见性
- 操作结果

## Traceability

每个自动化测试必须能追溯到 Case ID。

```python
@pytest.mark.case_id("XH_LOGIN_001")
def test_login_success():
    ...
```

## Unverifiable

如果预期结果需要数据库、第三方系统或人工确认，而当前自动化环境无法验证：
- 不伪造断言
- 标记 PARTIAL/MANUAL
- 说明缺失验证条件
