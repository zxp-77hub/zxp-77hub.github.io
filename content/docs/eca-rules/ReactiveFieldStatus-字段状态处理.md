---
title: "ReactiveFieldStatus-字段状态处理"
date: 2021-09-30T10:39:28+08:00
author: 张学鹏
---

### ReactiveFieldStatus
> 控制字段的各种状态，必填/只读

```angular2html
{
    "name": "ReactiveFieldStatus",
    "description": "描述处理的场景",
    "params": {
        "effect": {
            "expr": "true", // 
            "fireImmediately": true, // 是否立即执行
            "status": "Readonly", // Readonly，Required
            "when": "$root.createdOrg === undefined" // 触发条件
        },
        "field": "startPeriod"  // 处理字段
    }
},
```