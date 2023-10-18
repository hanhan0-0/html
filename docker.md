[TOC]

# docker入门

 

## 安装命令

使用官方脚本进行安装

```sh
 curl -fsSL https://test.docker.com -o test-docker.sh
 sudo sh test-docker.sh
```

## docker命令

```shell
docker run -d -p 6379:6379 --name redis redis:latest
```

这个命令是用于在Docker容器中运行Redis数据库实例。以下是各个参数的解释：

- `run`：指示Docker运行一个新的容器。
- `-d`：以后台模式运行容器，即容器将在后台运行而不阻塞命令行。
- `-p 6379:6379`：将主机的6379端口映射到容器的6379端口。这允许通过主机上的6379端口与容器中的Redis实例进行通信。
- `--name redis`：为容器指定一个名称为"redis"。这将使容器更易于识别和管理。
- `redis:latest`：指定要运行的Redis镜像及其标签。在这种情况下，`redis:latest`表示使用最新版本的Redis镜像。

1. 基本命令
   - `docker run`：运行一个新的容器。
   - `docker start`：启动一个已经创建但停止的容器。
   - `docker stop`：停止一个正在运行的容器。
   - `docker restart`：重启一个正在运行的容器。
   - `docker rm`：移除一个容器。
   - `docker ps`：列出正在运行的容器。
   - `docker images`：列出本地的镜像。
   - `docker pull`：从镜像仓库拉取一个镜像。
   - `docker push`：将一个镜像推送到镜像仓库。
   - `docker exec`：在正在运行的容器中执行一个命令。
   - `docker logs`：查看容器的日志。
   - `docker inspect`：查看容器或镜像的详细信息。
2. 常用命令
   - `docker build`：根据一个Dockerfile构建一个镜像。
   - `docker-compose up`：使用Docker Compose工具启动一组相关的容器。
   - `docker-compose down`：关闭并移除使用Docker Compose启动的容器。
   - `docker network create`：创建一个新的Docker网络。
   - `docker network connect`：将容器连接到一个现有的Docker网络。
   - `docker volume create`：创建一个新的Docker卷。
   - `docker volume ls`：列出所有的Docker卷。
   - `docker volume rm`：移除一个Docker卷。

## 制作自己的镜像

### 编写dockerfile

```dockerfile
# 基础镜像
FROM ubuntu:latest

# 维护者信息
MAINTAINER Your Name <your_email@example.com>

# 安装依赖
RUN apt-get update && apt-get install -y \
    package1 \
    package2 \
    package3

# 添加文件到容器
COPY ./app /app

# 设置工作目录
WORKDIR /app

# 暴露容器端口
EXPOSE 80

# 容器启动时执行的命令
CMD ["python", "app.py"]
```

### dockerfile解析

这里详细解析上述示例中的Dockerfile，逐行说明每个指令的作用和含义：

```
# 基础镜像
FROM ubuntu:latest
```

这个指令指定了基础镜像，该镜像是以最新版本的Ubuntu为基础构建的。

```
# 维护者信息
MAINTAINER Your Name <your_email@example.com>
```

此指令用于指定镜像的维护者信息，包括姓名和电子邮件地址。

```
# 安装依赖
# RUN 命令可以有多个，但是可以用 && 连接多个命令来减少层级。
# 例如 RUN npm install && cd /app && mkdir logs
RUN apt-get update && apt-get install -y \
    package1 \
    package2 \
    package3
```

这个指令使用`RUN`关键字来执行命令，更新apt软件包索引并安装所需的包。`-y`参数告诉apt-get在安装时不询问任何问题。

```
# 添加文件到容器
COPY ./app /app
```

此指令使用`COPY`命令将主机上的`./app`目录中的文件复制到镜像中的`/app`目录。

```
# 设置工作目录
WORKDIR /app
```

这个指令用于设置镜像中的工作目录为`/app`。

```
# 暴露容器端口
EXPOSE 80
```

此指令声明容器内的应用程序将使用80端口。在运行容器时，可以使用`-p`参数将主机的端口映射到容器的这个端口。

```
# 容器启动时执行的命令
CMD ["python", "app.py"]
```

这个指令指定容器启动时要执行的命令。在这个示例中，它以`python app.py`的形式执行Python脚本。

这是简单的Dockerfile示例，它包含了一些常见的指令和操作，可以根据自己的需求进行扩展和定制。在构建镜像时，Docker将逐行执行Dockerfile中的每个指令，并在每个指令的基础上创建一个新的镜像层。最终，这些层组合在一起形成了最终的镜像。

