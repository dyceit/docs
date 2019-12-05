# Docker

## Docker 架构

Docker 包括三个基本概念:

- **镜像（Image）**：Docker 镜像（Image），就相当于是一个 root 文件系统。比如官方镜像 ubuntu:16.04 就包含了完整的一套 Ubuntu16.04 最小系统的 root 文件系统。
- **容器（Container）**：镜像（Image）和容器（Container）的关系，就像是面向对象程序设计中的类和实例一样，镜像是静态的定义，容器是镜像运行时的实体。容器可以被创建、启动、停止、删除、暂停等。
- **仓库（Repository）**：仓库可看着一个代码控制中心，用来保存镜像。

## 网址

[Docker 环境搭建实战](https://cloud.tencent.com/edu/learning/course-1392-7452)

## 实践

### Docker 环境线上部署 nginx

从 Docker 镜像仓库中拉取或者更新指定镜像：

```shell
docker pull nginx
```

在 `docker pull` 之前确保已经登录 Docker 镜像仓库。

登录 Docker 镜像仓库：

```shell
docker login -u 用户名 -p 密码
```

登出 Docker 镜像仓库：

```shell
docker logout
```

镜像拉取完成后，可以查看当前镜像列表：

```shell
docker images
```

运行一个nginx容器：

```shell
docker run --name nginx -v /Users/dyce/mydocker/nginx/data:/usr/share/nginx/html -p 84:80 -d nginx

```

> -v 目录映射，必须使用绝对路径
> -p 端口映射
> -d 后台运行

列出容器：

```shell
docker ps
```

浏览器查看 nginx 是否已经运行：

http://localhost:84/

此时会报403错误。

创建一个 index.html，然后再访问浏览器页面：

```shell
cd /Users/dyce/mydocker/nginx/data
touch index.html
vim index.html # 内容为：hello nginx!!!
```

此时页面访问正常。

### Docker 环境线上部署 apache

拉取 httpd 镜像：

```shell
docker search apache # 搜索 apache 镜像，官方的是 httpd
docker pull httpd
```

运行容器：

```shell
cd /Users/dyce/mydocker
mkdir apache
mkdir data
cd /Users/dyce/mydocker/apache/data
docker run --name apache -v "$PWD":/usr/local/apache2/htdocs -p 85:80 -d httpd
docker ps # 列出容器
```

> 容器的80端口都是不一样的。

创建 index.html，然后访问页面：

```shell
cd /Users/dyce/mydocker/apache/data
touch index.html
vim index.html # 内容为：hello nginx!!!
```

### Docker 环境线上部署 Mysql

> 为避免不必要的麻烦，建议使用真机安装的 mysql。

```shell
#docker 中下载 mysql
docker pull mysql

#启动
docker run --name mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=rootroot -d mysql

#进入容器
docker exec -it mysql bash

#登录mysql
mysql -u root -p
ALTER USER 'root'@'localhost' IDENTIFIED BY 'Lzslov123!';

#添加远程登录用户
CREATE USER 'liaozesong'@'%' IDENTIFIED WITH mysql_native_password BY 'Lzslov123!';
GRANT ALL PRIVILEGES ON *.* TO 'liaozesong'@'%';
```

```shell
docker run -d --privileged=true --name myMysql -v /data/mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 -p 33306:3306 mysql:5.6
```

真机 mysql 连接容器 mysql：

```shell
docker run -it --link mysql:mysql --rm mysql sh -c 'exec mysql -h"$MYSQL_PORT_3306_TCP_ADDR" -P"$MYSQL_PORT_3306_TCP_PORT" -uroot -p"$MYSQL_ENV_MYSQL_ROOT_PASSWORD"'
```

### 应用实例搭建 wordpress

```shell
#拉取镜像
docker pull wordpress
```

运行容器：

```shell
#手动安装
docker run --name wordpress -v /Users/dyce/mydocker/wordpress:/var/www/html -p 86:80 -d wordpress
#一键安装
docker run --name wordpress -v /Users/dyce/mydocker/wordpress:/var/www/html -e WORDPRESS_DB_HOST=localhost:3305 -e WORDPRESS_DB_PASSWORD=rootroot -e WORDPRESS_DB_USER=root -e WORDPRESS_DB_NAME=wordpress -e WORDPRESS_TABLE_PREFIX=wp_ -p 86:80 -d wordpress

 --link mysql:mysql
```

> 在访问 http://localhost:86/ 的时间，由于之前设置了使用 localhost 来访问，所以无法连接数据库。后面改成局域网后就成功了。
>

### navicat 连接 docker mysql 失败：

> mysql Client does not support authentication protocol requested by server; consider upgrading MySQL

查看MYSQL数据库中所有用户：

```mysql
SELECT DISTINCT CONCAT('User: ''',user,'''@''',host,''';') AS query FROM mysql.user;
```

解决方法：

```mysql
ALTER USER 'root'@'%' IDENTIFIED WITH mysql_native_password BY 'rootroot'; # 我走到这步就可以连接了
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'rootroot';
SELECT plugin FROM mysql.user WHERE User = 'root';
```

> 至此，对 Docker 有了基本的了解，本文记录的就是视频 [Docker 环境搭建实战](https://cloud.tencent.com/edu/learning/course-1392-7452) 的步骤，按此步骤多实践几次，相信可以巩固对 Docker 的认知，也会有新的启发。
>

