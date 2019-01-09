[TOC]

# NicetyUploader

## 1. 用途

文件上传控件

## 2. 路径

```
webapp\nicety\src\components\Uploader\src\uploader.vue
```

## 3. 组件信息

### 3.1 props

| name | type | descr |
|------|------|-------|
| uploaderUrl | string | 上传地址 |
| storagePath | string | unknow |
| accessType | string | 允许上传的Content-Type，多个Content-Type使用半角耳号间隔。<br/> 关于Content-Type 详情见 [参考链接](#refs) <br/> 如：*image/gif, image/jpeg* |

### 3.2 api

#### 3.2.1 reset

重置控件，无输入，无输出

### 3.3 events

#### 3.3.1 uploaded

不确定

#### 3.3.2 submitted

不确定

#### 3.3.3 cancel

不确定

### 3.4 slots

无

---

## 附. 其它类型

---

## <b id="refs"></b>参考链接

* [MIME 参考手册](http://www.w3school.com.cn/media/media_mimeref.asp)

---

[返回首页][back]

[back]: ../index.md