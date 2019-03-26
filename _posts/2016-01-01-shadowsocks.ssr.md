If you want to keep a secret, you must also hide it from yourself.

Shadowsocks官网: https://shadowsocks.org

Shadowsocks官方GitHub: https://github.com/shadowsocks

A secure socks5 proxy, designed to protect your Internet traffic.

![](https://github.com/ss-ssrcom/ssrou/blob/master/img/blog/ss.png)

### Shadowsocks作者是谁？是否还在更新？

Shadowsocks是由若干人因为兴趣而制作的一个项目，主要开发者和领导者是@clowwindy ，但是在2015年下半年被“相关部门”约谈喝茶，于是被迫删除Github的源码及相关文档。

但Shadowsocks属于开源项目，所以删除前已经有人备份，同时由另一个志愿者跟进维护原版Shadowsocks客户端，而其他基于Shadowsocks项目的第三方项目有：ShadowsocksR、Shadowsocks-qt5、ShadowsocksCap等来维护更新Window/Linux客户端。

### Shadowsocks是否安全？加密性如何？

Shadowsocks是被设计来混淆数据，增加 墙 检查出流量特征所需的计算量，提高实时检测和匹配的成本。

SS的作者多次强调过这一点—>Correct username/password auth model · Issue #169 · shadowsocks/shadowsocks · GitHub

“我们不需要安全性。我们需要与随机字节无法区分。”

再三强调不要忘记SS作者的本意——这是一个能帮你上谷歌，上被墙屏蔽的网站的工具，其意义是瞒过 墙 的实时流量检测，而不是瞒过 墙 后面的master minds。

### Shadowsocks和VPN 的区别是什么？

### 百科：

VPN，即虚拟专用网络，功能是：在公用网络上建立专用网络，进行加密通讯。在企业网络中有广泛应用。VPN网关通过对数据包的加密和数据包目标地址的转换实现远程访问。VPN有多种分类方式，主要是按协议进行分类。VPN可通过服务器、硬件、软件等多种方式实现。顾名思义，虚拟专网，你接入VPN就是接入了一个专有网络，那么你访问网络都是从这个专有网络的出口出去，好比你在家，你家路由器后面的网络设备是在同一个网络，而VPN则是让你的设备进入了另一个网络。同时你的IP地址也变成了由VPN分配的一个IP地址。通常是一个私网地址。你和VPN服务器之间的通信是否加密取决于连接VPN的具体方式/协议。

Shadowsocks，即Sock5代理，采用socks协议的代理服务器就是SOCKS服务器，是一种通用的代理服务器。Socks是个电路级的底层网关，是DavidKoblas在1990年开发的，此后就一直作为Internet RFC标准的开放标准。Socks 不要求应用程序遵循特定的操作系统平台，Socks 代理与应用层代理、 HTTP 层代理不同，Socks 代理只是简单地传递数据包，而不必关心是何种应用协议（比如FTP、HTTP和NNTP请求）。所以，Socks代理比其他应用层代理要快得多。Sock5代理服务器则是把你的网络数据请求通过一条连接你和代理服务器之间的通道，由服务器转发到目的地。你没有加入任何新的网络，只是http/socks数据经过代理服务器的转发送出，并从代理服务器接收回应。你与代理服务器通信过程不会被额外处理，如果你用https，那本身就是加密的。

### 总结：

VPN的开发目的是给企业内网直接传输加密数据，最重要的就是安全性，相反VPN的流量特征变得很明显，特别是SSL VPN类型，比如Openvpn有SSL证书的加密，安全性不必多说，但是握手依然是明文，流量更加明显，导致匹配流量特征很容易，在我这里一旦链接Openvpn那就是秒封。

VPN目前就科学上网方面来讲，PPTP大部分地区已死，L2TP大部分地区已经出现干扰和断开连接情况，Openvpn一封一个准。而anyconnect大多数都是企业用的，所以墙不敢乱封，IKEv1/IKEv2需要注意证书中间人攻击问题。


 
所以，在VPN科学上网这方面，一些地区已经根据VPN的流量特征做出了相应的匹配策略，可以有效封杀VPN了。

Shadowsocks的开发目的就是穿透防火墙，最重要的是增加墙的匹配流量效率封杀成本和难度，也就是混淆隐秘性。

Shadowsocks是更注重流量混淆隐秘，VPN则是更注重加密安全性。如果你需要安全你可能需要 VPN 或者 Shadowsocks+TOR匿名 ，否则就抗干扰能力来说Shadowsocks更适合拿来科学上网，VPN中的Opnevpn是最安全的VPN协议之一，然而第一个被墙宣布效率检测、封杀！

没有完美的工具，VPN和Shadowsocks在某种程度上可以说是两种相反的技术，开发目的不一样，注重点也不一样，缺点相应的也不一样，所以根据当地运营商的封杀策略选择最适合自己的方式。

### Shadowsocks全局模式与VPN的区别：

VPN控制的是你电脑的整个网络，只要需要连接到互联网的流量都会经过vpn。

你的IP会被更换为VPN的IP。连接VPN只需要知道IP和账号密码。

Shadowsocks的全局模式，是设置你的系统代理的代理服务器，使你的所有http/socks数据经过代理服务器的转发送出。而只有支持socks5或者使用系统代理的软件才能使用Shadowsocks（一般的浏览器都是默认使用系统代理）。

经过代理服务器的IP会被更换。连接Shadowsocks需要知道IP、端口、账号密码和加密方式。但是Shadowsocks因为可以自由换端口，所以定期换端口就可以有效避免IP被封！

### Shadowsocks全局模式与PAC模式的区别：

上面已经解释了Shadowsocks的全局模式，而PAC模式就是会在你连接网站的时候读取PAC文件里的规则，来确定你访问的网站有没有被墙，如果符合，那就会使用代理服务器连接网站，而PAC列表一般都是从GFWList更新的。GFWList定期会更新被墙的网站（不过一般挺慢的）。

简单地说，在全局模式下，所有网站默认走代理。而PAC模式是只有被墙的才会走代理，推荐PAC模式，如果PAC模式无法访问一些网站，就换全局模式试试，一般是因为PAC更新不及时（也就是GFWList更新不及时）导致的。

### Shadowsocks原版和ShadowsocksR的区别是什么？

Shadowsocks原版在更新到 v2.5.8 之后被“相关部门”约谈喝茶了，于是就停止了更新。但是应网友要求，另一个开发者把 v2.5.8 的一些严重BUG修复了更新为 v3.0，然后宣布不再管了。

Shadowsocks原版本身，也是具有协议和混淆功能的，也就是原版协议/混淆，只是只有一个不能自行选择，并且全靠作者维护，作者喝茶后，就GG了，其他的接手者只是继续完善其他的功能。


 
而ShadowsocksR是在 原版作者喝茶前，由另一个程序员 @breakwa11 制作的第三方版本，主要特点是增加了一些人性化功能，比如服务器连接统计、连接管理、协议转换、多重代理等。

最主要的是ShadowsocksR的混淆协议和插件功能，因为Shadowsocks原版项目已经无人维护，同时 墙 的工作人员也在不停的寻找效率批量匹配特征的方法，目前SS原版协议在大部分地区已经被 匹配流量特征QOS限速了。

所以ShadowsocksR的混淆协议和插件就应运而生，其目的就是欺骗 墙 目前的流量匹配功能和QOS限速。

需要说明的是，ShadowsocksR目前最新的协议和混淆是会增加延迟和损耗15%的速度(因为混淆需要时间，越复杂的混淆越不容易被墙发现，同时混淆时间越长)，所以如果你没有限速，或许用原版协议和混淆会更好。


 
你可以理解为在原版协议的基础上加强了混淆功能，所以在部分地区只有使用ShadowsocksR的混淆功能才能达到最佳速度，当然不同地区也不一样，所以最好都试试！
