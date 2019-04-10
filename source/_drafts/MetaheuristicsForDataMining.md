---
title: 每天一篇计算机 Paper(2019/4/10)
date: 2019-04-10 15:44:18
tags: 
 - 每日 Paper
 - 研究生
---

# Metaheuristics for data mining

## 用于数据挖掘的元启发式方法

## 1. Introduction

大数据的概念为所有类型的数据分析方法提供了巨大的机遇和挑战。特别是，可以处理大问题的优化方法非常适合分析这些数据。实际上，正如将要示出的，许多数据挖掘任务可以被建模为组合优化问题。本文的目的是演示数据挖掘和优化之间的联系，并介绍一些最近在这个主题上进行的工作，特别是使用元启发式。本文将提供足够的信息来向读者介绍这些方法。本文是在2016年出版了一本关于这一主题的书（Dhaenens and Jourdan 2016）。 我们推荐那些希望在本书后面获得更深入信息的读者。但是，我们在此提供更新的参考资料和对当前趋势的分析。

The concept of big data offers great opportunities and challenges for all types of data analysis approaches. In particular, optimization approaches that can handle large problems are well suited to analyze such data. Indeed, as it will be shown, many data mining tasks may be modeled as combinatorial optimization problems. The aim of this article is to demonstrate the links between data mining and optimization, and to present some of the recent works that have been conducted on this subject, especially using metaheuristics. This article will provide enough information to educate a reader on such approaches. This article follows the publication of a book in 2016 concerning this subject (Dhaenens and Jourdan 2016). We refer readers who wish to gain deeper information subsequently to this book. However, we herein offer updated references and an analysis of the current trends.

### 1.1 Big data context

可以为术语大数据提出许多定义。 最常用的是基于三个（或五个）Vs定义：体积，多样性和速度，以及准确性和价值特征。 大数据在大数据流程的不同阶段提供了大量新的技术挑战（Laney 2001; Nunez和Attoh-Okine 2014）。 我们不会在此考虑数据生成和采集阶段所带来的挑战，也不会考虑可能删除异常值的存储或数据预处理，例如替换丢失的数据以准备要分析的数据。 但是，我们将重点关注旨在提取知识的数据分析阶段。

Many definitions can be proposed for the term big data. The most commonly used are based on the three (or five) Vs definition: Volume, Variety, and Velocity, as well as Veracity and Value characteristics. Big data offers plenty of new technical challenges at different phases ofthe big data process (Laney 2001; Nunez and Attoh-Okine 2014). We will not consider herein the challenges resulting from the data generation and the acquisition phase, nor the storage or the data preprocessing that may remove outliers, replace missing data, for example, in order to prepare data to be analyzed. However, we will focus on the data analysis phase that aims at extracting knowledge. 

数据库中的知识发现（KDD）是从大型数据集中识别有效，新颖，有用且易于理解的模式的过程。 数据挖掘是KDD过程的数学核心，涉及推断算法，探索数据，开发数学模型，发现重要模式（隐式或显式），这是有价值知识的本质（Maimon和Rokach 2010）。

Knowledge Discovery in Databases (KDD) is the process of identifying valid, novel, useful, and understandable patterns from large datasets. Data mining is the mathematical core of the KDD process, involving the inferring algorithms that explore the data, develop mathematical models, and discover significant patterns (implicit or explicit), which are the essence of valuable knowledge (Maimon and Rokach 2010).

与传统数据相比，大数据在五个V方面有所不同。 使用传统的数据分析工具分析大数据变得很困难，并引入了大数据挖掘这一术语（Che et al.2013）。

In contrast to traditional data, big data varies in terms of the five V’s. It becomes difficult to analyze big data with traditional data analytics tools, and the term big data mining has been introduced (Che et al. 2013). 

诸如Hadoop和MapReduce等技术改进已经允许大数据的开发，以及大数据的元启发式（Barba-Gonzaléz等人2017）。 Hadoop是一个开源框架，依赖于Java并支持分布式计算环境中的大数据处理（Shvachko等人，2010）。 MapReduce是一种编程模型，是处理和生成适用于各种实际任务的大型数据集的相关实现。 用户根据map和reduce函数指定计算，底层运行时系统自动在大型机器集群中并行化计算（Dean和Ghemawat 2008）。

Technological improvements such as Hadoop and MapReduce have allowed the development of big data, as well as metaheuristics for big data (Barba-Gonzaléz et al. 2017). Hadoop is an open-source framework that relies on Java and supports large data processing in distributed computing environments (Shvachko et al. 2010). MapReduce is a programming model and an associated implementation for processing and generating large datasets that is amenable to a broad variety of real-world tasks. Users specify the computation in terms of a map and a reduce function, and the underlying runtime system automatically parallelizes the computation across large-scale clusters of machines (Dean and Ghemawat 2008).

