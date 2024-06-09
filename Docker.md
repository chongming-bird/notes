# 【Docker】

> **Docker**是一个开源的开放平台软件，用于开发应用、交付（shipping）应用和运行应用。Docker允许用户将基础设施（Infrastructure）中的应用单独分割出来，形成更小的颗粒（容器），从而提高交付软件的速度。
>
> **Docker容器**与虚拟机类似，但二者在原理上不同。容器是将操作系统层虚拟化，虚拟机则是虚拟化硬件，因此容器更具有便携性、更能高效地利用服务器。 容器更多的用于表示软件的一个标准化单元。由于容器的标准化，因此它可以无视基础设施（Infrastructure）的差异，部署到任何一个地方。另外，Docker也为容器提供更强的业界的隔离兼容。
>
> **Docker可以打包应用及其运行环境，可以用于快速构建、分享和部署应用。**

- **镜像（Image）：**用于创建 Docker 容器的模板，是一个特殊的文件系统，除了提供容器运行时所需的一切依赖环境与配置项。镜像**不包含**任何动态数据，其内容在构建之后也不会被改变。
- **容器（Container）：**轻量、快速、隔离、可移植，是镜像的运行的实例，通过镜像创建。容器有自己的文件系统
- **仓库（Repository）**：仓库可看成一个代码控制中心，用来保存镜像。一个仓库通常保存一种软件的不同版本镜像。

类比：镜像-对象，容器-类实例

## 安装Docker

**Homebrew命令：**

```shell
=$ brew install --cask --appdir=/Applications docker

==> Creating Caskroom at /usr/local/Caskroom
==> We'll set permissions properly so we won't need sudo in the future
Password:          # 输入 macOS 密码
==> Satisfying dependencies
==> Downloading https://download.docker.com/mac/stable/21090/Docker.dmg
######################################################################## 100.0%
==> Verifying checksum for Cask docker
==> Installing Cask docker
==> Moving App 'Docker.app' to '/Applications/Docker.app'.
&#x1f37a;  docker was successfully installed!
```



## Docker命令

> docker [command] --help
>
> 容器id不用打全称，有区分的前几位就行

### 容器操作

|            命令             |                作用                |
| :-------------------------: | :--------------------------------: |
|   `docker search [image]`   |                检索                |
|  `docker pull [image:tag]`  |       下载，默认tag为lastest       |
|       `docker images`       |                列表                |
|        `docker rmi`         |                删除                |
|    `docker run [image]`     | 运行镜像（生成容器），第一次时使用 |
|         `docker ps`         |    查看，`-a`可查看已停止的容器    |
|  `docker start [image/id]`  |         启动（已存在）容器         |
|  `docker stop [image/id]`   |                停止                |
| `docker restart [image/id]` |                重启                |
|        `docker logs`        |                日志                |
|        `docker exec`        |            进入（容器）            |
|   `docker rm [image/id]`    |         删除，`-f`强制删除         |
|       `docker stats`        |                状态                |



**`docker run`**

```shell
# -d 后台启动
# --name [image name] 给容器起名字
# -p [localhost port:container port] 端口映射，让主机能访问容器，主机端口不可重复
docker run -d --name [image name] -p [localhost port:container port] [image]
```



**`docker exec`**

```shell
# -it 以交互方式进入
# /bash/bin 进入容器内部控制台 
docker exec -it [image name] /bash/bin 

exit # 退出容器
```

### 镜像操作

|                    命令                     |      作用      |
| :-----------------------------------------: | :------------: |
| `docker commit -m "[message] -a "[author]"` | 提交容器为镜像 |
| `docker save -o [dir/name.tar] [image:tag]` |    保存镜像    |
|       `docker load -i [dir/name.tar]`       |    加载镜像    |

### 分享镜像

> 推荐制作镜像时制作一个image:lastest版本，确保其他用户使用默认tag时可以拉取镜像

|                         命令                         |               作用               |
| :--------------------------------------------------: | :------------------------------: |
|                    `docker login`                    |               登陆               |
| `docker tag [source_image:tag] [username/image:tag]` | 改名(images中的)并制作一个新镜像 |
|                    `docker push`                     |               推送               |



## Docker存储

### 目录挂载

> 挂载容器目录到本地，防止数据丢失，同时方便修改数据



## Docker网络



## Docker Compose



## DockerFile

