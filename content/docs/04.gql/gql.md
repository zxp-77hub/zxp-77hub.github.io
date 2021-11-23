---
title: GQL基础
author: 王书硕
weight: 1
---
## 普通的gql
最简单的，直接查一个对象（表）的全部数据
```
{
  BudgetAccount{
    id
    name
    accountType {
      id
      name
    }
  }
}
```

加一点查询条件
```
{
  BudgetAccount(criteriaStr:"name in ('1','2','3')"){
    id
    name
    accountType {
      id
      name
    }
  }
}
```
这个会查到name为1、2、3的多条数据

## 常用的 gql 查询语句
### 1. 查看某种业务对象的实体名
```angular2html
// 例如出入库业务
ObjectType(criteriaStr: "appName='inventory'") {
  id
  title
}
```
### 2. 查询预制列表组
```angular2html
// 例如公告列表组
QueryDefinitionGroup(criteriaStr:"objectType='Notice'"){
	id
  objectType
  title
}
```
### 3. 预制列表方案
```angular2html
// 例如公告列表方案
QueryListDefinition(criteriaStr:"objectType='Notice'"){
  id
  objectType
  title
}
```
## 高级的gql
上面只能查到一个表的数据及其关联的外键，子表的数据。下面来搞一个子查询。
> 因为有的时候，后端的模型中，没有包含我们需要的子表，只能我们自己构建
```
{
  BudgetAccount(criteriaStr:""){
    a: exprField(expr:"()")
    b: exprField(expr:"()")
  }
}
```
其中`a:`是个模型上的一个字段起别名，`exprField`是一个可以扩展的额外字段，利用这两个就可以做成子查询了。

举个例子。对于预算指标，复合指标有若干个子指标，但是直接通过BudgetIndicator模型获取不到它们。就可以这样做
```
{
  BudgetIndicator(criteriaStr:"isComposite=true"){
    id
    isComposite
    child: exprField(expr:"(select string_agg(CONCAT_WS(',',childIndicator.id,childIndicator.name),';')  from BudgetIndicatorComposition where parentIndicatorId=m.id)")
  }
}
```
这里使用了两个sql函数把多条记录、多个字段组合成了一个字符串。拿到数据后前端经过简单的split转化就可以拿到json对象了。

### 常用的sql函数
**string_agg**: 如果查出来有多条结果，会将它们拼装为一个字符串  
例子：string_agg(object.name, ', ')

**coalesce**：如果alias存在则取alias，不存在取name  
例子：string_agg((coalesce(indicator.alias, indicator.name)), ', ')

**concat_ws**：拼装一条记录的多个字段为一个字段  
例子：string_agg(CONCAT_WS(',',childIndicator.id,childIndicator.name),';')


## DataLoader
```ts
const settingDataLoader = new DataLoader(EN_Setting, ['values.value'], {
  criteriaStr: `key='${accountingBook}'`,
} as QueryOptions);

const ret = await settingDataLoader.query();
```

## 不适用DataLoader，直接使用gql
```ts
import client from '@client';
const fetchControlBalance = async (criteriaStr: string, dimensionField: string[]) => {
  const res = await client.query<{ data: Array<IInvoiceType> }>({
    query: `
    {
      data: BudgetControlBalance(criteriaStr: "${criteriaStr}"){
        id
      }
    }
    `,
  });
  return res.data.data
};
```

## Go怎么查GQL
```go
func GetFieldMapping(c context.TrekContext, billClassId string) []Mapping {
	queryString := `{
  BudgetDimensionFieldMapping(criteriaStr:"billClassId = '{{.billClassId}}' and dimensionId = 'FinancialOrg'"){
    mappingToWhereId mappingField
}
}`
	query := graphql.GraphqlTemplate(queryString, map[string]string{
		"billClassId": billClassId,
	})

	data := map[string]interface{}{
		"query": query,
	}

	var dataJson FieldMappingRes

	context.HttpRequest.DoHTTPPost(c, urls.AppGraphQL, &context.HTTPOptions{
		BindBody:    &dataJson,
		ParamStruct: &data,
	})
	return dataJson.Data.BudgetDimensionFieldMapping
}

type Mapping struct {
	MappingToWhereId string `json:"mappingToWhereId"`
	MappingField     string `json:"mappingField"`
}

type FieldMappingRes struct {
	Data struct {
		BudgetDimensionFieldMapping []Mapping `json:"BudgetDimensionFieldMapping"`
	} `json:"data"`
	Errors []interface{} `json:"errors"`
}
```
1. queryString定义语句的模板，其中可以包含一些模板变量
2. GraphqlTemplate将模板变量引用到模板
3. 用DoHTTPPost发起请求

