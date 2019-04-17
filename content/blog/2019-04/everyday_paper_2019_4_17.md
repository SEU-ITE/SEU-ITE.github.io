---
date: "2019-04-17T13:29:43+08:00"
publishdate: "2019-04-17+08:00"
lastmod: "2019-04-17+08:00"
draft: true
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

本文隶属于"每天一篇计算机 Paper"系列博客，更多内容请点击[这个链接](https://seuite.github.io/tags/%E6%AF%8F%E6%97%A5-Paper/)。

本系列博客均非完整译文，如需阅读完整文章，请访问相关图书馆订阅。

## Abstract

FORTH是一个将键盘与计算机连接的程序。 它提供了分时用户和管理核心和磁盘内存所需的所有软件。 它的关键是一个字典，它将内存划分为识别字符串，代码和数据的条目。 由此产生的语言足以描述FORTH本身，并且足够灵活，可以进行查询。 可以很容易地扩展以处理硬件允许的尽可能多的复杂应用程序。 在 B-5500 上，FORTH上使用2K的核心，并且可以在剩余的30个1K核心区域中的每一个中表达复杂的应用。

FORTH is a program that interfaces keyboards with computer. It provides all the software necessary to time-share users and manage core and disk memory. Its key is a dictionary that divides memory into entries that identify character strings, code and data. The resulting language is sufficiently powerful to describe FORTH itself, and sufficiently flexible to make inquiries with. It may be readily extended to handle as many, and as complex, applications as hardware permits. On the B-5500 FORTH uses 2K of core and can express a complex application in each of the 30 1K regions of core that remain.

## What is FORTH?

FORTH is a computer program. It provides a software interface between terminal and computer. It provides a complete Software interface with a large computer. Including a language in which the user can describe his application. And in which FORTH is written.

The software provided with large conmputers supplies a heirarchy of languages; The assembler defines the language for describing the compiler and supervisor; the supervisor the language for job control; the compiler the language for application programs; the application program the language for its input. The user may not know, or know of, all these languages; but they are there. They stand between him and the computer, imposing their restrictions on what he can do and what it will cost.
And cost it does, for this vast heirarchy of languages reguires a huge investment of man and machine time to produce, and an equally large effort to maintain. The cost of documenting these programs and of reading the documentation is enormous. And after all this effort the programs are still full of bugs, awkward to use and satisfying to no one.
We maintain that this multi-level nightmare is precisely that. We place the blame upon the lack of a suitable language. FORTH provides a suitable language, and by using it an order of magnitude improvement in the cost, effort and efficiency of providing a terminal interface.

FORTH-1We introduce a language with which a man at a keyboard can talk to a computer - man-machine communication. The reverse problem does not arise. The computer handles machine-man communication in rote fashion-typing specified replies.
We insert FORTH between man and machine and define 2 dictionaraies: man-FORTH and FORTH-machine. The man-FORTH dictionary is a collection of documentation - of which this is a part - that teaches the man how to express his thoughts in FORTH.
The FORTH-machine dictionary is the subject of this paper, for it is the key to the dramatic sucess of FORTH.

## Dictionary

A dictionary is an association of words with meanings. FORTH’s dictionary is a list of words together with their definitions (Fig. 1). Almost the entire program is contained in the dictionary, excepting only certain control information.

## The Program

The dictionary organizes core and thus forms a major component of FORTH. However most words do not modify the dictionary - they merely reside there. Fig. 3 is a functional diagram of FORTH. The major blocks besides the dictionary are the scanner and the queue. Notice that although FORTH implements a supervisor, compiler and loader these aspects cannot be localized.

## Dictionary Search:

Finding a word in the dictionary involves more than the structure of the dictionary. The search proceeds from later to earlier entries. This is a convenient way to search since a word may be redefined and the latest definition found.

## The Queue:

The purpose of the queue is to share the computer among users. When a user enters the system he is allotted a region in memory for his dictionary and for the buffers and indicators required by his presence. This includes notifying the queue of his arrival and of his priority and linking him into the existing dictionary at the appropriate place, which may be the basis system definitions or some resident application (Fig. 7).

## Sheets:

The definitions we have discussed to far have referenced character strings in core. Another kind of definition is stored on disk. The phrase 

    1017 SHEET FIT

declares FIT as a sheet with disk address 1017. When FIT is encountered, the scanner is directed to disk for further input.

## The Language

We have been speaking of FORTH as a program that implements a language and we have described the dictionary that explains the language to the computer. But we have not described the language beyond mentioning the basic kinds of words: nouns, verbs, and definitions.

## Verbs vs. Definitions:

It is useful to distinguish 2 classes of words: those that cause instructions to be generated and those that do not. The former are used only to describe the code for verbs, the latter are used everywhere.

## Status

FORTH was developed in the fall of 1968 on an IBM 1130. We used it primarily to generate pictures on the 2250 display scope, a task it handles with ease. We also developed a report generator that would select, sort and print records from sequential files with an ease and versitility beyond the range of a conventional approach.

## In Summary

FORTH is a program that interfaces keyboards with computer. It is a small program, though not intended for small computers. FORTH requires about 4K of core and each application (keyboard) requires an additional 1K. It also requires perhaps 100K characters of disk storage for source language. Modest enough requirements, but beyond the scope of desk-top computers.

FORTH implements a language that gives the user the complete access to hardware capabilities, and complete freedom to design a compact POL. Interestingly enough, FORTH applications do not use subscripts, counters and such housekeeping variables. They require very little data storage - usually in the form of arrays. They are composed mostly of definitions - seemingly endless nests of definitions - which are simple to write and simple to use. FORTH applications make efficient use of computer resources, and share these readily with other applications. In a word, FORTH is THE computer language.