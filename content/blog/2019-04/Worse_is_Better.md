---
date: "2019-04-13T13:12:3+08:00"
publishdate: "2019-04-13+08:00"
lastmod: "2019-04-13+08:00"
draft: false
title: "越糟糕越好：简单之美 (Worse Is Better)"
tags: [ "计算机", "blog", "经典作品"]
categories: ["周末闲谈"]
img: "https://i.loli.net/2019/04/06/5ca87b7dac457.jpg"
toc: false
summary: "简单压倒一切"
---
# 越糟糕越好：简单之美 (Worse Is Better)
> 原作者：Richard P. Gabriel
> 
> 译者：陈思源

被称为"worse is better"的概念地认为在软件制作中（也许在其他领域），最好从最小的创作开始并根据需要增长。Christopher Alexander 可能称之为零碎增长。这个故事是关于这个概念如何演变的。

这是 Worse is better 的摘要：["Worse is Better"之后](http://www.dreamsongs.com/RiseOfWorseIsBetter.html)。

1984 年到 1994 年间，我经营了一家叫做 Lucid 的 Lisp 公司。（译者注：Lisp 是一门函数式编程语言，著名的 Hacknews 网站就是用它编写的）1989年，Lisp 的生意明显的不是很好，部分原因是很多 AI（译者注：Artificial Intelligence，人工智能）公司举步维艰，其他则是因为那些 AI 公司开始将他们的失败归咎于 Lisp 及其实现。1989年春的某天，我和一群黑客坐在 Lucid 的门廊处闲聊，有人问我为什么我认为人们相信 C 和 Unix 比 Lisp 更好，我开玩笑的说到：因为越糟糕的东西越好呀。大家哄堂大笑，同时我开始试着解释『为什么一些蹩脚的事情可能是更好的』。

几个月后，1989年的夏天，可能是因为 Lucid 是一个优秀的Lisp公司，一个名为 EuroPAL 的小型 Lisp 会议（欧洲 Lisp 实际应用会议）邀请我发表主题演讲。我同意了，在讨论演讲主题的时候，我想详细阐释一下如何把我们开玩笑的时候说的" Worse is better" 的想法应用于 Lisp。在 Lucid，我们知道很多关于如何使用Lisp来实现我们眼中的现实业务，因此"Lisp Good News，Bad News，How to Win Big"出现了。 [略有删节版本的html](http://www.dreamsongs.com/WIB.html) 和 [有关Treeshaker和Lisp应用程序交付的更多详细信息的pdf](http://www.dreamsongs.com/Files/LispGoodNewsBadNews.pdf)

我于 1990 年 3 月在剑桥大学做了这个演讲。我从未去过剑桥（也没去过牛津大学），而且我对在牛顿所在的学校讲话感到非常紧张。在礼堂里大约有 500 人 -800 人，在我的演讲之前他们音响正播放 Notting Hillbillies——我以前从未听过这个乐队，事实上，这张专辑还没有在美国上映。音乐显得非常合适，因为我在演讲中决定使用非常口语化的美式写作。尽管是英国乐队，Notting Hillbillies 演奏的音乐风格深受传统美国音乐的影响。因为座无虚席，所以我演讲时有些畏惧，最后，沉默了很长一段时间的。第一个说出来的人是 Gerry Sussman，他对这个话题很是讥讽了一番，其次是 Carl Hewitt，他同样不太友好。我花了 30 分钟试图向他们解释我的演讲.他们绝不想听到这样的批评——也许他们更希望有一个啦啦队长那样的演讲。

当然，我活了下来，然后回到了加利福尼亚州。那时候，互联网刚刚启动，所以可以预期没有太多人会听到有关这次谈话以及它引起的轩然大波。然而，当时在场的媒体在英国广泛地讨论了它。Headlines in computer rags 宣称"Lisp 已死，Gabriel 当立"(Lisp Dead, Gabriel States)。其中有一副 Bruce Springsteen 的画作，标题是『新泽西风格』(New Jersey Style)，指的是我对"worse is better"设计方法的昵称。然而，我躲开了这些话题，确信它很快就会平静下来。

大约一年后，我们聘请了一位名叫 Jamie Zawinski 的匹兹堡小孩。他还不到20岁，并得到 Scott Fahlman 的高度赞扬（译者注：Scott Fahlman 是 Lucid 联合创始人，卡内基梅隆大学计算机科学家，Common Lisp 业内领袖）。我们称他为"The Kid"。让他加入我们是一件非常有趣的事情：作为一个黑客他做的不差，而且在 Lucid 没有多少这类人的情况下就更是如此了。他想了解公司里的人，特别是我，因为我是承担让他加入的风险的人，包括把他带到西海岸。他的寻找方式是查看我的计算机文件——它们都处于无保护状态。他找到了 EuroPAL 文件，并发现了 worse is better 的部分。他将这些想法与 Richard Stallman 的想法联系起来。自从多年前我担任自由编程联盟的发言人以来，我就非常了解 Richard Stallman。 JWZ摘录了 worse is better 那个部分并将它们发送给他在卡耐基梅隆大学的朋友，他们将它们发送给他们在贝尔实验室的朋友，他们又将它们发送给各地的朋友。

不久后，我收到了十几封请求论文稿件的邮件。几家大公司的部门请我允许将这件作品用作他们20世纪90年代软件工程策略思想的一部分。我记得其中有 DEC，HP 和 IBM。 1991年6月，AI Expert 杂志重新出版了这篇论文，以在美国获得更大的读者群。

然而，尽管世界其他地方表现出了明显的热情，但我对于 worse is better 概念开始感到不安，特别是与我的联系。在20世纪90年代早期，我为杂志和期刊撰写了大量的论文和专栏，多到我得为其中一些使用 [Nickieben Bourbaki](http://www.dreamsongs.com/Nickieben.html) 这个笔名。这个名字最初的想法是，我在 Lucid 的工作人员会参与写作，而用单个假名代表集体，就像20世纪30年代的法国数学家在重写他们那个数学领域的基础时，使用 Nicolas Bourbaki 作为他们的集体名称一样。但是之后，只有我在用这个名字写东西。

在 1991-1992 的那个冬季，我用 Nickieben Bourbaki 的名字写了一篇名为 ["越糟糕越好糟糕透了"(Worse Is Better Is Worse)](http://www.dreamsongs.com/Files/worse-is-worse.pdf) 的文章。这篇文章是用来攻击 worse is better 的。在其中，小说的创作是 Nickieben 是 Richard P. Gabriel 的发小和同事，作为朋友，为了 Richard 好，Nickieben 在纠正 Richard 的信仰。

在1992年秋天，我在面向对象程序设计期刊（JOOP）对"Worse Is Better Is Worse"发表了一篇反驳社论，叫做 ["Is Worse Really Better?"](http://www.dreamsongs.com/Files/IsWorseReallyBetter.pdf)。Lucid 的人开始有点担心，因为我会带他们检查（作为我）支持 worse is better 的论文草稿，然后我会带他们反对（作为Nickieben）自己。一个同事对我可能患有精神疾病非常忧虑。

于是我阅读了很多经济学与生物学书籍，试着去理解经济系统中发生的进化。后来，将大部分学习到的这方面知识汇集到了一次 presentation 的 keynote 上，名字叫做：[Software Acceptance：How Winners Win](http://www.dreamsongs.com/Files/PatternsOfSoftware.pdf)。另外一部分则加到了我的论文书籍，[Patterns of Software: Tales from the Software Community](http://www.dreamsongs.com/Files/PatternsOfSoftware.pdf)，作为其中一个章节：[Money Through Innovation Reconsiderd](http://www.dreamsongs.com/Files/Innovation.pdf)。

你可能会想，经过十年的思考与讲演，不断的推到重来不断的更新进化，我对 worse is better 的观点已经毋庸置疑了（译者注：这篇文章写作于 2000 年）。其实不然，在 2000 年的 OOPSLA（面向对象技术的高峰会议）年度会议上，我被安排在一个名为『Back to the Future： Is Worse (still) Better ?』的专门小组（panel），准备期间，小组的组织者 Martine Devos 让我起草一篇意见书（position paper），于是我写了一篇公然反对 worse is better 思想的短文：[Back to the Future： Is Worse (still) Better?](http://www.dreamsongs.com/Files/WorseIsBetterPositionPaper.pdf)

但是几个月后，我又写了一篇：[Back to the Future：Worse (still) is Better!](http://www.dreamsongs.com/Files/ProWorseIsBetterPosition.pdf) 用于支持 worse is better 的观点。是的，我仍无法决定。于是Martine把这两篇短文合成了一份，作为小组的意见书。按照例行，小组的讨论期间出席者通常会从 worse is better 的支持方转向会议桌的另一侧：反对方。那天早上我坐在观众席上，几乎也是声嘶力竭的和他们辩论。我想正是因为大家对于『Worse is Better』的冒险精神、开明以及反驳的态度，才使得优秀成为可能。如果有一种可能性，不仅仅只是技术意义上的，而是一种美学上的失败，那么天使也会邀请恶魔，即便他们每天都在彼此斗争。

你自己决定吧！

## 摘自 Rise of Worse is Better 的部分：

Worse is Better，强调**简单压倒一切**，为了简单性，其他方便都可以做出牺牲，包含以下几点：

1. 简单性：设计必须简单，这既是对实现的要求，也是对接口的要求。实现的简单要比接口的简单更加重要。简单是设计中需要第一重视的因素。
2. 正确性：设计在任何值得注意的方面都要求正确。为了简单性，正确性可以做轻微的让步。
3. 一致性：设计不能过度不兼容一致。为了简单，一致性可以在某些方面做些牺牲，但与其允许设计中的这些处理不常见情况的部分去增加实现的复杂性和不一致性，不如丢掉它们。
4. 完整性：设计必须覆盖到实际应用的各种重要场景。所有可预料到的情况都应该覆盖到。为了保证其它几种特征的品质，完整性可以作出牺牲。事实上，一旦简单性受到危害，完整性必须做出牺牲。一致性可以为实现的完整性作出牺牲；最不重要的是接口上的一致性。