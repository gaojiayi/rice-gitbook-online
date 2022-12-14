---
description: 以rice-demo为例，分别介绍如何接入到rice平台，创建各种类型的任务，以及任务如何被调度。
---

# 🎉 Quick Start

## 前置工作

参考前一个章节的部署，这边本地运行。

![](<.gitbook/assets/image (7) (1).png>)

* 分别启动3个controller服务器  ControllerServer1   ControllerServer2   ControllerServer3
* 启动dispatcher 调度器   RiceDispatcher1
* UI端注册任务          &#x20;
* 最后启动处理器      ProcessorServiceInstance

## 1.一个简单的任务调度

假设有一个任务，该任务分布在多个实例上，现在需要每3秒钟全局执行一次。

### 任务注册

在控制台上分别注册一个业务线和在该业务线下创建一个task。

SQL:

### 编写一个基本的java任务

```
package com.gaojy.rice.demo.processor.basic;

import com.gaojy.rice.processor.api.ProcessResult;
import com.gaojy.rice.processor.api.RiceBasicProcessor;
import com.gaojy.rice.processor.api.TaskContext;
import com.gaojy.rice.processor.api.annotation.Executer;
import com.gaojy.rice.processor.api.annotation.LogEnable;
import java.util.HashMap;
import java.util.Map;

/**
 * @author gaojy
 * @ClassName BasicDemoTask.java
 * @Description
 * @createTime 2022/11/05 11:52:00
 */
@Executer(taskCode = "demoTaskCode",taskName = "demoTaskName")
@LogEnable
public class BasicDemoTask implements RiceBasicProcessor {
    @Override
    public ProcessResult process(TaskContext context) {
        //  处理具体的任务逻辑
        ProcessResult result = new ProcessResult();
        Map<Object, Object> map = new HashMap<>();
        map.put("result", "success");
        result.setData(map);
        return result;
    }
}

```

### 启动任务处理器

```
package com.gaojy.rice.demo.processor;

import com.gaojy.rice.processor.api.RiceProcessorManager;

/**
 * @author gaojy
 * @ClassName ProcessorServiceInstance.java
 * @Description
 * @createTime 2022/11/04 22:58:00
 */
public class ProcessorServiceInstance {
    public static void main(String[] args) {
        // 初始化rice处理器管理
        RiceProcessorManager manager = RiceProcessorManager.getManager();
        // 任务暴露
        manager.export();
    }
}

```

### 查看任务执行状态

<figure><img src=".gitbook/assets/image (9).png" alt=""><figcaption><p>处理器上线记录</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (8).png" alt=""><figcaption><p>任务上线通知</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (7).png" alt=""><figcaption><p>任务执行记录</p></figcaption></figure>

## 2.Map任务

_<mark style="color:red;">**待持续更新中.........**</mark>_

## 3.Http任务

_<mark style="color:red;">**待持续更新中.........**</mark>_

## 4.工作流任务

_<mark style="color:red;">**待持续更新中.........**</mark>_
