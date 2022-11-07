# 🎉 Quick Start

## 一个简单的任务调度

### 任务注册

在控制台上分别注册一个业务线和在该业务线下创建一个task。

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

### 查看任务执行状态

## Map任务

## Http任务

## 工作流任务