### 例子

以下是一个更经典且实用的Dockerfile示例，适合构建一个基于Python和Flask的Web应用程序的镜像：

```dockerfile
# 使用官方的Python镜像作为基础镜像
FROM python:3.8

# 设置工作目录
WORKDIR /app

# 复制应用程序的依赖文件到容器中
COPY requirements.txt .

# 安装应用程序的依赖
RUN pip install --no-cache-dir -r requirements.txt

# 复制应用程序代码到容器中
COPY . .

# 设置容器启动时的环境变量
ENV FLASK_APP=app.py

# 暴露容器的端口
EXPOSE 5000

# 容器启动时执行的命令
CMD ["flask", "run", "--host=0.0.0.0"]
```

这个Dockerfile包含了一些常见的指令和最佳实践：

1. 使用官方的Python镜像作为基础镜像，通过`FROM python:3.8`指定。
2. 设置工作目录为`/app`，通过`WORKDIR`指令。
3. 复制当前目录下的`requirements.txt`文件到容器中，通过`COPY requirements.txt .`指令。这个文件通常用于指定应用程序的依赖项。
4. 在容器中安装应用程序的依赖，通过`RUN pip install --no-cache-dir -r requirements.txt`指令。这个命令将使用`pip`安装依赖项，`--no-cache-dir`选项是为了避免缓存依赖。
5. 复制当前目录中的所有文件到容器中，通过`COPY . .`指令。这将包括应用程序代码和其他静态文件。
6. 设置容器启动时的环境变量`FLASK_APP`，通过`ENV`指令。这个环境变量告诉Flask框架要运行的主应用程序文件。
7. 暴露容器的端口5000，通过`EXPOSE`指令。
8. 容器启动时执行的命令为`flask run --host=0.0.0.0`，通过`CMD`指令。这个命令将在容器中启动Flask应用程序，监听所有接口并使用5000端口。

## 构建镜像-Build

构建镜像的过程涉及使用 `docker build` 命令来执行 Dockerfile 中的指令，然后将指令逐行执行的结果作为镜像的层存储到 Docker 镜像仓库中。下面是详细解析构建镜像的过程：

1.在终端中导航到包含 Dockerfile 的目录：打开一个终端窗口，并使用 `cd` 命令导航到包含 Dockerfile 文件的目录。

2.执行 `docker build` 命令：在该目录下，执行以下命令：

```shell
docker build -t your_image_name:tag .
```

- `-t` 参数可以为镜像设置一个名称和标签，例如 `your_image_name:tag`。
- `.` 表示使用当前目录作为上下文路径。

3.解析 Dockerfile：Docker 在该目录中寻找名为 `Dockerfile` 的文件，并按照其中的指令构建镜像。Dockerfile 文件的位置可以通过 `-f` 参数指定，例如：

```shell
docker build -t your_image_name:tag -f /path/to/Dockerfile .
```

4.获取基础镜像：Docker 解析 Dockerfile 中的 `FROM` 指令，根据指定的基础镜像名称，从 Docker 镜像仓库中获取基础镜像。如果本地没有该基础镜像，Docker 会下载基础镜像。

5.逐行执行 Dockerfile 中的每个指令：Docker 从 Dockerfile 的第一行开始逐行执行每个指令，构建镜像的层。

- `RUN`：用于在镜像中执行命令，例如安装依赖、设置环境变量等。每个 `RUN` 指令都在一个新的临时容器中执行。
- `COPY` 和 `ADD`：用于将本地文件复制到镜像中的指定路径。`COPY` 和 `ADD` 指令在构建过程中将本地文件添加到镜像的文件系统中。
- `WORKDIR`：用于设置镜像中的工作目录，后续的指令将在该工作目录中执行。如果没有指定工作目录，默认为根目录。
- `ENV`：用于设置环境变量，这些变量在容器运行时可用。
- `EXPOSE`：用于声明镜像中应用程序的监听端口。
- `CMD` 和 `ENTRYPOINT`：用于在容器启动时执行命令或指定容器的入口点。

6.添加元数据和创建镜像：当 Dockerfile 中的所有指令都被成功执行后，Docker 添加元数据（比如标签、作者、创建日期等）并生成镜像。镜像由多个层组成，每个层对应一个指令执行的结果。

7.完成构建：构建过程完成后，构建的镜像将被打上标签并存储在本地的 Docker 镜像仓库中。通过 `docker images` 命令可以查看已构建的镜像列表。

