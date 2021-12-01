---
title: Springboot AlibabaCloud Demo使用说明
date: 2021-11-27 21:22:00
tags:
 - alibaba-cloud
 - nacos
 - feign
 - restTemplate
categories:
 - [springcloud]
 - [quickstart]
 - [alibaba-cloud]
---
### Springboot AlibabaCloud Demo使用说明

> [springboot-alibabacloud-demo源码地址](https://github.com/mauersu/springboot-demo)  其中springboot-alibabacloud-demo模块

1. 下载并启动nacos[官网快速开始](https://nacos.io/zh-cn/docs/quick-start.html)
2. 启动nacos后，导入项目document文件夹下nacos_config_export.zip文件
3. 导入mysql数据库test初始化脚本，在document文件夹下的sql文件夹init.sql文件
4. 启动provider-demo项目
5. 访问'http://localhost:8081/test/1'，如果返回

```
{"id":"1","username":"11","password":"111"}
```

则证明项目连接数据库成功。
6. 访问'http://localhost:8081/provider',如果返回

```
alibabacloud-demo-name
```

则证明项目连接nacos配置中心成功。
7. 启动consumer-demo项目
8. 访问'http://localhost:8082/provider/name',如果返回

```
alibabacloud-demo-name
```

则证明项目连接nacos配置中心成功。
9. 访问'http://localhost:8082/consumer',如果返回

```
alibabacloud-demo-name:alibabacloud-demo-name
```

则证明项目使用feign访问provider-demo成功。
10. 访问'http://localhost:8082/consumer1',如果返回

```
alibabacloud-demo-name
```

则证明项目使用RestTemplate访问provider-demo成功。
11. 访问'http://localhost:8082/consumer2',如果返回

```
alibabacloud-demo-name
```

则证明项目使用RestTemplate访问provider-demo成功。