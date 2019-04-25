---
date: "2019-04-25T09:32:15+08:00"
publishdate: "2019-04-25+08:00"
lastmod: "2019-04-25+08:00"
draft: false
title: "符号表达式的递归函数及其机器计算"
tags: ["每日 Paper", "计算机", "blog"]
series: ["经典论著"]
categories: ["每日 Paper"]
img: "img/everday_paper/recursive_functions_of_symbolic_expressions_and_their_computation_by_machine.jpg"
toc: true
summary: "每天一篇计算机 Paper (2019/4/25)"
---
>John McCarthy. 1960. Recursive functions of symbolic expressions and their computation by machine, Part I. Commun. ACM 3, 4 (April 1960), 184-195.
>
>译者：陈思源

本文隶属于"每天一篇计算机 Paper"系列博客，更多内容请点击[这个链接](https://seuite.github.io/categories/%E6%AF%8F%E6%97%A5-paper/)。

本系列博客均非完整译文，如需阅读完整文章，请访问相关图书馆订阅。

译者注：1960 年提出 LISP 的那篇著名论文。本文里还提出了动态类型检查，垃圾回收, 递归函数，S-expression, 程序及数据……可谓贡献辉煌。另外，本文使用了 Latex 作为排版系统哟。

## Introduction

由麻省理工学院的人工智能小组为 IBM 704 计算机开发了一个名为 LISP（用于 LISt Processor）的编程系统。 该系统旨在促进一个名为 Advice Taker 的拟议系统的实验，从而可以指示机器处理声明性和命令式句子，并且在执行其指令时可以表现出“常识”。Advice Taker 最初的提案[1]是在 1958 年 11 月制定的。主要要求是一个编程系统，用于操纵表达形式化的陈述性和命令性句子的表达式，以便 Advice Taker 系统可以进行推演。

>A programming system called LISP (for LISt Processor) has been developed for the IBM 704 computer by the Artificial Intelligence group at M.I.T. The system was designed to facilitate experiments with a proposed system called the Advice Taker, whereby a machine could be instructed to handle declarative as well as imperative sentences and could exhibit “common sense” in carrying out its instructions. The original proposal [1] for the Advice Taker was made in November 1958. The main requirement was a programming system for manipulating expressions representing formalized declarative and imperative sentences so that the Advice Taker system could make deductions. 

在其开发过程中，LISP 系统经历了几个简化阶段，并最终基于表示某类符号表达式的部分递归函数的方案。这种表示独立于 IBM 704 计算机或任何其他电子计算机。从现在来看，通过从称为 S 表达式的表达式类和称为 S 函数的函数开始来阐述系统似乎是有利的。

>In the course of its development the LISP system went through several stages of simplification and eventually came to be based on a scheme for representing the partial recursive functions of a certain class of symbolic expressions. This representation is independent of the IBM 704 computer, or of any other electronic computer, and it now seems expedient to expound the system by starting with the class of expressions called S-expressions and the functions called S-functions.

在本文中，我们首先描述了一种递归定义函数的形式。 我们相信这种形式主义既有编程语言，也有发展计算理论的工具。接下来，我们描述 S 表达式和 S 函数，给出一些例子，然后描述通用 S 函数应用，它起着通用图灵机的理论作用和解释器的实际作用。然后，我们通过类似于 Newell，Shaw和Simon [2]使用的列表结构以及程序对 S 函数的表示来描述 S 表达式在 IBM 704 的内存中的表示。再然后我们提到了 IBM 704 的 LISP 编程系统的主要特性。接下来介绍了用符号表达式描述计算的另一种方法，最后我们给出了流程图的递归函数解释。

>In this article, we first describe a formalism for defining functions recursively. We believe this formalism has advantages both as a programming language and as a vehicle for developing a theory of computation. Next, we describe S-expressions and S-functions, give some examples, and then describe the universal S-function apply which plays the theoretical role of a universal Turing machine and the practical role of an interpreter. Then we describe the representation of S-expressions in the memory of the IBM 704 by list structures similar to those used by Newell, Shaw and Simon [2], and the representation of S-functions by program. Then we mention the main features of the LISP programming system for the IBM 704. Next comes another way of describing computations with symbolic expressions, and finally we give a recursive function interpretation of flow charts.

我们希望描述一些已经在另一篇论文中使用的 LISP 的符号计算，并且还在其他地方给出了我们的递归函数形式主义在数学逻辑和机械定理证明问题上的一些应用。

>We hope to describe some of the symbolic computations for which LISP
has been used in another paper, and also to give elsewhere some applications of our recursive function formalism to mathematical logic and to the problem of mechanical theorem proving.

## 一些有关的讨论

我认为，这种觉得“Lisp是神秘的魔法”的文化基因是非常奇特和有趣的事情。Lisp是作为一个人工智能研究的工具在象牙塔里构建出来的，因而对于外行来说显得不熟悉和神秘。然而现在的程序员奉劝别人在死之前尝试一下Lisp，仿佛那是一种让人脑洞大开的致幻剂。事实上Lisp是当今还在广泛使用的第二古老的编程语言了，仅仅比Fortran年轻一岁。试想如果你的工作推广新的编程语言，能让人相信该语言具备神秘力量岂不是很棒。

### 理论A：公理语言

John McCarthy，Lisp的创造者，起初没有刻意使得Lisp成为计算原理的一个优雅馏化物。然而在经历了一系列的精炼后，Lisp就成型了。Paul Graham——后面会提到他——这样写道，使用Lisp，McCarthy“对编程做的事情就好像是欧几里得对几何学做的事情”。人们能在Lisp中发现深层的含义，原因就是McCarthy使用了最基本的部件构建了Lisp，这些基本部件与其说是他发明还不如说是他发现的。

McCarthy在1956年关于人工智能的达特茅斯夏季研究项目期间开始考虑创建一个编程语言。夏季研究项目是一个持续多周的学术会议，人工智能领域的先驱。McCarthy当时是达特茅斯的数学助理教授，事实上“人工智能”这一词汇也是他首次提出的。有十个人左右参与了会议。其中有Allen Newell和Herbert Simon，两位研究员分别隶属于RAND公司和卡内基梅隆大学，后者刚设计了一个语言叫IPL。

Newwell和Simon已经开始着手创建一个能从命题逻辑中生成证明的系统。他们意识到在计算机原始指令的层次开展工作是很困难的，于是决定创建一个语言——或者按照他们称呼的那样“伪代码”——可以帮助他们更自然的表达关于“逻辑理论机”的工作成果。IPL代表“Information Processing Language”，即“信息处理语言”，该语言相比如今的编程语言来说更像是一个高级汇编方言。Newwell和Simon，可能是参照了Fortran，留意到其他正在开发的“伪代码”语言都想用标准的数学符号表示等式。他们的语言则专注于使用符号化的表达式列表来表示命题逻辑中的句子。IPL程序基本是使用一系列的汇编语言宏来操作和求值这些列表中的表达式。

McCarthy认为在语言中添加Fortran类型的代数表达式是很有用的。所以他不是很喜欢IPL。然而他认为符号列表是建模人工智能领域问题的好方法，特别是涉及到推导的问题。这启发了McCarthy创建一个代数列表处理语言的想法，该语言既像Fortran同时又能像IPL处理符号列表。

当然，今天的Lisp不像Fortran。在接下来的几年里，McCarthy关于理想的符号处理语言的想法在演化。他的想法在1957年开始改变，当时他开始用Fortran编写棋类程序的子例程。长期使用Fortran的经验使他意识到其设计中存在很多错误，最主要的就是笨拙的IF语言。McCarthy发明了替代品，那就是真值条件表达式，如果条件测试成功返回子表达式A反之则返回子表达式B并且仅仅对返回的子表达式求值。1958年夏天，当McCarthy在设计一个微分程序时，他意识到真值条件表达式使得编写递归函数更简单更自然。微分问题也促使McCarthy设计了maplist函数，该函数接受另一个函数作为参数并将其应用于列表中的每个元素。This was useful for differentiating sums of arbitrarily many terms.

这些事情都不能用Fortran来表达，所以在1958年秋天，McCarthy分配一些学生来实现Lisp。这个时候McCarthy已经是MIT的助理教授了，所以这些都是MIT的学生。在McCarthy和学生们将他的想法转变为代码的时候，他们又进一步简化了语言。最大的改变就是Lisp的语法。在McCarthy最初的想法中，该语言包含了一种称为“M表达式”的东西，这是一个使得Lisp的语法像Fortran的语法糖层。即使M表达式可以被转化为S表达式——Lisp闻名的圆括号列表——S表达式事实上是针对机器的一种低级表示。问题是McCarthy指定M表达式使用方括号，然而当时McCarthy小组在MIT使用的键控穿孔器键盘没有方括号这个键。因此Lisp小组被迫使用S表达式来表示数据列表和函数调用。McCarthy和学生们还做出了其他一些简化，包括切换到前缀表示法和可变的内存模型，这意味着语言只有一种真实的类型。

1960年，McCarthy发表了他关于Lisp的著名论文“符号表达式的递归函数及其机器计算”。当时的Lisp经过修剪使得McCarthy意识到他创造一个“优雅的数学系统”而不仅仅是另一个编程语言。他后来写道，多次简化使得Lisp成为一种描述可计算函数的方式，该方式比图灵机或者递归函数理论中使用的通用递归定义更简练。在论文中，他展示了Lisp可以同时作为一种工作的编程语言和研究递归函数行为的形式工具。

McCarthy向读者阐述Lisp的方式是使用一个很小的规则集合来构建一个Lisp系统。Paul Graham后来在他的文章“Lisp之根”中重复了McCarthy的步骤，不过使用了可读性更高的语言。Graham可以仅仅使用七个基本运算符，两个函数的表示法，以及半打根据基本运算符定义的高阶函数来解释Lisp。Lisp可以使用一系列很少的基本规则来定义的特点无疑加深了其神秘性。Graham认为McCarthy的论文目的是使“计算公理化”。这的确可以认为是Lisp具有吸引力重要原因。其他语言中有明显的由关键字指示的人造构件，例如while或typedef或public static void，而Lisp的设计完全来自运算的逻辑需求。系统的质量再加上和“递归函数理论”等深奥领域的原始连接无疑使得Lisp在今天如此有声望。

### 理论B：未来的机器

在Lisp诞生后二十年，著名的黑客字典说Lisp已经成为了人工智能研究的“母语”。前期Lisp迅速流行大概是因为其规整的语法很容易在新的机器上实现。后来的研究者继续使用Lisp是因为在人工智能的符号时期能很好的处理符号表达式是很重要的。Lisp被用在了一些开创性的人工智能项目，如SHRDLU自然语言程序，Macsyma代数系统以及ACL2逻辑系统。

在1970年代中期，人工智能研究已经开始耗尽计算机的运算能力了。PDP-10机器——人工智能领域工作人员的最爱——具有18位的寻址空间，已经不再能满足Lisp的AI程序的需求了。许多AI程序需要的交互性对于分时系统来说也是个挑战。MIT的Peter Deutsch开始提出解决方案，那就是专门为Lisp程序制造计算机。这些Lisp机器，正如我在上一篇文章中描述的，可以给每个用户分配一个针对Lisp优化过的处理器。这样对于硬核Lisp程序员来说，他的工作环境就全部是Lisp写成的。在小型机时代末尾和全面开花微型机革命之前的尴尬时机设计的Lisp机器，当时成为了编程精英们的高性能个人计算机。

当时看来Lisp机器可能是未来的潮流。出现了好几个公司竞相对其进行商业化。这些公司中最成功的当属由MIT的AI实验室成立的Symbolics。1980年代，Symbolics生产了3600系列的计算机，在AI领域和其他需要高性能计算的产业广受欢迎。3600系列计算机具有这些特性，大屏幕，位图图形，鼠标接口，强大的图形和动画软件。的确是强大的机器才能支持强大的程序。例如，从事机器人研究的Bob Culley通过Twitter联系我，说可以在1985年的Symbolics 3650上实现并可视化寻路算法。他向我解释道，位图图形和面向对象编程（Lisp机器通过Flavors扩展实现）在1980年代是很新的技术。Symbolics走在时代前沿。

结果是Symbolics机器出奇的贵。1983的Symbolics 3600要花费110000美元。因此大部分的人对强大的Lisp机器只有羡慕的份。Byte杂志在1979年到1980年代末尾都在报道Lisp和Lisp机器。在1979年8月的Lisp特刊中，杂志编辑大力吹捧说MIT的新机器拥有“惊人的内存”和“先进的操作系统”。该机器如此有前途，以致Apple II，Commodore PET和TRS-80相形见绌。5年后的1985年，Byte杂志的一位作者描述了如何给“超级计算机Symbolics 3670”编写Lisp程序并且敦促读者学习Lisp，他还宣称Lisp不仅仅是“AI领域人士的语言”而且很快会成为一个通用编程语言。

关于人们是从何时开始觉得Lisp是天赐之物的问题，我向山景城的计算机历史博物馆的Paul McJones讨教，他做了很多Lisp相关的保存工作。他认为语言的固有属性无疑与之有关，然而他同时表示Lisp和1960s到1970s强大的人工智能应用的紧密联系也促成了这点。当1980年代Lisp机器可以购买了的时候，MIT和斯坦福之外的一些人也能领略到Lisp的强大了，因而传奇继续。Lisp机器和Symbolics在今天已经很少有人知道了，但是他们将Lisp的神秘延续到了1980年代尾声。

### 理论C：如何编程

在1985年，MIT的教授Harold Abelson和Gerald Sussman联同Sussman的妻子，Julie Sussman，出版了一本书“计算机程序的构造和解释”。该书使用一个Lisp方言Scheme教导读者编程。这本书在MIT的编程导论课上使用了20年。我觉得SICP（书名简称）加深了Lisp的“神秘因子”。SICP使用Lisp阐述了计算机编程艺术中的一些深邃甚至充满哲学意味的概念。这些概念是通用的，其实使用任何语言都可以，然而SICP的作者选择了Lisp。结果就是Lisp的声望随着这本优秀的书进一步增强，迷住了一代代的程序员。Lisp原本一直是“McCarthy优雅的形式论”；如今“这个语言也可以向你传达编程的奥义”。

仔细想想SICP其实是很怪异的，因为我觉得该书的怪异和Lisp的怪异在今天已经融合了。首先这本书的封面就很怪异。上面描画了一个男巫或炼金术士靠近一个桌子，准备施展法术。他的一个手里拿着卡尺或是罗盘，另一个手拿着一个刻着“eval”和“apply”字样的球状物。对面的妇女拿手指着桌子；在背景上有个希腊字母lambda漂浮在半空，发着光。
The cover art for SICP.
谁能告诉我这是在干嘛？为什么桌子长着动物的脚？妇女为什么指着桌子？球状物上的文字是何意？男巫是否已经解开宇宙的奥秘，奥秘是否蕴含在“eval/apply”循环和lambda演算中？看起来是这样的。单单这幅图片就极大的塑造了今天人们谈论Lisp时的基调。

书中的内容也很奇怪。SICP不像其他你读过的计算机科学书籍。作者在书的前言中写道，该书不仅仅是关于使用Lisp编程——它关注了三种现象，人类心智，计算机程序集合以及计算机。后面详细说明了他们的信念，那就是编程不应该被看作是计算机科学的学科而应该看作是“过程认识论”的一种新的表示方法。程序是组织思维的新方式只是恰好也可以给计算机运行。第一章简要介绍了Lisp，之后的大部分内容都是抽象的概念。里面由关于不同编程范式的讨论，关于面向对象系统中“时间”和“本体”的本质，以及通信的根本限制造成的同步问题，类似相对论中的光速限制。都是干货呀。

并不是想说这本书不好。事实上这本书很棒。它从一个很高的层次讨论编程概念，这些概念我一直找不到合适的语言来描述。让人惊奇的是一本编程导论书可以很快就进入对面向对象编程根本不足的讨论，以及函数式语言最小化可变状态带来的好处。更让人叹为观止的是接着讨论了流范式，类似于当今的RxJS，该范式可以各取所长。SICP提取了高阶编程设计的本质，使人回想起McCarthy的Lisp论文。你读了这本书后也应该推荐给你的程序员朋友；如果他们看了封面就不读了，留给他们的印象就是神秘的“eval/apply”在长着兽脚的桌子前施展魔法。

可能SICP最重大的贡献就是将Lisp从让人好奇的事物提升到了教育必需品。在SICP之前就有人说学习Lisp能让人在程序设计方面更优秀。1979年的Byte杂志就是证明。鼓吹MIT新Lisp机器的编辑同样也解释说这个语言值得学习，因为它“代表了一种分析问题的不同视角”。然而SICP不是将Lisp以其他语言的衬托展示出来的；SICP将Lisp用作了编程入门语言，暗示Lisp是掌握计算机编程基础的最优秀的语言。今天的程序员告诉他人在死之前尝试一下Lisp，这些都归功于SICP。毕竟Brainfuck语言按说也提供了“分析问题的不同视角”。但是人们还是会选择学习Lisp，因为二十多年来MIT都将Lisp在一开始就教授给学生，说明Lisp的视角是很有用的。

### Lisp归来

在SICP发表的同一年，Bjarne Stroustrup发表了第一版C++程序设计语言，给大伙带来了面向对象编程。几年之后，Lisp机器的市场萎缩AI寒冬来临。在接下来的十几年，C++和Java成为了未来的语言Lisp则遭到冷遇。

很难说人们从什么时候开始重新对Lisp产生兴趣的。有可能是在Y-Combinator联合创始人和Hacker News创始人，Paul Graham发表了一系列有影响力的文章后，这些文章里面力推Lisp是初创公司最好的开发语言。在他的文章“拒绝平庸”中，Graham强调是Lisp宏使得Lisp比其他语言更加强大。他声称自己在创业Viaweb时使用了Lisp，因此他可以比竞争者更快的开发特性。至少有些程序员被鼓动了。但是大部分的程序员并没有切换到Lisp。

如今越来越多的Lisp特性被加入到大家使用的编程语言中了。Python有了列表comprehensions。C#有了Linq。Ruby有了…，好吧，Ruby就是一种Lisp。就像Graham早在2001年的时候就提到，“嵌入到这些后续流行语言的默认语言，正在逐渐变成Lisp”。即使其他语言都是逐渐变成Lisp，Lisp本身却依然保留它专属的声望，作为一个很少人理解同时每个人都应该学的神秘语言。1980年，Lisp的20周年纪念日上，McCarthy写道Lisp已经活得够长了，它占用了“某种编程语言空间中的近似局部最优”。这真的是低估Lisp的真正影响力了。Lisp活了超过半个世纪，因为程序员不得不承认，十年又十年，Lisp依然是工作的最好工具。事实上，即便大多数的程序员根本不用它，Lisp还是活着的。得益于它的起源和在人工智能中的应用以及SICP的遗留，Lisp继续使人们着迷。直到我们能想象上帝创世使用了一种新语言，Lisp将长存。

## 上帝生活在 LISP 之上（摘自"GNU 幽默集"）
上帝在使用Lisp  
当他用绿色填充树叶。  
分形的花朵和递归的树根：  
是我见过的最有趣的hack。  
当我思考雪花时，  
每一片都不同，  
我知道上帝喜欢  
这有四字符名字的语言。

## 提问

请问：将 LISP 和其他语言分开的最主要特征是什么呢？

请将你的答案发送至 [Susan 的邮箱](seuite@outlook.com)

每期言之成理的答案均将得到一份小礼品，同时每周答对次数最多及最佳回答的同学将获得一份 Susan 送上的实体礼品~

我们会在每周周报当中发表 实体礼品 获奖名单，你可以[点击这里](https://seuite.github.io/report/)查看我们的周报~

## Inspired

- [How Lisp Became God's Own Programming Language](https://news.ycombinator.com/item?id=18225870) - from [Hacker News](https://news.ycombinator.com/news)