---
title: ARTS 022
date: "2020-08-10 23:32:00"
description: "Remove Nth Node From End of List, The Computer Revolution Hasn't Happened Yet"
---

## Algorithm
[Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

Given a linked list, remove the n-th node from the end of list and return its head.

Example:

> Given linked list: 1->2->3->4->5, and n = 2.
>
> After removing the second node from the end, the linked list becomes 1->2->3->5.

## Solutoin
```kotlin
fun removeNthFromEnd(head: ListNode?, n: Int): ListNode? {
    val dummyHead:ListNode? = ListNode(0)
    dummyHead!!.next = head

    var slow = dummyHead
    var fast = dummyHead
    for (i in 0..n) {
        fast = fast!!.next
    }

    while (fast != null) {
        fast = fast!!.next
        slow = slow!!.next
    }
    slow!!.next = slow.next?.next
    
    return dummyHead.next
}
```

## Review
[The Computer Revolution Hasn't Happened Yet](https://catonmat.net/videos/the-computer-revolution-hasnt-happened-yet)

最近一直在看 Alan Kay 的一些观点，准备写一篇关于 Smalltalk 和面向对象的文章。

## Tips
None

## Share
> The way to stay with the future as it moves is to always play your systems more grand than it seems to be right now.

这个是前面提到的 Alan Kay 的演讲里面讲的最后一句话。在 1960 年代 Alan Kay 的思想算是绝对的另类，但是如果没有这些思想，就没有后来的个人电脑时代。而现在回头看 1997 年 Alan Kay 所思考的问题，这么多年电脑除了 UI 更好用了、网络更快了之外，其他好像没本质的变化，远没到 Alan Kay 在 1997 年所设想的状态。