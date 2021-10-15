---
title: "ReactiveFieldValidator"
date: 2021-10-14T14:17:38+08:00
author: 张学鹏
---
### ReactiveFieldValidator
>

```javascript
type IReactiveFieldValidatorItem = struct {
	/**
	  Validator 名称
	*/
	Name string `json:"name"`
	/**
	  验证参数
	*/
	Params map[string]interface{} `json:"params"`
	/**
	  是否是结构化的 默认是false
	  如果是false 则
	    按照实例进行验证 也就是验证加载FormField 实例
	  如果结构化为true 会剔除实例的影响 直接用logicPath 新增验证
	    这样的话 就会对当前字表的某一列都有效
	*/
	IsStruct bool `json:"isStruct"`
	/**
	  当 when = true 时，才会执行规则
	  默认值：true
	*/
	When string `json:"when,omitempty"`
	/**
	  是否立即执行
	  默认值：false
	*/
	FireImmediately bool `json:"fireImmediately"`
}

type IReactiveFieldValidatorParams = struct {
	/**
	  目标字段
	*/
	Field string `json:"field"`
	/**
	  校验器定义
	*/
	Effect  *IReactiveFieldValidatorItem   `json:"effect,omitempty"`
	Effects []*IReactiveFieldValidatorItem `json:"effects,omitempty"`
}

```