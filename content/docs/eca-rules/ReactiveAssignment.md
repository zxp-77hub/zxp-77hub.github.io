---
title: "ReactiveAssignment"
date: 2021-10-14T14:15:05+08:00
author: 张学鹏
---
### ReactiveAssignment
>

```javascript
type IReactiveAssignmentEffect = struct {
	/**
	取值表达式
	*/
	Expr string `json:"expr"`
	/**
	当目标字段有值时，根据 overrideExpr 的结果来判断是否需要覆盖
	默认值：false
	*/
	Override bool `json:"override"`
	/**
	当取值表达式为空时，根据 autoClear 的结果判断是否同步清空
	默认值：false
	*/
	AutoClear bool `json:"autoClear"`
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
type IReactiveAssignmentEffectV2 = struct {
	/**
	取值表达式
	*/
	Expr string `json:"expr"`
	/**
	当目标字段有值时，根据 overrideExpr 的结果来判断是否需要覆盖
	默认值：false
	*/
	Override string `json:"override"`
	/**
	当取值表达式为空时，根据 autoClear 的结果判断是否同步清空
	默认值：false
	*/
	AutoClear string `json:"autoClear"`
	/**
	当 when = true 时，才会执行规则
	默认值：true
	*/
	When string `json:"when,omitempty"`
	/**
	是否立即生效
	默认值：false
	*/
	FireImmediately string `json:"fireImmediately"`
}

type IReactiveAssignmentParams = struct {
	/**
	目标字段
	*/
	Field string `json:"field"`
	/**
	赋值来源
	*/
	Effect  *IReactiveAssignmentEffect   `json:"effect,omitempty"`
	Effects []*IReactiveAssignmentEffect `json:"effects,omitempty"`
}
type IReactiveAssignmentParamsV2 = struct {
	/**
	目标字段
	*/
	Field string `json:"field"`
	/**
	赋值来源
	*/
	Effect  *IReactiveAssignmentEffectV2   `json:"effect,omitempty"`
	Effects []*IReactiveAssignmentEffectV2 `json:"effects,omitempty"`
}

```
