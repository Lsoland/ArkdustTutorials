---
description: 服务器与客户端的通讯
writers:
  - kitUIN
versions:
  id: "networkindex"
  vanilla: "1.20.4"
  loaders:
    - text: "NeoForge"
      loader: "neoforge"  
---

# 网络

> NeoForge在1.20.4重构了网络部分

使用规范化的消息结构-数据包(即包含任意数据的网络包)，在客户端与服务端间进行通讯

网络通讯中使用`FriendlyByteBuf`作为中间件

也就是说，无论你的数据是什么类型，都将打包为`FriendlyByteBuf` 然后发送给另一端，在另一端中解包为原始数据

通常由于两种情况，我们会用到网络通讯

#### 数据同步

服务端与客户端需要同步一些数据

比如：容器内容，实体状态等等

#### 主动告知/请求

模组需要从服务端/客户端主动获取一些数据，或者主动发送一些数据

比如：通知服务端玩家按下某个键