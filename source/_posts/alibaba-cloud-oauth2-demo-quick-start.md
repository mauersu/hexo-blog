---
title: Springboot AlibabaCloud OAuth2 Demo使用说明
date: 2021-12-1 22:03:00
tags:
 - alibaba-cloud
 - nacos
 - feign
 - restTemplate
categories: 
 - [springcloud]
 - [quickstart]
 - [oauth2]
 - [alibaba-cloud]
---
### Springboot AlibabaCloud OAuth2 Demo使用说明

> [springboot-alibabacloud-oauth2-demo源码地址](https://github.com/mauersu/springboot-demo)  其中springboot-oauth2-demo模块

1. 下载并启动nacos[官网快速开始](https://nacos.io/zh-cn/docs/quick-start.html)
2. 启动nacos后，导入项目document文件夹下nacos_config_export.zip文件
3. 导入mysql数据库test初始化脚本，在document文件夹下的sql文件夹oauth_demo.sql文件
4. 安装redis-server并启动
5. 导入项目下document文件夹下oauth2-server.postman_collection.json文件到[Http请求工具Postman](https://www.postman.com/)
6. 启动oauth2-server项目
7. 访问Postman中auth-server:密码模式获取令牌接口，如果返回

```
{
    "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX25hbWUiOiJhZG1pbiIsInNjb3BlIjpbImFsbCJdLCJleHAiOjE2MzgzNzM4NzAsImF1dGhvcml0aWVzIjpbImRlbW86dGVzdCJdLCJqdGkiOiJkNDc3YzI1NS02MGQ2LTQ0NDUtOThlMC05OGJmNzBlYzBlYWMiLCJjbGllbnRfaWQiOiJ0ZXN0IiwidXNlcm5hbWUiOiJhZG1pbiJ9.VcppGmpAMQPSwrtvEinSnEF5P_yti-fJVijg0-6gyAg",
    "token_type": "bearer",
    "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX25hbWUiOiJhZG1pbiIsInNjb3BlIjpbImFsbCJdLCJhdGkiOiJkNDc3YzI1NS02MGQ2LTQ0NDUtOThlMC05OGJmNzBlYzBlYWMiLCJleHAiOjE2Mzg0NTMwNzAsImF1dGhvcml0aWVzIjpbImRlbW86dGVzdCJdLCJqdGkiOiJiM2MxYzU1MS0wOWYxLTQ1ZTItYThjZi00MmU2YjQ5Y2E4ZWEiLCJjbGllbnRfaWQiOiJ0ZXN0IiwidXNlcm5hbWUiOiJhZG1pbiJ9.MhsgG-qwmsAdaFa5qH-jDrTwa0ZL4t6IkK9-5On0yZU",
    "expires_in": 7199,
    "scope": "all",
    "username": "admin",
    "jti": "d477c255-60d6-4445-98e0-98bf70ec0eac"
}
```
则证明项目连接数据库以及oauth2密码模式登录成功。
8. 访问Postman中auth-server:provider接口，并设置Headers中Authorization参数为最新accesstoken，如果返回

```
alibabacloud-demo-name
```

则证明项目连接nacos配置中心成功。
9. 启动oauth2-resource项目
10. 访问Postman中resource:testfeign接口，并设置Headers中Authorization参数为最新accesstoken，如果返回

```
alibabacloud-demo-name
```
则证明资源服务器feign调用oauth-server成功。