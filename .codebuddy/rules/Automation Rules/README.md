# Automation Rules

本目录只负责**自动化脚本生成**，不替代原有测试用例生成规则。

## Relationship

```text
Test Case Rules
    ↓
生成测试用例
    ↓
用户明确要求自动化
    ↓
Automation Main Control
    ↓
┌──────────────┬──────────────┐
│ UI           │ API          │
│ Appium       │ requests     │
│ Pytest       │ Pytest       │
└──────────────┴──────────────┘
```

## Important Rules

1. 测试用例生成与自动化脚本生成严格分离。
2. UI 自动化与 API 自动化严格分离。
3. API 自动化不要求必须存在接口文档。
4. 没有可靠接口信息时禁止猜测接口。
5. Case ID 与 pytest test function 分离。
6. AUTO / PARTIAL / MANUAL 三态管理自动化可行性。
7. 无法可靠自动化的用例不强行生成脚本。
8. UI 项目使用 Appium + Pytest。
9. API 项目使用 requests + Pytest。
10. 自动化代码必须能追溯到原始测试用例。

## Existing Test Case Rules

你现有的测试用例规则继续作为测试用例生成层，不需要迁移到本目录。
