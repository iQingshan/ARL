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

## 问题
1.external volume "arl db" not found

答：docker volume create arl db


