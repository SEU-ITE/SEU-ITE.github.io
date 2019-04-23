
date: "20190423T16:07:30+08:00"
publishdate: "20190423+08:00"
lastmod: "20190423+08:00"
draft: false
title: "一个用于大型共享数据库的数据关系模型"
tags: ["每日 Paper", "计算机", "blog"]
series: ["经典论著"]
categories: ["每日 Paper"]
img: "img/everday_paper/the_unix_timesharing_system.jpg"
toc: true
summary: "每天一篇计算机 Paper (2019/4/23)"

>M. Ritchie, Dennis & Thompson, Ken. (1974). The UNIX timesharing system. Commun. ACM. 17. 365375. 10.1145/357980.358014. 
>
>译者：陈思源

本文隶属于"每天一篇计算机 Paper"系列博客，更多内容请点击[这个链接](https://seuite.github.io/tags/%E6%AF%8F%E6%97%A5Paper/)。

本系列博客均非完整译文，如需阅读完整文章，请访问相关图书馆订阅。

译者注：大家都非常熟悉 Unix 了，这是它诞生的故事。

## Abstract

也许 Unix 的最重要的成就是证明一个强大的交互式使用操作系统无论是在设备上还是在人力方面都不需要昂贵的开销：它可以在只需 40,000 美元的硬件上运行，并且开发其主要系统软件的花费不到两个人年。然而，我们希望用户发现这个系统最重要的特征是其简洁、优雅和易用性。

>Perhaps the most important achievement of Unix is to demonstrate that a powerful operating systemfor interactive use need not be expensive either in equipment or in human effort: it can run on hardwarecosting as little as $40,000, and less than two manyears were spent on the main system software. Wehope, however, that users find that the most important characteristics of the system are its simplicity elegance, and ease of use.

除了合适的操作系统，Unix 下的一些主要程序是
 C 语言编译器
 基于 QED 的文本编辑器
 汇编程序，链接加载程序，符号调试程序
 排版和公式设定程序[2,3]
 数十种语言，包括Fortran 77，Basic，Snobol，APL，Algol 68，M6，TMG，Pascal

>Besides the operating system proper, some major programs available under Unix are

> C compiler
> Text editor based on QED[1];
> Assembler, linking loader, symbolic debugger
> Phototypesetting and equation setting programs[2, 3]
> Dozens of languages including Fortran 77, Basic, Snobol, APL, Algol 68, M6, TMG, Pascal

这里有大量的维护，实用，娱乐和新奇程序。Unix 用户社区数以千计，贡献了更多的程序和语言。值得注意的是，该系统完全是自我支持的。所有 Unix 软件都在系统上维护;同样地，本文和本期中的所有其他文档都是由 Unix 编辑器和文本格式化程序生成和格式化的。

>There is a host of maintenance, utility, recreation and novelty programs, all written locally. The Unix usercommunity, which numbers in the thousands, has contributed many more programs and languages. It isworth noting that the system is totally selfsupporting. All Unix software is maintained on the system; likewise, this paper and all other documents in this issue were generated and formatted by the Unix editor andtext formatting programs.

译者注：1-7 节的内容各位读者将在本科、研究生、博士生的操作系统课中掌握的不能更好了。

## VIII. PERSPECTIVE

也许矛盾的是，Unix 系统的成功很大程度上归功于它没有设计成满足任何预定义的目标。第一个版本是在我们其中一个人（汤普森）对可用的计算机设备不满意的情况下编写的，他们发现了一个很少使用的 PDP7 并着手创造一个更友好的环境。这种（基本上是个人的）努力足以获得其他作者和几位同事的兴趣，后来证明了 PDP11/20 的实现，特别是支持文本编辑和格式化系统。当反过来 11/20 已经不合时宜时，该系统目前的形式足以说服管理层投资 PDP11/45，后来又投资于 PDP11/70 和 Interdata 8/32 机器。我们在整个工作过程中的目标一直是与机器建立舒适的关系，并在操作系统和其他软件中探索和创新。我们没有面对满足别人要求的需要，为了这种自由，我们感激不尽。

>Perhaps paradoxically, the success of the Unix system is largely due to the fact that it was notdesigned to meet any predefined objectives. The first version was written when one of us (Thompson), dissatisfied with the available computer facilities, discovered a littleused PDP7 and set out to create a morehospitable environment. This (essentially personal) effort was sufficiently successful to gain the interest ofthe other author and several colleagues, and later to justify the acquisition of the PDP11/20, specifically tosupport a text editing and formatting system. When in turn the 11/20 was outgrown, the system had proveduseful enough to persuade management to invest in the PDP11/45, and later in the PDP11/70 and Interdata 8/32 machines, upon which it developed to its present form. Our goals throughout the effort, whenarticulated at all, have always been to build a comfortable relationship with the machine and to exploreideas and inventions in operating systems and other software. We have not been faced with the need to satisfy someone else’s requirements, and for this freedom we are grateful.

回想起来，可以看到影响Unix设计的三个因素。

>Three considerations that influenced the design of Unix are visible in retrospect.

第一：因为我们是程序员，所以我们设计系统时，自然地会使其便于编写，测试和运行程序。我们对编程方便的最重要表现是系统被安排用于交互式使用，即使原始版本仅支持一个用户。我们认为，正确设计的交互式系统比"批量"系统更高效，更令人满意。而且，这种系统很容易适应非交互式使用，而相反的情况并非如此。

>First: because we are programmers, we naturally designed the system to make it easy to write, test, and run programs. The most important expression of our desire for programming convenience was that thesystem was arranged for interactive use, even though the original version only supported one user. Webelieve that a properly designed interactive system is much more productive and satisfying to use than a 'batch' system. Moreover, such a system is rather easily adaptable to noninteractive use, while the converse is not true.

第二：系统及其软件一直存在相当严重的尺寸限制。鉴于对合理效率和表现力的部分敌对欲望，规模约束不仅鼓励经济，而且还鼓励设计的某种优雅。这可能是对"通过痛苦的救赎"哲学的一种极其伪装的版本，但在我们的案例中它起到了一些作用。

>Second: there have always been fairly severe size constraints on the system and its software. Given the partially antagonistic desires for reasonable efficiency and expressive power, the size constraint hasencouraged not only economy, but also a certain elegance of design. This may be a thinly disguised version of the "salvation through suffering" philosophy, but in our case it worked.

第三：几乎从一开始，系统就能够并且确实自我维持下去。这个事实比看起来更重要。如果系统的设计者被迫使用该系统，他们很快就会意识到其功能性和表面缺陷，并且在为时已晚之前有很强的动力去纠正它们。因为所有的源程序总是可用并且很容易在线修改，所以我们是当新想法被他人发明，发现或建议时，他们愿意修改和重写系统及其软件。

>Third: nearly from the start, the system was able to, and did, maintain itself. This fact is more important than it might seem. If designers of a system are forced to use that system, they quickly become aware of its functional and superficial deficiencies and are strongly motivated to correct them before it is too late.Because all source programs were always available and easily modified online, we were willing to reviseand rewrite the system and its software when new ideas were invented, discovered, or suggested by others.

本文讨论 Unix 的方面至少清楚地表明了这两种设计方面的前两个方面。例如，从编程的角度来看，文件系统的接口非常方便。可能的最低接口级别旨在消除各种设备和文件之间以及直接和顺序访问之间的区别。不需要大的“访问方法”例程来使程序员与系统调用隔离;实际上，所有用户程序都可以直接调用system或者使用一个小于一页的小型库程序来缓冲许多字符，并且读取器会一次性写入它们。

>The aspects of Unix discussed in this paper exhibit clearly at least the first two of these design con-siderations. The interface to the file system, for example, is extremely convenient from a programmingstandpoint. The lowest possible interface level is designed to eliminate distinctions between the variousdevices and files and between direct and sequential access. No large "access method" routines arerequired to insulate the programmer from the system calls; in fact, all user programs either call the systemdirectly or use a small library program, less than a page long, that buffers a number of characters and readsor writes them all at once.

编程方便性的另一个重要方面是没有“控制块”——具有由文件系统或其他系统调用部分维护和依赖的复杂结构。一般来说，程序的地址空间的内容是程序的属性，我们试图避免对该地址空间内的数据结构施加限制。

>Another important aspect of programming convenience is that there are no "control blocks" with acomplicated structure partially maintained by and depended on by the file system or other system calls.Generally speaking, the contents of a program’s address space are the property of the program, and we havetried to avoid placing restrictions on the data structures within that address space.

鉴于要求所有程序都可以作为输入或输出用于任何文件或设备，所以还希望将依赖于设备的考虑因素推入操作系统本身。唯一的替代方案似乎是加载所有程序，用于处理每个设备的例程，这是昂贵的空间，或者依赖于动态链接到实际需要时适合于每个设备的例程的一些方法，这是无论是在设计上还是在硬件上都非常昂贵

>Given the requirement that all programs should be usable with any file or device as input or output, itis also desirable to push device-dependent considerations into the operating system itself. The only alterna-tives seem to be to load, with all programs, routines for dealing with each device, which is expensive inspace, or to depend on some means of dynamically linking to the routine appropriate to each device when itis actually needed, which is expensive either in overhead or in hardware.

同样，过程控制方案和命令接口都被证明既方便又有效。由于 shell 作为一个普通的，可交换的用户程序运行，因此它不会在系统中消耗任何“断线”空间，并且可以以很低的成本制作所需的强大功能。特别是，给定shell作为生成其他进程来执行命令的进程执行的框架，I/O 重定向，后台进程，命令文件和用户可选择的系统接口的概念在实现时都变得非常简单。

>Likewise, the process-control scheme and the command interface have proved both convenient andefficient. Because the shell operates as an ordinary, swappable user program, it consumes no "wired-down" space in the system proper, and it may be made as powerful as desired at little cost. In particular,given the framework in which the shell executes as a process that spawns other processes to perform com-mands, the notions of I/O redirection, background processes, command files, and user-selectable systeminterfaces all become essentially trivial to implement.