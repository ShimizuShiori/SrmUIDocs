[TOC]

# SrmBaseList

## 1. 用途

在 Srm 项目中，使用风格一致的，具备查询和服务端分页的最高级表格控件。

## 2. 路径

```
```

## 3. 组件信息

### 3.1 props

| name | type | descr |
|------|------|-------|
| operations | [OperationObject](#operationobject)[] | 操作按钮 |
| columnDefs | [ColumnDefObject](#columndefobject)[] | 列定义 
| filterOptions | Object | 过滤条件 |
| resourceUrl | string | 拉取数据的 url |
| rowSelection | string | unknow, default is 'single' |
| checkBoxSelection | boolean | unknow |

### 3.2 api

#### refresh

刷新数据，无参数，无返回

#### resetFilterOptions

重复过滤条件，无参数，无返回

#### restHeight

重新绘制控件高度，无参数，无返回

### 3.3 events

#### gridAction

当由 *opertations* 生成的按钮被点击后触发的事件。

事件参数

| name | type | descr |
|------|------|-------|
| actionType | string | 对应 [OperationObject](#operationobject) 中的 *display*  |
| selectRows | object[] | 当前表格所选中的行数据 |

### 3.4 slots

#### 默认

放置查询表单

---

## 附. 其它类型

### OperationObject

| name | type | descr |
|------|------|-------|
| display | string | 按钮的显示名称 |
| type | string | 按钮点击后触发的消息类型 |

### DridOptionObject

| name | type | descr |
|------|------|-------|
| enableColResize | boolean | 是否允许调列的大小 |
| enableSorting | boolean | 是否允许排序 |
| animateRows | boolean | unknow，一般给 true |
| suppressRowClickSelection | boolean | unknow，一般给 true |
| rowSelection | string | 是否单选多选、 "multiple"为多选，不定义为单选 |
| domLayout | string | "autoHeight"表示自动高度 |
| pagination | boolean | unknow，一般给 false |

### ColumnDefObject

| name | type | descr |
|------|------|-------|
| headerName | string | 列抬头 |
| field | string | 该列显示的字段 |
| valueFormatter | [ValueFormatterFunc](#valueformatterfunc) | 值格式化方法 |
| renderType | string | 渲染内容 |
| getProps | [getPropsFunc](#getpropsfunc) | 对渲染内容的 props 提供值的方法 |

### ValueFormatterFunc

用于格式化单元格数据用的方法

* 参数
  * [ValueFormatterArgument](#valueformatterargument)
* 输出
  * string，表示结果 

### ValueFormatterArgument

| name | type | descr |
|------|------|-------|
| data | object | 数据行 |

### GetPropsFunc

* 参数
  * [GetPropsFuncArgument](#getpropsfuncargument)
* 输出
  * object，表示向 renderType 中的组件提供 props

### GetPropsFuncArgument

| name | type | descr |
|------|------|-------|
| rowData | object | 数据行 |

---

[返回首页][back]

[back]: ../index.md