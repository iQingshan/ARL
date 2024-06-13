# 灯塔ARL
灯塔v2.6.2_docker版本

本仓库作者：青山

后续可能进行二次开发！

## 安装教程

### 1.安装docker

```shell
yum install docker
```

### 2.配置config-docker.yaml


### 3.安装arl

```shell
docker-compse up -d
```

## Tips

1.docker与docker-compse都需要安装

2.自行开放5003端口

3.默认账号密码 admin/arlpass

## 问题
1.external volume "arl db" not found

答：执行 docker volume create arl db

2.提示配置yaml文件 'version'的报错

答：删除配置yaml文件第一行version即可

3.拉取镜像失败

答：https://do.nark.eu.org/ dockerhub最新可用镜像源
