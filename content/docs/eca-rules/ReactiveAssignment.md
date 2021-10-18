---
title: "ReactiveAssignment"
date: 2021-10-14T14:15:05+08:00
author: 张学鹏
---
### ReactiveAssignment
> 创建一个响应式的赋值动作，会根据规则中的依赖字段返回实时的新计算结果，并赋给目标字段

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
### 示例 
#### 1.明细行主单位根据存货带出 
```json
{
  "name": "ReactiveAssignment",
  "description": "主单位跟具存货赋值",
  "params":{
    "effects":[
      {
        "autoClear":true, // 
        "expr":"$current.product.unit", // 赋值表达式：取存货下的unit 
        "fireImmediately":true, // 是否立即执行
        "when":"true"  // 只有为 true 时才执行
      }
    ],
    "field":"baseUnit"  // 需要被赋值（操作）的字段名： 主单位
  }
}
```