[TOC]

# NicetyDataGrid

## 1. 用途

比 SimgleTableList 具备更丰富的功能，原型是 ag-grid

## 2. 路径

```
webapp\nicety\src\components\DataGrid\src\DataGrid.vue
```

## 3. 组件信息

### 3.1 props

| name | type | descr |
|------|------|-------|
| gridOptions | [DridOptionObject] | 用于构建 *ag-grid* 的参数 |
| operations | [OperationObject][OperationObject][] | 操作按钮 |
| columnDefs | [ColumnDefObject](#columndefobject)[] | 列定义 |
| rowData | object[] | 需要显示的数据行 |
| pageSizes | number[] | 可用的分页数 |
| pageSize | number | 默认的分页数 |
| total | number | 总行数 |
| currentPage | number | 当前页码数 |
| checkBoxSelection | boolean | unknow |

### 3.2 api

#### 3.2.1 select

用于在界面上显示出选中数据样的外观

参数是一个 filter 的回调函数

该函数接受一个参数表示行数据，返回true/false表示是否选中

示例如下

```javascript
// 选中 id = 3 的数据行
this.$refs.grid.select(x => x.id === 3);
```

### 3.3 events

#### 3.3.1 gridAction

当由 *opertations* 生成的按钮被点击后触发的事件。

事件参数

| name | type | descr |
|------|------|-------|
| actionType | string | 对应 [OperationObject] 中的 *display*  |
| selectRows | object[] | 当前表格所选中的行数据 |


---

## 附一. 其它类型

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
| renderType | string | 渲染内容，详见 [附二](#f2) |
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

## <b id="f2"></b> 附二. 可用的 renderType 


| name | descr |
|------|-------|
| [ActionRender](./ActionRender.md) | 在单元格内渲染按钮的渲染器 |
| [RouteLinkRender](./RouteLinkRender.md) | 在单元格里渲染路由链接的渲染器 |

---

[返回首页][back]

[back]: ../index.md
[OperationObject]: #operationobject
[DridOptionObject]: #dridoptionobject