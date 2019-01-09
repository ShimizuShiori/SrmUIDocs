[TOC]

# SimgleTableList

## 1. 用途

简单的表格列表

## 2. 路径

```
webapp\app\components\SimgleTableList.vue
```

## 3. 组件信息

### 3.1 props

| name | type | descr |
|------|------|-------|
| titles | string[] | 所有的列显示名 |
| keys | string[] | 每一列需要显示的字段名 |
| rows | object[] | 所有数据行 |
| readonly | boolean | 是否只读，只读时不显示 checkbox |
| renders | [renders](#renders) | 内容渲染器

### 3.2 api

#### 3.2.1 getSelectedData

* 入参 : 无
* 返回 : object[]

返回选择中的行的数据内容

#### 3.2.2 select

* 入参 : [selectFunc](#selectfunc)
* 返回 : void

以编码的方式选择某些数据行

---

## 附. 其它类型

### renders

renders 本身是一个 object 对象，但是它的属性名是 keys 中的内容，值是一个方法，用来从行中计算出需要显示的内容

```javascript
let renders = {
    name : function(rowData){
        return rowData.name.toUpperCase();
    }
};
```

### selectFunc

方类型是一个方法，参数是当前行上的数据，即 rows 中的一条。
需要返回 true / false 表示该行是否选中

---

[返回首页][back]

[back]: ../index.md