## 目录挂载

### 查看容器的目录

要查看容器的目录结构，可以使用`docker exec`命令进入容器内部，并在容器内执行命令来查看文件和目录。

以下是查看容器目录的步骤：

1.首先，获取容器的ID或名称。可以使用`docker ps`命令列出当前正在运行的容器，并找到要查看的容器的ID或名称。

2.使用以下命令来进入容器内部的交互式终端：

```
docker exec -it <容器ID或名称> /bin/bash
```

请将 `<容器ID或名称>` 替换为实际的容器标识符。

3.进入容器后，你可以使用常规的文件管理命令来浏览容器的文件系统，如`ls`、`cd`等。

4.使用`exit`命令退出容器的交互式终端。

通过以上步骤，你可以进入容器并查看容器的文件和目录结构。请注意，要使用`docker exec`命令，容器必须处于运行状态。

### 几种挂载方式

- `bind mount` 直接把宿主机目录映射到容器内，适合挂代码目录和配置文件。可挂到多个容器上
- `volume` 由容器创建和管理，创建在宿主机，所以删除容器不会丢失，官方推荐，更高效，Linux 文件系统，适合存储数据库数据。可挂到多个容器上
- `tmpfs mount` 适合存储临时文件，存宿主机内存中。不可多容器共享。

### 挂载演示

```
bind mount 方式用绝对路径 -v D:/code:/app
volume 方式，只需要一个名字 -v db-data:/app
```

示例：
`docker run -p 8080:8080 --name test-hello -v D:/code:/app -d test:v1`

这个指令是使用 Docker 运行容器的命令，它有以下几个参数和选项：

- `docker run`: 运行 Docker 容器的命令。
- `-p 8080:8080`: 指定容器的端口映射，将容器内部的 8080 端口映射到宿主主机的 8080 端口。这样，在宿主主机上访问 localhost:8080 就可以访问到容器内部的应用程序。
- `--name test-hello`: 为容器指定一个名称，本例中为 `test-hello`。
- `-v D:/code:/app`: 指定了一个目录挂载，将宿主主机上的 `D:/code` 目录挂载到容器中的 `/app` 路径。这样做的目的是将宿主主机上的代码文件挂载到容器内部，以供容器内的应用程序使用。
- `-d`: 指定容器以“守护模式”（Detached mode）运行，这意味着容器将以后台进程的方式运行。
- `test:v1`: 指定了容器运行所使用的镜像名称和镜像版本。

综上所述，该指令的作用是在 Docker 中运行一个容器，该容器将使用指定的镜像`test:v1`来创建。容器将会绑定到宿主主机的端口号8080，并将宿主主机上的`D:/code`目录挂载到容器内部的`/app`路径。这样，可以通过访问`localhost:8080`来访问容器内部的应用程序，而容器内的应用程序可以直接读取和修改`D:/code`目录中的文件。此外，该容器将以后台进程的方式运行。

注意，该指令中的路径`D:/code`为 Windows 系统上的路径示例，如果在 Linux 系统上运行则需要使用相应的路径格式，例如`/path/to/code`。

## 多容器通信

### 创建虚拟网络

##### 创建一个名为`test-net`的网络：

```
docker network create test-net
```

容器可以使用 `docker network connect` 命令连接到该网络,然后容器之间就可以通过网络名进行通信

## 运行 Redis 在 `test-net` 网络中，别名`redis`

```
docker run -d --name redis --network test-net --network-alias redis redis:latest
```

这条 docker run 命令的作用是使用刚刚创建的 test-net 网络启动一个 redis 容器。

具体参数解析:

- -d: 在后台运行容器并打印出容器 ID。
- --name redis: 为容器指定一个名称为 redis。
- --network test-net: 指定将该容器连接到 test-net 网络。
- ***--network-alias redis: 为容器设置网络别名为 redis。***
- redis:latest: 指定启动最新版本的 redis 镜像。

这样通过为 redis 容器指定 test-net 网络,并设置网络别名为 redis,其他连接到 test-net 网络的容器就可以通过别名访问到这个 redis 容器。

比如我们可以再启动一个应用容器,指定连接到 test-net 网络,然后应用就可以通过别名 redis 访问到这个 redis 容器,实现容器之间的通信。

在其他容器中使用这个网络来进行通信

