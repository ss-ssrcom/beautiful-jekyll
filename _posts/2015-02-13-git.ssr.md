---
layout: post
title: 如何远程连接Linux服务器
subtitle: 世界这么大
tags: [Linux]
---

如果你本地电脑使用的是 Windows 系统，那我推荐你下载一个叫 Git Bash 的软件来远程连接你的Linux服务器。

官方免费下载地址：https://git-scm.com/downloads

![](https://raw.githubusercontent.com/ss-ssrcom/ssrou/master/img/blog/git1.png)

如果你是 Linux 或者 MacOS 用户，请忽略上面的软件。

直接打开终端（Terminal），输入 ssh root@ip 其中 ip 替换成你服务器的 IPv4 地址, 按回车键，然后复制粘贴密码，按回车键即可登录。

粘贴密码时不显示密码，但不影响。

在开始登陆服务器之前，我们先打开命令行ping一下自己服务器上的IP地址是否能ping通（运行—CMD—ping ip）。

ping通后接着打开 git bash 软件，输入 ssh root@你的服务器ip地址，你就可以成功登陆你的服务器了！

补充：怎么修改Vultr服务器 root 用户密码？

先通过命令行连接上服务器，然后使用命令：passwd root

然后根据提示输入新的密码。

修改完成之后立即生效(请谨慎操作)，断开服务器，下次再连接服务器就需要输入修改后的新密码了。
