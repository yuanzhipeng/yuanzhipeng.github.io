---
layout: post
Title: "Zookeeper基础"
Date: 2020-04-19 16:06:34.00000000 + 09:00
---

# Zookeeper基础

### Zookeeper是什么

Zookeeper是一个分布式的，开放源码的分布式应用程序协调服务，是Goole的Chubby一个开源的实现，它是集群的管理者，监视者集群中各个节点的状态根据几诶单提交的反馈进行下一步合理操作。最终，将简单易用的接口个性能高效，功能稳定的系统提供给用户。

客户端的读请求可以被集群中的任意一台机器处理，如果读请求在节点上航注册了监听器，这个监听器也是有所连接的zookeeper机器来处理。对于写请求，这些请求会同事发送给其他zookeeper机器并且达成一致后，请求才会返回成功。因此，随着zookeeper中非常重要的一个特性，所有的更新都是全局有序的，每个更新都有一个唯一的时间戳，这个时间戳称为zxid（Zookeeper Transaction Id）。而读请求只会相对与更新有序，也就是读请求的返回结果中会带有这个zookeeper最新的zxid。

### Zookeeper提供了什么？

* 文件系统	
* 通知机制

### Zookeeper文件系统

Zookeeper提供一个多层级的节点命名空间(节点称为znode)。与文件系统不同的是，这些节点**都可以设置关联的数据**，而文件系统中只有文件节点可以存放数据而目录节点不行。Zookeeper为了保证高吞吐和低延迟，在内存中维护了梳妆的目录结构，这种特性使得Zookeeper不能存放大量数据，每个节点的存放数据上限为**1M**。

### 四种类型的znode

1.**PERSISTENT-持久化目录节点**

​	客户端与zookeeper断开连接后，该节点依旧存在

2.**PERSISENT_SEQUENTIAL-持久化顺序编号目录节点**

 	客户端与zookeeper断开连接后，该节点依旧存在，只是Zookeeper给该节点名称进行顺序编号

3.**EPHEMERAL-临时目录节点**

​	客户端与zookeeper断开连接后，该节点被删除

4.**EPHEMERAL_SEQUENTIAL-临时顺序编号目录节点**

​	客户端与zookeeper断开后，该节点被删除，只是Zookeeper给该节点名称进行顺序编号