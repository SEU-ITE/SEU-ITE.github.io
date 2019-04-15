---
date: "2019-04-15T17:14:40+08:00"
publishdate: "2019-04-10+08:00"
lastmod: "2019-04-10+08:00"
draft: false
title: "一种 APL 机器"
tags: ["每日 Paper", "计算机", "blog"]
series: ["经典论著"]
categories: ["每日 Paper"]
img: "https://i.loli.net/2019/04/06/5ca87b7dac457.jpg"
toc: true
summary: "每天一篇计算机 Paper (2019/4/15)"
---
>Philip Samuel Abrams. 1970. An Apl Machine. Ph.D. Dissertation. Stanford University, Stanford, CA, USA. AAI7022146.
- 译者：陈思源

本文隶属于"每天一篇计算机 Paper"系列博客，更多内容请点击[这个链接](https://seuite.github.io/tags/%E6%AF%8F%E6%97%A5-Paper/)。

# 摘要

本论文提出了一种适用于APL的机器结构设计，可以有效地评估该语言的程序。

This dissertation proposes a design for a machine structure which is appropriate for APL and which evaluates programs in this language efficiently. 

采用的方法是严格和分析地研究APL运算符和数据结构的语义。我们为选择表达式展示了一个可紧凑表示的标准形式，它由运算符组成，这些运算符改变了数组结构的大小和顺序。此外，我们提供了一组足以导出任何选择表达式的等效标准形式的转换。然后扩展标准表单和转换以包含包含其他APL运算符的表达式。

The approach taken is to study the semantics of APL operators and data structures rigorously and analytically. We exhibit a compactly representable standard form for select expressions, which are composed of operators which alter the size and ordering of array structures. In addition, we present a set of transformations sufficient to derive the equivalent standard form for any select expression. The standard form and transformations are then extended to include expressions containing other APL operators. 

通过将标准表单转换应用于数组的存储访问函数，可以在不必操作数组值的情况下评估机器中的选择表达式。这个过程叫做殴打。拖拽是第二个基本过程，它推迟对数组表达式的操作，通过跳动实现整个表达式的简化，并且还可以更有效地评估包含多个操作的数组表达式。

By applying the standard form transformations to storage access functions for arrays, select expressions in the machine can be evaluated without having to manipulate array values; this process is called beating. Drag-along is a second fundamental process which defers operations on array expressions, making possible simplifications of entire expressions through beating and also leading to more efficient evaluations of array expressions containing several operations. 

APL机器由两个共享相同内存和寄存器的独立子机器组成。D-machine 应用跳动和拖动来推迟简化的程序，然后 E-machine 进行评估。主要的机器寄存器是堆栈，程序被“组织成逻辑段”。

The APL machine consists of two separate sub-machines sharing the same memory and registers. The D-machine applies beating and drag-along to defer simplified programs which the E-machine then evaluates. The major machine registers are stacks, and programs are 'organized into logical segments. 

整个APL机器的性能通过将其与基于当前可用的语言实现的假想天真机器进行比较来进行分析评估。对于所检查的各种问题，APL机器在两者中效率更高，因为它使用更少的内存访问，算术运算和临时存储; 对于某些示例，改进因子与数组操作数的大小成比例。

The performance of the entire APL machine is evaluated analytically by comparing it to a hypothetical naive machine based upon presently-available implementations for the language. For a variety of problems examined, the APL machine is the more efficient of the two in that it uses fewer memory accesses, arithmetic operations, and temporary stores; for some examples, the factor of improvement is proportional to the size of array operands.

## Introduction

电子数字计算机已经从一个梦想，一个好奇的好奇心发展到现在社会中普遍存在的不可或缺的角色。 多年来，人类对计算机的使用变得越来越复杂。 特别重要的是使用高级编程语言，使问题解决者更容易使用机器。

The electronic digital computer has progressed from being a dream, to anesoteric curiosity, to its present pervasive and indispensable role in modern society. Over the years, man's uses of computers have become increasingly sophisticated. Of particular importance is the use of high-level programming languages which have made machines more accessible to problem- solvers.

通常，使用面向问题的编程语言需要相对复杂的翻译过程才能将它们呈现给机器。 虽然这可以由编译器自动完成，但是在编程语言（如ALGOL，PL / I或APL）中的高度结构化概念与当今计算机的相对原子性系统之间存在很大差距。 实际上，我们想要向机器呈现的任务类型与机器本身之间存在不匹配。 消除这种差异的一种可能方法是研究构造机器的方法，使它们更接近人们希望用它们解决的各种问题。

In general, the use of problem-oriented programming languages requires a relatively complex translation process in order to present them to machines. Although this can be done automatically by compilers, there is a wide gap to bridge between the highly-structured concepts in a programming language such as ALGOL, PL/I, or APL and the relatively atomic regime of today's computers. In effect, there exists a mismatch between the kinds of tasks we want to present to machines and the machines themselves. One possible way to eliminate this difference is to investigate ways of structuring machines to bring them closer to the kinds of problems people wish to solve with them.

### A. A Programming Language (APL)

APL基于K.E. Iverson的工作（Iverson [1962]），其中与现代机器不匹配的特定编程语言尤为明显。 APL是一种简洁，高度数学的编程语言，旨在处理数组结构化数据。 APL程序通常包含表达式，其中数组作为操作数并且对数组求值，而大多数其他语言要求逐个元素地表示数组操作。为了补充其使用数组作为操作数，APL具有丰富的运算符，便于进行数组计算。此外，它在语法和语义上都是高度一致的，因此可以称为“数学”。由于结构化数据的使用及其与经典数字计算机完全不同的原语集，APL不适合普通机器。有可能这样做，并且已经为至少三种不同的机器编写了解释器（Abrams [1966]; Berry [1968]; Pakin [1968]）。最后，由于其数学属性，可以严格地讨论语言的语义，并得出关于语言中表达式的重要正式结果。

A particular programming language in which this mismatch with contemporary machines is especially obvious is APL, based on the work of K. E. Iverson (Iverson [1962]). APL is a concise, highly mathematical programming language designed to deal with array-structured data. APL programs generally contain expressions with arrays as operands and which evaluate to arrays, while most other languages require that array manipulations be expressed element-by-element. To complement its use of arrays as operands, APL is rich in operators which facilitate array calculations. Also, it is highly consistent internally both syntactically and semantically, and hence could be called "mathematical". Because of .its use of structured data and its set of primitives which are quite different from those of a classical digital computer, APL does not fit well onto ordinary machines. It is possible to do so, and interpreters have been written for at least three different machines (Abrams [1966]; Berry [1968]; Pakin [1968]). Finally, because of its mathematical properties, it is possible to discuss the semantics of the language rigorously and to derive significant formal results about expressions in the language.

### B. The Problem

本文研究的问题是设计一种适合APL的机器结构。这里的“机器结构”是指一般的功能方案，而不是详细的逻辑设计。预期结果不是电路设计者可以从中产生工作设备的一组规范，而是一种上层结构，其中语言的特征适合于干净利落。因此，这种设计在某种意义上必须是语言的自然。例如，原始操作和数据结构应包括APL的操作和数据结构。此外，机器应利用所有可用信息，以便尽可能高效地执行程序。我们在广义上使用“机器”这个词：它在这里的真正含义是“算法”，而不一定是任何特定的物理设备。这种机器可以实现为传统程序或硬连线设备或适当系统中的微程序。出于这项工作的目的，它并不重要。

The problem considered in this dissertation is to design a machine structure which is appropriate to APL. "Machine structure" here means a general functional scheme and not a detailed logical design. The expected result is not a set of spec.ifications from which a circuit designer could produce a working device, but rather a superstructure into which the features of the language fit cleanly. Thus, this design must in some sense be natural for the language. For example, the primitive operations and data structures should include those of APL. In addition, the machine should take advantage of all available information in order to execute programs as efficiently as possible. We use the word "machine" in a very broad sense: what it really means here is "algorithm" and not necessarily any particular physical device. Such a machine could be implemented as a conventional program or as a hardwired device or as a microprogram in an appropriate system. For the purposes of this work, it doesn't really matter.

“APL”表示包含APL \ 360（Pakin [1968]）语义的任何编程语言。 我们不会关注APL的特定语法，尽管这似乎是表示语言语义概念的最佳方式。 简而言之，机器应该能够轻松处理阵列结构化数据，并且应该能够使用APL的运算符作为基本原语来评估这些数据的函数。

"APL" means any programming language which includes the semantics of APL\360 (Pakin [1968]). We shall not be concerned with the particular syntax of APL, although this currently appears to be the best way to represent the semantic ideas of the language. In short, the machine should be able to handle array-structured data with ease and should be able to evaluate functions on such data using the operators of APL as basic primitives.

所采取的方法是投入大量精力来分析APL的操作员和数据结构的数学特性，并将这些结果用于机器的设计。 因此，这项工作的主要部分将致力于对APL表达的严格的数学研究。 本研究载于第二章。 在第三章中，第二章的工作涉及机器的设计，并详细阐述了设计目标。 第四章讨论了所提出的机器设计，第五章是关于第三章目标的机器评估。

The approach taken is to invest a considerable amount of effort in the analysis of the mathematical properties of the operators and data structures of APL and to exploit these results in the design of the machine. Thus, a major part of this work will be dedicated to a rigorous, mathematical investigation of APL expressions. This study is contained in Chapter II. In Chapter III, the work of Chapter II is related to the design of a machine, and the design goals are set forth in detail. Chapter IV discusses the proposed machine design, and Chapter V is an evaluation of the machine with respect to the goals of Chapter III.

应该强调的是，设计APL机器的目标是相当广泛的。 虽然这种设计有明显的实际应用，但这不是这项工作的主要重点。 相反，我们希望通过详细研究这种语言和机器，可以了解计算中的基本过程，并找到在机器结构中反映这些过程的方法。 第六章总结的结果和这项工作提出的新研究问题表明，这一目标已经实现。

It should be emphasized that the goal of designing an APL machine is a rather broad one. Although there are clearly practical applications of such a design, that is not the major focus of this work. Rather, we hope that by investigating this language and machine in detail, it will be possible to learn something about the basic processes in computing and find ways of reflecting these processes in a machine structure. The results summarized in Chapter VI and the new research problems suggested by this work indicate that this goal has been fulfilled.

### C. Historical Perspective

出于本论文的目的，我们主要关注语言导向机器设计领域的先前工作（McKeemanQ..967J; Barton [1965]）。 在某种程度上，所有机器设计都可以被认为是语言导向的，因为人们希望在一个硬件中实现某种特定的（机器）语言。 但是，让我们只考虑一类可能被称为“更高语言启发”的机器; 也就是说，以某种方式基于能够在比通常与汇编代码相关联的更高级别表达概念的语言的机器。

For the purposes of this dissertation, we are primarily interested in previous work in the area of language-directed machine design (McKeemanQ..967J; Barton [1965]). To some extent, all machine design can be considered to be language-directed, in that one wishes to implement some particular (machine) language in a piece of hardware. However, let us consider only the class of machines which might better be called "higher language inspired"; that is, machines which are based in some way on languages capable of expressing concepts at a higher level than are normally associated with assembly code.

1954年报道了第一台这样的机器，它是一种能够直接评估逻辑表达式的中继设备（Burks，Warren和Wright（1954）。此外，这台机器使用无括号（波兰）表示法的输入，从而使其加倍 历史兴趣。逻辑机器代表了一类主要的语言启发机器设计，其机器语言与高级源语言相同。另一类主要的语言启发设计更关注语言的语义处理。 源语言，而不是直接接受机器的确切语言。实际上，大多数设计都介于两个极端之间，因为即使那些接受源语言的设计也直接对其进行一些初步转换以产生更简单的中间语言。

The first such machine was reported in 1954, and was a relay device capable of directly evaluating logical expressions (Burks, Warren, and Wright (1954). In addition, this machine used input in parenthesis-free (Polish) notation, thus doubling its historical interest. The logic machine typifies one major class of language-inspired machine designs in that its machine language is identical to the high-level source language. The other major class of language-inspired designs is more concerned with the processing of the semantics of the source language, rather than direct acceptance of the exact language by the machine. In fact, most designs fall between the two extremes, as even those which accept the source language directly do some preliminary transformations on it to produce a simpler intermediate language.

其他受语言启发的机器直接接受源语言包括ALGOL 60机器（Anderson [1961]），两台FORTRAN机器（Bashkow，Sasson和Kronfeld [1967];墨尔本和Pugmire [1965]），ADAM机器，基于特殊 符号导向的语言（Mullery，Schauer和Rice [1963J; Meggitt [1964]），以及EULER的机器，ALGOL的概括（Weber [1967]）。 在这些装置中，一些装置用硬件实现（例如，Bashkow等人; Mullery等人），而其他装置用微程序（Meggitt; Weber）实现。

Other language-inspired machines accepting source language directly include an ALGOL 60 machine (Anderson [1961]), two FORTRAN machines (Bashkow, Sasson and Kronfeld [1967]; Melbourne and Pugmire [1965]), the ADAM machine, based on a special symbol-oriented language (Mullery, Schauer and Rice [1963J; Meggitt [1964]), and a machine for EULER, a generalization of ALGOL (Weber [1967]). Of these devices, some were to be implemented in hardware (e.g., Bashkow et al.; Mullery et al.) while others were implemented in microprogram (Meggitt; Weber).

在机器语言与高级语言明显不同的情况下，更关注语义处理的机器包括Burroughs BSOOO（Barton [1961]; Burroughs [1963]），它本质上是一台ALGOL机器，一台PL / I 机器（Sugimoto [1969]和莱斯大学计算机（lliffe和Jadeit [1962]）。 该领域目前的工作包括PL / I机器（Wortman（1970）和能够轻松模拟高级过程的微型计算机（Lesser [1969]）。

Machines which are more concerned with semantic processing to the extent that their machine languages are significantly different from a higher-level language include the Burroughs BSOOO (Barton [1961]; Burroughs [1963]) which is essentially an ALGOL machine, a PL/I machine (Sugimoto [1969) and the Rice University computer (lliffe and Jadeit [1962). Current work in this area includes a PL/I machine (Wortman (1970) and a micro-computer capable of emulating high-level processes easily (Lesser [1969]).

这些努力中的大多数与本论文的工作没有直接关系，因此这里只是为了完整性而报告。 所有这些设计的共同方面是它们关注的是处理比传统的冯·诺依曼式架构中更高度组织的信息和程序。 其中大多数包括使用描述符的一些修改的通用寻址方案，以及至少一个堆栈。

Most of these efforts are not directly relevant to the work in this dissertation and are thus reported here only for completeness. The common aspect of all these designs is that they are concerned with the processing of more highly organized information and programs than are found in the conventional von Neumann type architectures. Most of them include generalized addressing schemes using some modification of descriptors, as well as at least one stack.

尽管Burks，Warren和Wright机器是第一个使用波兰表示法作为机器语言的机器，但第一批商业化生产的设备显然是英国电气KDF9（Davis [1960]和Burroughs B5000）。 这两台机器都包括堆栈。 尚未提及的其他相关工作是基于较低级机器语言的两台机器，但旨在处理高级原语。 其中之一（Iliffe [1968]基于广泛使用描述符逻辑用于程序和数据，而另一个（Myamlin和Smirnov [1968]更倾向于更高级别的语言。 特别是后者，对中缀算术表达式进行运行时评估。

Although the Burks, Warren, and Wright machine was the first to use Polish notation as a machine language, the first commercially produced devices to do so apparently were the English Electric KDF9 (Davis [1960) and the Burroughs B5000. Both of these machines included stacks. Other related efforts not yet mentioned are two machines based on lower-level machine languages, but intended to deal with high-level primitives. One of these (Iliffe [1968) is based on extensive use of descriptor logic for both programs and data, while the other (Myamlin and Smirnov [1968) is somewhat more clQsely oriented toward higher-level languages. The latter, in particular, does run-time evaluation of infix arithmetic expressions.

除了Burks等人的工作之外，文献中的设计似乎都不是源于对输入语言的明确数学分析。 此外，除了模拟或实际表现之外，文献中没有一篇论文对其设计提出令人满意的评价。 这并不是说设计不令人满意：相反，Burroughs系列计算机和KDF9的成功表明，语言启发式设计是开发新机器的可行方法。 另一方面，似乎没有人确定这些设计到底有多可行。

Aside from the work of Burks et al: , none of the designs in the literature seem to be derived from explicit mathematical analysis of their input languages. Further, except for simulations or actual performance, none of the papers in the literature present satisfactory evaluations of their designs. This is not to say that the designs are not satisfactory: to the contrary, the success of the Burroughs family of computers and the KDF9 show that language-inspired designs are a viable approach to the development of new machines. On the other hand, nobody seems to have established exactly how viable such designs really are.

### D. Conclusion

简要回顾了迄今为止语言启发的机器设计的发展，现在可以将它们留在后台。 本方法与过去的方法不同，它基于对源语言语义的数学分析。 此外，对所得设计的评估是分析性的，并且将该APL机器与其他类似设备进行了清晰的比较。 当然，与过去的设计有相似之处。 特别是，程序段，数据描述符和堆栈的使用本身并不新颖，尽管这里开发的机器与上一节中提到的机器有很大不同。

Having briefly reviewed the developments of language-inspired machine design to date, they can now be left in the background. The present approach is different from those in the past in that it is based on a mathematical analysis of the semantics of the source language. Also, the evaluation of the resulting design is analytic, and gives a clear comparison of this APL machine to other similar devices. There are, of course, similarities to the designs of the past. In particular, the use of program segments, data descriptors, and stacks is not novel in itself, although the machine developed here is substantially different from those mentioned in the last section.

