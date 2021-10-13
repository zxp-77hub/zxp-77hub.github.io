---
title: "ReactiveCriteria-字段过滤处理"
date: 2021-09-30T14:33:16+08:00
author: 张学鹏
---
### ReactiveCriteria
>  添加参照字段过滤条件

```angular2html
{
    "name": "ReactiveCriteria",
    "description": "描述",
    "params": {
        "field": "字段id",
        "fragment": {
            "bindVars": {
                "createOrgId": "$root.createOrg.id" // 变量
            },
            "criteriaStr": "createOrgId = :createOrgId",
            "fireImmediately": true,
            "when": "$root.createOrg.id !== undefined"
        }
    }
}
```