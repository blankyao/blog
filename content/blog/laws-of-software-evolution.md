---
title: Review | Laws of Software Evolution
date: "2020-05-04 10:22:00"
description: "Laws of Software Evolution 是 Manny Lehman 通过对实际软件项目的观察总结的关于软件演进的规律，这个定律从 1970 年代到 1990 年代也演进了好几个版本。"
---
Laws of Software Evolution 是 [Manny Lehman](https://en.wikipedia.org/wiki/Meir_Manny_Lehman) 通过对实际软件项目的观察总结的关于软件演进的规律，这个定律本身从 1970 年代到 1990 年代也演进了好几个版本。本文是根据 [The evolution of the laws of software evolution: A discussion based on a systematic literature review](https://dl.acm.org/doi/10.1145/2543581.2543595) 这篇论文的内容对这个定律做的简单介绍。

## 最新版内容
### 1. Continuing Change
E 类型系统必须不断的进行改进，否则就会逐渐变得无法满足需求。

### 2. Increasing Complexity
随着 E 类型系统的演进，它的复杂度会不断的提升，除非专门进行维护或者降低复杂度的工作。
> Lehman 把复杂度氛围了三种：internal complexity 跟代码的结构属性相关；intrinsic complexity 跟系统的不同组件之间的依赖关系相关；external complexity 是代码是否易于理解的一种度量，前提是提供了相关文档。

### 3. Self Regulation
E 类型系统会根据反馈进行自我调节。

### 4. Conservation of Organisational Stability (invariant work rate)
随着 E 类型系统的演进，组织的工作效率是不变的。

### 5. Conservation of Familiarity
随着 E 类型系统的演进，与之相关的开发者、销售人员以及用户，需要掌握系统的内容和行为才能达到令人满意的发展，系统过度的发展会减弱这种掌握，所以，随着系统的演进，平均的增量发展是保持不变的。

### 6. Continuing Growth
在 E 类型系统的生命周期中，必须不断的改进以满足用户的需求。

### 7.Declining Quality
除非进行专门的维护和改进，否则 E 类型系统的质量会逐渐下降。

### 8. Feedback System
E 类型系统构成了一个多级的、多环的、多主体的反馈系统，必须将其视为这样才能在合理的基础上获得有效的改进。（「反馈」也是 Lehman 在 1990 年代研究的基石。）

## 软件系统分类
在每一条里面都有提到「 E 类型系统」这个概念，这是 Lehman 为了更客观的分析，将软件系统（程序）分成了三种类型，分别是：
1. S 类型（speciﬁed）程序来自于静态规范，且可以被形式化的证明是否正确，比如做数学计算的程序。
2. P 类型 (problem-solving) 程序是对真实世界的抽象，包含不确定、不可知、任意的情况，在某种程度上，它反映的是分析师的个人观点，对问题的表述以及解决方法接近真实的世界，比如下棋或者天气预报程序。
3. E 类型 (evolutionary) 程序是更容易发生变化的一种类型，程序成为它所建模世界的一部分，主要用来处理有人或者真实世界参与的活动，比如操作系统、交通控制系统。

Lehman 的软件演进定律开创了用统计学的方法来分析软件工程，也引起了更多学者在软件演进领域进行研究。虽然近些年也引起了挺多争议，比如有人认为这个定律所讲的东西都太含糊不清了，也有人质疑是否适用于所有的软件系统（一个比较有意思的案例是 Linux Kernal，由于 Linus Torvalds 对 Linux Kernal 有非常强的影响，所以这个项目并不是反馈驱动的），但是对我们普通的软件开发或者软件项目的负责人来说，其分析问题的方法以及总结的这些结论，都可以作为我们制定决策的参考。