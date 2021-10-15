---
title: "ReactiveFieldComponentProps"
date: 2021-10-14T14:16:59+08:00
author: 张学鹏
---
### ReactiveFieldComponentProps
```javascript
type IReactiveFieldComponentPropsItem = struct {
	Props           map[string]interface{} `json:"props,omitempty"`
	IsDestruct      bool                   `json:"isDestruct"`
	When            string                 `json:"when,omitempty"`
	FireImmediately bool                   `json:"fireImmediately,omitempty"`
}

type IReactiveFieldComponentProps = struct {
	Field   string                              `json:"field"`
	Effect  *IReactiveFieldComponentPropsItem   `json:"effect,omitempty"`
	Effects []*IReactiveFieldComponentPropsItem `json:"effects,omitempty"`
}
```