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

### 实现对CPU利用率或是CPU核数
####方法一
https://www.cnblogs.com/kabi/p/5209315.html
Sigar（System Information Gatherer And Reporter），是一个开源的工具，提供了跨平台的系统信息收集的API，核心由C语言实现的。

可以被以下语音调用：

    C/C++

    Java (sigar.jar auto-loads the native library)

    Perl (requires bindings/perl build)

    .NET C# (requires bindings/csharp build)

    Ruby (requires bindings/ruby build)

    Python (requires bindings/python build)

    PHP (requires bindings/php build)

    Erlang (requires bindings/erl build)

可以收集的信息包括：
1， CPU信息，包括基本信息（vendor、model、mhz、cacheSize）和统计信息（user、sys、idle、nice、wait）
2， 文件系统信息，包括Filesystem、Size、Used、Avail、Use%、Type
3， 事件信息，类似Service Control Manager
4， 内存信息，物理内存和交换内存的总数、使用数、剩余数；RAM的大小
5， 网络信息，包括网络接口信息和网络路由信息
6， 进程信息，包括每个进程的内存、CPU占用数、状态、参数、句柄
7， IO信息，包括IO的状态，读写大小等
8， 服务状态信息
9， 系统信息，包括操作系统版本，系统资源限制情况，系统运行时间以及负载，JAVA的版本信息等.

#### 方法二
https://stackoverflow.com/questions/47177/how-do-i-monitor-the-computers-cpu-memory-and-disk-usage-in-java?rq=1

Java ManagementFactory
是一个为我们提供各种获取JVM信息的工厂类，使用ManagementFactory可以获取大量的运行时JVM信息，比如JVM堆的使用情况，以及GC情况，线程信息等，通过这些数据项我们可以了解正在运行的JVM的情况，以便我们可以做出相应的调整。

### JNI / Java Native Interface
1. 你可以使用JNI来实现“本地方法”（native methods），并在JAVA程序中调用它们。
2. JNI支持一个“调用接口”（invocation interface），它允许你把一个JVM嵌入到本地程序中。本地程序可以链接一个实现了JVM的本地库，然后使用“调用接口”执行JAVA语言编写的软件模块。例如，一个用C语言写的浏览器可以在一个嵌入式JVM上面执行从网上下载下来的applets。

缺点：
一旦使用JNI，JAVA程序就丧失了JAVA平台的两个优点：
1、程序不再跨平台。要想跨平台，必须在不同的系统环境下重新编译本地语言部分。
2、程序不再是绝对安全的，本地代码的不当使用可能导致整个程序崩溃。一个通用规则是，你应该让本地方法集中在少数几个类当中。这样就降低了JAVA和C之间的耦合性。


# 错误记录
### 1. Terminal打包sbt assembly报OOM
    原因：JVM垃圾回收内存不够用
    解决方案：Run -> Edit Configurations -> Temlates -> Application -> VM options 
    
    内容设置为：-Xmx3072m
    同时把Sbt下Java Heap设置得大一些。
    同时最好是在Sbt Shell 下进行打包
    
### 2. org.hyperic.sigar这个包用sbt导入时出错
    原因： sbt仓库文件里的仓库都不包含这个包，再查包的时候，应该注意这个包在那个仓库才有
    
    解决方法：仓库文件添加上spring-plugin: http://repo.spring.io/plugins-release/
    
### 3.  org.hyperic.sigar.Sigar.getCpuInfoList()报错
    错误信息：Exception in thread "main"java.lang.UnsatisfiedLinkError: org.hyperic.sigar.Sigar.getCpuInfoList()[Lorg/hyperic/sigar/CpuInfo;at org.hyperic.sigar.Sigar.getCpuInfoList(Native Method)
    
    原因：Sigar works via JNI. As such, the appropriate .so or .dll file needs to be in the path specified by the java.library.path property.