![img](https://sjwx.easydoc.xyz/46901064/files/kv98rfvb.png)

## Docker-Compose

如果项目依赖更多的第三方软件，需要管理的容器就更加多，每个都要单独配置运行，指定网络。
这节，使用 docker-compose 把项目的多个服务集合到一起，一键运行。

dockercompose都默认会创建一个网络，不需要额外创建网络。

以下是一个经典实用的docker-compose脚本的例子，并提供了详细解析，包括每个部分的作用和用法。

```yaml
version: '3'
services:
  webapp:
    build: ./webapp
    ports:
      - "8000:8000"
    volumes:
      - ./webapp:/usr/src/app
    environment:
      - DEBUG=True
      - DB_HOST=db
  db:
    image: postgres:latest
    environment:
      - POSTGRES_USER=webapp
      - POSTGRES_PASSWORD=webapp
      - POSTGRES_DB=webappdb
    volumes:
      - db_data:/var/lib/postgresql/data

volumes:
  db_data:
```

- `version`: 指定docker-compose文件的版本，这里使用的是版本3。
- `services`: 定义了将要启动的服务列表。
- `webapp`: 定义了一个名为webapp的服务。
  - `build`: 指定构建镜像所在的路径，这里是在当前目录下的webapp文件夹。
  - `ports`: 指定端口映射，将宿主机的8000端口映射到容器的8000端口。
  - `volumes`: 指定挂载路径，将宿主机的./webapp目录挂载到容器的/usr/src/app目录，实现代码同步。
  - `environment`: 指定环境变量，这里设置了DEBUG为True和DB_HOST为db。
- `db`: 定义了一个名为db的服务。
  - `image`: 指定使用的镜像，这里使用的是最新的postgres镜像。
  - `environment`: 指定环境变量，设置了POSTGRES_USER、POSTGRES_PASSWORD和POSTGRES_DB。
  - `volumes`: 指定挂载路径，将db数据存储在名为db_data的卷中。
- `volumes`: 定义了一个名为db_data的卷，用于持久化存储数据库数据。

这个docker-compose脚本实现了一个简单的web应用和数据库的部署，通过构建webapp镜像并映射端口，可以在宿主机的8000端口访问web应用。同时，通过挂载宿主机的./webapp目录到容器内的/usr/src/app目录，可以实现代码的同步和热更新。数据库服务使用了最新的postgres镜像，并设置了密码和数据库名称，同时使用了一个卷来持久化存储数据。

通过`docker-compose up`命令运行该脚本，Docker将会启动webapp和db两个服务，并创建相应的容器。

### 跑起来

在`docker-compose.yml` 文件所在目录，执行：`docker-compose up`就可以跑起来了。

在后台运行只需要加一个 -d 参数`docker-compose up -d`
查看运行状态：`docker-compose ps`
停止运行：`docker-compose stop`
重启：`docker-compose restart`
重启单个服务：`docker-compose restart service-name`
进入容器命令行：`docker-compose exec service-name sh`
查看容器运行log：`docker-compose logs [service-name]`

## 发布和部署

- 命令行登录账号：
  `docker login -u username`
- 新建一个tag，名字必须跟你注册账号一样
  `docker tag test:v1 username/test:v1`
- 推上去
  `docker push username/test:v1`
- 部署试下
  `docker run -dp 8080:8080 username/test:v1`

## 使用环境变量 .env 文件

```env
APP_PORT=9964
DB_PORT=6333
OPENAI_API_KEY=sk-*****************
OPENAI_BASE_URL=https://*********
```

dockerfile:

```dockerfile
# Dockerfile
# 从官方Go镜像开始构建
FROM golang:1.20 as builder

# 在容器内部设置工作目录
WORKDIR /src

# 将gomod和gosum文件复制到工作目录
COPY go.mod go.sum ./

# 下载所有依赖项
RUN go mod tidy

# 将源代码复制到工作目录
COPY . .

# 编译应用
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o app .

# 使用 scratch 作为基础镜像创建一个新的阶段
FROM scratch

# 从 builder 阶段复制编译好的二进制文件
COPY --from=builder /src/app .

# 暴露容器端口
EXPOSE 9964

# 容器启动时执行的命令
CMD ["./app"]
```

docker-compose：

```dockerfile
# docker-compose.yml
version: "3.9"

services:
  app:
    build:
      context: .
      dockerfile: Dockerfile
    env_file:
      - .env
    ports:
      - "9964:${APP_PORT}"
    depends_on:
      - db

  db:
    image: qdrant/qdrant
    env_file:
      - .env
    ports:
      - "6333:${DB_PORT}"
    volumes:
      - qdrant_storage:/qdrant/storage

volumes:
  qdrant_storage:
```

