---
date: "2019-04-20T23:47:25+08:00"
publishdate: "2019-04-20+08:00"
lastmod: "2019-04-20+08:00"
draft: false
title: "编程警句 130"
tags: ["来点轻松的", "计算机", "blog"]
series: ["周末闲谈"]
categories: ["周末闲谈"]
img: "img/weekend_talks/epigrams_on_programming_1.jpg"
toc: false
summary: "边笑边哭"
---

## Epigrams on Programming 编程警句


## 译者说


正如第72句所言 *An adequate bootstrap is a contradiction in terms.*，需要解释的笑话多多少少有些悖论的影子。解释笑话总是件吃力不讨好的事，一来容易隐射说笑话的人说得不高明，二来容易隐射听笑话的人反应不够快。

一来这笑话是外国笑话，难免中外笑点不同；二来这笑话是三十年前的笑话，笑点不一定是这个时代的笑点；三来，最大的幸福，莫过于有人告诉我说“你这句话解释错了，原意应该是如此如此”。

*Epigrams on Programming* 作者是 [Alen Jay Perlis](http://en.wikipedia.org/wiki/Alan_Perlis) ，美国计算机科学家，程序员中的上古巨神，因在编程语言中的早期探索和获得首届图灵奖闻名。

*Epigrams on Programming* 发表于 [ACM SIGPLAN Notices, Volume 17 Issue 9, September 1982](http://portalparts.acm.org/950000/947955/fm/frontmatter.pdf?ip=198.55.120.199&CFID=552884859&CFTOKEN=85666119)

耶鲁大学网站上刊登的本文以 [Epigrams in Programming](http://www.cs.yale.edu/homes/perlis-alan/quotes.html) 为题。Epigrams on Programming 比 Epigrams in Programming 多了 10 条 meta-epigram。

正文小标题为译者所加。

感谢 [marrowleaves](https://github.com/marrowleaves) 的校正。

## 正文


### Preface 前言

The phenomena surrounding computers are diverse and yield a surprisingly rich base for launching metaphors at individual and group activities. Conversely, classical human endeavors provide an inexhaustible source of metaphor for those of us who are in labor within computation. Such relationships between society and device are not new, but the incredible growth of the computer's influence (both real and implied).lends this symbiotic dependency a vitality like a gangly youth growing out of his clothes within an endless puberty.

The epigrams that follow attempt to capture some of the dimensions of this traffic in imagery that sharpens, forcuses, clarifies, enlarges and beclouds our view of this most remarkable of all roans' artifacts, the computer.

### Epigrams 警句
--------------

1. >One man's constant is another man's variable.
    
   吾之常量，彼之变量。

2. >Functions delay binding: data structures induce binding. Moral: Structure data late in the programming process.

   函数推迟绑定；数据结构导致绑定。寓意：(编程中)推迟数据结构化的时间。

3. >Syntactic sugar causes cancer of the semi-colons.

   语法糖导致分号癌。

   `吐槽: Python 说，我没有分号癌！`

4. >Every program is a part of some other program and rarely fits.

   每个程序都是其他程序不合适的一部分。

5. >If a program manipulates a large amount of data, it does so in a small number of ways.

   如果一个程序用于处理大量数据，它就没几种选择了。

6. >Symmetry is a complexity reducing concept (co-routines include sub-routines); seek it everywhere.

   对称性有助于减少复杂度（协程包含例程）。对称性无处不在。

   `sub-routines: 和通常所见的function、method、procedure是同义词，使用return返回。co-routines 使用yield。`

7. >It is easier to write an incorrect program than understand a correct one.

   写错误的程序比理解正确的程序简单。

8. >A programming language is low level when its programs require attention to the irrelevant.

   任何编程语言在处理无关事务时都是低级语言。

9. > It is better to have 100 functions operate on one data structure than 10 functions on 10 data structures.

   用100个函数操作一个数据结构比仅用10个函数但是操作10个不同的数据结构要好。

10. >Get into a rut early: Do the same processes the same way. Accumulate idioms. Standardize. The only difference (!) between Shakespeare and you was the size of his idiom list - not the size of his vocabulary.

    早立规矩：同样方式做的同样处理。积累固定用法(idiom)。标准化。你和莎士比亚的唯一区别是成语(idiom)量——不是词汇量。

   `吐槽: idiom有两个意思，可惜不能都翻译成“成语”。`

11. >If you have a procedure with 10 parameters, you probably missed some.

    如果你写了一个需要10个参数的函数，你或许还漏了什么。

12. >Recursion is the root of computation since it trades description for time.

    递归是计算之母。她用描述换取时间。

13. >If two people write exactly the same program, each should be put in micro-code and then they certainly won't be the same.

    如果两个人用低级语言写同一个程序，它们显然不会相同。

14. >In the long run every program becomes rococo - then rubble.

    程序终将成为洛可可，然后是碎石。

    `Rococo: 洛可可，起源于18世纪法国的艺术风格。华而不实，过度装饰。`

    吐槽: 这句话原型应该是:

        But this long run is a misleading guide to current affairs. 
        In the long run we are all dead - John Maynard Keynes

    这种长远的眼光对当下事物是一种误导。长远来看，我们都要要死的 —— 凯恩斯（经济学家，不要说没听过这个名字。。。）

15. >Everything should be built top-down, except the first time.

    凡事都应该自顶向下，除了第一次。

16. >Every program has (at least) two purposes: the one for which it was written and another for which it wasn’t.

    程序都有至少两个目的：一个是写它的目的，另一个不是。

17. >If a listener nods his head when you're explaining your program, wake him up.

    如果有人听你讲解程序时点头了，把他叫醒。

18. >A program without a loop and a structured variable isn't worth writing.

    没有循环和结构变量的程序不值得写。

    吐槽: 这句话原型应该是:

        The unexamined life is not worth living for a human being - Socrates

    未经审视的生活不值得度过 —— 苏格拉底

19. >A language that doesn't affect the way you think about programming, is not worth knowing.

    没有影响你思考编程的语言不值得学。

20. >Wherever there is modularity there is the potential for misunderstanding: Hiding information implies a need to check communication.

    模块是误解之源；信息隐藏预示沟通的必要。

    吐槽: 这句话原型应该是:

        Wherever there is a will there is a way.

    有志者事竟成。

21. >Optimization hinders evolution.

    优化阻碍进化。

22. >A good system can't have a weak command language.

    好系统无坏指令。

23. >To understand a program you must become both the machine and the program.

    要理解一段程序，你得同时成为机器和这段程序。

24. >Perhaps if we wrote programs from childhood on, as adults we'd be able to read them.

    从童年开始写程序，长大了就能读懂了。

25. >One can only display complex information in the mind. Like seeing, movement or flow or alteration of view is more important than the static picture, no matter how lovely.

    脑海中只能呈现复杂的信息。就像视觉，无论静止的画面多么美丽，变化更加重要。

26. >There will always be things we wish to say in our programs that in all 
   known languages can only be said poorly.

    程序中总有些话，所有已知的语言都不能很好的表达。

    `吐槽: 何不把programs改成love letter，千言万语道不尽我对你的爱云云。`

27. >Once you understand how to write a program get someone else to write it.

    一旦你理解了怎么写某个程序，让别人去写它吧。

28. >Around computers it is difficult to find the correct unit of time to measure progress. Some cathedrals took a century to complete. Can you imagine the grandeur and scope of a program that would take as long?

    很难找到合适的时间单位来衡量计算机领域内的进展。有些教堂建了一个世纪。  
    你能想象写了一个世纪的程序的雄伟壮丽吗？

29. >For systems, the analogue of a face-lift is to add to the control graph 
   an edge that creates a cycle, not just an additional node.

    系统的整容是在控制图上加一条边，而不是新的节点。  
    [Control graph](http://en.wikipedia.org/wiki/Control_flow_graph) 指程序运行逻辑。其 node 是顺序执行的基本单元，edge 表示跳转。

30. >In programming, everything we do is a special case of something more general - and often we know it too quickly.

    编程中，我们常常过快的了解到，所做的都是普遍情况的特例，