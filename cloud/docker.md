### 文档参考

- 中文

https://www.runoob.com/docker/docker-container-usage.html

- 官方

https://docs.docker.com/engine/reference/run/

### 常用命令

#### 帮助

```
docker --help
docker pull --help
```

#### 镜像相关

```
# 拉取 tag可以省略，省略则为latest
docker pull imageName[:tag]
# 查看本地镜像
docker images
# 搜索镜像库可用镜像
docker search xxx
# 删除镜像
docker rmi imageName[:tag]/image id
# 导出镜像
docker save -o file.tar iamgeName1:[tag] imageName2[:tag]
# 导入镜像
docker load -i file.tar
```

#### 创建容器

```
docker create --name ContainerName imageName[:tag] [命令] [参数]
# 打开交互运行容器，交互后会终止容器
docker run -it --name ContainerName imageName[:tag] [命令] [参数]
#后台创建并运行
docker run -d --name ContainerName imageName[:tag] [命令] [参数] 
# 其余常用参数
# 目录映射，多个则多个-v参数
-v 物理机目录:容器目录 
# 端口映射 多个则多个-P参数
-p 物理机端口:容器端口
# 默认端口映射,dockerfile中expose的端口自动随机映射到主机
-P 
# 运行一次后就删除，常用于工具类容器
--rm 
```

#### 容器管理

```
# 删除
docker rm 容器name or id
# 启动
docker start 容器name or id
# 重启，未启动也可以用
docker restart 容器name or id
# 停止
docker stop 容器name or id
# 进入容器
docker exec -it 容器name or id 命令(常用/bin/bash)
# 进入容器 退出会导致容器终止
docer attach -it 容器name or id 命令(常用/bin/bash)
# 查看容器,默认查看运行中的-a 可以查看所有
docker ps [-a]
# 日志,-f 会滚动
docker logs [-f] 容器name or id
# 查看容器状态
docker stats 容器name or id
# 容器中的进程信息
docker top 容器name or id
# 容器详细信息
docker inspect 容器name or id
# 复制，参数反着就反着复制
docker cp 物理机目录或文件 容器:目录或文件
# 导出容器 不会包含-v 的目录，--volumes-from 其他容器名 会包含
docker export -o file.tar 容器name or id
# 导入容器为镜像
doker import file.tar imagename[:tag]
# 基于当前容器制作镜像
docker commit [OPTIONS] CONTAINER [REPOSITORY[:TAG]]

```

#### 制作镜像

```
# 使用当前Dockerfile 文件
docker build . [-t imageName[:tag]]
# 指定Dockerfile文件
docker build -f Dockerfile路径
# 登录容器hub
docker login
# docker push image[:tag]
```

dockerFile 编写文档

https://docs.docker.com/engine/reference/builder/

https://www.runoob.com/docker/docker-dockerfile.html





