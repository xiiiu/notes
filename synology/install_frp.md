# 阿里云服务器配置FRP内网穿透
---
> 准备

- [x] 阿里云ECS服务器
- [x] frp_0.35.1_linux_amd64.tar.gz
- [ ] ...

[frp下载地址](https://github.com/fatedier/frp/releases)

## ①...

> 记录以下数据,后面修改用 
```ksh
> cd /usr/local
> wget https://github.com/fatedier/frp/releases/download/v0.35.1/frp_0.35.1_linux_amd64.tar.gz
> tar -zxvf frp_0.35.1_linux_amd64.tar.gz
[root@fozn local]# mv frp_0.35.1_linux_amd64 frp
[root@fozn local]# cd frp
[root@fozn frp]# rm -rf frpc*

nohup ./frps -c ./frps.ini &
```
> 将`ds3617_6.1.img`刻录至U盘

## ②用U盘启动
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

> 群晖开机运行
```
回到群晖，进入 控制面板> 计划任务 >新建触发任务 >自定义脚本> 事件默认是开机>设置名字frp>任务设置  
自定义脚本里面写 /usr/local/frp/frpc -c /usr/local/frp/frpc.ini

```
## 疑难杂症

```console
[root@fozn]# cd /usr/local
[root@fozn local]#  wget https://github.com/fatedier/frp/releases/download/v0.35.1/frp_0.35.1_linux_amd64.tar.gz
[root@fozn local]# tar -zxvf frp_0.35.1_linux_amd64.tar.gz
[root@fozn local]# mv frp_0.35.1_linux_amd64 frp
[root@fozn local]# cd frp
[root@fozn frp]# rm -rf frpc*
```

> 安装方式

```vb
[root@fozn]# cd /usr/local
[root@fozn local]#  wget https://github.com/fatedier/frp/releases/download/v0.35.1/frp_0.35.1_linux_amd64.tar.gz
[root@fozn local]# tar -zxvf frp_0.35.1_linux_amd64.tar.gz
[root@fozn local]# mv frp_0.35.1_linux_amd64 frp
[root@fozn local]# cd frp
[root@fozn frp]# rm -rf frpc*
```
