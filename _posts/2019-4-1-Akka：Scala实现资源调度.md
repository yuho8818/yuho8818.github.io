---
layout:     post
title:      Akka 资源调度
subtitle:   Akka 实现对集群的资源调度
date:       2019-04-01
author:     Hugo Yu
header-img: 
catalog: true
tags:
    - Akka
---

### Akka Scala中 ！ 和 ？

    Messages are sent to an Actor through one of the following methods.

    ! means “fire-and-forget”, e.g. send a message asynchronously and return immediately. Also known as tell.

    ? sends a message
    asynchronously and returns a Future representing a possible reply.
    Also known as ask.
    
    
### ActorRef
一个参与者的不可变的、可序列化的句柄，它可能驻留在本地主机上，也可能不驻留在同一个参与者系统中。ActorRef可以从ActorRefFactory中获得，ActorRefFactory是一个由ActorSystem和ActorContext实现的接口。这意味着可以在actor系统的顶层创建参与者，或者作为现有参与者的子元素创建参与者，但是只能从该参与者内部创建。通过消息传递，可以在参与者之间自由共享actorref。相反地传递消息是它们的唯一目的。
