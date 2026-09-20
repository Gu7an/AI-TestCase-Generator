---
description: Appium Page Object设计与业务封装规则。
alwaysApply: false
---

# UI Page Object Rule

## Responsibility

Page Object 负责：
- 页面元素定位
- 页面操作
- 页面状态判断
- 可复用业务动作

测试层负责：
- 测试流程
- 测试数据组织
- 断言

## Method Design

方法必须语义化：

```text
login()
submit_order()
open_settings()
delete_account()
```

禁止：

```text
click_button_1()
click_element()
do_action()
```

除非它们确实是底层通用能力。

## Reuse

公共操作进入 BasePage。
页面专属操作进入对应 Page Object。
禁止复制粘贴相同定位和操作逻辑。

## Back

涉及系统页面或返回操作时，优先使用统一 back 能力：
UI返回 → Page内部返回 → driver.back/物理返回兜底。
具体实现必须符合项目实际能力，不能虚构不存在的方法。
