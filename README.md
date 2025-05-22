# 灯塔ARL
灯塔v2.6.2_docker版本

本仓库作者：青山



## 安装教程

### 1.安装docker

```shell
yum install docker
```

### 2.配置config-docker.yaml

```shell
vim config-docker.yaml
```
### 3.安装arl

```shell
docker-compse up -d
```
### 4.添加指纹

```shell
python ./1.py https://127.0.0.1:5003/ admin arlpass old 
```

## Tips

1.docker与docker-compse都需要安装

2.自行开放5003端口

3.默认账号密码 admin/arlpass

## 问题
1.external volume "arl_db" not found

答： 
```shell
docker volume create arl_db
```
2.提示配置yaml文件 'version'的报错

答：删除配置yaml文件第一行version即可

3.拉取镜像失败

答：https://docker.1panel.live/ （正常访问即可使用）
```shell
sudo tee /etc/docker/daemon.json <<-'EOF'
{
    "registry-mirrors": [
    	"https://docker.1panel.live/"
    ]
}
EOF
```
重启docker即可
```shell
systemctl restart docker
```
