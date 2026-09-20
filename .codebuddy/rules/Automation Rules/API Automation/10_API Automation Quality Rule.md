---
description: API自动化脚本质量检查规则。
alwaysApply: false
---

# API Automation Quality Rule

生成代码后必须检查：

[ ] 每个 AUTO 用例都有脚本
[ ] PARTIAL/MANUAL 正确标记
[ ] 没有猜测 URL/Method/Header/Body
[ ] Case ID 与 pytest 函数正确映射
[ ] test 文件/函数符合 pytest discovery
[ ] requests 调用分层合理
[ ] timeout 已设置
[ ] Token/密码/Secret 未硬编码
[ ] 动态数据正确传递
[ ] 非幂等请求没有危险重试
[ ] 断言与测试用例一致
[ ] 响应敏感数据已脱敏
[ ] 依赖链明确
[ ] 异步流程有合理等待/轮询
[ ] 无效或无法验证的脚本未被伪装成可执行脚本

发现问题必须修正后再输出。
