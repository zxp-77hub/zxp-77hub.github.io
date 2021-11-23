---
title: "Assignment"
date: 2021-10-14T14:16:26+08:00
author: 张学鹏
---                                                                
### Assignment
> 给目标字段进行赋值

```javascript
type IAssignmentParams struct {
	/**
	 * 被赋值字段
	 */
	Field string `json:"field"`

	/**
	 * 赋值结果，支持表达式
	 */
	Expr string `json:"expr"`

}
```

### 示例
### 1. 仓库子表初始化默认值

```json
{
  "id": "d4f0a045-f3c2-4b59-be9d-279edfe08184",
  "description": "表体初始化默认值",
  "reference": "miscReceiptItems",
  "condition": {
    "if": "$current.editFlag === 'add' && $current.srcObject === undefined"
  },
  "actions": [
    {
      "name": "Assignment",
      "params": {
        "expr": "$root.warehouse",
        "field": "warehouse"
      }
    }
  ]
}
```