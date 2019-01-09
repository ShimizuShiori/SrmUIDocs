[TOC]

# NicetyField

## 1. 用途

一个录入控件

## 2. 路径

```
webapp\nicety\src\components\Form\src\Field.vue
```

## 3. 组件信息

### 3.1 props

| name | type | descr |
|------|------|-------|
| inputValue | string, Object, Number, Boolean | 录入值 |
| label | string | 标签名称 |
| inputPlaceholder | string | ... |
| renderType | string | 控件的具体形式，见[附二](#f2) |
| span | number | 宽度，12最大 |
| inline | boolean | 是否行内显示 |
| labelSpan | number | label宽度 | 
| inputWidth | string | ... |
| name | string | ... |
| rules | string | 校验规则? |
| inputReadonly | boolean | 只读 |
| visible | boolean | 可见性 |


### 3.2 api

#### addError

* 入参
  * string，消息内容
* 返回
  * 无
* 用途 : 在控件处显示一个错误消息

#### clearError
无参数
用于清空显示的错误消息

### 3.3 events

无

### 3.4 slots

---

## 附一. 其它类型

无

## <b id="f2"></b>附二. 可用的 renderType

| name | descr |
|------|-------|
| CheckboxInput | 复选框 |
| TextInput | 文本框 |
| EmailInput | ... |
| PasswordInput | ... |
| TextareaInput | ... |
| SelectInput | ... |
| CheckboxInput | ... |

---

[返回首页][back]

[back]: ../index.md