---
title: "五. BizForm实用攻略"
weight: 500
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: true
---
注意：
单据设计默些字段无法展开时,注释掉以下代码刷新后重试。
```ts
// *注释的代码别提交* 

if (hasParent) { 
  return field.properties.asCriteria;
}
```

> devs/query-list/components/list-columns-def/FieldSelectorDialogOptionBuilder.ts