---
title: ARTS 021
date: "2020-08-03 08:21:00"
description: "Flatten Binary Tree to Linked List, Dr. Alan Kay on the Meaning of \"Object-Oriented Programming\""
---

## Algorithm
[Flatten Binary Tree to Linked List](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/)

Given a binary tree, flatten it to a linked list in-place.

### Solution
```kotlin
class Solution {
    fun flatten(root: TreeNode?): Unit {
        if (root == null) return

        val left = root.left
        val right = root.right
        
        root.left = null
        
        flatten(left)
        flatten(right)

        root.right = left

        var lastNode = root
        while (lastNode!!.right != null) lastNode = lastNode.right
        lastNode!!.right = right
    }
}
```

## Review
[Dr. Alan Kay on the Meaning of "Object-Oriented Programming"](http://userpage.fu-berlin.de/~ram/pub/pub_jf47ht81Ht/doc_kay_oop_en)

面向对象编程的原始设想：
1. 我想到对象就像生物细胞或者网络上的个体计算机，只能通过消息进行通信；
2. 我想摆脱数据，我意识到细胞或者 whole-computer 的隐喻可以摆脱数据，并且 '<-' 只是一个消息 token;
3. 我的数学背景让我意识到每个对象都应该有与之相关联的代数运算。「多态」这个术语是后来被强加进来的，不是太合适，因为是从函数的术语里来的，我想要的不只是函数。后来我决定用 "genericity" 以一个类似代数的形式来处理通用行为；
4. 我不喜欢 Simula I 或者 Simula 67 继承的方式，所以决定不考虑将继承作为内置的特性，直到我有更好的理解。

## Tips
None

## Share
最近很是焦虑，每次要动手开始做一些业余研究时都要想很久到底要做什么，因为脑子里有很多方向在回荡，而破解焦虑的最好方法是沉下心去开始动手做，所以经过一系列的心理斗争，决定收窄业余研究的方向，同一个时间段只研究一个主题。