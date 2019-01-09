[TOC]

# NicetyForm

## 1. 用途

表单

## 2. 路径

```
webapp\nicety\src\components\Form\src\Form.vue
```

## 3. 组件信息

### 3.1 props

| name | type | descr |
|------|------|-------|
| inline | boolean | 与样式相关，效果不确定 |
| disabled | boolean | 是否禁用 |
| statusIcon | boolean | unknow |


### 3.2 api

#### clearError

* 输入
  * 无
* 输出
  * 无
* 用途 : 清除显示的错误消息

#### addError

* 输入
  * [ErrorInfo] | [ErrorInfo][ErrorInfo][] | string
* 输出
  * 无
* 用途 : 显示一些错误

### 3.3 events

### 3.4 slots

默认

---

## 附. 其它类型

### ErrorInfo

| name | type | descr |
|------|------|-------|
| field | string | 错误消息所属的控件 |
| errorMsg | string | 错误消息的内容 |

---

[返回首页][back]

[back]: ../index.md
[ErrorInfo]: #errorinfo