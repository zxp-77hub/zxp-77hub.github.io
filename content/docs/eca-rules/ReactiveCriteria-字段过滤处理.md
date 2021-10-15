---
title: "ReactiveCriteria-字段过滤处理"
date: 2021-09-30T14:33:16+08:00
author: 张学鹏
---
### ReactiveCriteria
>  添加参照字段过滤条件

```javascript
type IReactiveCriteriaFragment = struct {
	/**
	  取值表达式
	*/
	CriteriaStr string `json:"criteriaStr"`
	/**
	  动态参数
	*/
	BindVars map[string]interface{} `json:"bindVars,omitempty"`
	/**
	  当取值表达式为空时，根据 autoClear 的结果判断是否同步清空
	  默认值：false
	*/
	AutoClear bool `json:"autoClear,omitempty"`
	/**
	  当 when = true 时，才会执行规则
	  默认值：true
	*/
	When string `json:"when,omitempty"`
	/**
	  和其他条件的 与或关系
	*/
	Join string `json:"join,omitempty"`
	/**
	  是否立即生效
	  默认值：false
	*/
	FireImmediately bool `json:"fireImmediately,omitempty"`
}

type IReactiveCriteriaParams = struct {
	/**
	  目标字段
	*/
	Field string `json:"field"`
	/**
	  过滤因素, 支持简单的静态过滤条件字符串 和 复杂的结构化设置
	*/
	Fragment  *IReactiveCriteriaFragment   `json:"fragment,omitempty"`
	Fragments []*IReactiveCriteriaFragment `json:"fragments,omitempty"`
}
```
### 示例
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