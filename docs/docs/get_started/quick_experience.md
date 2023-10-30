---
sidebar_position: 1
id: quick_experience
title: 快速体验
---
本篇将手把手带您在Dinky上使用`CDCSOURCE全库同步`和`FlinkSQL`两种方式进行MySQL-MySQL数据同步。
## 环境要求
基于已部署Dinky，Flink和MySQL环境，如未部署请参照[Docker快速部署](../get_started/docker_deploy "Docker快速部署")中`启动快速体验服务`部分。

## 登录Dinky并添加Flink和MySQL数据源
`IP:8888` 地址打开平台并 `admin/admin` 登录

### 添加Flink实例
在[运维中心](../) - 集群 - Flink实例 中新建实例

[image-2023](http://www.aiwenmo.com/dinky/docs/zh-CN/quick_start/docker/none.png)

添加MySQL数据源：


## 创建作业
创建名为 `功能示例` 的目录

### 创建 MySQL 作业

选择数据源：

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

结果查询：

BI：

血缘关系：




## 结束语
至此，到此Dinky的快速体验便已经结束，接下来







---
!! OLD，WAIT FOR EDIT
---

```sql
CREATE TABLE Orders (
    order_number BIGINT,
    price        DECIMAL(32,2),
    buyer        ROW<first_name STRING, last_name STRING>,
    order_time   TIMESTAMP(3)
) WITH (
  'connector' = 'datagen',
  'rows-per-second' = '1',
  'number-of-rows' = '50'
);
select order_number,price,first_name,last_name,order_time from Orders 
```

![image-20230308222328163](http://www.aiwenmo.com/dinky/docs/zh-CN/quick_start/docker/helloword.png)

### 调试查询

点击 `执行按钮`（执行当前的SQL），下方切换至 `结果` 选项卡，点击 `获取最新数据` ，即可查看 Select 语句的执行结果。

![image-20230308222416050](http://www.aiwenmo.com/dinky/docs/zh-CN/quick_start/docker/selecttable.png)

