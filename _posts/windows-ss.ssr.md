---
layout: post
title: 微软桌面Windows如何使用shadowsocks软件
subtitle: 世界那么大，我想去看看！
gh-repo: daattali/beautiful-jekyll
tags: [shadowsocks]
comments: true
---

一、下载

1、首先下载最新版 Shadowsocks Windows 或者【shadowsocks-win：GitHub】。

2、需要安装 .NET Framework 4.6.2 和 Microsoft Visual C++ 2015 Redistributable (x86)   【一般电脑均已安装，可省略此步骤】。

二、基本使用

1、在任务栏找到 Shadowsocks 图标。

2、在 服务器 菜单添加多个服务器【或者依次操作：服务器-> 扫描屏幕上的二维码 -> 扫描 我的套餐 中服务器节点的二维码】。

3、选择 启用系统代理 来启用系统代理。请禁用浏览器里的代理插件，或把它们设置为使用系统代理。

4、除了设为系统代理，你也可以直接自己配置浏览器代理。在 SwitchyOmega 中把代理设置为 SOCKS5 或 HTTP 的 127.0.0.1:1080。这个 1080 端口可以在服务器设置中设置。

三、PAC说明

1、可以编辑 PAC 文件来修改 PAC 设置。Shadowsocks 会监听文件变化，修改后会自动生效。

2、你也可以从 GFWList （由第三方维护）更新 PAC 文件。

3、你也可以使用在线 PAC URL。

四、服务器自动切换说明

1、负载均衡：随机选择服务器。

2、高可用：根据延迟和丢包率自动选择服务器。

3、累计丢包率：通过定时 ping 来测速和选择。如果要使用本功能，请打开菜单里的【统计可用性】。

4、也可以实现 IStrategy 接口来自定义切换规则，然后给我们发一个 pull request。
