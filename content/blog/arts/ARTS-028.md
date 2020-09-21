---
title: ARTS 028
date: "2020-09-21 23:07:00"
description: "How Books and Television Affect Your Brain Differently, According to Science; 谨防长期规划；House Robber III"
---
## Review
[How Books and Television Affect Your Brain Differently, According to Science](https://medium.com/jumpstart-your-dream-life/how-books-and-television-affect-your-brain-differently-according-to-science-34ca8be1493) 这篇文章讲的是看电视是如何让人变「笨」的，科学研究表明，看电视越多，大脑额叶会越厚，这会降低言语推理能力；而读书越多的人，大脑中和语言相关的各部分的连通性会越强。

这里面的原因在于看电视这种行为是被动的在接受，而读书是在主动的获取，在这两种不同的行为模式中，大脑所产生的反应是不一样的。

## Share
我们通常会认为不管是工作还是生活都要有长期规划，而《演进式架构》这本书第七章的最后却说不要做长期规划，因为人们对某件事情投入的时间和精力越多就越难放弃它，而这件事情可能是错误的。原文引用如下：
> 人们对某件事情投入的时间和精力越多，就越难放弃它。在软件中，它表现为不合理的工件附件。例如，人们在规划和文档上投入的时间和精力越多，就越看你保护其中的内容，即便有证据表明它们不准确或过时了。

> 谨防长期规划，因为它会迫使架构师做出的决策不可逆转，同时找到方法来保证多个可选方案。

> 将大型项目分解成更小的早期可交付物，以测试架构选型和开发基础设施的可行性。
## Algorithm
[House Robber III](https://leetcode.com/problems/house-robber-iii/)

The thief has found himself a new place for his thievery again. There is only one entrance to this area, called the "root." Besides the root, each house has one and only one parent house. After a tour, the smart thief realized that "all houses in this place forms a binary tree". It will automatically contact the police if two directly-linked houses were broken into on the same night.

Determine the maximum amount of money the thief can rob tonight without alerting the police.

### Solution
```kotlin
fun rob(root: TreeNode?): Int {
    return robWithRoot(root, true)
}

fun robWithRoot(root: TreeNode?, withRoot: Boolean): Int {
    if (root == null) return 0

    return if (withRoot) {
        ((root?.`val` ?: 0) + robWithRoot(root?.left, false) + robWithRoot(root?.right, false))
                .coerceAtLeast(robWithRoot(root?.left, true) + robWithRoot(root?.right, true))
    } else {
        robWithRoot(root?.left, true) + robWithRoot(root?.right, true)
    }
}
```

美丽的递归。
