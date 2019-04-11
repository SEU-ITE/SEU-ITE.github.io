---
title: 每天一篇计算机 Paper (draft)
tags: 
 - 每日 Paper
 - 研究生
---

# All for one and one for all

>Bayer, M. (2019). "All for one and one for all." Science 364(6435): 30-31.
- 译者：陈思源

本文隶属于"每天一篇计算机 Paper"系列博客，更多内容请点击[这个链接](https://seuite.github.io/tags/%E6%AF%8F%E6%97%A5-Paper/)。

量子信息（QI）在过去二十年中已成为研究的焦点，其目标是利用量子态叠加和纠缠所提供的潜力（1）。首先 QI 的硬件实现依赖于量子系统，该系统托管干净，隔离良好的两级系统，如原子或离子。尽管这些系统取得了成功，但固态QI实现仍然保证了稳健性，小型化，已建立的制造工具，对大量相关组件的可扩展性以及与传统硬件的轻松连接。然而，一个主要的挑战是量子态与晶体中的多体环境的相互作用会损害QI。在半导体纳米结构中，晶格核提供足够长的QI存储时间，但是真正连贯的界面，即将QI忠实地存储在核自旋集合中所需的，仍然是难以捉摸的。在本期第62页，Gangloff等人。 （2）通过利用超精细相互作用实现了量子点中具有原子核的电子的这一目标的实现。

Quantum information (QI) has become a focus of research during the past two decades, with the goal of exploiting the potentialities offered by superposition and entanglement of quantum states (1). The first hardware implementations of QI relied on quantum systems hosting clean, well-isolated two-level systems such as atoms or ions. Despite the success of these systems, solid-state QI implementations promise robustness, miniaturization, established fabrication tools, scalability to large numbers of involved components, and easy connectivity to classical hardware. However, a major challenge is that the interaction of quantum states with the many-body environment in a crystal can compromise QI. In semiconductor nanostructures, the lattice nuclei offer sufficiently long QI storage times, but a truly coherent interface, which is needed to store QI faithfully in an ensemble of nuclear spins, has remained elusive. On page 62 of this issue, Gangloff et al. (2) report the realization of this goal for an electron with the nuclei in a quantum dot, which they achieved by exploiting hyperfine interactions.

固态量子位最有希望的候选者是缺陷（3），例如钻石中的氮空位，它们与周围环境隔离良好（4）。 原子状或更确切地说，类似缺陷的定位可以通过具有三维载流子限制的量子点结构来模仿（5）。 这种方法已经产生了有价值的QI硬件成就，例如高效和高质量的单光子或纠缠光子源（6）。 作为固定量子比特，量子点提供纳秒范围内的电荷相干时间和微秒范围内的自旋相干时间，但是这些值仍然比其他的竞争对手短几个数量级（7）。 量子点的原子核是这个缺点的原因。 在几开尔文的低温下，晶格振动被冻结，使得量子点载体旋转所经历的主要相互作用是与晶格核的超精细耦合。

The most promising candidates for quantum bits in the solid state are defects (3), such as nitrogen vacancies in diamond, which are well isolated from their surroundings (4). Atom-like or, more precisely, defect-like localization can be mimicked with quantum dot structures with threedimensional carrier confinement (5). This approach has led to valuable QI hardware achievements, such as efficient and highquality single or entangled photon sources (6). As stationary qubits, quantum dots offer charge coherence times in the nanosecond range and spin coherence times in the microsecond range, but these values are still orders of magnitude shorter than other olid-state competitors (7). The nuclei of the quantum dot are responsible for this shortcoming. At cryogenic temperatures of a few kelvin, the lattice vibrations are frozen out, so that the main interaction that quantum dot carrier spins undergo is the hyperfine coupling with the lattice nuclei.

晶核的长寿命自旋相干性在核磁共振研究中是众所周知的，因此核被认为是来自载体自旋的QI可以改组和储存的资源，可能通过该耦合随后恢复。 然而，核自旋非常复杂。 在Gangloff等人研究的量子点中，该浴由数万个铟，镓和砷原子核形成，形成非常不均匀的整体。 这种不均匀性是自旋受到由分子束外延生长的这些结构中的应变产生的电场强烈扰动的结果。 此外，即使在几开尔文的低温下，核系统也是“热的”并且是无序的。 因此，电子自旋与核的耦合通常被认为是有害的，因为载流子自旋携带的QI快速消散，这限制了量子点中的载流子自旋相干性（7）。

Long-lived spin coherence of lattice nuclei is well known from nuclear magnetic resonance studies, so nuclei have been considered as a resource into which QI from the carrier spins can be shuffled and stored with possible subsequent recovery through this coupling. However, the nuclear spin is highly complex. In the quantum dots studied by Gangloff et al., this bath is formed by tens of thousands of nuclei of indium, gallium, and arsenic atoms that form a very inhomogeneous ensemble. This inhomogeneity is the result of the spins being strongly perturbed by electric fields created by strain in these structures that are grown by molecular beam epitaxy. Further, even at low temperatures of a few kelvin, the nuclear system is ”hot” and disordered. Thus, coupling of an electron spin to the nuclei is generally considered to be detrimental, as QI carried by carrier spins quickly dissipates, which limits the carrier spin coherence in quantum dots (7).

为了将核浴用作量子资源，需要在载体和核自旋之间建立强烈的，非耗散的耦合，到目前为止，这对于量子点几乎是不可能的。 然而，可以发现暗示超精细相互作用不一定必须破坏性地起作用，例如在磁场中量子点集合中的电子自旋进动的研究中。 这里，通过电子 - 核触发过程在每个点中建立核磁场，使得非常不均匀的，广泛分布的进动频率被聚焦到非常少的模式或甚至单个模式（8）。

In order to use the nuclear bath as a quantum resource, a strong, nondissipative coupling would need to be established between carrier and nuclear spins, which until now has been considered almost impossible for quantum dots. However, hints that the hyperfine interaction does not necessarily have to act destructively could be found, such as in studies of the electron spin precession in a quantum dot ensemble in a magnetic field. Here, a nuclear magnetic field is established in each dot through electron-nuclei flip-flop processes so that the otherwise very inhomogeneous, broadly distributed precession frequencies are focused onto very few modes or even a single mode (8).

Gangloff等人采取的方法取得了成功。 取决于几个突破。 作者最初通过使用光脉冲来触发系统的拉曼跃迁来冷却核自旋系统。 单个量子点中的电子自旋被取向，然后其极化被转移到核。 对于在优化条件下足够长的泵送，实现了低至200μK的核温度，远低于热晶体的2K温度。

The success of the approach taken by Gangloff et al. depended on several breakthroughs. The authors initially cooled the nuclear spin systems by using optical pulses to trigger Raman transitions of the system. The electron spin in a single quantum dot was oriented, and then its polarization was transferred to the nuclei. For sufficiently long pumping under optimized conditions, a nuclear temperature as low as 200 µK was achieved, far below the 2 K temperature of the hot crystal.

在这种情况下，作者发现电子自旋和核系综形成了强耦合状态。 他们可以用光谱法绘制出一个单位角动量的总核自旋变化。 这种变化对应于单核核子，即集体核波的基本量子单位（见图）。

In this regime, the authors found that the electron spin and nuclear ensemble formed a strongly coupled state. They could map out spectroscopically a change of total nuclear spin by a single unit of angular momentum. This change corresponded to a single nuclear magnon, the elementary quantum unit of a collective nuclear wave (see the figure).

最后，Gangloff等人。 相干地操纵耦合的电子 - 核实体，其中涉及大部分量子点核，其通过全光学手段发射核磁共振。 这个过程对应于电子自旋和原子核集合之间的连贯，非耗散的交换 - 量子记忆的先决条件。

Finally, Gangloff et al. coherently manipulated the coupled electron-nuclei entity in which a large fraction of quantum dot nuclei are involved, which launched a nuclear magnon by all-optical means. This process corresponds to a coherent, nondissipative exchange between the electron spin and the collective of nuclei—a prerequisite for a quantum memory.

这些结果可能是开发具有足够长的量子点相干时间的量子存储器接口的第一步。一致性得益于核系统的多体性质，这提供了稳健性。而且，默认情况下，每个量子位都与其专用固有存储器相关联。这一步骤一直是半导体纳米结构QI平台难题的一部分。至于载流子自旋量子比特，已经提供了其他关键演示（6），例如在纳秒或甚至更短的时间尺度上的有效初始化和操纵以及用于信息传递的光子的有效互换。而且，在基本水平上，这些结果非常有趣，因为已经建立了核的量子多体状态，其可以通过电子自旋光学地相干地操纵。应该有可能创建特定的非经典核态，例如薛定谔猫州。

These results could be the first steptoward the development of a quantum memory interface with sufficiently long coherence time with quantum dots. The coherence benefits from the many-body nature of the nuclear system, which provides robustness. Moreover, every quantum bit would be associated with its dedicated inherent memory by default. This step has been the missing piece of the puzzle for a semiconductor nanostructure QI platform. As for carrier spin quantum bits, other key demonstrations (6) have been provided already, such as efficient initialization and manipulation on time scales of nanoseconds or even shorter as well as the efficient interconversion with photons for information transfer. Also, at a fundamental level, these results are highly interesting because a quantum many-body state for the nuclei has been established that can be coherently manipulated optically through the electron spin. It should be possible to create specific nonclassical nuclear states, such as Schrödinger cat states. 

REFERENCES AND NOTES 
1. M. A. Nielsen, I. L. Chuang, Quantum Computation and Quantum Information (Cambridge Univ. Press, 2010).
2. D. A. Gangloff et al., Science 364, 62 (2019). 
3. J. R. Weber et al., Proc. Natl. Acad. Sci. U.S.A. 107, 8513 (2010).
4. J. Clarke, F. K. Wilhelm, Nature 453, 1031 (2008).
5. D. Loss, D. P. DiVincenzo, Phys. Rev. A 57, 120 (1998). 
6. P. Michler, Ed., Quantum Dots for Quantum Information Technologies (Springer, 2017).
7. B. Urbaszek et al., Rev. Mod. Phys. 85, 79 (2013). 
8. A. Greilich et al., Science 317, 1896 (2007).