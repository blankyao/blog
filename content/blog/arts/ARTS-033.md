---
title: ARTS 033
date: "2020-11-28 22:09:00"
description: "Machines for creative enablement；开诚布公地探讨你的观察；Minimum Number of Arrows to Burst Balloons"
---

## Review
[Machines for creative enablement (not human replacement)](https://medium.com/@howietl/machines-for-creative-enablement-not-human-replacement-da40f875a976)

这篇文章是 Airtable 的创始人在 2016 年为了解释 Airtable 到底是做什么的写的一篇文章，计算机发展到今天，其实和几十年前没什么太大区别，我们依然用着最古老的文件管理方式，用着最古老的文档工具。在计算机领域出现「文件」这个概念时，其实是对物理文件的一种隐喻，类似 Word 的文档工具是对纸张的一种隐喻，Excel 的鼻祖 VisiCalc 的作者是因为在工商管理课上因为计算账目非常繁琐而发明了计算机上的电子表格工具，PPT 是用计算机来模拟实体的幻灯片，这些都只是在那个时代增量式的创新，但是计算机作为一个强大的计算工具，能够做的事情远不仅仅是现在这个样子，真正革命性的创新还没有发生。

这几十年变化最大的是互联网，互联网让我们的生活变的越来越便捷、让信息传播得更加高效，但是这些改变不一定让这个世界更加美好。所以未来我并不想去做一个像电商或者社交类的互联网产品，而是想做一款能够发挥计算机价值的创新科技产品，这样的工具可以辅助拓宽人类的想象力、革命性的提升人类的工作效率，它有可能是一个像文档编辑、海报制作、视频剪辑这类创作型工具，也有可能是一个软件开发工具。每个人都可以使用这些工具来提高自己的工作效率，甚至可以基于这样的工具开发出满足自己需求的工具，而不是被掌握了 AI 技术的商业公司开发的机器人替代掉。

## Share
如果你对那些需要被考察的员工有自己的看法，但是你却不开诚布公地去探讨，这是不道德和毫无助益的。因为每个人都有权去直面指责自己的人，而且你的判断也不一定是正确的，因此你需要对自己的想法进行压力测试。这样做对你自己和他们都很有帮助。开诚布公地探讨你的观察，目的是弄清你和你的员工是怎样的人，这样才能人岗匹配。

—— 《原则》

## Algorithm
[Minimum Number of Arrows to Burst Balloons](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/)

There are some spherical balloons spread in two-dimensional space. For each balloon, provided input is the start and end coordinates of the horizontal diameter. Since it's horizontal, y-coordinates don't matter, and hence the x-coordinates of start and end of the diameter suffice. The start is always smaller than the end.

An arrow can be shot up exactly vertically from different points along the x-axis. A balloon with xstart and xend bursts by an arrow shot at x if xstart ≤ x ≤ xend. There is no limit to the number of arrows that can be shot. An arrow once shot keeps traveling up infinitely.

Given an array points where points[i] = [xstart, xend], return the minimum number of arrows that must be shot to burst all balloons.

### Solution
```kotlin
fun findMinArrowShots(points: Array<IntArray>): Int {
    points.sortBy { it -> it[1] }

    if (points.isEmpty()) return 0

    var shots = 1
    var lastShotPoint = points[0][1]

    for (index in 1 until points.size) {
        if (lastShotPoint < points[index][0]) {
            lastShotPoint = points[index][1]
            shots++
        }
    }
    return shots 
}
```