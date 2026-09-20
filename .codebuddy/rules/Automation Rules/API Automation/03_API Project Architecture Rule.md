---
description: requests + Pytest接口自动化项目架构规则。
alwaysApply: false
---

# API Project Architecture Rule

## Standard Structure

```text
api_automation/
├── config/
│   └── settings.py
├── clients/
│   └── api_client.py
├── services/
│   └── xxx_service.py
├── data/
├── tests/
│   └── test_xxx.py
├── utils/
│   ├── logger.py
│   └── report.py
├── conftest.py
├── pytest.ini
├── requirements.txt
└── run_tests.py
```

## Layering

- tests：测试场景与断言
- services：业务 API 封装
- clients：HTTP 通用能力
- config：环境和认证配置
- data：测试数据
- utils：日志和报告

测试用例中避免直接堆叠大量 requests 请求细节。
