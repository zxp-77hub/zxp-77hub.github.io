---
title: "BizFirmPageApi"
date: 2022-04-01T14:16:24+08:00
author: 张学鹏
weight: 20
---
### authController: 权限控制器
```js
 authController.actionId // 权限行为动作id
 authController.resourceId // 资源id
 authController.setResourceId // 设置资源id
 authController.checkAuth  // 权限校验
 authController.checkAuthWithData // 校验数据权限
 authController.backViewMode // 返回查看态
```
### createMasterCriteriaRaction:

### criteriaController:
```js
criteriaController.createCriteriaStrReaction(path, producer, fireImmediately) // 设置字段查询参数
criteriaController.createCriteriaReaction(path, producer, fireImmediately)
criteriaController.createDetailCriteriaStrReaction(rowField, subpath, producer, fireImmediately)
criteriaController.createDetailCriteriaReaction

criteriaController.getDetailCriteriaStr(rowField, fieldName) // 获取子表字段查询参数
criteriaController.getDetailBindVars(rowField, fieldName) // 获取子表字段 bindvar 变量
criteriaController.getCriteriaStr(path)  // 获取字段查询参数
criteriaController.getBindVars(path) // 获取字段bindvar 变量
```

### defaultValueController

### detailController

### detailDefaultController

### detailEnricherController

### ecaLogController

### eventController

### fieldAuthController

### fieldComponentPropsController

### formController

### formRuntimeController

### initialController

### masterController

### masterRendererController

### menuController

### paramsController

### polymorphicRenderController

### rangeWalkController

### reactionScenariosController

### sectionController

### stateController
```js
StateController.billStatus //单据状态
StateController.mode //单据模式
```
### tabApi
```js
tabApi.changeTitle() // 变更标签 title
tabApi.changePath  // 变更页面路由
tabApi.closeTab() // 关闭标签
tabApi.showLoading()  // 显示页面加载loading状态
tabApi.hideLoading()  // 隐藏页面加载loading状态
tabApi.getInstance    
tabApi.getParams() // 获取路由params
tabApi.getTitle // 获取当前标签栏titile
tabApi.getUrlParams() // 获取路由url参数 
tabApi.isActive  // 当前标签栏是否激活
tabApi.isClosed // 当前标签栏是否关闭
tabApi.whenActive(callback) // 当标签页激活状态时
tabApi.whenDeactive(callback) // 
tabApi.whenClosed(callback) // 当当标签栏关闭时触发
tabApi.whenRefresh(callback) // 当页面刷新时触发
```

### tabTitleController // 标签栏控制器
```js
tabTitleController.setTabTitle() // 设置标签栏 title
```
