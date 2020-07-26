---
title: "ALL in ONE"
date: "2020-07-03T00:00:00+08:00"
tags: 
categories: 
draft: false
---

> 这是一个类似于inbox的东西，乱七八糟的内容都会放进来





```shell

```





打开 prometheus.yml 文件, 在 scrape_configs 中添加如下配置：

```yaml

```



文件传输（复制到本地）

```shell
scp root@www.abc.com:/usr/local/sin.sh /home/administrato
```



解压

`tar -xzvf file.tar.gz` //解压tar.gz



每篇暂时搁置的论文都总结一下值得借鉴的点吧

- CCS里的图1，需要人工确认anomaly的图
- 清华那个CPS实在是太难读懂了
- 清华CDC那篇神经网络图，想法牛逼，但是具体实施看不懂啊
- MatchSim计算邻居的相似度



[点的重要性](https://blog.csdn.net/kindred_joe/article/details/102584337) 这篇论文笔记我觉得写得挺好：

1、PageRank：忽略了点的重要性评分
2、Personalized PageRank：PPR考虑点重要性评分但忽略了边的类型。

可能PPR也有可以改进的空间

例如针对诈骗传播的场景，可以[个性化修改PPR的权重](https://zhuanlan.zhihu.com/p/64065188)：





istio自动注入的方法：

```shell
kubectl label namespace ns-xxx istio-injection=enabled
```

然后查看是否注入成功：

```shell
kubectl get namespace -L istio-injection
```



参考：https://istio.io/latest/zh/docs/setup/additional-setup/sidecar-injection/

---



[xml的方式表示图](https://github.com/amir-f/delta-simrank/blob/master/non_mr_simrank/test/simrank_test_graph_widom.graphml)



一句话讲清楚PCA是做什么的：

将一组N维向量降为R维，其目标是选择R个**单位正交基**，使得原始数据变换到这组基上后，各维度两两间的**协方差**为0，而每个维度的**方差**则尽可能大（在正交的约束下，取最大的R个方差）。



## GCN好文

- https://zhuanlan.zhihu.com/p/89503068
- https://mp.weixin.qq.com/s/sg9O761F0KHAmCPOfMW_kQ
- https://zhuanlan.zhihu.com/p/78452993
- https://github.com/LYuhang/GNN_Review







奥卡姆剃刀原则：假如两个假说具有相同的解释力和预测力，我们应当以那个较为简单的假说作为讨论根据。



Microscope和MS-Rank都没有提到Precision是如何计算的。要我自己去猜吗？不过好像就是我猜的那个思路。



新的idea：RCA这些论文里对anomaly detection是怎么做的？他们关注的重点是analysis，就是找异常节点，异常发生如何检测是怎么做的？



## RCA

一些例子：

比如接口成功率下降了，发现北京的接口成功率的曲线和接口成功率最相似，那将“北京的接口成功率”定位为根因。

KPI anomaly

当某个总指标（如总流量）发生异常时，需要快速准确地定位到是哪个交叉维度的细粒度指标（如“省份=北京 & 运营商=联通”的流量）的异常导致的，以便尽快做进一步的修复止损操作。

对于网络运维中多数的关键性能指标（KPI，CPU利用率、某页面点击量等），对其应用实时的异常检测算法，即可快速发现异常状况

Fault Injection方式：

- 对一个container进行CPU消耗
- 网络包延迟（具体delay到某个微服务还是？）
- Container Pause



MS-Rank就根本没提什么是微服务系统的Root Cause，但是在RW里提到了两类：

1. Network traffic analysis
2. web service anomaly detection

MS-Rank评价Microscope是基于单指标，也就是Latency



Anomaly Detection和Root Cause Analysis又有什么关系？



### 回应的问题

Q1: 选择的metric是什么，他们之间有权重吗

A1: 目前论文里看到的是没有的，MircoScope是用latency单指标，MS-Rank是用多指标，但是没有说明指标之前的权重，icws2020也是用latency单指标。

Q2: Root Cause 检测的anomaly是个什么异常？

A2: 看Fault Injection方式，也就是说1. 一个或多个微服务停机 2. 一个或多个微服务的网络延迟高



### 为什么实验表明和论文里的有出入

感觉不是forward、selfward和backward的问题。因为这是解决不能向兄弟节点random walk的问题。而不是整个调用链latency相似的问题。





docker 格式化查看 container

```shell
docker ps --format "table {{.ID}}\t{{.Names}}\t{{.Status}}"
```



其中Reviews有3个版本：

- v1只提供评论
- v2同时提供评论和评分，评分以黑色星星展现
- v3同时提供评论和评分，评分以红色星星展现