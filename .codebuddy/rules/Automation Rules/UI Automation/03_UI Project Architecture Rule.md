---
description: Appium + Pytest UI自动化项目架构规则。
alwaysApply: false
---

# UI Project Architecture Rule

## Standard Structure

```text
ui_automation/
├── config/
│   └── settings.py
├── core/
│   ├── base_page.py
│   ├── driver_factory.py
│   └── logger.py
├── pages/
│   └── xxx_page.py
├── locators/
│   └── xxx_locator.py
├── tests/
│   └── test_xxx.py
├── utils/
│   ├── screenshot.py
│   ├── dump_ui.py
│   └── report.py
├── conftest.py
├── pytest.ini
├── requirements.txt
└── run_tests.py
```

## Layer Boundaries

- tests：业务流程与断言
- pages：页面对象和业务操作
- locators：定位信息
- core：Driver、BasePage、通用能力
- config：设备、包名、超时、环境变量
- utils：日志、截图、dump、报告

禁止：
- test 中直接写复杂 XPath
- test 中直接调用 driver 原始操作
- Page Object 中写业务断言
- 硬编码设备、账号、密码、环境地址

## Pytest Discovery

测试文件推荐：
`test_*.py`

测试函数必须：
`test_*`

Case ID 不承担 pytest discovery 职责。

## Case Mapping

```python
@pytest.mark.case_id("XH_ORD_001")
def test_create_order_success():
    ...
```
