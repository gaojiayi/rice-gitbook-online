---
description: 使用rice处理器，需要你的业务系统引入rice-processor，启动后，会在你的系统中新开一个rice端口，提供给rice调度器远程调用。
---

# 处理器

### 配置说明

|                   配置项                  |          说明          |                     示例                    |
| :------------------------------------: | :------------------: | :---------------------------------------: |
|           rice.application.id          |         应用标识         |                   10001                   |
|         rice.controller.address        |      控制器地址 以,分隔      | 27.0.0.1:8881,27.0.0.1:8882,27.0.0.1:8883 |
|                rice.port               |      rice处理器监听端口     |                    8888                   |
|      rice.processor.scan.packages      | 处理器tasks所在的包，多个包以,分隔 |    com.gaojy.rice.processor.api.invoker   |
|          server.worker.threads         |       服务器工作线程数       |                     16                    |
|         server.selector.threads        |   selector处理连接的线程数   |                     2                     |
|    server.callback.executor.threads    |       处理请求回调线程数      |                     4                     |
|      server.oneway.semaphore.value     |        单向请求并发数       |                    100                    |
|      server.async.semaphore.value      |        异步请求并发数       |                    100                    |
|   server.channel.max.idleTime.seconds  |        连接最大空闲数       |                    100                    |
| server.pooled.bytebuf.allocator.enable |       是否启用直接内存池      |                   false                   |
|                                        |                      |                                           |

### API启动

**引入rice-processor-api**

```
<dependency>
    <groupId>com.gaojy</groupId>
    <artifactId>rice-processor-api</artifactId>
    <version>1.0.0</version>
</dependency>
```

**code**

<pre><code><strong>// 初始化rice处理器管理
</strong><strong>RiceProcessorManager manager = RiceProcessorManager.getManager();
</strong>// 任务暴露
manager.export();</code></pre>

### Spring启动

**引入rice-processor-spring**

```
<dependency>
    <groupId>com.gaojy</groupId>
    <artifactId>rice-processor-spring</artifactId>
    <version>1.0.0</version>
</dependency>
```

_<mark style="color:red;">**code 待持续更新中.........**</mark>_

_<mark style="color:red;">****</mark>_
