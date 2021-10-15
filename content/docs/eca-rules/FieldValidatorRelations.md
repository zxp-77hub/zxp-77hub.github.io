---
title: "FieldValidatorRelations"
date: 2021-10-14T14:15:46+08:00
author: 张学鹏
---
### FieldValidatorRelations
>

```javascript
type IFieldValidatorRelationsItem = struct {

	/**
	 * 目标字段
	 */
	Source string `json:"source"`

	/**
	 * 校验字段
	 */
	Targets []string `json:"targets"`

	/**
	 * 是否双向影响
	 * 默认值：false
	 */
	Bidirectional bool `json:"bidirectional"`
}

type IFieldValidatorRelations = struct {
	Relations []IFieldValidatorRelationsItem `json:"relations"`
}

```