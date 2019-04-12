---
title: 每天一篇计算机 Paper (2019/4/12)
date: 2019-04-12 9:21:18
tags: 
 - 每日 Paper
 - 研究生
---

# 双目标进化优化中的生殖偏差，连锁学习和多样性保持

>Martins, J. P. and A. C. B. Delbem (2019). "Reproductive bias, linkage learning and diversity preservation in bi-objective evolutionary optimization." Swarm and Evolutionary Computation.
- 译者：陈思源

本文隶属于"每天一篇计算机 Paper"系列博客，更多内容请点击[这个链接](https://seuite.github.io/tags/%E6%AF%8F%E6%97%A5-Paper/)。

# Introduction

最成功的多样性保存机制提供了从多个解决方案中选择代表整个帕累托前沿的子集的方法。（译者注：帕累托前沿，又称帕累托最优，指资源分配的一种理想状态，假定固有的一群人和可分配的资源，从一种分配状态到另一种状态的变化中，在没有使任何人境况变坏的前提下，使得至少一个人变得更好。）通常，为了实现该目标，例如通过使用拥挤距离或超体积测量[1,2,3]来评估其目标向量的隔离程度。通过这些测量，可以为非主导解决方案分配更高的准确度，其目标向量位于目标空间的人口较少的区域，有利于再生产生这些区域的后代。由于非主导排序遗传算法II（NSGA-II）[11]等算法的成功，多样性保存机制和繁殖作为独立组件的使用变得无处不在，即使在最近的方法中它的影响仍然很明显[4]。

Most successful diversity preservation mechanisms pro vide ways to select, from a multiset of solutions, a subset that is representative of the whole Pareto front. Usually, to achieve this goal, solutions are evaluated on how isolated their objective vectors are, e.g., by using crowding distance or hypervolume measures [1, 2, 3]. From such measures it is possible to assign higher ﬁtness to non-dominated solutions whose objective vectors are in less populated regions of the objective-space, favoring reproduction to generate offspring in those regions. Motivated by the success of algorithms such as the Non-dominated Sorting Genetic Algorithm II (NSGA-II) [1], the use of diversity preservation mechanisms and reproduction as separate components became pervasive and its impact is evident even in more recent approaches [4].

在本文中，我们分析了繁殖操作者对多样性保存的有效性的影响。通过对p均匀和n点交叉的分析，我们评估了这些算子的假设，这些假设有助于降低客观空间的多样性（它们是有偏见的）。由于有偏见的操作者会妨碍更好的多样性保存，因此本研究可以更好地理解多目标繁殖算子。

In this paper, we analyze the inﬂuence of reproduction operators on the effectiveness of diversity preservation. Through the analysis of p-uniform and n-point cross over we evaluate the hypothesis of these operators contributing to the decreasing of diversity in objective-space (they are biased). Since biased operators would impede better diversity preservation, this study enables a better understanding of multiobjective reproduction operators.

从这个意义上讲，我们研究了 ρMNK 模型的双目标实例中的生殖偏差以及连锁学习对规避它的作用。结果表明，高度破坏性的交叉算子，即那些经常破坏先前构建解的算子，产生了一种平均效应的平均效应，它将它们的目标向量偏向目标空间的中心区域。

In this sense, we investigate reproductive bias in bi-objective instances of the ρMNK-model and the role of linkage learning on circumventing it. The results indicated that highly disruptive crossover operators, i.e., those that frequently destroy previously build solutions, produce a kind of averaging effect on the quality of the offspring that bias their objective vectors towards the central region of the objective space.

另一方面，使用连锁引导的交叉通过允许更好地保留父母的有用特征来修正这种偏差。当繁殖不是太具有破坏性时，后代往往与至少一个父母的品质相似。因此，解决方案覆盖的客观空间区域可能会继续被下一代的子孙覆盖，这是多样性保护的一个基本特征。

The use of a linkage-guided crossover, on the other hand, amended such bias by allowing better preservation of useful features from the parents. When reproduction is not too disruptive, offspring tend to be of similar quality to at least one of the parents. As a result, regions in objective-space covered by solutions are likely to continue being covered by offspring in the next generations, an essential characteristic for diversity preservation.

第2节回顾了从生殖角度提出的改善多样性保护的许多机制。第3节分析了p均匀和n点交叉的决策空间中的偏差。第3节展示了这种偏差如何影响目标向量的定位。第5节定义了我们对双目标进化优化的无偏复制的想法。第6节分析了不同操作者的生殖偏差，突出了这种偏见的联系学习的影响。

Section 2 reviews many mechanisms proposed to improve diversity preservation from the perspective of reproduction. Section 3 analyzes the bias in decision space of p-uniform and n-point crossover. Section 3 demonstrates how such bias might impact the positioning of the objective vectors. Section 5 deﬁnes our idea of unbiased reproduction for bi-objective evolutionary optimization. Section 6 analyzes the reproductive bias of different operators, high lighting the inﬂuence of linkage learning on such bias.


## Conclusion

多样性保持问题一直是多目标进化优化中的一个问题。然而，解决这个问题的大多数早期提议都认为它是进化算法中的一个独立组件。因此，众所周知的算法，如NSGA-II及其同时代的那些，首先工作，产生一个子代，然后指定一个适应的精度，以表明解决方案对于多样性保存有多么有趣。在本文中，我们发现这样的策略可能会受到常用复制算子的影响，因为在它们的标准设置中，它们会产生偏向于目标空间某些区域的子代。从这个意义上说，无偏见的再现算子可以通过避免这种冲突来显着改善多样性保存，并且应该是通用多目标再现算子的要求。

The diversity preservation problem has always been a concern in multiobjective evolutionary optimization. However, most of the early proposals to solve this problem have considered it an independent component within evolutionary algorithms. As a result, well-known algorithms such as NSGA-II and its contemporaries, worked by ﬁrst, generating an offspring, and then assigning an adapted ﬁtness to indicate how interesting a solution is regarding diversity preservation. In this paper, we showed that such strategies might have their eﬃcacy hampered by commonly used reproduction operators since in, their standard settings, they produce offspring that are biased to some areas of the objective-space. In this sense, unbiased reproduction operators can considerably improve diversity preservation by avoiding such a conﬂict and should be a requirement for a general purpose multiobjective reproduction operator.

首先，我们分析了传统的再生算子，例如p均匀和n点交叉，并证明了由于它们的高破坏性，它们产生的后代（对于p = 0.5和任何n）会偏向于客观中心。 我们认为这种偏见是对父母质量的平均影响的结果。 因此，我们证实了通过减少破坏性，可以减少生殖偏差并产生更好分布的后代。

At first, we analyzed traditional reproduction operators, such as p-uniform and n-point crossover, and demonstrated that, due to their high disruptiveness, the offspring they produce (for p = 0.5 and any n) were biased towards the center of the objective-space. We argued that such bias was the result of an averaging effect on the quality of the parents. Therefore, we veriﬁed that by decreasing disruptiveness it is possible to decrease the reproductive bias and produce a more well-distributed offspring.

但是，如何减少繁殖操作者的破坏性？ 我们验证了两种选择：（1）使用小p进行均匀交叉（2）使用联动引导交叉。p <0.5688 的均匀交叉在父母之间交换较少的遗传物质，因此它具有较小的破坏性。另一方面，联动引导的交叉将避免破坏父母的有价值的子结构，减少破坏性。我们对 ρMNK 模型的实例进行了实验，结果证实了这一假设，即随着操作者的破坏性降低，生殖偏差减小。

However, how to decrease the disruptiveness of reproduction operators? We validated two alternatives: (1) the use of a small p for uniform crossover (2) the use of a linkage-guided crossover. A uniform crossover with p < 0.5688 exchanges less genetic material between the parents, therefore, it is less disruptive. A linkage-guided crossover, on the other hand, will avoid destroying valuable substructures of the parents, being less disruptive. We performed experiments on instances of the ρMNK-model, and the results corroborated the hypothesis, i.e., the reproductive bias decreases as the disruptiveness of the operators decrease.

此外，我们证明了所识别的连锁集可能代表关于多个目标的相关决策变量，即对目标达成一致或完全不同意的决策变量。我们的结果证实了Sastry等人的观点。[27]的论点，通过表明在双目标情景中从个体目标函数中学习信息确实是困难的。然而，该分析还表明，另一种类型的信息（来自不同目标函数的相关决策变量）仍然是可检测的并且对于再现操作者是有用的。这个事实可以解释Shah和Reed [40]的良好结果并调解两种解释。本文从众所周知的交叉算子和链接学习的角度分析了生殖对多样性保存的影响。我们的结论表明，在双目标 ρMNK 实例的背景下，即使单个连锁模型也可以促进多样性保存并提高整体优化的有效性。我们相信这里讨论的结果提高了我们对多目标再生算子的基本原理及其与分布算法估计的相互作用的理解。

Additionally, we showed evidence that the linkage sets identiﬁed might represent correlated decision variables regarding the multiple objectives, i.e., decision variables that agree or completely disagree over the objectives. Our results corroborate Sastry et al. [27]’s arguments, by showing that it is indeed diﬃculty to learn information from the individual objective functions in a bi-objective scenario. However, the analysis also shows that another type of information (the correlated decision variables from different objective functions) is still detectable and useful for reproduction operators. A fact that could explain Shah and Reed [40]’s good results and conciliate both interpretations. This paper analyzed the inﬂuence of reproduction on708 diversity preservation from the perspective of well-known crossover operators and linkage learning. Our conclusions suggest that, in the context of bi-objective ρMNK instances, even single linkage models can facilitate diversity preservation and improve the effectiveness of optimization as a whole. We believe the results here discussed improves our understanding on the fundamentals of multiobjective reproduction operators and their interaction with estimation of distribution algorithms.