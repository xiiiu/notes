# 黑群晖6.1.7搭建
---
> 准备

- [x] ds3617_6.1.img
- [x] DS_3617xs_15284.pat
- [ ] DiskGenius分区工具
- [ ] Win32DiskImager 或 Diskimage
- [ ] Notepad++

###[阿文菌的安装教程](https://post.smzdm.com/p/ag82zdd3/)
###[所需工具下载链接](https://pan.baidu.com/s/1ngx-yzYUPSGwhTMtO9I0ig) 提取码：0p7h

## ①制作群晖引导U盘

> 记录以下数据,后面修改用 
```bash
# 查看NAS设备MAC地址,类似:
  00-1E-37-86-B7-AB
# 查看U盘的设备ID,类似:
  VID = 0930 PID = 140A
```
> 将ds3617_6.1.img刻录至U盘
```bash
  - 刻录前最好删除U盘所有分区并格式化
  - 用Win32DiskImager 或 Diskimage都行
  - 用Diskimage的话,在 Write Image to 下拉菜单中选择 Physical Disk开头的选项
```
> 修改grub.cfg
```bash
  - 用DiskGenius分区工具查看U盘,找到ESP/grub/grub.cfg,右键复制到桌面
  - 用Notepad++打开grub.cfg,按照之前查到的设备 ID (U盘的)和 MAC 地址(NAS的)修改,保存
  - 把修改过的grub.cfg文件拖回ESP/grub/目录,替换原文件
```

## ②用U盘启动

1. U盘插入NAS
1. 将NAS用网线连接至路由器
1. 开机,设置为U盘启动

## ③安装群晖系统

> 安装方式

```bash
docker run -d -p 9000:9000 --restart=always -v /var/run/docker.sock:/var/run/docker.sock --name prtainer-demo docker.io/portainer/portainer

```

- 访问地址：http://设备IP :9000

## 疑难杂症

> 安装方式

```bash
# 配置文件路径：~/homeassistant
docker run -d --net="host" --name="ha" --restart=always --privileged=true -v ~/homeassistant:/config -p 8123:8123  -e TZ="Asia/Shanghai" homeassistant/home-assistant:latest

```
!> 可以自定义修改HomeAssistant配置文件的路径，“~”代表当前登录用户的根目录


