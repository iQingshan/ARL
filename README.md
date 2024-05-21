# 灯塔ARL
灯塔v2.6.2_docker版本

## 安装教程

### 1.安装docker

```shell
yum install docker
```

### 2.配置config-docker.yaml

参考配置

```yaml
CELERY:
  BROKER_URL : "amqp://arl:arlpassword@rabbitmq:5672/arlv2host"


MONGO:
  URI : 'mongodb://admin:admin@mongodb:27017/'
  DB : 'arl'



#GeoIP 数据库文件配置项
GEOIP:
  CITY: '/data/GeoLite2/GeoLite2-City.mmdb'
  ASN: '/data/GeoLite2/GeoLite2-ASN.mmdb'


#Fofa API 配置项
FOFA:
  URL: "https://fofa.info"
  EMAIL: "" 
  KEY: ""
  MAX_PAGE: 5
  PAGE_SIZE: 2000


# 利用三方API进行域名收集
# 测试命令 python3.6 -m test.test_query_plugin [source1] [source2]
# 域名查询插件配置, enable 字段可以单独控制是否启用该插件，如果没有这个字段也会默认启用
QUERY_PLUGIN:
  alienvault:
    enable: true
  certspotter: # https://www.certspotter.com/
    after_id: 1
    max_page: 3
    enable: true
  crtsh:
    enable: true
  fofa:  # fofa 的key配置在上面
    enable: true
  hunter_qax: # 网站 https://hunter.qianxin.com/
    api_key:
    page_size: 100
    max_page: 5
    enable: false
  passivetotal: # 请前往 https://community.riskiq.com/ 注册自己的key并替换
    auth_email:
    auth_key:
    enable: false
  quake_360: # 网站 https://quake.360.cn/
    quake_token:
    max_size: 500
    enable: false
  rapiddns:
    enable: true
  securitytrails: # 网站 https://securitytrails.com/
    api_key:
    enable: false
  virustotal: # 网站 https://www.virustotal.com/gui/
    api_key:
    enable: false
  zoomeye:
    api_key:
    max_page: 20
    enable: false


#钉钉消息推送配置
#钉钉添加机器人，请查看
#https://github.com/TophantTechnology/ARL/wiki/ARL%202.3%20%E6%96%B0%E6%B7%BB%E5%8A%A0%E5%8A%9F%E8%83%BD%E8%AF%B4%E6%98%8E
DINGDING:
  SECRET: ""
  ACCESS_TOKEN: ""

#邮件推送配置
EMAIL:
  HOST: ""
  PORT: ""
  USERNAME: ""
  PASSWORD: ""
  TO: ""

# 监控任务 WEBHOOK 配置
# IP/域名监控和站点监控结束后会往下面的URL POST提交JSON数据
# 为了验证身份会在Header中带上Token 字段
# 进入容器测试  docker-compose exec worker bash
# 测试命令 python3.6 -m test.test_webhook <task_id> <scope_id>
WEBHOOK:
  URL: ""
  TOKEN: ""


#GITHUB 搜索 TOKEN
GITHUB:
  TOKEN: ""

#代理配置项，如"http://127.0.0.1:8080", 端口扫描不会走代理
PROXY:
  HTTP_URL: ""

ARL:
  AUTH: true
  #API 认证key, 可以访问api/doc查看文档
  API_KEY: "qingshan"
  BLACK_IPS:
    - 127.0.0.0/8
    - 0.0.0.0/8
    - 172.16.0.0/12
    - 100.64.0.0/10
    #- 10.0.0.0/8
    #- 192.168.0.0/16
  ## 禁止域名，不可为空数组
  FORBIDDEN_DOMAINS:
    - baidu.com
  #端口对应前端测试选项
  PORT_TOP_10: "80,443,8443,8080,8081,8888,8089,5000,5001,8085,800,81,9000,88,8001,8090"
  #域名爆破字典前端大字典选项
  DOMAIN_DICT: "/code/app/dicts/domain_2w.txt"
  #文件泄漏字典
  FILE_LEAK_DICT: "/code/app/dicts/file_top_2000.txt"

  #域名爆破并发数
  DOMAIN_BRUTE_CONCURRENT: 300
  #组合生成的域名爆破并发数
  ALT_DNS_CONCURRENT: 1500

```



### 3.安装arl

```shell
docker-compse up -d
```



## Tips

1.docker与docker-compse都需要安装
2.自行开放5003端口
