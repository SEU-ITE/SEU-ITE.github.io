---
title: 每天一篇计算机 Paper (2019/4/11)
date: 2019-04-11 9:21:18
tags: 
 - 每日 Paper
 - 研究生
---

# 关于偏好的任务分配的分式 0-1 规划

>Güngör, M. (2019). "A fractional 0–1 program for task assignment with respect to preferences." Computers & Industrial Engineering 131: 263-268.
- 译者：陈思源

本文隶属于"每天一篇计算机 Paper"系列博客，更多内容请点击[这个链接](https://seuite.github.io/tags/%E6%AF%8F%E6%97%A5-Paper/)。

## 1. Introduction

我们考虑一个分配问题，其中每个任务必须分配给一个独特的人，负载分配必须公平; 更确切地说，任何人的负载都可能偏离平均值超过指定的常数。假设每个人都为每项任务指定一个偏好级别。对于给定的任务，我们将满意度定义为这些水平相对于负荷的加权平均值。例如，如果有人用负载 3 和 12 执行任务 A 和 B，并且如果他们对这些任务的偏好等级分别为 1 和 10，那么他的满意度就是 $ \frac{(3×1)+(12×10)}{3+12} = 8.2 $。我们希望在总加权满意度最大化的意义上找到最佳分配。我们的动机来自教学辅助任务分配问题。

We consider an assignment problem where each task must be assigned to a unique person, and load distribution must be fair; more precisely, nobody’s load can deviate from the average more than a specified constant. Every person is assumed to designate a preference level for each task. For a given assignment, we define satisfaction as the weighted average of these levels with respect to loads. For instance, if somebody undertakes tasks A and B with loads 3 and 12, and if his preference levels for these tasks are 1 and 10, respectively, then his satisfaction is (3×1)+(12×10) 3+12 = 8.2. We want to find the best assignment in the sense that total weighted satisfaction is maximized. Our motivation comes from the teaching assistant-task assignment problem. 

因为满意度被定义为两个线性函数的比率，数学模型是一个多比率，约束的 0-1 分式规划。在最近的一项讨论中，Borrero等人（2016b）概述了关于分式 0-1 程序（通常也称为双曲 0-1 程序）的文献，包括它们的应用，相关的计算复杂性和解决方法。可以将分式 0-1 程序重新表示为等效的混合整数线性程序。Li（1994）提出了这种方法，Wu（1997）进一步讨论了这种方法。Tawarmalani等（2002）开发了八种不同的混合整数凸规划重构，与 Li 相比，它具有更好的松弛界限。Borrero等（2016a）提出了一种改进线性化配方的简单技术。关键思想是利用 0-1 决策变量的某些特定线性组合的二进制表示。

The mathematical model turns out to be a multiple-ratio, constrained, fractional 0-1 program since satisfaction is defined as a ratio of two linear functions. In a recent survey, Borrero et al. (2016b) overview the literature on fractional 0-1 programs (also, often referred to as hyperbolic 0-1 programs) including their applications, related computational complexity, and solution methods. It is possible to reformulate fractional 0-1 programs as equivalent mixed-integer linear programs. Li (1994) propose such an approach that is further discussed by Wu (1997). Tawarmalani et al. (2002) develop eight different mixed-integer convex programming reformulations which have superior relaxation bounds compared to Li’s. Borrero et al. (2016a) suggest a simple technique to improve linearized formulations. The key idea is to exploit binary representations of certain linear combinations of the 0-1 decision variables. 

Pentico（2007）提出了一项关于过去五十年来文献中出现的任务问题变化的考察。我们考虑的问题与那里提到的分式分配问题的不同之处在于，在我们的案例中，可以将多个任务分配给同一个对象。广义赋值问题具有这种特点，但其目标函数是线性的，并且其对象的负载没有下限（仅上限）。Krumke和Thielen（2013）探讨了广义赋值的变体，特别是包含了下界假设的研讨会赋值的问题; 但是，它们允许了对象完全闲置的可能性。

Pentico (2007) presents a survey of the variations of the assignment problem that have appeared in the literature over the past fifty years. The problem we consider differs from the fractional assignment problem mentioned there in that multiple tasks may be assigned to the same agent in our case. The generalized assignment problem enjoys this property, but its objective function is linear, and there is no lower bound on agents’ loads (only upper bounds). Krumke and Thielen (2013) investigate a variation of generalized assignment, particularly the seminar assignment, that assume lower bounds; however, they allow for the possibility that an agent be left completely idle. 

许多分配模型都考虑了偏好。在兼职人员安排的背景下有一些例子（Mohan，2008; Akbari等，2013; Ruiz-Torres等，2015），大学时间表（Daskalaki等，2004）及其子问题 学院-课程分配问题（Ozdemir和Gasimov，2004; Ismayilova等，2007; Al-Yakoob和Sherali，2015），助教-作业分配问题（G¨uler等，2015），和研讨会主题-学生分配问题（Geiger和温格，2010）。大多数情况下，满意度直接表示为线性函数而不是线性函数的比率，并与其他几个目标一起并入模型中。Ozdemir和Gasimov（2004）和Ruiz-Torres等人（2015）是少数在定义中使用比率的人之一。Ruiz-Torres等人（2015）没有提供数学模型，但提出了启发式算法。Ozdemir和Gasimov（2004）考虑了多个目标，其中之一是平均满意度的优化。他们通过分析层次过程将这些目标转化为单一目标，将问题重新表述为非线性非凸性程序，并使用Gasimov（2002）中描述的修改后的次梯度方法来解决它。

Many assignment models take preferences into account. There are examples in the contexts of part-time personnel scheduling (Mohan, 2008; Akbari et al., 2013; Ruiz-Torres et al., 2015), university timetabling (Daskalaki et al., 2004) and its subproblem of faculty-course assignment (Ozdemir and Gasimov, 2004; Ismayilova et al., 2007; Al-Yakoob and Sherali, 2015), teaching assistant-task assignment (G¨uler et al., 2015), and seminar topic-student assignment (Geiger and Wenger, 2010). Most often satisfactions are expressed directly as linear functions rather than ratios of linear functions, and incorporated into the model together with several other objectives. Ozdemir and Gasimov (2004) and Ruiz-Torres et al. (2015) are among those few who use ratios in their definitions. Ruiz-Torres et al. (2015) do not provide a mathematical program, but propose heuristics. Ozdemir and Gasimov (2004) consider multiple objectives, one of them being the optimization of average satisfaction level. They transform these objectives into a single objective by means of the analytic hierarchy process, reformulate the problem as a nonlinear nonconvex program, and use the modified subgradient method described in Gasimov (2002) to solve it. 

本文的贡献是双重的。一方面，我们提供了一个新的分式 0-1 应用：关于偏好的任务分配（参见Borrero等，2016b）。另一方面，我们建议对 Ozdemir 和 Gasimov（2004）中类似问题采用替代解决方案，将其视为非线性非凸性程序。也就是说，我们建议将问题线性化，然后通过现成的求解器求解等效的混合整数模型。

The contribution of this paper is twofold. On the one hand, we provide a new application of fractional 0-1 programming: task assignment with respect to preferences (cf. Borrero et al., 2016b). On the other hand, we suggest an alternative solution approach for the similar problem in Ozdemir and Gasimov (2004) treated as a nonlinear nonconvex program. Namely, we propose to linearize the problem and then solve an equivalent mixed-integer model by an off-the-shelf solver. 

在精确的定义之后，我们在 §2.1 中展示问题的计算复杂度，并在 §2.2 给出三种等效混合整数线性公式。接下来，我们在 §3 中讨论一些实际问题，并在 §4 中引入启发式。然后我们在 §5 中提供计算研究。最后在 §6 中，我们总结了主要结果，并提到了进一步研究的一些机会。

After a precise definition, we show the problem’s computational complexity in §2.1, and givethree equivalent mixed-integer linear formulations in §2.2. Next, we discuss some practical issues in §3, and introduce a heuristic in §4. Then we provide a computational study in §5. Finally, we make a summary of main results and mention a few opportunities for further research in §6.