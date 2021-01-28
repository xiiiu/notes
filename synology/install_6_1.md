# 黑群晖6.1.7搭建
---
> 准备
```bash
- [*] ds3617_6.1.img
- [*] DS_3617xs_15284.pat
- [ ] DiskGenius分区工具
- [ ] Win32DiskImager 或 Diskimage
- [ ] Notepad++
```
[阿文菌的安装教程](https://post.smzdm.com/p/ag82zdd3/)
[所需工具下载链接](https://pan.baidu.com/s/1ngx-yzYUPSGwhTMtO9I0ig) 提取码：0p7h

## ①制作群晖引导U盘

> 安装方式 
```bash
# 查看安装设备MAC地址,类似:
  00-1E-37-86-B7-AB
# 查看U盘的设备ID,类似:
  VID = 0930 PID = 140A
```
```bash
# 将ds3617_6.1.img刻录至U盘
  - 刻录前最好删除U盘所有分区并格式化
  - 用Win32DiskImager 或 Diskimage都行
  - 用Diskimage的话,在 Write Image to 下拉菜单中选择 Physical Disk开头的选项
```
```bash
# 修改grub.cfg
  - 用DiskGenius分区工具查看U盘,找到ESP/grub/grub.cfg,右键复制到桌面
  - 用Notepad++打开grub.cfg,按照之前查到的设备 ID (U盘的)和 MAC 地址(NAS的)修改,保存
  - 把修改过的grub.cfg文件拖回ESP/grub/目录,替换原文件
```
[具体操作请查看详细安装文档](https://www.runoob.com/docker/ubuntu-docker-install.html)

## ②用U盘启动

!> 注意：如果拉取速度没问题，可以不用换
```bash
# 编辑配置文件
nano /etc/docker/daemon.json
```
> 配置文件的内容
```json
{
  "registry-mirrors": ["https://docker.mirrors.ustc.edu.cn"]
}
```
[具体操作请查看详细操作文档](https://lug.ustc.edu.cn/wiki/mirrors/help/docker)


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


