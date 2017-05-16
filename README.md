基于docker环境建立的php开发环境，内含xdebug、dnsmasq

自定义镜像：

* [Docker hub => php-xdebug](https://hub.docker.com/r/zfming/php-xdebug/)
* [Docker hub => dnsmasq](https://hub.docker.com/r/zfming/dnsmasq/)

里面已经包含了平常开发所需的基本php扩展，比如gd,pdo_mysql等。

###前置条件
* 安装好docker和docker-compose

###目录简介
|目录|简介|
| ----- | ----- |
|app|存放代码的目录|
|data|数据库目录|
|run|docker-compose 的运行目录|
|run/etc|容器运行的配置文件|

		
###安装

* 获取代码，运行docker-compose：

```bash
git clone git@github.com:zfuming/docker-php-dev.git
cd run/
docker-compose up -d
```

* 添加网卡别名

```bash
sudo -S ifconfig en0 alias 10.254.254.254 255.255.255.0
```
