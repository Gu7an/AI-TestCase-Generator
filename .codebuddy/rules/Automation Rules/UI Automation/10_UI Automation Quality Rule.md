---
description: UI自动化脚本质量检查规则。
alwaysApply: false
---

# UI Automation Quality Rule

生成代码后必须二次检查：

[ ] 每个 AUTO 用例都有脚本
[ ] PARTIAL 未被伪装成完整自动化
[ ] MANUAL 未生成伪造脚本
[ ] Case ID 与 pytest 函数正确映射
[ ] test 文件/函数符合 pytest discovery
[ ] locator 集中管理
[ ] 无明显硬编码
[ ] Page Object 与 tests 分层正确
[ ] 没有 Page Object 断言
[ ] 等待机制合理
[ ] 没有无限重试
[ ] 失败证据配置正确
[ ] 测试之间尽量隔离
[ ] 脚本与测试用例预期结果一致
[ ] 所有无法实现的部分有原因

发现问题必须修正后再输出。
