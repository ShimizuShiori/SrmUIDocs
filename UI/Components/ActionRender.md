[TOC]

# ActionRender

## 1. 用途

在单元格内渲染出按钮的渲染器

## 2. 路径

```
webapp\nicety\src\components\DataGrid\src\CellRenderComponent\ActionRender.vue
```

## 3. 组件信息

### 3.1 props

| name | type | descr |
|------|------|-------|
| rowData | object | 这个按钮所对应的数据行 |
| actions | [ActionObject](#actionobject)[] | 按钮集合 |

---

## 附. 其它类型

### ActionObject

| name | type | descr |
|------|------|-------|
| display | string | 按钮的显示名称 |
| type | string | 按钮的类型，可能会与事件通知相关 |
| callback | function | 按钮点击后的回调事件 |

---

[返回 NicetyDataGrid ](./NicetyDataGrid.md)

[返回首页][back]

[back]: ../index.md