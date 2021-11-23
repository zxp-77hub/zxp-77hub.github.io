---
title: "ReactiveFieldComponentProps"
date: 2021-10-14T14:16:59+08:00
author: 张学鹏
---
### ReactiveFieldComponentProps
> 创建一个响应式的透传UI组件Props动作，会自动根据依赖数据实时计算新的 props 结果，并添加到目标字段对应的 UI 组件上

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
#### 示例
```typescript
{
    "name": "ReactiveFieldComponentProps",
    "params": {
        "field": "createdOrg",
        "effect": {
            "props": {
                "orgRoleTypeIds": [
                    "InventoryOrg"
                ]
            },
            "isDestruct": false,
            "when": "true",
            "fireImmediately": true
        }
    }
}
```