---
title: ARTS 010
date: "2020-05-18 22:20"
description: "ARTS #010"
---
## Algorithm
题目：[Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/)
Given a linked list, return the node where the cycle begins. If there is no cycle, return null.

To represent a cycle in the given linked list, we use an integer pos which represents the position (0-indexed) in the linked list where tail connects to. If pos is -1, then there is no cycle in the linked list.

Note: Do not modify the linked list.

Example 1:

> Input: head = [3,2,0,-4], pos = 1
>
> Output: tail connects to node index 1
>
> Explanation: There is a cycle in the linked list, where tail connects to the second node.

### Solution
```kotlin
fun detectCycle(head: ListNode?): ListNode? {
    var fast = head?.next?.next
    var slow = head?.next
    while (fast != slow) {
        fast = fast?.next?.next
        slow = slow?.next
    }

    if (fast == null) return null

    fast = head
    while (fast != slow) {
        fast = fast?.next
        slow = slow?.next
    }

    return fast
}
```
## Review
[Falling Into The Pit of Success](https://blog.codinghorror.com/falling-into-the-pit-of-success/)
C++ 在保护你免受自己的最大敌人（自己）伤害方面做得很糟糕，你永远都在绝望之坑徘徊，一不小心就会跌入深渊。
当你在用 C#, Ruby, Python 来替代 C++ 时，或许会舍弃一些性能，但是你收获的是避免痛苦的绝望之坑的可能性，以及跌入令人向往的成功之坑的机会。

一个设计良好的系统，应该让做正确的事情非常的简单、做错误的事情非常的困难，如果我们合理的设计我们的应用，我们的用户应该不不可避免的跌入成功之坑。在这 API 设计、大型应用、小型应用、web 应用、GUI 应用、终端应用都是通用的。

原文中的链接已经失效，原始内容在这里：[The Pit of Success](https://medium.com/@ricomariani/the-pit-of-success-cfefc6cb64c8)

## Tips
在 kotlin 里怎样交换两个变量的值？ a = b.also { b = a}

## Share
说说软件工程师的工匠精神 —— 工程师文化。在工作中经常看到一种论调，比如某老板可能会说给这个项目配个架构师，然后再配几个普通开发就可以了吧？反正也没技术难度；再比如有些工程师同仁会说写单元测试的时间比写业务逻辑花的时间还要长，所以写单元测试不划算。写代码真的是这么「内卷」的工作吗？这个世界上有那么多优秀的开源项目可以用来学习，为什么大部分项目中的代码连最基本的可读性都无所保障？有那么多前辈总结出了各种架构思想和设计模式，为什么我们还是无法写出具备比较好的维护性的代码？为什么我们的软件经过一轮一轮的测试之后还是 BUG 频发？为什么小区的电梯隔三差五的就要「维护」一下？我想原因可能是在这个急功近利的行业，能够做到精益求精的工匠太少了，而这些工匠也没得到足够的尊重，35 岁还要担心失业，刚毕业的年轻人做出来的东西看起来好像也是可以用的。

我们需要工匠精神，我们需要工程师文化，我们需要在写出每一行代码时都用心的思考，我们需要给这些工匠足够的尊重。只有这样，才能真正做出来艺术品级别的产品，而不是一坨垃圾做出来的垃圾；才能提高工程师的幸福感，而不是被 996摧残；才能真正提高效率，而不用总是在算计着缩减成本。