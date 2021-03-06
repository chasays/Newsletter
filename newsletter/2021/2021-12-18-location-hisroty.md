---
layout: post
title: "16 - 根据 IP 地址找到对应的小区"
subtitle: ''
author: "叉叉敌"
header-style: text
tags:
  - Newsletter
  - 定位
---

![](https://gitee.com/chasays/mdPic/raw/master/uPic/MhpGIT.jpg)

就在本周，大家都知道 `Apache Jog4j` 的 0-day 漏洞，导致大批量的使用 Java 的工程都需要做临时紧急的修复。

这里就不对 Log4Shell 漏洞展开聊了，我比较好奇的是，在我们完成上线后，第二天就收到大量的 xss 注入。

一开始我以为是安全部门在做常规的安全测试，但是也没有收到过邮件通知，就有了下面的事情了。

我首先从 Nginx 日志里面获取到用户的 IP，然后在百度搜索 IP，同时就可以得到这个 IP 地址的对于的地理地址，这个地理地址比较模糊，一般情况下只有`xx省xx市xx区`，没有具体到哪个小区。

![](https://gitee.com/chasays/mdPic/raw/master/uPic/EhJuWN.png)

这个 IP 具体的地址是：陕西省西安市新城区， 从地图上看，新城区看上去还是不小。

![](https://gitee.com/chasays/mdPic/raw/master/uPic/lxef3e.png)

有没有办法把范围缩小喃。

我们在手机上用一些软件的时候，会发现有些(应该是99%)软件会请求定位，基于手机手机定位的地址，就相对比较准确。

智能手机自带的定位系统，比较常见的就是这么几类：GPS、GLONASS、Galileo、QZSS 及北斗、LBS定位。

定位系统比较多，简单介绍下常见的系统：

- GPS： 全球定位系统，定位精度高
- GLONASS：前苏联的全球定位系统，类似GPS
- Galileo：伽利略是欧盟的一个定位系统
- LBS 定位： 定位精度不好，取决于基站的密度
- 北斗：中国大器，定位`精度可以达到 1m 以内`，目前 iPhone 12 及以上都支持

上面这几种大部分的定位精度可以在 10米 以内，以此往来，知道这个 IP 地址的`经度和纬度`，那么就可以更加详细的知道。

目前的运营商分配的 IP 都是动态的。

我曾经试过用家里宽带对外的IP，用这个固定的 IP 来做一个域名解析，就可以用外网就可以访问，加上 NAS 备份也方面，想想都很美好。但是奸商不会这么放过你，都是采用的动态 IP，意思是过几天这个IP就变化了，导致解析就会失败，也访问不了家里的 NAS。也不是没有办法，四川电信升级宽带后，可以向运营商申请一个固定 IP。不过每年的升级的宽带费，都够在其他云服务商那里轻松的买到一个服务器了。


`看了市面上公开已有的 IP 地址和地理数据，并不能实时的获取到当前用户的地址信息，只能通过这个 IP 段下面的地理地址信息`。



通过上面这个地址，计算出对应的`网段地址和路由`，找到该路由过去一段时间的定位的经度和纬度。

```
IP：1.83.211.77
掩码为 24： 255.255.255.0
1.83.211.0/24
```

在高德地图里面导入获取到的定位经度和纬度数据，就获取到一个热力图。

![](https://gitee.com/chasays/mdPic/raw/master/uPic/ZPU8fo.png)

如果要真正的获取到用户的地址，在打开网页的时候，开始请求用户定位。这样就可以拿到用户的经度和纬度，能更好的向公安机关报案。比如下面的定位信息，可以定位到具体的小区楼栋，这样可以根据硬件型号侦测设备，是完全可以找到是哪一户人家的，就是成本太高。

![](https://gitee.com/chasays/mdPic/raw/master/uPic/mrec7o.png)

大家不要以为在网上的匿名，就是真正的匿名，实际上一举一动都是暴露公众视野下的，千万不要做违法乱纪的事。

---

# 文章推荐

-  [居家实验](https://www.cdstm.cn/videos/Tops/jujiashiyan/)


来自`中国数字科技馆`，居家实验这个栏目里面提供许多的小实验，用家里的常见的工具就可以完成。

家里有小孩和巨婴的，玩起来吧，根本停不下来。




- [一名安全工程师的2021年度总结](https://blog.dornea.nu/2021/12/13/my-2021-review/)


本文的作者是一名安全工程师和终生学习者，在他的年终总结中，提到了一些软件方面的工具以及效率提升，还涉及到了几本书，包括软件架构方面的。值得一读


- [奔驰自动驾驶](https://arstechnica.com/cars/2021/12/mercedes-benz-gets-worlds-first-approval-for-automated-driving-system)



梅赛德斯-奔驰的自动驾驶系统已获得德国联邦汽车运输管理局的监管批准，3级系统将于明年首次亮相。Drive Pilot结合使用雷达、相机、激光雷达、麦克风、湿度传感器和高精度全球导航卫星系统，以提供真正的自动驾驶。

它可以处理意外的交通情况，并在必要时采取规避行动。Drive Pilot将仅限于时速高达37英里的预制、地理围栏、封闭式高速公路。



- [关于钱的描述](https://moretothat.com/money)

如果从生存的角度来看待这个世界，金钱只会放大你的不足感。但是如果自由定义了自己，那么无论我们拥有多少钱，你都会觉得钱很多。如果权力和影响力是我们想要的，那么金钱将驱使你的人际关系朝着这个方向发展。



- [PyTorch vs TensorFlow](https://www.assemblyai.com/blog/pytorch-vs-tensorflow-in-2022/)



本指南介绍了PyTorch与TensorFlow的主要优缺点，以及如何选择正确的框架。



- [自动化测试框架设计](https://mp.weixin.qq.com/s/u69jyW1Ae8a6fOhTpGcUbw)


作者提到关于自动设计的一些概念。


- [关于冒烟测试](https://pythonspeed.com/articles/test-your-docker-build/)


冒烟测试简单、快速、易于运行，没有理由不用到项目中。


- [iPad支持app开发](https://www.apple.com/swift/playgrounds/)



iPad支持直接提交app到商店。对于有好想法的来说的，确实不错，成本低了不少






# 工具、资源推荐

- [文本加密工具](https://burnernote.com/)



Burner Note是一项免费、无广告和开源的服务，用于发送基于文本的安全笔记，这些笔记一旦被读取，就会被完全抹掉。使用的签名是AES-256-CBC加密的。


- [kavita 阅读平台](https://github.com/Kareadita/Kavita)



Kavita是一款快速、功能丰富、跨平台阅读服务器。以漫画为重点，目标是成为满足您所有阅读需求的完整解决方案。

不知道在内网nas上是否可以用起来。


-  [ZenJournal](https://thezenjournal.com)



快速、仅离线、支持标签、快速搜索。

适合一些很好的灵感，突然要记下来。


-  [Drgn 调试工具](https://github.com/osandov/drgn)



drgn（发音为“dragon”）是一个强调可编程性的调试器。Drgn旨在使脚本编写尽可能自然，使调试感觉像编码。

drgn公开程序中的类型和变量，以便在Python中轻松、富有表现力地编写脚本。


- [Web3 应用构建工具](https://thirdweb.com/)

这个平台使得构建 web3 应用程序和游戏变得难以置信的容易。不用关注区块链的复杂性，通过部署智能合同与自己的钱包(ETH之类的)关联 ，并提供 sdk，小部件和界面，以集成到任何应用程序，游戏或 DAO 的 web3功能。支持 Javascript、Typescript、 Python、 Golang、 Unity。

---

# 过去一周

上周的思考时刻： 

在小红书平台上，更新了大概 30+ 个视频，粉丝目前是 1000+，每天增加在20~50左右。先说说制作这个视频的时间成本，以 5~8 分钟的视频为例
- 写脚本：10分钟+， 如何才能更好让用户被你的视频笔记抓住
- 录制视频：10分钟+，逐字稿念的话，很尴尬，有些地方没有录好的，需要录2次或者更多
- 剪辑视频：15分钟+，我个人是普通话不好，要加字幕，不然用户听不懂，比较难
- 发布：5分钟左右，这一块最快，标题、封面、标签、发布时间等

大概这么算下来一个视频的时间成本就是 40 分钟左右，还有一个经验就是小红书喜欢`资料性`笔记。怎么理解喃？就是用户一看你的笔记就忍不住的想`收藏`那种。

做这些东西最后都是要转化，成年人放下面子赚钱才是最大的体面。怎么转化我目前还没有想好思路。不过有一个公式可以用一下：`收益 = 流量 * 转化率 * 客单价`。

将想法转化为可以与他人分享的项目的过程。即使很少人查看我创造的东西，知道我做了改进，不管有多小，内心都会有一种平静和满足。
我相信我的创作是出于正确的原因，为我自己写。



本周思考：Web3.0 有哪些东西，自己可以尝试？

---

看书最重要的就是定好`固定的时间`，比如每天早起20分钟，那这个时间就可以用阅读，可以做自己喜欢事情，就可以避免日后每天纠结到底啥时候读。

- 脱不花的「沟通的方法」 - 40%

这本书和下面的幽默感有部分呼应，如何幽默的与人交流和沟通。


- 李新：[幽默感](https://read.douban.com/ebook/138344064/) - 100%

反复训练，不要怕犯错。就像小孩刚开始走路一样，摔倒了再爬起来。

- 福格行为模型 - 0%

这本是讲习惯培养的，可以把这个模型要到其他地方。目前还没有开始，刚加入书单。


今天是坚持分享：第 `16/30` 天。

