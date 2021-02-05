# 阿里云服务器配置FRP内网穿透
---
> 准备

- [x] 阿里云ECS服务器
- [x] frp_0.35.1_linux_amd64.tar.gz
- [ ] ...

[frp下载地址](https://github.com/fatedier/frp/releases)

## ①阿里云服务器安装

> 记录以下数据,后面修改用 
```ksh
# cd /usr/local
# wget https://github.com/fatedier/frp/releases/download/v0.35.1/frp_0.35.1_linux_amd64.tar.gz
# tar -zxvf frp_0.35.1_linux_amd64.tar.gz
# mv frp_0.35.1_linux_amd64 frp
# rm -rf frpc*
# vim frps.ini
```
> 修改服务端ini
```
[common]
bind_port = 8888 #客户端和服务端连接的端口，这个端口号我们之后在配置客户端的时候要用到。
  dashboard_port = 7500 #服务器端仪表板的端口，可以查看服务器状态。
  token = 123456 #登录令牌口令，这个也是配置客户端要用到的。
  dashboard_user = admin #表示打开仪表板页面登录的用户名。
  dashboard_pwd = admin #表示打开仪表板页面登录的密码。
vhost_http_port = 8080 #反向代理HTTP主机时使用。
  vhost_https_port = 10443 #反向代理HTTPS主机时使用。
```
[frps.ini Server](https://github.com/fatedier/frp/blob/dev/conf/frps_full.ini)
> 服务端自动运行
# 编写 frp service 文件，以 centos7 为例,适用于 debian
vim /usr/lib/systemd/system/frpc.service
# 内容如下
```
[Unit]
Description=frpc
After=network.target

[Service]
TimeoutStartSec=30
ExecStart=/usr/local/frp/frpc -c /usr/local/frp/frpc.ini
ExecStop=/bin/kill $MAINPID

[Install]
WantedBy=multi-user.target
```
# 启动 frp 并设置开机启动
```
systemctl enable frpc
systemctl start frpc
systemctl status frpc
```
# 部分服务器上,可以需要加 .service 后缀来操作,即:
```
systemctl enable frpc.service
systemctl start frpc.service
systemctl status frpc.service
```
## ②群晖客户端安装
```shell-session
# cd /usr/local
# wget https://github.com/fatedier/frp/releases/download/v0.35.1/frp_0.35.1_linux_amd64.tar.gz
# tar -zxvf frp_0.35.1_linux_amd64.tar.gz
# mv frp_0.35.1_linux_amd64 frp
# cd frp
# rm -rf frps*
# vim frpc.ini
```
> 修改客户端ini
```

```
[frpc.ini Client](https://github.com/fatedier/frp/blob/dev/conf/frpc_full.ini)

> 群晖开机运行
```
回到群晖，进入 控制面板> 计划任务 >新建触发任务 >自定义脚本> 事件默认是开机>设置名字frp>任务设置  
自定义脚本里面写 /usr/local/frp/frpc -c /usr/local/frp/frpc.ini

```
## 疑难杂症



> 安装方式
