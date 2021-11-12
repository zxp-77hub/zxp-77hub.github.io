---
title: "库存相关字段过滤Eca Rules"
date: 2021-11-11T14:21:51+08:00
author: 张学鹏
---

### 1. 明细表存货字段参照过滤-基准类型为数量型
> 
```typescript
{
    "reference": "miscReceiptItems",
    "actions": [
        {
            "name": "ReactiveCriteria",
            "description": "存货参照过滤基准类型为数量型",
            "params": {
                "field": "product",
                "fragment": {
                    "autoClear": true,
                    "criteriaStr": "productStandardTypeId = 'ProductStandardType.quantity'",
                    "fireImmediately": true,
                    "when": "true"
                }
            }
        }
    ]
}
```

### 2. 字段过滤透传props 
```typescript
{
    "name": "ReactiveFieldComponentProps",
    "description": "field: 出入库类型",
    "params": {
        "field": "stockTransType",
        "effects": [
            {
                "props": {
                    "contextOrgIds": "[$current.createdOrg.id]"
                },
                "isDestruct": false,
                "when": "$current.createdOrg.id",
                "fireImmediately": true
            }
        ]
    }
}
```