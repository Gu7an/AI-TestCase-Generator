---
description: UI Pytest执行、标记、报告和失败证据规则。
alwaysApply: false
---

# UI Execution & Report Rule

## Pytest

必须支持：
```bash
pytest
pytest -m smoke
pytest -m "case_id('XH_LOGIN_001')"
```

如果 pytest marker 表达式不适合直接按 case_id 过滤，则提供稳定可执行的替代方案，例如按 nodeid 或专用脚本筛选，不得输出不可执行命令。

## Markers

至少支持：
- case_id
- priority
- smoke

## Reports

根据项目实际选择 HTML/Allure 等报告。
不得声称已经生成某种报告而项目中没有对应依赖或配置。

## Failure Evidence

失败测试应关联：
- Case ID
- screenshot
- UI dump
- log
- exception
