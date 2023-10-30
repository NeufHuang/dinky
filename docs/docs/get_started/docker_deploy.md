---
sidebar_position: 2
id: docker_deploy
title: Docker快速部署
---

新版本Dinky默认采用[H2](https://github.com/h2database/h2database "https://github.com/h2database/h2database") 作为后端数据库，因此只需拉起一个容器即可快速体验FlinkSQL丝滑之旅。
如需采用MySQL, PostgreSQL作为后端数据库请根据部署文档修改镜像，参数详见[安装部署](../deploy_guide/deploy.mdx "安装部署")。

官方镜像仅提供测试所需依赖，如需定制依赖请参照[Docker镜像构建](../deploy_guide)。
## 环境准备

部署需要[Docker](https://docs.docker.com/engine/install/) 1.13.1+版本，如需快速体验功能可能还需[Docker Compose ](https://docs.docker.com/compose/) 1.28.0+版本。

## 启动快速体验服务
### 使用docker-compose启动
创建docker-compose.yaml：
```yaml
version: '3'

services: 
  dinky:
    image: dinky-standalone-server:1.0.0-flink16 
    container_name: dinky 
    ports:  
      - "8888:8888" 
    network_mode: host

  flink: 
    image: flink:16
    container_name: flink
    ports:
      - "8081:8081"
    network_mode: host

  db:
    image: mysql:8
    container_name: mysql
    ports:
      - "3306:3306"
    network_mode: host

```
在docker-compose.yaml文件目录下使用以下命令启动、删除docker容器
```shell
docker compose up -d
docker compose down
```

### 使用 docker run 命令启动
分别执行以下命令
```shell
docker run ....
```

##  dinky-standalone-server 

启动该镜像部署 Dinky 实时计算平台。

```sh
docker run --restart=always -p 8888:8888 -p 8081:8081 --name dinky dinkydocker/dinky-standalone-server:1.0.0-flink14
```

见以下内容证明启动成功：

```java
Dinky pid is not exist in /opt/dinky/run/dinky.pid
FLINK VERSION : 1.14
........................................Start Dinky Successfully........................................
........................................Restart Successfully........................................
```

:::tip 说明
如果 `docker image` 需要加速，请把 `dinkydocker` 替换成 `registry.cn-hangzhou.aliyuncs.com/dinky`
:::

