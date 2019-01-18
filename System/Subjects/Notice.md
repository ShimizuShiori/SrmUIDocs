[TOC]

---

| 版本号 | 作者 | 内容
|---|---|---|
| 1.0 | Felix | 初稿 |

---

# 通知

## 1. 用途

关于通知，大家应该都能明白，这里不再对其进行说明。

## 2. 名词约定

### 2.1. 消息

通知的主体，发送的内容。

#### 2.1.1. 目标

指接口消息的人

#### 2.1.2. 来源

指发送消息的人

#### 2.1.3. 消息正文

指消息的主体，信息的载体

#### 2.1.4. 消息标题

正文的摘要

#### 2.1.5. 消息头

类似于 HTTP 头的用法，将一些上述信息除外的，但又与发送消息过程相关内容记录在此。
消息头是键值对格式的。

### 2.2. 发送器

根据不同的目的地，会产生不同的发送器。
如：邮件、微信、站内等。

发送器会与消息形成适用关系，即，某个消息是否能使用某个发送器进行发送。

## 3. 如何使用通知

### 3.1. 创建消息

无论是哪一种消息（微信、邮件、站内）。
原则上，都要向外提供一个 **builder** 让外部使用。
以便使用者在不关心内部实现的情况下 **轻松地** 创建一个消息。

以下以邮件消息为例 
```java
/**
 * 邮件消息的构建器
 */
MailMessageBuilder builder = new MailMessageBuilder();
Message message = builder.setFrom(new MailFrom("shimizushiori@outlook.com")) // 来源
        .setTarget(new MailTarget("shimizushiori@outlook.com")) // 发给谁
        .setTitle("Hello") // 消息标题
        .setBody(MailMessageBody.fromText("World!")) // 消息正文
        .build(); // 构建成消息
```

### 3.2. 发送消息

无论哪一种消息，均使用同一个通知服务进行发送。
```java
// 邮件发送服务
NoticeService service = contextRefreshedEvent.getApplicationContext().getBean(NoticeService.class);
MailMessageBuilder builder = new MailMessageBuilder();
Message message = builder.setFrom(new MailFrom("shimizushiori@outlook.com")) 
        .setTarget(new MailTarget("shimizushiori@outlook.com"))
        .setTitle("Hello")
        .setBody(MailMessageBody.fromText("World!"))
        .build();
// 发送消息
service.notify(message);
```

## 4. 开发新的消息类型

开发新的消息类型，原则就需要新的发送器。
新的消息类型，必须有着不同其它的信息格式。
因此，每开发一个新的消息类型，都应当建立一个新的 module

### 4.1. 创建 module 的约束

#### 4.1.1. module名称约束
module 应当以 notify 开头，- 加消息类型结束，如：
```
> common
> fas
> srm
> notify
> notify-yourNewMessageType
```

#### 4.1.2. 包名约束

```
com.dexi.notify.yourNewMessageType
```

### 4.2. 依赖包

```xml
<dependency>
    <groupId>com.dexi</groupId>
    <artifactId>notify</artifactId>
</dependency>
```

### 4.3. 需要做的事情

1. 编写 Target 实现类
2. 编写 From 实现类
3. 编写 MessageBody 实现类
4. 编写 Sender 实现类，该类需要加上 @Component 注解
5. 编写 Builder 助手类  [1](#z1)
6. 编写 Config 和 @Enable ，并能够扫描到 Sender 类
7. 将 @Enable 注释添加到启动 module 中

<b id="z1"></b>
> 1. builder 助手类必须要实现对 Target From Title Body Header 的构建，另外还可以对更细粒度的信息进行创建，如：setXXXHeader(String value)，可以让使用人对头的键不再关心。


---

[返回](../index.md)