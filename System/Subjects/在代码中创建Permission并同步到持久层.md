[TOC]

# 1 使用Permission进行权限管理

---

| version | author | abstract |
|---|---|---|
| 1.0 | Felix | 第一稿 |

## 1.1 自动生成Permission

---

1. 你的 module 必须添加依赖项 **security**

2. 在你的 module 中创建一个名为 providers 的包名，创建后目录结构大致如下。providers 尽可能的与 service、controllers 位于同级目录中。
```
- com.dexi.hello
  + controllers
  + dao
  + entities
  + service
  + providers [+]
```

3. 在 **providers** 中创建该 **module** 的权限提供器
```java
package com.dexi.hello.providers;

import com.dexi.security.Constant;
import com.dexi.security.PermissionCollection;
import com.dexi.security.PermissionDefinition;
import com.dexi.security.PermissionDefinitionProvider;
import org.springframework.stereotype.Component;


/**
 * @author yourName
 * hello 模块所需要的权限集合
 */
@Component
public class SecurityPermissionDefinitionProvider implements PermissionDefinitionProvider {

    @Override
    public void provide(PermissionCollection permissionCollection) {
        permissionCollection
                .add(new PermissionDefinition("Code1", "Name1", "Desc1"))
                .add(new PermissionDefinition("Code2", "Name2", "Desc2"))
                .add(new PermissionDefinition("Code3", "Name3", "Desc3"))
                .add(new PermissionDefinition("Code4", "Name4", "Desc4"))
        ;
    }
}

```
注意事项如下:
- **@Component** 不要忘记加
- 所有的 **PermissionDefinitionProvider** 实现类都必须名称各不相同，因此建议以 Permissions 的作用域加开头，如 **SecurityPermissionDefinitionProvider**
- 请不要往 **permissionCollection** 中添加 Code 重复的权限。因为这将会使得后添加的权限无法持久化，并且我们无法精确的控制所有 **PermissionDefinictionProvider** 进行持久化的顺序

1. 修改你在 **@Import()** 中的配置类，使得它在 **@Componentcan** 时，可以对你的 **providers**包进行扫描，示例代码如下：
```java
// HelloConfig.java
package com.dexi.hello;

@EntityScan("com.dexi.hello.entities")
@EnableJpaRepositories(basePackages = "com.dexi.hello.dao")
@ComponentScan(basePackages = {"com.dexi.hello.controllers", "com.dexi.hello.services", "com.dexi.hello.providers"}) //重点在这儿
@EnableConfigurationProperties(SecurityProperties.class)
@EnableWebSecurity
public class HelloConfig{

}
```

# 2. 使用Permission

## 2.1 在 controller 中对 Permission 判定

在你需要进行授权判断的 method 加上 **@PreAuthorize** 标记。
```java

    @DeleteMapping("some route there")
    @PreAuthorize("hasAuthority('Permission Here')")
    public ResponseEntity<ResponseModel<String>> someMethod(){
        /**
         * some code here
         */
    }
```

上面的 **@PreAuthorize** 的参数是使用的 SpEl 表达式。
更多可选的表达式可参见最未的[参考资料](#p-refs)。

## 2.2 以编码的方式进行Permission判定

```java

public class SomeClass implements SomeInterface{

    private final CurrentUserAccessor currentUserAccessor;

    public SomeClass(CurrentUserAccessor currentUserAccessor){
        this.currentUserAccessor = currentUserAccessor;
    }

    public void SomeMethod(){
        AuthUser user = this.currentUserAccesssor.getCurrentUser();

        /**
         * 此处会对当前登录人是否具备某个权限进行断言
         * 三个参数分别是，判定人，判定权限的Code和Name, Name主要用来抛出异常，没有其它用途。
         * 这是一个中断方法，若不存在该 Permission 则会抛出异常
         */
        com.dexi.security.Checker.hasPermission(user, "PermissionCode", "PermissionName");

        /**
         * 如果项目中没有引用 security 包，则可以使用以下方法
         */
         if(!user.hasPermission("Code")){
             throw new SomeException();
         }
    }

}

```

注意：

* 永远不要以 Role 进行操作的判断，因为 Role 是可以被用户维护的，具备不确定性。
* Permission 的创建请按照上面的方法来实现，而在系统中使用 Permission 判断的时候， Code 和 Name 请使用常量


# <b id="p-refs"></b> 参考链接

* [Spring Security 基于表达式的权限控制](https://blog.csdn.net/caomiao2006/article/details/51812458)

---
[返回](../Index.md)