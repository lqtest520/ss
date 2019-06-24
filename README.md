Shadowsocks 一键安装脚本（四合一）
本脚本适用环境
系统支持：CentOS 6+，Debian 7+，Ubuntu 12+
内存要求：≥128M
日期　　：2019 年 01 月 11 日

关于本脚本
1、一键安装 Shadowsocks-Python， ShadowsocksR， Shadowsocks-Go， Shadowsocks-libev 版（四选一）服务端；
2、各版本的启动脚本及配置文件名不再重合；
3、每次运行可安装一种版本；
4、支持以多次运行来安装多个版本，且各个版本可以共存（注意端口号需设成不同）；
5、若已安装多个版本，则卸载时也需多次运行（每次卸载一种）；

友情提示：如果你有问题，请先阅读这篇《Shadowsocks Troubleshooting》之后再询问。


默认配置
服务器端口：自己设定（如不设定，默认从 9000-19999 之间随机生成）
密码：自己设定（如不设定，默认为 teddysun.com）
加密方式：自己设定（如不设定，Python 和 libev 版默认为 aes-256-gcm，R 和 Go 版默认为 aes-256-cfb）
协议（protocol）：自己设定（如不设定，默认为 origin）（仅限 ShadowsocksR 版）
混淆（obfs）：自己设定（如不设定，默认为 plain）（仅限 ShadowsocksR 版）
备注：脚本默认创建单用户配置文件，如需配置多用户，请手动修改相应的配置文件后重启即可。

客户端下载
常规版 Windows 客户端
https://github.com/shadowsocks/shadowsocks-windows/releases

ShadowsocksR 版 Windows 客户端
https://github.com/shadowsocksrr/shadowsocksr-csharp/releases

使用方法
使用root用户登录，运行以下命令：

wget --no-check-certificate -O shadowsocks-all.sh https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-all.sh
chmod +x shadowsocks-all.sh
./shadowsocks-all.sh 2>&1 | tee shadowsocks-all.log
安装完成后，脚本提示如下
Congratulations, your_shadowsocks_version install completed!
Your Server IP        :your_server_ip
Your Server Port      :your_server_port
Your Password         :your_password
Your Encryption Method:your_encryption_method

Your QR Code: (For Shadowsocks Windows, OSX, Android and iOS clients)
ss://your_encryption_method:your_password@your_server_ip:your_server_port
Your QR Code has been saved as a PNG file path:
your_path.png

Welcome to visit:https://teddysun.com/486.html
Enjoy it!
卸载方法
若已安装多个版本，则卸载时也需多次运行（每次卸载一种）

使用root用户登录，运行以下命令：

./shadowsocks-all.sh uninstall
启动脚本
启动脚本后面的参数含义，从左至右依次为：启动，停止，重启，查看状态。

Shadowsocks-Python 版：
/etc/init.d/shadowsocks-python start | stop | restart | status

ShadowsocksR 版：
/etc/init.d/shadowsocks-r start | stop | restart | status

Shadowsocks-Go 版：
/etc/init.d/shadowsocks-go start | stop | restart | status

Shadowsocks-libev 版：
/etc/init.d/shadowsocks-libev start | stop | restart | status

各版本默认配置文件
Shadowsocks-Python 版：
/etc/shadowsocks-python/config.json

ShadowsocksR 版：
/etc/shadowsocks-r/config.json

Shadowsocks-Go 版：
/etc/shadowsocks-go/config.json

Shadowsocks-libev 版：
/etc/shadowsocks-libev/config.json

------------------------------------------
ShadowsocksR一键安装脚本

本脚本适用环境：
系统支持：CentOS，Debian，Ubuntu
内存要求：≥128M
日期：2018 年 02 月 07 日

关于本脚本：
一键安装 ShadowsocksR 服务端。
请下载与之配套的客户端程序来连接。
（以下客户端只有 Windows 客户端和 Python 版客户端可以使用 SSR 新特性，其他原版客户端只能以兼容的方式连接 SSR 服务器）

默认配置：
服务器端口：自己设定（如不设定，默认从 9000-19999 之间随机生成）
密码：自己设定（如不设定，默认为 teddysun.com）
加密方式：自己设定（如不设定，默认为 aes-256-cfb）
协议（Protocol）：自己设定（如不设定，默认为 origin）
混淆（obfs）：自己设定（如不设定，默认为 plain）

客户端下载：
Windows / OS X
Linux
Android / iOS
OpenWRT

使用方法：
使用root用户登录，运行以下命令：

wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocksR.sh
chmod +x shadowsocksR.sh
./shadowsocksR.sh 2>&1 | tee shadowsocksR.log
安装完成后，脚本提示如下：

Congratulations, ShadowsocksR server install completed!
Your Server IP        :your_server_ip
Your Server Port      :your_server_port
Your Password         :your_password
Your Protocol         :your_protocol
Your obfs             :your_obfs
Your Encryption Method:your_encryption_method

Welcome to visit:https://shadowsocks.be/9.html
Enjoy it!
卸载方法：
使用 root 用户登录，运行以下命令：

./shadowsocksR.sh uninstall
安装完成后即已后台启动 ShadowsocksR ，运行：

/etc/init.d/shadowsocks status
可以查看 ShadowsocksR 进程是否已经启动。
本脚本安装完成后，已将 ShadowsocksR 自动加入开机自启动。

使用命令：
启动：/etc/init.d/shadowsocks start
停止：/etc/init.d/shadowsocks stop
重启：/etc/init.d/shadowsocks restart
状态：/etc/init.d/shadowsocks status

配置文件路径：/etc/shadowsocks.json
日志文件路径：/var/log/shadowsocks.log
代码安装目录：/usr/local/shadowsocks

多用户配置示例：

{
"server":"0.0.0.0",
"server_ipv6": "[::]",
"local_address":"127.0.0.1",
"local_port":1080,
"port_password":{
    "8989":"password1",
    "8990":"password2",
    "8991":"password3"
},
"timeout":300,
"method":"aes-256-cfb",
"protocol": "origin",
"protocol_param": "",
"obfs": "plain",
"obfs_param": "",
"redirect": "",
"dns_ipv6": false,
"fast_open": false,
"workers": 1
}
如果你想修改配置文件，请参考：
https://github.com/shadowsocksr-backup/shadowsocks-rss/wiki/Server-Setup
https://github.com/shadowsocksr-backup/shadowsocks-rss/blob/master/ssr.md
https://github.com/shadowsocksr-backup/shadowsocks-rss/wiki/config.json
