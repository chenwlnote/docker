# docker 基础操作

### 查看网卡列表
`docker network ls`

### 创建Docker镜像

``docker build -f ./Dockerfile -t fun_hyperf_swoole:v1 . ``

### 列出镜像列表
```
docker image ls
docker images
```

```
docker save
docker load 
docker search

FROM：指定基础镜像
RUN：执行命令
COPY：复制文件
ADD：更高级的复制文件
CMD：容器启动命令
ENV：设置环境变量
EXPOSE：暴露端口

```


```
 # 新建并启动
 docker run [镜像名/镜像ID]
 # 启动已终止容器
 docker start [容器ID]

查看容器
 # 列出本机运行的容器
 $ docker ps
 # 列出本机所有的容器（包括停止和运行）
 $ docker ps -a

停止容器
 # 停止运行的容器
 docker stop [容器ID]
 # 杀死容器进程
 docker kill [容器ID]

重启容器
 docker restart [容器ID]
 
 
进入容器有两种方式：

  # 如果从这个 stdin 中 exit，会导致容器的停止
 docker attach [容器ID]
 # 交互式进入容器
 docker exec [容器ID] 
 
 
 查看日志
 # 导出的容器快照文件可以再导入为镜像
 docker logs [容器ID]

这个命令有以下常用参数 -f : 跟踪日志输出

--since :显示某个开始时间的所有日志 -t : 显示时间戳 --tail :仅列出最新N条容器日志

复制文件
 # 从主机复制到容器
 sudo docker cp host_path containerID:container_path
 # 从容器复制到主机
 sudo docker cp containerID:container_path host_path
```

### 查看网卡信息
`` docker network inspect `docker network ls | grep 'cwl' | awk '{print $1}' ``

### 进入容器
`docker exec -it `docker ps | grep master | awk '{print $1}'` /bin/bash`

`docker exec -it `docker ps | grep salve-01 | awk '{print $1}'` /bin/bash`

`docker exec -it `docker ps | grep salve-02 | awk '{print $1}'` /bin/bash`

`docker exec -it `docker ps | grep salve-03 | awk '{print $1}'` /bin/bash`

### 清空容器镜像
`docker system prune -af`