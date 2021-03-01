# 联通宽带光猫超级密码

## ①1.设置工程账号登陆
在浏览器上输入 [192.168.2.1/logoffaccount.html](http://192.168.2.1/logoffaccount.html)
设置隐藏用户改为启用，这样就可以用工程账号登陆了。

## ②登录工程帐号
登陆地址：[192.168.2.1](http://192.168.2.1)
用户名：fiberhomehg2x0
密码：hg2x0

## ③开启Telnet服务器
工程模式中，服务设置-->Telnet服务器-->勾选”允许Telnet服务器“（自己设置好用户名和密码）。

## ④用Xsheel获取账户密码
下载安装xsheel telnet进你的猫 账号密码为你刚刚设置的 然后输入`get telname`得到管理员账户名，`get telpwd`得到管理员密码。

用超级账户登陆光猫后台
登陆地址：[192.168.2.1/cu.html](http://192.168.2.1/cu.html)

到此你就可以看到光猫的配置了，开始折腾路由器吧！
# 黑群晖6.1.7搭建
---
> 准备

- [x] ds3617_6.1.img
- [x] DS_3617xs_15284.pat
- [ ] DiskGenius分区工具
- [ ] Win32DiskImager 或 Diskimage
- [ ] Notepad++

[阿文菌的安装教程](https://post.smzdm.com/p/ag82zdd3/)

## ①制作群晖引导U盘

> 记录以下数据,后面修改用 
```ruby
# 查看NAS设备MAC地址,类似:
  00-1E-37-86-B7-AB
# 查看U盘的设备ID,类似:
  VID = 0930 PID = 140A
```
> 将`ds3617_6.1.img`刻录至U盘
```bash
  - 刻录前最好删除U盘所有分区并格式化
  - 用Win32DiskImager 或 Diskimage都行
  - 用Diskimage的话,在 Write Image to 下拉菜单中选择 Physical Disk开头的选项
```
> 修改`grub.cfg`
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
1. 浏览器访问[find.synology.com](http://find.synology.com/)
2. 搜索到NAS设备后进入安装界面,点 *设置*
3. 用`手动安装`,点 *浏览*  选择 `DS_3617xs_15284.pat`

!> 注意! NAS中所有硬盘数据将删除!!!

4. 等待安装完成

## 疑难杂症

> 安装方式


