  # Docker的基础知识
---

```
    概述：Docker 是一个容器化平台，允许开发者将应用程序及其依赖项打包到
    一个标准化的单元（容器）中，确保应用在不同环境中快速、可靠地运行。

```

### 一.基础概念

#### 容器

轻量级、独立的软件包，包含运行应用所需的代码、运行时、系统工具和库。
与传统虚拟机的区别：容器共享主机操作系统内核，无需虚拟化整个操作系统，因此更轻量、启动更快。
    

#### 镜像
容器的静态模板，包含创建容器所需的所有层。

#### 如何构建自己的镜像
1. 创建 Dockerfile
2. 构建镜像
3. 查看构建的镜像
4. 运行你的镜像
5. 推送镜像到仓库

#### 持久化

容器默认是临时性的（容器删除，内部数据也会丢失）。
1. Docker 卷（Volumes）
   ```
    创建卷
    docker volume create mydata

    查看所有卷
    docker volume ls

    运行容器并挂载卷
    docker run -d \
         --name mysql-container \
        -v mydata:/var/lib/mysql \
         mysql:latest

        详细查看卷信息
        docker volume inspect mydata
   ```
2.  绑定挂载（Bind Mounts）
3.  临时文件系统（tmpfs mount）

#### 数据卷


### 
- 什么是容器
- 什么事镜像
- 挂载
- 数据卷
- 持久化
- 可视化
- 等等其他
- 实战
- 结合面试需求和实际使用场景