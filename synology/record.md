# 记录

## 群晖安装python3.8.并安装pip
> 先卸载官方python3.5
> 添加第三方套件网址
```http://packages.synocommunity.com```
> 安装python3.8：
```
群晖控制面板打开ssh
连接群晖ssh
sudo -i 输入密码获取root
添加软链接：
ln -s /volume1/@appstore/python38/bin/python3 /usr/bin/python3
ln -s /volume1/@appstore/python38/bin/python3.8 /usr/bin/python3.8
此时输入python3或者python3.8应该就能看到python3.8
ln -s /volume1/@appstore/python38/bin/pip /usr/bin/pip
ln -s /volume1/@appstore/python38/bin/pip3 /usr/bin/pip3
ln -s /volume1/@appstore/python38/bin/pip3.8 /usr/bin/pip3.8
```
