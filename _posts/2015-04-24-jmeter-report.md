---
layout: post
title:  "Jmeter  + PerfMon 压力测试小结"
date:   2015-04-24 18:00:00
categories: [压力测试,Jmeter]
excerpt: jemter perfmon 压力测试 分布式
---

* content
{:toc}

##序

---

最近工作需要，临时充当了一回大QA，对项目网站进行压力测试评估。开始觉得就是模拟高并发，看看服务器能够承受多大的压力，随着找个流行工具就能搞定问题但是没那么简单。

###性能测试常见指标

*	响应时间、错误率、吞吐量
*	CPU利用率、内存利用率、IO、网卡
*	`Hit Per Second`：HPS，每秒点击率，即用户每秒向Web服务器提交的HTTP请求数
*	`Transaciton Per Second`：TPS，每秒通过事务数，每秒钟系统能够处理的交易或者事务的数量，它是衡量系统处理能力的重要指标

###测试场景
>确定测试的目标，即明确本次测试的需要得出的结论或需要测试的方面。因此测试场景中往往需要首先固定一些环境因素，作为初始参数，另外需要设计出一套测试用例，通过分析测试用例的执行结果，得出结论。

<br />

##测试工具：Jmeter

---

###下载&安装
-	下载地址：http://jmeter.apache.org/download_jmeter.cgi 
-	安装：解压后即可使用
-	运行： bin/jmeter.bat（windows系统）； Linux下需要首先更改jmeter的权限(`chmod 777 jmeter`)

###简单使用实例
1，	添加线程组:在`测试计划`节点上右键，`添加`→`Threads(Users)`→`线程组`
&nbsp;&nbsp;![X]({{"/img/jmeter/xianchengzu.png"}})  
`线程数`：要模拟的并发用户量。  
`Ramp Up Period (in seconds)`：在多长时间内均匀启动所有的线程。比如`线程数`设为10，Ramp Up Period设为1，则jmeter每隔0.1秒启动1个线程。  
`循环次数`：单用户任务重复执行的次数。可以设为`永远`，这样jmeter就不会自动停止，需要强制终止。
还可以设置`调度器`。  
这里有两组设置:

-	`启动时间`和`结束时间`让jmeter在特定的时间区段内执行工作；  
-	`启动延时（秒）`表示从当前时刻开始延迟多长时间开始运行，`持续时间（秒）`设定运行时长。

2,	添加HTTP请求：在`线程组`节点上右键，`添加`→`Sampler`→`HTTP请求`  
![X]({{"/img/jmeter/http.png"}})  

