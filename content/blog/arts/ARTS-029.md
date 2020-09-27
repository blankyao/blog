---
title: ARTS 029
date: "2020-09-27 22:11:00"
description: "A clean start for the web; 把什么放入架构设计；Convert Sorted List to Binary Search Tree"
---
## Review
[A clean start for the web](https://macwright.com/2020/08/22/clean-starts-for-the-web.html)

WWW 已经出现很多年了，虽然从最开始静态的页面到现在动态的应用都能够支撑，但是作者认为这样导致在用 Web 技术进行开发时对开发者和使用者都有很多的弊端，所以提出来了重新设计 Web 的设想。我赞同作者的出发点，但是不赞同具体的实现方案。不过文章里面有一些有意思的项目，可以了解一下。

## Share
架构组的意义是什么？今天看了一个很好的解释：
> 我们的目标是让架构组可以聚焦到一大群打仗的开发团队忽略掉的，长远来说非常重要的逻辑上，给开发团队在满足需求市场一线不断发生的需求的前提下，引入额外的约束，从而制造长远的竞争力。
> 
> —— [把什么放入架构设计](https://zhuanlan.zhihu.com/p/248625181)

## Algorithm
[Convert Sorted List to Binary Search Tree](https://leetcode.com/problems/convert-sorted-list-to-binary-search-tree/)

Given the head of a singly linked list where elements are sorted in ascending order, convert it to a height balanced BST.

For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of every node never differ by more than 1.

### Solution
```kotlin
fun sortedListToBST(head: ListNode?): TreeNode? {
    if (head == null) return null
    return buildTree(head, null)
}

fun buildTree(head: ListNode?, tail: ListNode?): TreeNode? {
    if (head == tail) return null
    var fastNode = head
    var slowNode = head

    while (fastNode != tail && fastNode!!.next != tail) {
        slowNode = slowNode!!.next
        fastNode = fastNode.next!!.next
    }

    val root = TreeNode(slowNode!!.`val`)
    root.left = buildTree(head, slowNode)
    root.right = buildTree(slowNode.next, tail)
    return root
}
```

依然是美丽的递归，最开始我用了一个比较土的方式实现，后来看评论区里有有这种双指针的方式，效率会好很多，其实用双指针找链表的中间值我也实现过，但是做这道题时一下没想起来。
