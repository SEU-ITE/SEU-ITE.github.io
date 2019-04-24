---
date: "2019-04-17T13:29:43+08:00"
publishdate: "2019-04-17+08:00"
lastmod: "2019-04-17+08:00"
draft: false
title: "FORTH - 一种交互式计算的语言"
tags: ["每日 Paper", "计算机", "blog"]
series: ["经典论著"]
categories: ["每日 Paper"]
img: "img/everday_paper/forth_a_language_for_interactive_computing.jpg"
toc: true
summary: "每天一篇计算机 Paper (2019/4/17)"
---
>H Moore, Charles & C Leach, Geoffrey. (1970). FORTH -A Language for Interactive Computing. 
>
>译者：陈思源

本文隶属于"每天一篇计算机 Paper"系列博客，更多内容请点击[这个链接](https://seuite.github.io/categories/%E6%AF%8F%E6%97%A5-paper/)。

本系列博客均非完整译文，如需阅读完整文章，请访问相关图书馆订阅。

## Abstract

FORTH 是一个将键盘与计算机连接的程序。它提供了分时用户和管理核心和磁盘内存所需的所有软件。它的核心是一个字典，它将内存划分为定义字符串，代码和数据的条目。由此产生的语言足以描述 FORTH 本身，并且足够灵活，可以进行查询。可以很容易地扩展以处理硬件允许的尽可能多的复杂应用程序。在 B-5500 上，FORTH上使用 2K 的核心，并且可以在剩余的 30 个 1K 核心区域中的每一个中表达复杂的应用。

>FORTH is a program that interfaces keyboards with computer. It provides all the software necessary to time-share users and manage core and disk memory. Its key is a dictionary that divides memory into entries that identify character strings, code and data. The resulting language is sufficiently powerful to describe FORTH itself, and sufficiently flexible to make inquiries with. It may be readily extended to handle as many, and as complex, applications as hardware permits. On the B-5500 FORTH uses 2K of core and can express a complex application in each of the 30 1K regions of core that remain.

## What is FORTH?

FORTH 是一个计算机程序。它提供终端和计算机之间的软件接口。它提供了一个与大型计算机交互的完整的软件接口。包括用户可以描述其应用程序的语言。并在其中编写 FORTH。

>FORTH is a computer program. It provides a software interface between terminal and computer. It provides a complete Software interface with a large computer. Including a language in which the user can describe his application. And in which FORTH is written.

随着大型计算机提供的软件提供了语言的层次结构; 汇编程序定义了描述编译器和管理程序的语言; 管理进程定义了工作控制的语言; 编译器定义了应用程序的语言; 应用程序定义了其输入的语言。用户可能不知道或不知道所有这些语言; 但它们在那里。它们处于他和电脑之间，限制他能做什么以及它的开销。

>The software provided with large conmputers supplies a heirarchy of languages; The assembler defines the language for describing the compiler and supervisor; the supervisor the language for job control; the compiler the language for application programs; the application program the language for its input. The user may not know, or know of, all these languages; but they are there. They stand between him and the computer, imposing their restrictions on what he can do and what it will cost.

它的成本确实如此，因为这种庞大的语言层次需要大量的人力和机器时间来进行生产，以及同样大的维护工作。记录这些程序和阅读文档的成本是巨大的。在所有这些努力之后，这些程序仍然充满了错误，使用起来很难受，并且不能使任何人满意。

>And cost it does, for this vast heirarchy of languages reguires a huge investment of man and machine time to produce, and an equally large effort to maintain. The cost of documenting these programs and of reading the documentation is enormous. And after all this effort the programs are still full of bugs, awkward to use and satisfying to no one.

我们认为，这种多层次的噩梦就是这样。我们把责任归咎于缺乏合适的语言。FORTH 提供了一种合适的语言，并且通过使用它提供终端接口的成本，工作量和效率的数量级改进。

>We maintain that this multi-level nightmare is precisely that. We place the blame upon the lack of a suitable language. FORTH provides a suitable language, and by using it an order of magnitude improvement in the cost, effort and efficiency of providing a terminal interface.

我们介绍一种键盘上的人可以与计算机交谈的语言——人机交流。反向问题不会出现。计算机以死记硬背的方式处理机器到人的通信——输出指定的回复。

>We introduce a language with which a man at a keyboard can talk to a computer - man-machine communication. The reverse problem does not arise. The computer handles machine-man communication in rote fashion-typing specified replies.

我们在人与机器之间插入FORTH并定义2个字典：人-FORTH 和 FORTH-机器。人-FORTH 字典是一个文档集合，其中的一部分教导人如何在 FORTH 中表达他的想法。

>We insert FORTH between man and machine and define 2 dictionaraies: man-FORTH and FORTH-machine. The man-FORTH dictionary is a collection of documentation - of which this is a part - that teaches the man how to express his thoughts in FORTH.

FORTH-机器词典是本文的主题，因为它是 FORTH 巨大成功的关键。

>The FORTH-machine dictionary is the subject of this paper, for it is the key to the dramatic sucess of FORTH.

## Dictionary

字典是单词与含义的关联。FORTH 的字典是一个单词列表及其定义（图1）。除了某些控制信息之外，几乎整个程序都包含在字典中。

>A dictionary is an association of words with meanings. FORTH’s dictionary is a list of words together with their definitions (Fig. 1). Almost the entire program is contained in the dictionary, excepting only certain control information.

## The Program

字典组织核心，因此构成了 FORTH 的主要组成部分。然而，大多数单词不会修改字典——它们只是驻留在那里。图 3 是 FORTH 的功能图。字典之外的主要块是扫描器和队列。请注意，虽然 FORTH 实现了一个管理进程，编译器和加载器，但这些方面无法进行本地化。

>The dictionary organizes core and thus forms a major component of FORTH. However most words do not modify the dictionary - they merely reside there. Fig. 3 is a functional diagram of FORTH. The major blocks besides the dictionary are the scanner and the queue. Notice that although FORTH implements a supervisor, compiler and loader these aspects cannot be localized.

## Dictionary Search:

在字典中查找单词涉及的不仅仅是字典的结构。搜索从稍后进行到较早的条目。这是一种便捷的搜索方式，因为可以重新定义一个单词并找到最新的定义。

>Finding a word in the dictionary involves more than the structure of the dictionary. The search proceeds from later to earlier entries. This is a convenient way to search since a word may be redefined and the latest definition found.

## The Queue:

队列的目的是在用户之间共享计算机。当用户进入系统时，他会在内存中为他的字典以及他的存在所需的缓冲区和指示符分配一个区域。这包括通知队列他的到来和他的优先级，并将他链接到适当位置的现有字典，这可能是基础系统定义或一些常驻应用程序（图7）。

>The purpose of the queue is to share the computer among users. When a user enters the system he is allotted a region in memory for his dictionary and for the buffers and indicators required by his presence. This includes notifying the queue of his arrival and of his priority and linking him into the existing dictionary at the appropriate place, which may be the basis system definitions or some resident application (Fig. 7).

## Sheets:

我们讨论过的定义远远引用了核心中的字符串。另一种定义存储在磁盘上。词组

     1017 SHEET FIT

将 FIT 声明为具有磁盘地址 1017 的工作表（SHEET）。遇到 FIT 时，扫描程序将被定向到磁盘以进一步输入。

>The definitions we have discussed to far have referenced character strings in core. Another kind of definition is stored on disk. The phrase 
>
>    1017 SHEET FIT
>
>declares FIT as a sheet with disk address 1017. When FIT is encountered, the scanner is directed to disk for further input.

## The Language

我们一直在谈论 FORTH 作为实现语言的程序，我们已经描述了向计算机解释语言的字典。但是我们没有提到语言，而是提到基本类型的单词：名词，动词和定义。

We have been speaking of FORTH as a program that implements a language and we have described the dictionary that explains the language to the computer. But we have not described the language beyond mentioning the basic kinds of words: nouns, verbs, and definitions.

## Verbs vs. Definitions:

区分两类单词是有用的：那些导致生成指令的单词和不生成指令的单词。前者仅用于描述动词的代码，后者随处可见。

It is useful to distinguish 2 classes of words: those that cause instructions to be generated and those that do not. The former are used only to describe the code for verbs, the latter are used everywhere.

## Status

FORTH 是在 1968 年秋天在 IBM 1130 上开发的。我们主要使用它在 2250 显示器范围内生成图片，这是一个轻松的任务。我们还开发了一个报告生成器，可以从顺序文件中选择，排序和打印记录，其简便性和多功能性超出了传统方法的范围。

FORTH was developed in the fall of 1968 on an IBM 1130. We used it primarily to generate pictures on the 2250 display scope, a task it handles with ease. We also developed a report generator that would select, sort and print records from sequential files with an ease and versitility beyond the range of a conventional approach.

## In Summary

FORTH 是一个将键盘与计算机连接的程序。这是一个小程序，但不适用于小型计算机。FORTH 需要大约 4K 的核心，每个应用程序（键盘）需要额外的 1K。对于源语言，它还需要大约 100K 字符的磁盘存储空间。要求并不过分，但超出了台式计算机的范围。

FORTH is a program that interfaces keyboards with computer. It is a small program, though not intended for small computers. FORTH requires about 4K of core and each application (keyboard) requires an additional 1K. It also requires perhaps 100K characters of disk storage for source language. Modest enough requirements, but beyond the scope of desk-top computers.

FORTH 实现了一种语言，使用户可以完全访问硬件功能，并可以完全自由地设计紧凑的 POL。有趣的是，FORTH 应用程序不使用下标，计数器和此类内务处理变量。它们需要非常少的数据存储——通常以数组的形式存储。它们主要由定义组成——看似无穷无尽的定义——它们易于编写且易于使用。FORTH 应用程序可以有效利用计算机资源，并可以与其他应用程序轻松共享。总之，FORTH 就是**计算机语言**。

FORTH implements a language that gives the user the complete access to hardware capabilities, and complete freedom to design a compact POL. Interestingly enough, FORTH applications do not use subscripts, counters and such housekeeping variables. They require very little data storage - usually in the form of arrays. They are composed mostly of definitions - seemingly endless nests of definitions - which are simple to write and simple to use. FORTH applications make efficient use of computer resources, and share these readily with other applications. In a word, FORTH is THE computer language.