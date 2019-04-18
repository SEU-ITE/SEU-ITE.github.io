---
date: "2019-04-18T23:29:43+08:00"
publishdate: "2019-04-18+08:00"
lastmod: "2019-04-18+08:00"
draft: false
title: "无痛理解贝叶斯网络理论"
tags: ["每日 Paper", "计算机", "blog"]
series: ["经典论著"]
categories: ["每日 Paper"]
img: "img/everday_paper/bayesian_networks_without_tears.jpg"
toc: true
summary: "每天一篇计算机 Paper (2019/4/17)"
---
>Eugene Charniak (1991). Bayesian Networks without Tears. AI Magazine Contents, Volume 12(4): 50-63
>
>译者：陈思源

本文隶属于"每天一篇计算机 Paper"系列博客，更多内容请点击[这个链接](https://seuite.github.io/tags/%E6%AF%8F%E6%97%A5-Paper/)。

本系列博客均非完整译文，如需阅读完整文章，请访问相关图书馆订阅。

## Abstract

为概率理论基础相当有限的人工智能研究人员，我给出了一个关于贝叶斯网络的介绍。在过去的几年中，这种使用概率推理的方法在 AI 概率和不确定性社区中变得相当流行。实际上可以说，AI-不确定性社区的一大部分都使用了贝叶斯网络作为解决方案的 AI 逻辑论证。然而，尽管它们显然具有明显的重要性，但这些思想和技术并没有传播到相关的研究领域之外。这可能是因为这些想法和技术并不容易理解。为纠正这种情况，我希望使概率上不复杂的贝叶斯网络更容易理解。

I give an introduction to Bayesian networks for AI researchers with a limited grounding in probability theory. Over the last few years, this method of reasoning using probabilities has become popular within the AI probability and uncertainty community. Indeed, it is probably fair to say that Bayesian networks are to a large segment of the AI-uncertainty community what resolution theorem proving is to the AI-logic community. Nevertheless, despite what seems to be their obvious importance, the ideas and techniques have not spread much beyond the research community responsible for them. This is probably because the ideas and techniques are not that easy to understand. I hope to rectify this situation by making Bayesian networks more accessible to the probabilistically unsophisticated.

## Introduction

在过去的几年中，使用概率推理的方法，或者称做信念网络，贝叶斯网络，知识地图，概率因果网络等，已经在AI概率和不确定性社区中变得流行。这种方法在 Judea Pearl（1988）的书中得到了最好的总结，但这些想法是许多人的产物。我采用了 Pearl 的命名，贝叶斯网络，理由是这个名称对于网络的状态是完全中立的（他们真的代表信仰，因果关系或者其它东西吗？）。贝叶斯网络已应用于医学诊断中的问题（Heckerman 1990; Spiegelhalter，Franklin和Bull 1989），地图学习（Dean 1990），语言理解（Charniak和Goldman 1989a，1989b; Goldman 1990），视觉问题（Levitt，Mullin，和Binford 1989），启发式搜索（Hansson和Mayer 1989）等。实际上可以说，AI-不确定性社区的一大部分都使用了贝叶斯网络作为解决方案的 AI 逻辑论证。然而，尽管它们显然具有明显的重要性，但这些思想和技术并没有传播到相关的研究领域之外。这可能是因为这些想法和技术并不容易理解。为纠正这种情况，我希望使概率上不复杂的贝叶斯网络更容易理解。也就是说，本文试图使概率论基础有限的人可以获得基本的相关思想和理论直觉（相当于Charniak和McDermott [1985]中提出的内容）。

Over the last few years, a method of reasoning using probabilities, variously called belief networks, Bayesian networks, knowledge maps, probabilistic causal networks, and so on, has become popular within the AI probability and uncertainty community. This method is best summarized in Judea Pearl’s (1988) book, but the ideas are a product of many hands. I adopted Pearl’s name, Bayesian networks, on the grounds that the name is completely neutral about the status of the networks (do they really represent beliefs, causality, or what?). Bayesian networks have been applied to problems in medical diagnosis (Heckerman 1990; Spiegelhalter, Franklin, and Bull 1989), map learning (Dean 1990), language understanding (Charniak and Goldman 1989a, 1989b; Goldman 1990), vision (Levitt, Mullin, and Binford 1989), heuristic search (Hansson and Mayer 1989), and so on. It is probably fair to say that Bayesian networks are to a large segment of the AI-uncertainty community what resolution theorem proving is to the AIlogic community. Nevertheless, despite what seems to be their obvious importance, the ideas and techniques have not spread much beyond the research community responsible for them. This is probably because the ideas and techniques are not that easy to understand. I hope to rectify this situation by making Bayesian networks more accessible to the probabilistically unsophisticated. That is, this article tries to make the basic ideas and intuitions accessible to someone with a limited grounding in probability theory (equivalent to what is presented in Charniak and McDermott [1985]).

## Conclusions

贝叶斯网络为人工智能研究人员提供了一种方便的方法来尝试解决众多问题，在这些问题中，人们希望得出逻辑上无法保证的结论，而不是概率性的结论。此外，它们允许您在没有指定一组数字的传统障碍的情况下尝试解决这些问题，这些数字随模型的复杂性呈指数级增长。可能它们使用的主要缺点是评估时间（一般情况下的指数时间）。但是，由于现在有很多人使用贝叶斯网络，因此对有效的精确求解方法以及各种近似方案进行了大量研究。我相信贝叶斯网络或其后代是未来的潮流。

Bayesian networks offer the AI researcher a convenient way to attack a multitude of problems in which one wants to come to conclusions that are not warranted logically but, rather, probabilistically. Furthermore, they allow you to attack these problems without the traditional hurdles of specifying a set of numbers that grows exponentially with the complexity of the model. Probably the major drawback to their use is the time of evaluation (exponential time for the general case). However, because a large number of people are now using Bayesian networks, there is a great deal of research on efficient exact solution methods as well as a variety of approximation schemes. It is my belief that Bayesian networks or their descendants are the wave of the future.
