[TOC]

# WorkflowHistory

## 1. 用途

为工作流的表单提供，历史查询，触发下推的功能。

## 2. 路径

```
webapp\app\pages\approval\workflowHistory.vue
```

## 3. 组件信息

### 3.1 props

| name | type | descr |
|------|------|-------|
| objectId | String | 表单数据的主键，与工作流历史表中的 Object_Id 对应 |
| type | String | Unknow |
| onSubmit | [OnSubmitFunc] | 判断是否可以提交工作流至下一步(同步) |
| onSubmitAsync | [OnSubmitAsyncFunc] | 上面的异步形式 |

### 3.2 api

无

### 3.3 events

无

### 3.4 slots

无

---

## 附. 其它类型

<b id="OnSubmitFunc"></b>
### OnSubmitFunc

返回 true / false 以表示工作流是否可以进行提交，例：

```javascript
onSubmit : function(){
    return true;
}
```

该方法是同步的，因此只能进行前台的校验

<b id="OnSubmitAsyncFunc"></b>
### OnSubmitAsyncFunc

使用 Promise 响应成功与失败来表示工作流是否可以进行提交，例：

```javascript
onSubmitAsync : function(){
    return new Promise((ok,fail) => {
        $.get("url")
            .then(rlt=>{
                if(rlt) ok();
                else fail();
            })
            .catch(err => {
                throw err;
            })
    });
}
```

该方法因为是异步的，所以可以进行服务器校验。


---

[返回首页][back]

[back]: ../index.md
[OnSubmitFunc]: #OnSubmitFunc
[OnSubmitAsyncFunc]: #OnSubmitAsyncFunc