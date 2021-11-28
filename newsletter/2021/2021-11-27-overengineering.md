---
layout: post
title: "13 - 过度工程"
subtitle: ''
author: "叉叉敌"
header-style: text
tags:
  - Newsletter
  - 过度
---

![](https://gitee.com/chasays/mdPic/raw/master/uPic/wLoiHT.jpg)

周末愉快。

本周在思考未来从事什么样工作的时候，首先考虑到的远程工作。

由于当前通勤时间比较长，住在「乡」下，上班高峰这个没有办法避免，下班之后可以晚一点出发，与此同时每天通勤时间大概是 3 个小时左右。如果能把这部分时间用到其他事情上，再加上万小时定律，说不定可以有点意外喃。

额外，就是成都最近新冠疫情有反复，导致我们分为 AB 班在家远程办公。不划水那是可不能的，只要把自己的时间规划好(推荐是番茄工作法)，在别人还在上班的时候，我却在晒太阳，这个优越感太爽了。

如上所述，首先考虑到的`远程`工作。

作为程序员的一员，发现有很多岗位：测试、前端、后端、设计、运营、产品等，到底哪一个岗位适合自己，而且还是可以远程办公的？

好巧不巧，看到一篇文章是关于[过度工程](https://www.mindtheproduct.com/overengineering-can-kill-your-product/)。先说说是什么过度工程，来自维基百科

> 过度设计(或过度设计) ，是指以一种精心设计的或复杂的方式来设计一个产品或提供一个问题的解决方案，其中一个更简单的解决方案可以被证明与原始设计的效率和有效性一样存在。

没有工程师是故意这样做的，对于刚入行的开发者，代码也比较简单，甚至语法糖都比较少用；随着时间的积累，了解了很多设计模型、语法糖，以及对业务相对熟悉后，实现的复杂就上来了，经常加一些`无中生有`的代码和功能；相反，再往后，成为专家、资深开发后，代码就`越来越简单`。

![](https://gitee.com/chasays/mdPic/raw/master/uPic/DQqJ3a.jpg)

导致过度开发的主要问题，大致分为 2 类：

一个是主观的，我们对功能、业务熟悉之后，就没有什么挑战，也`没有令人兴奋`的点，就导致我们喜欢把简单的问题复杂化；
二个是客观的，`需求不明确`。从用户到业务，然后到产品经理，再到我们程序员，过滤了很多层，最终我们实现出来的效果、交互，不一定是用户真正需要的功能，为了避免不确定性，会采用过度开发来满足这个需求；


影响也是显而易见，不仅浪费了不必要的时间、人力，还可能导致产品的复杂度指数增长，影响迭代速度。

对于我们的用户和业务，他们关心不是我们代码有多么的高级，多么的优雅，与此同时`他们更关心我们是否帮他们解决了问题`。

既不能需求不明确，又要对代码架构熟悉，那么就是`会编程的产品经理`，而不是一个把积压的需求整理为用户故事的产品经理。


文章提到几个点：
- 减少歧义、缩小范围、期望一个好方法：https://cloud.google.com/blog/products/devops-sre/sre-fundamentals-slis-slas-and-slos
- 让系统更容易修复、迭代和维护：KISS - Keep it simple stupid
- 要做减法，避免增加复杂性：Less is more
- 减少迭代速度：Reduce your iteration speed

如上所述，我目前希望从事的是一份`远程产品经理`，从电鸭、Turing、Upwork上面招聘数据来看，目前能远程+产品非常少见。最重要的是自己能胜任吧，后面好好学习下关于产品的知识，希望有前辈和读者能推荐一些资料等，谢谢。

你对过度工程有什么建议或自己的看法么？直接回复本邮件即可。



---

# 文章推荐

疫情反复，先来 2 篇医学相关的文章。

- [不伤害人类细胞的情况下粉碎超级细菌](https://newatlas.com/medical/ultrashort-laser-pulses-superbugs/)

研究人员已经证明，超短激光脉冲可以杀死细菌和病毒，而不会伤害人类细胞。虽然抗生素是20世纪最重要的发明之一，但细菌会对其产生耐药性，因此找到其他`无法产生耐药性的杀死细菌的方法很重要`。激光的工作原理是激发病毒和细菌内部的蛋白质结构，导致一些分子键断裂并杀死微生物。这项技术可用于生物制品的体外消毒，将来还可用于`治疗血液感染`，方法是让患者接受透析，让血液通过激光治疗设备。

- [用转基因微小蠕虫可以在早期发现胰腺癌](https://interestingengineering.com/genetically-modified-tiny-worms-can-detect-pancreatic-cancer-at-an-early-stage)

未来可期，同样是医学方面的文章，日本生物技术初创公司开发了一种癌症筛查测试，这个`准确率相当高`，在试验期间，该方法对胰腺癌的检测准确率为100%，对其他类型癌症的检测准确率为91.3%，。

- [Pytorch Lightning让训练速度慢了4倍](https://medium.com/@florian-ernst/finding-why-pytorch-lightning-made-my-training-4x-slower-ae64a4720bd1) 

作者在将一些深度学习代码移植到Pytorch Lightning之后，t注意到培训模型的时间，增加了4倍，就是`慢了4倍`。在这篇文章中，描述了作者如何找到的root cause，最后反馈给官方修复。


- [Python 3.10发布](https://www.python.org/downloads/release/python-3100/)

python3.10发布，对新功能的介绍。
新版本对语言进行了大量改进，包括改进的`错误消息`，错误提示更精准了，还有其他的新功能。

![](https://gitee.com/chasays/mdPic/raw/master/uPic/3VDrpl.jpg)

- [How to live 读书笔记](https://mp.weixin.qq.com/s/6VVTxzFPAx41H7-8Kr7rcA)

自荐。仁者见仁，智者见智。每一种活法，以及每一句每个人的理解都可能不一样，很中性，不带感情，没有任何个人色彩在里面。结合自己经历来思考，会有不一样的结论，和书最后的图片、文字一样，有可能是鸭子、也有可能是兔子，没有孰是孰非。

- [国外找远程工作的平台](https://dev.to/thenomadevel/top-10-websites-to-find-remote-jobs-f7i)

国内的话，我推荐电鸭社区。英语好的话，可以找上面推荐(11.25更新)的网站看看，反正都远程，不分地域、国界。

# 工具、资源推荐

- [Taichi](https://github.com/taichi-dev/taichi)
Taichi(太极) 是一种用于`高性能数值计算`的并行编程语言。它嵌入Python中，其实时编译器将计算密集型任务卸载到多核CPU和大规模并行GPU。


- [Filament](https://github.com/google/filament)

谷歌出品，Filament是适用于Android、iOS、Linux、macOS、Windows和WebGL的`实时物理渲染`引擎。它为Android开发人员提供了一套工具和API，使他们能够轻松创建高质量的2D和3D渲染。有渲染场景的示例。

![](https://gitee.com/chasays/mdPic/raw/master/uPic/123.png)

- [Pglet](https://github.com/pglet/pglet)

Pglet 是后端开发人员的`Web UI框架`。

它支持Python、Bash、PowerShell和Node.js。

其他语言可以轻松添加Pglet可用于在不了解任何HTML、CSS或JavaScript的情况下构建Web应用程序。

- [lazygit](https://github.com/jesseduffield/lazygit)

lazygit是git命令的简单UI。虽然git是一个强大的工具，但许多时候用于复杂处理，很难做到。lazygit使添加文件、解决合并冲突、查看最近的分支等变得`非常容易`。

![](https://gitee.com/chasays/mdPic/raw/master/uPic/MXZm4x.jpg)

---

# 过去一周

上周的思考时刻： **未来想从事什么样的工作？打工、创业、其他？**
我目前自己的思考答案是：
- 自由、没有束缚
- 产品经理

本周思考：**在职场，是先提拔后培养，还是先培养后提拔？**

---

- 脱不花的「沟通的方法」 - 30%

没有变化。


- 「芬奇」 Finch (2021)


- Derek Sivers的「How to live」 https://sive.rs/h - 80%

从一开始我以为，只要读完整本书，里面可以找到一种很明确的那种生活方式是正确的。然而我当看完第一遍的时候，发现不是这样的。没有明确的信息，每一句看完一遍之后都有不同的感受，那看完第二遍，结合自己的认知还有不同的想法。




今天是坚持分享：第 `13/30` 天。

