---
title: ARTS 032
date: "2020-11-15 22:43:00"
description: "创造者 VS 管理者，日程规划能成就了你的工作，也可能毁掉你的工作；不考运气赚钱；Find Bottom Left Tree Value"
---

## Review
[创造者 VS 管理者，日程规划能成就了你的工作，也可能毁掉你的工作](https://lyric.im/maker-vs-manager)
> 你只能在这24小时里生活。 你只能用这24小时得到健康，快乐，金钱，自我充实，尊重和不朽灵魂。对这 24 小时加以善用，这个世界上没有什么比高效利用它更紧迫的事情了

## Share
最近在看 Naval 的一个访谈，访谈的内容起源于 Naval 在 2018 年在 twitter 上发布的[如何不靠运气致富](https://twitter.com/naval/status/1002103360646823936)。分享一下其中对[运气](https://nav.al/money-luck)的看法：

1. 随机的纯运气

第一种运气你可能叫它“狗屎运”，俗话说的 “瞎猫碰见死耗子”——那些完全超出我所控制范围内而发生的好事，它们也就是所谓的时运，或是叫天命。

2. 来自大胆拼搏的实干运

另一种运气则来自一个人长期不懈的坚持、努力打拼的过程；来自于积极进取，敢想敢做的行动。当你东奔西跑，到处折腾的时候，就在创造着大量机会，产生出很多能量——正所谓：但行好事，莫问前程。

3. 来自蓄谋已久的先手运

第三种获得好运的方式是通过你过人的洞察力：如果你在某个领域很有造诣，你会留意到这个行业中不为外人道的突破性机会。这是通过相关技能，知识和**长期积累的**工作经验培养的对机遇的敏锐嗅觉。

4. **你的独特人格带来的好运**

而最后一种运气是最古怪、最难的，却正是我们想要重点探讨的。它的涵义是：凭借你**为自己打造的一个独一无二的人设角色，一个特立独行的个人品牌，一种与众不同的思维模式**，而后运气就会找到你。

## Algorithm
[Find Bottom Left Tree Value](https://leetcode.com/problems/find-bottom-left-tree-value/)

Given a binary tree, find the leftmost value in the last row of the tree.

### Solution

```kotlin
fun findBottomLeftValue(root: TreeNode?): Int {
    val queue = LinkedList<TreeNode>()
    queue.push(root)
    var node = root
    while (queue.size > 0) {
        node = queue.poll()
        if (node.right != null) {
            queue.add(node.right)
        }

        if (node.left != null) {
            queue.add(node.left)
        }
    }
    return node!!.`val`
}
```