### 1.2 Primary data mining tasks

如前所述，数据挖掘是KDD过程的数学核心。 数据挖掘任务可以分为两类：预测（或监督）和描述（或无监督）任务。 受监督的任务学习可用数据以预测新数据，而无监督任务提供数据和现有关系的描述。 主要数据挖掘任务，如图1所示，如下：

As indicated before, data mining is the mathematical core of the KDD process. Data mining tasks can be classified into two categories: predictive (or supervised) and descriptive (or unsupervised) tasks. The supervised tasks learn on available data to predict for new data, whereas unsupervised tasks provide a description of the data and existing relationships. Primary data mining tasks, as depicted in Fig. 1, are as follows: 

- 聚类（也称为无监督分类） - 将数据集分解或分组为组，使得组中的元素彼此相似，并且尽可能与其他组的元素不同。
- 关联规则挖掘 - 提取描述不同元素的特征之间的关系。
- （监督）分类 - 构建模型以根据其他特征的已知值预测目标特征（类）的未知值。
- 特征选择 - 通过选择有意义的特征来减小数据集的大小。

- Clustering (also called unsupervised classification)—to decompose or partition a dataset into groups such that elements in a group are similar to each other, and are as different as possible from elements of other groups.
- Association rule mining—to extract relationships between features describing different elements.
- (supervised) Classification—to build a model to predict the unknown value of a target feature (the class) from the known values of other features.
- Feature selection—to reduce the size of the dataset by selecting meaningful features.

### 1.3 Some optimization problems

如上所述，数据挖掘任务适应诸如将元素分配给类，元素分组和特征选择之类的操作。 一旦可以定义优化标准，所有这些问题可以被表述为组合优化问题。 因此，已经提出了许多使用优化方法来解决数据挖掘问题的工作，如以下评论中所述（Olafsson等人2008; Meisel和Mattfeld 2010; Corne等人2012）。

As explained above, datamining tasks accommodate operations such as the assignment of an element to a class, the grouping of elements, and the selection of features. All of these problems may be formulated as combinatorial optimization problems, as soon as an optimization criterion may be defined. Hence, numerous works using optimization methods to solve data mining problems have been proposed, as described in the following reviews (Olafsson et al. 2008; Meisel and Mattfeld 2010; Corne et al. 2012).

### 1.4 Metaheuristics

但是，大数据的背景使得使用精确方法难以解决这些问题。 因此，metaheuristics提供了一个有趣的选择。 在他们的书中，Maimon等人。 专注于软计算以进行知识发现（Maimon和Rokach 2007）。 不同的章节提出了不同的方法，很大一部分涉及元启发式，特别是进化算法和群体智能。 在他的书中，Freitas专注于使用进化算法进行数据挖掘和知识发现，这些算法代表了元启发式的一部分（Freitas 2008,2013）。 特别是，这些书籍描述了如何使用进化算法进行数据准备，规则发现（包括模糊规则）或聚类。 让我们注意一章专门用于扩展此类算法以适应大型数据集。 最近，我们在大数据背景下提出了一本致力于元启发式的书（Dhaenens和Jourdan 2016）。

However, the context of big data makes it difficult to solve those problems using exact approaches. Hence, metaheuristics provide an interesting option. In their book, Maimon et al. focused on soft computing for knowledge discovery (Maimon and Rokach 2007). Different chapters present different approaches, and a large part pertains to metaheuristics, in particular, evolutionary algorithms and swarm intelligence. In his books, Freitas focused on data mining and knowledge discovery with evolutionary algorithms, which represent one part of metaheuristics (Freitas 2008, 2013). In particular, these books describe how evolutionary algorithms may be used as well for data preparation, rule discovery (including fuzzy rules), or clustering. Let us remark that one chapter is dedicated to the scaling of such algorithms to accommodate large datasets. More recently, we proposed a book dedicated to metaheuristics in the context of big data (Dhaenens and Jourdan 2016). 

因此，本文的其余部分将针对上面提出的四个主要数据挖掘任务（聚类，关联规则，分类和特征选择），如何使用元启发式而特别关注大数据。 因此，对于每个数据挖掘任务，将首先给出描述。 随后，描述了作为组合优化问题的问题的表达。 最后，将介绍为此任务提出的主要元启发式的概述。 每个部分最后将简要介绍当前的趋势。

Hence, the remainder of this article will present, for the four primary data mining tasks presented above (clustering, association rules, classification, and feature selec-tion), how metaheuristics have been used with a particular focus on big data. Thus, for each data mining task, a description will be given first. Subsequently, the expression of the problem as a combinatorial optimization problem is described. Finally, an overview of the primary metaheuristics proposed for this task will be presented. Each part will end with a brief conclusion on the current trends.