[TOC]

# NicetyDialog

## 1. 用途

对话框

## 2. 路径

```
webpp\nicety\src\Dialog\src\component.vue
```

## 3. 组件信息

### 3.1 props

| name | type | descr |
|------|------|-------|
| title | string | 对话框标题 |
| modal | boolean | 是否显示 |
| modalAppendToBody | boolean | unknow |
| appendToBody | boolean | unknow |
| lockScroll | boolean | 锁滚动条? |
| modalClass | string | 自定义样式 |
| closeOnClickModal | boolean | unknow |
| closeOnPressEscape | boolean | 是否通过 **ESC** 键关闭 |
| showClose | boolean | 是否显示关闭叉叉 |
| width | string | 宽度 |
| fullscreen | boolean | 是否全屏 |
| customClass | string | unknow |
| top | string | unknow |
| beforeClose | function | 关闭前事件? |
| center | boolean | 居中 |


### 3.2 api

无

### 3.3 events

#### opened

打开时的事件，无参数

#### closed

关闭后的事件，无参数

### 3.4 slots

#### 默认

对话框内容，无默认内容

#### title

标题栏，有默认内容

### footer

底部（一般用于放置按钮），无默认内容

---

## 附. 其它类型

无

---

[返回首页][back]

[back]: ../index.md