---
title: "ReactiveFieldStatus"
date: 2021-09-30T10:39:28+08:00
author: 张学鹏
---

### ReactiveFieldStatus
> 创建一个响应式的字段状态，会根据依赖数据实时返回新状态，并添加到目标字段上
```javascript
type IReactiveFieldStatusEffect = struct {
	/**
	  状态名称
	  目前支持：Readonly、Required
	*/
	Status string `json:"status"`
	/**
	  状态值表达式
	*/
	Expr interface{} `json:"expr"`
	/**
	  当 when = true 时，才会执行规则
	  默认值：true
	*/
	When string `json:"when,omitempty"`
	/**
	  是否立即生效
	  默认值：false
	*/
	FireImmediately bool `json:"fireImmediately"`
}

type IReactiveFieldStatusParams = struct {
	/**
	  目标字段
	*/
	Field string `json:"field"`
	/**
	  状态设置
	*/
	Effect  *IReactiveFieldStatusEffect   `json:"effect,omitempty"`
	Effects []*IReactiveFieldStatusEffect `json:"effects,omitempty"`
}
```
### 示例
#### 1. 当创建组织为空时，startPeriod 字段禁用
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