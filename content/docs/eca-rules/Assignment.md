---
title: "Assignment"
date: 2021-10-14T14:16:26+08:00
author: 张学鹏
---
### Assignment
>

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