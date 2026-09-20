---
description: 接口自动化测试数据与环境配置规则。
alwaysApply: false
---

# API Test Data Rule

## Data Separation

测试数据与测试逻辑分离。

优先使用：
- fixture
- JSON/YAML
- 参数化
- 环境变量

## Sensitive Data

账号、密码、Token、Secret、密钥等不得硬编码到源码。

## Data Dependency

必须识别：
- 前置创建数据
- 上游 ID
- Token
- Session
- 数据清理
- 状态依赖

## Isolation

测试之间尽量独立。
如果必须依赖前置接口，明确依赖关系并控制执行顺序。
