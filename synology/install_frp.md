# 阿里云服务器配置FRP内网穿透
---
> 准备

- [x] 阿里云ECS服务器
- [x] frp_0.35.1_linux_amd64.tar.gz
- [ ] ...

[frp下载地址](https://github.com/fatedier/frp/releases)

## ①...

> 记录以下数据,后面修改用 
```sh
[root@fozn]# cd /usr/local
[root@fozn local]#  wget https://github.com/fatedier/frp/releases/download/v0.35.1/frp_0.35.1_linux_amd64.tar.gz
[root@fozn local]# tar -zxvf frp_0.35.1_linux_amd64.tar.gz
[root@fozn local]# mv frp_0.35.1_linux_amd64 frp
[root@fozn local]# cd frp
[root@fozn frp]# rm -rf frpc*
```
> 将`ds3617_6.1.img`刻录至U盘

## ②用U盘启动
```shell
[root@fozn]# cd /usr/local
[root@fozn local]#  wget https://github.com/fatedier/frp/releases/download/v0.35.1/frp_0.35.1_linux_amd64.tar.gz
[root@fozn local]# tar -zxvf frp_0.35.1_linux_amd64.tar.gz
[root@fozn local]# mv frp_0.35.1_linux_amd64 frp
[root@fozn local]# cd frp
[root@fozn frp]# rm -rf frpc*
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
