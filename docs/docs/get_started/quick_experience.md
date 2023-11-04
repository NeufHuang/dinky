---
sidebar_position: 1
id: quick_experience
title: 快速体验
---
本篇将手把手带您在Dinky上使用`CDCSOURCE全库同步`和`FlinkSQL`两种方式进行MySQL-MySQL数据同步。  

## 环境要求
快速体验容器需要[Docker](https://docs.docker.com/engine/install/) 1.13.1+版本。  

快速体验镜像已集成本章案例所需环境及依赖：   

| Name    | Version |
|---------|---------|  
| Dinky   | 1.0.0   |
| OpenJDK | 11      |
| MySQL   | 8.0     |   
| Flink   | 1.16.2  |   
| CDC     | 2.4.1   |

同时MySQL已默认开启binlog。

请执行以下命令启动快速体验容器，分别是dinky端口8888，mysql端口3306（可选），flink端口8081（可选），自行修改端口避开占用。
```shell
sudo docker run -itd -p 8888:8888 -p 3306:3306 -p 8081:8081 --name dinkyall dinky-qe:1.0
```
:::tip 注意  
本镜像仅为快速体验提供，为避免产生不可预料风险，请避免在其他场景使用本镜像。  
:::  
如需要详细的镜像及容器化部署教程请参照[Docker快速部署](../deploy_guide/docker_deploy.md "Docker部署")。   
如需要本地部署请参照[部署](../deploy_guide/deploy.mdx "部署")。

## 登录Dinky并添加Flink和MySQL数据源
打开地址`localhost:8888`进入Dinky登录页面，输入`admin/admin` 登录 Dinky 


`localhost:8081`可以看到Flink webui


### 添加Flink实例

在[注册中心](../) - 集群 - Flink实例 中新建实例
输入

[image-2023](http://www.aiwenmo.com/dinky/docs/zh-CN/quick_start/docker/none.png)

:::tip 说明
Dinky目前支持多种FLink实例，本篇以Standalone为例，了解更多请参阅[环境配置](../deploy_guide/deploy.mdx "环境配置")。
:::
### 添加MySQL数据源

在[注册中心](../) - 数据源 中添加MySQL数据源

填完后点击测试,上方显示成功或失败

:::tip 说明
Dinky目前支持连接多种数据源，本篇以MySQL为例，了解更多请参阅[数据源](../deploy_guide/deploy.mdx "数据源")。
:::


## 创建作业

创建名为 `快速体验` 的目录

### 创建 MySQL 作业
此步骤将通过dinky在镜像集成的MySQL创建一个源库源表和目标库，为后续Flink作业提供数据基础

右侧选择数据源：

执行以下SQL导入源数据
```sql
create database testdb;
create table
```
再执行以下SQL创建目标数据库
```sql
create database test；
```


### 创建 FlinkSQL 作业

#### CDCSOURCE全库同步
```sql

```

#### FlinkSQL单表同步
```sql

```
### 查看结果



### 控制台栏
控制台：
查看运行日志

结果查询：
可以查询FlinkSQL读取的数据
BI：

血缘关系：




## 结束语
至此，到此Dinky的快速体验便已经结束了，接下来可以开始在Dinky上体验FlinkSQL的丝滑之旅了。


