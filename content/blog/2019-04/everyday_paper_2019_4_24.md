---
date: "2019-04-24T16:07:30+08:00"
publishdate: "2019-04-24+08:00"
lastmod: "2019-04-24+08:00"
draft: false
title: "定理证明程序的复杂性"
tags: ["每日 Paper", "计算机", "blog"]
series: ["经典论著"]
categories: ["每日 Paper"]
img: "img/everday_paper/the_complexity_of_theorem-proving_procedures.png"
toc: true
summary: "每天一篇计算机 Paper (2019/4/24)"
---
>A. Cook, Stephen. (1971). The Complexity of Theorem-Proving Procedures. Proc 3rd FOCS. 151-158. 10.1145/800157.805047.
>
>译者：陈思源

本文隶属于"每天一篇计算机 Paper"系列博客，更多内容请点击[这个链接](https://seuite.github.io/categories/%E6%AF%8F%E6%97%A5-paper/)。

本系列博客均非完整译文，如需阅读完整文章，请访问相关图书馆订阅。

译者注：本文定义了第一个 NPC 问题，也是 NP 完全理论的奠基之作

## Summary

结果表明，由多项式时间边界非确定性图灵机解决的任何识别问题都可以“归约”到确定给定命题公式是否是重言式的问题。 这里“归约”意味着，粗略地说，如果第二个问题是可解决的，那么第一个问题可以在多项式时间内确定地解决。 根据这种可简化的概念，定义了多项式难度，并且表明确定同义性的问题具有与确定两个给定图中的第一个是否与第二个子图同构的问题相同的多项式度。 本文也讨论了其他例子，介绍和讨论了一种测量谓词演算证明程序复杂性的方法。

>It is shown that any recognition problem solved by a polynomial timebounded nondeterministic Turing machine can be "reduced" to the problem of determining whether a given propositional formula is a tautology. Here "reduced" means, roughly speaking, that the first problem can be solved deterministically in polynomial time provided an oracle is available for solving the second. From this notion of reducible, polynomial degrees of difficulty are defined, and it is shown that the problem of determining tautologyhood has the same polynomial degree as the problem of determining whether the first of two given graphs is isomorphic to a subgraph of the second. Other examples are discussed. A method of measuring the complexity of proof procedures for the predicate calculus is introduced and discussed. 

在本文中，一组字符串表示一些固定的，足够大的，有限字母集 Z 上的一组字符串。该字母表足够大，可以包含此处描述的所有集合的符号。 除非明确说明，否则所有图灵机都是确定性识别装置

>Throughout this paper, a set of strings means a set of strings on some fixed, large, finite alphabet Z. This alphabet is large enough to in- clude symbols for all sets described here. All Turing machines are deter- ministic recognition devices, unless the contrary is explicitly stated

原文之后的部分涉及大量数学符号和公式，建议阅读原文，这里给出一个有关的讨论：

## 有关本文的一些讨论

NP 问题是指其解的正确性可以在多项式时间内被检查的一类问题。  
有一部分 NP 问题的解已经可以在多项式时间内找到，比如数组求和，这部分问题是 NP 中比较简单的一部分，被命名为 P 类问题。P 以外的 NP 问题，是目前还不能够在多项式时间内求解的问题。

显然，用遍历法证明 NP = P 是不可取的，因为NP问题实在太多了。这时 Stephen A. Cook 出现了，写了这篇 The Complexity of Theorem Proving Procedures，提出了一个 NP-Complete 的概念。NPC 指的是 NP 问题中最难的一部分问题，所有的 NP 问题都能在多项式时间内归约到 NPC 上。

所谓归约是指，若 A 归约到 B，B 很容易解决（是 P 问题），则 A 也很容易解决（是 P 问题）。显然，如果有任何一道 NPC 问题在多项式时间内解决了，那么所有的 NP 问题就都成了 P 类问题，即证明了 NP=P，这极大的简化了证明过程。那么要怎样证明一个问题 C 是 NPC 问题？

首先，要证明 C 是 NP 问题，也就是 C 的解的正确性可以在多项式时间内被检查；然后要证明有一个 NPC 问题 B，能够在多项式时间内归约到 C。这就要求必须先存在至少一个 NPC 问题。

这时 Cook 在 1971 年的这篇文章中就证明了第一个 NPC 问题：SAT 问题。SAT 问题是指：  
给定一个包含 n 个布尔变量的逻辑式，问是否存在一个取值组合，使得该式被满足。  
Cook 证明了 SAT 是一个 NPC 问题，如果 SAT 容易解决（是 P 问题），那么所有NP都容易解决（是 P 问题）。其证明方法利用了非确定性图灵机。

非确定性图灵机是一类特殊的图灵机，这种机器的性质是：只要问题有一个解，它就能够在多项式时间内解决该问题。Cook 证明了，SAT 是该机器在计算过程中必须满足的所有约束条件的总集，任何一个 NP 问题在这种机器上的计算过程，都可以描述成一个 SAT 问题。所以，如果你能有一个解决 SAT 的好算法，你就能够解决非确定性图灵机的计算问题，因为 NP 问题在非图机上都是多项式解决的。

所以你解决了SAT，就能解决所有 NP，因此——SAT 是一个NPC 问题。感谢 Cook，我们已经有了一个 NPC 问题，剩下的就好办了，用归约来证明就可以了。目前人们已经发现了成千上万的 NPC 问题，只要解决其中的任何一个，NP=P 就立刻得证，可以得千年大奖了（我认为还能立刻获得图灵奖）。

那么NP之外，存不存在一些连验证解都不能多项式解决的问题呢。当然！这部分问题，就算是NP=P，都不一定能多项式解决，被命名为 NP-Hard 问题。一个 NP-Hard 问题，可以被一个 NPC 问题归约到，也就是说，如果有一个 NP-Hard 得到解决，那么所有 NP 也就都得到解决了。

从直觉上说，P<=NP<=NP-Complete<=NP-Hard，问题的难度递增。但目前只能证明 P 属于 NP，究竟 P=NP 还是 P 真包含于 NP 还属于人类的未知领域。这个问题就留给同学们继续讨论吧（笑

## 提问

请问：NPC 问题和 P 问题的关系是什么呢？

请将你的答案发送至 [Susan 的邮箱](mailto:seuite@outlook.com)

每期言之成理的答案均将得到一份小礼品，同时每周答对次数最多及最佳回答的同学将获得一份 Susan 送上的实体礼品~

我们会在每周周报当中发表 实体礼品 获奖名单，你可以[点击这里](https://seuite.github.io/report/)查看我们的周报~
