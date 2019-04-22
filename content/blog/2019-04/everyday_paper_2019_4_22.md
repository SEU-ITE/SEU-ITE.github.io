---
date: "2019-04-22T19:07:30+08:00"
publishdate: "2019-04-22+08:00"
lastmod: "2019-04-22+08:00"
draft: false
title: "FORTH - 一种交互式计算的语言"
tags: ["每日 Paper", "计算机", "blog"]
series: ["经典论著"]
categories: ["每日 Paper"]
img: "img/everday_paper/forth_a_language_for_interactive_computing.jpg"
toc: true
summary: "每天一篇计算机 Paper (2019/4/22)"
---
>F. Codd, E. (1970). A Relational Model of Data for Large Shared Data Banks. Commun. ACM. 13. 377-387. 10.1007/978-3-642-48354-7_4. 
>
>译者：陈思源

本文隶属于"每天一篇计算机 Paper"系列博客，更多内容请点击[这个链接](https://seuite.github.io/tags/%E6%AF%8F%E6%97%A5-Paper/)。

本系列博客均非完整译文，如需阅读完整文章，请访问相关图书馆订阅。

译者说：没有关系代数，人类将会怎样？Codd 划时代的论文奠定了现代数据库的基础。顺便说一句，现在的 ORM 试图把 data schema 和对象系统映射起来。问题是，data schema 只是对关系的一种表达方式而已，还和具体的系统实现有关。也许把对象间的结构和关系映射起来才是正道。

## Abstract

必须保护大型数据库的未来用户不必知道数据在机器中的组织方式（内部表示）。提供这种信息的提示服务不是令人满意的解决方案。当数据的内部表示发生变化时，即使外部表示的某些方面发生变化，终端和大多数应用程序的用户活动也不会受到影响。数据表示是需要经常更改的，因为查询，更新和报告流量会发生变化，存储信息类型也会自然增长。

>Future users of large data banks must be protected from having to know how the data is organized in the machine (the internal representation). A prompting service which supplies such information is not a satisfactory solution. Activities of users at terminals and most application programs should remain unaffected when the internal representation of data is changed and even when some aspects of the external representation are changed. Changes in data representation will often be needed as a result of changes in query, update, and report traffic and natural growth in the types of stored information. 

现有的非推理格式化数据系统为用户提供树状结构文件或稍微更一般的数据网络模型。在第 1 节中，讨论了这些模型的不足之处。基于 n 元关系的模型，一种正常形式。对于数据库关系，引入了通用数据子语言的概念。在第 2 节中，讨论了关系（逻辑推理除外）的某些操作，并将其应用于用户模型中的冗余和一致性问题。

>Existing noninferential, formatted data systems provide users with tree-structured files or slightly more general network models of the data. In Section 1, inadequacies of these models are discussed. A model based on n-ary relations, a normal form for data base relations, and the concept of a universal data sublanguage are introduced. In Section 2, certain opera- tions on relations (other than logical inference) are discussed and applied to the problems of redundancy and consistency in the user’s model. 

## 1. Introduction

本文涉及基本关系理论在系统中的应用，这些系统提供对大量格式化数据库的共享访问。除了 Childs 的论文[1]，关系到数据系统的主要应用是演绎问答系统。Levein 和 Maron[2]为这一领域的工作提供了大量参考.

>This paper is concerned with the application of elementary relation theory to systems which provide shared access to large banks of formatted data. Except for a paper by Childs [l], the principal application of relations to data systems has been to deductive question-answering systems. Levein and Maron [2] provide numerous references to work in this area. 

相比之下，这里处理的问题是数据独立性 - 应用程序和终端活动的独立性，数据类型的增长和数据表示的变化，以及某些类型的数据不一致，即使在非负面系统中也会变得麻烦。

>In contrast, the problems treated here are those of data independence - the independence of application programs and terminal activities from growth in data types and changes in data representation Ñ and certain kinds of data inconsistency which are expected to become troublesome even in nondeductive systems.

第 1 节中描述的数据的关系视图（或模型）似乎在几个方面优于目前非推理系统流行的图形或网络模型[3,4]。它提供了一种仅使用其自然结构来描述数据的方法——也就是说，不会为机器表示姿势叠加任何其他结构。因此，它为高级数据语言提供了基础，该语言一方面在程序之间产生最大的独立性，另一方面在机器表示和数据组织方面产生最大的独立性。

>The relational view (or model) of data described in Section 1 appears to be superior in several respects to the graph or network model [ 3 , 4 ] presently in vogue for non-inferential systems. It provides a means of describing data with its natural structure only -- that is, without superimposing any additional structure for machine representation poses. Accordingly, it provides a basis for a high level data language which will yield maximal independence between programs on the one hand and machine representation and organization of data on the other.

关系视图的另一个优点是它为处理关系的可导性，冗余和一致性奠定了坚实的基础 - 这些将在第2节中讨论。另一方面，网络模型产生了许多混淆，其中最重要的是错误地推导出用于推导关系的连接（参见第 2 节关于“连接陷阱”的评论）。

>A further advantage of the relational view is that it forms a sound basis for treating derivability, redundancy, and consistency of relations - these are discussed in Section 2.The network model, on the other hand, has spawned a number of confusions, not the least of which is mistaking the derivation of connections for the derivation of relations (see remarks in Section 2 on the "connection trap" ).

最后，关系视图允许更清楚地评估当前格式化数据系统的范围和逻辑限制，以及单个系统内数据的竞争表示的相对优点（从逻辑角度来看）。本文的各个部分都引用了这种更清晰的视角的例子。没有讨论支持关系模型的系统实现。

Finally, the relational view permits a clearer evaluation of the scope and logical limitations of present formatted data systems, and also the relative merits (from a logical standpoint) of competing representations of data within a single system.Examples of this clearer perspective are cited in various parts of this paper.Implementations of systems to support the relational model are not discussed.