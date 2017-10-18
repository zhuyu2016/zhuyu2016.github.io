---
layout:         post
title:          apache 403 forbidden 解决办法
subtitle:       Windows Server2016 install WampServer3.0
card-image:     http://imglf6.nosdn.127.net/img/ZCtaSzhXeWllVkM0bFVtblFYYmtKMGY2VG5KWFRucWdaU1lMQUFrY1h1bk5NRjFyRGtkbVBBPT0.jpg?imageView&thumbnail=1680x0&quality=96&stripmeta=0&type=jpg
date:           2017-04-02 19:31:16
tags:           code
post-card-type: image
---

## 说明

同一个局域网内，本机服务器可以正常访问我的站点，别的外网ip不能访问。

1. 防火墙关闭

2. 修改 apache 的 httpd.con f文件，将其中的 Require local 修改成 Require all granted.这个是2.4后新的处理方法，之前的方法不管用了。

![](http://images2015.cnblogs.com/blog/692110/201702/692110-20170206113607479-470814389.png)

3. 修改 httpd-vhosts.conf. 找到 <VirtualHost *:80>节点上的所有虚拟站点，将其中的 Require local 都改成 Require all granted。
![](http://images2015.cnblogs.com/blog/692110/201702/692110-20170206114011666-354485479.png)