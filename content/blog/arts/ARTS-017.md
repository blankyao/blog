---
title: ARTS 017
date: "2020-07-06 11:15:00"
description: " Find the Duplicate Number, Teach Yourself Programming in Ten Years"
---

## Algorithm
[287. Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/)

Given an array nums containing n + 1 integers where each integer is between 1 and n (inclusive), prove that at least one duplicate number must exist. Assume that there is only one duplicate number, find the duplicate one.

Example 1:

> Input: [1,3,4,2,2]
>
> Output: 2
>
> Example 2:

Input: [3,1,3,4,2]Output: 3

### Solution
```kotlin
fun findDuplicate(nums: IntArray): Int {
    var slow = nums[0]
    var fast = nums[nums[0]]
    while (slow != fast) {
        slow = nums[slow]
        fast = nums[nums[fast]]
    }

    slow = 0
    while (slow != fast) {
        slow = nums[slow]
        fast = nums[fast]
    }
    return slow
}
```
和寻找链表闭环入口如出一辙。

## Review
[Teach Yourself Programming in Ten Years](http://www.norvig.com/21-days.html)

第一次读这篇文章是在十几年前，但是当时没有太深的感触，如今从事这个行业也有十年了，读起来感触会更加深刻一些。虽然写过几年代码，但是依然不认为自己是个优秀的软件工程师，像大部分人一样，工作几年后就因为各种各样的原因转做管理岗位，最近几年加起来写的代码还不如刚毕业时半年写的多，虽然也曾安慰过自己告诉自己在做更重要的事情，而如果一个技术管理者没有很深的技术功底，如何能做出最优的决策呢？如果一个团队都是 21 天速成的程序员，又如何能做出优秀的项目呢？

所以，与其称自己为技术管理者，我更希望称自己为工程科学家，扎扎实实的学习计算机领域的基础知识，踏踏实实的在工程上实践，通过在工程上的实践设计出最优的架构，写出最优雅的代码，总结实践经验，传播经过验证的思想，带领团队用正确的方式做正确的事情。

## Tips
None

## Share
周末发了条 twitter:
> 昨晚和同事一块聚餐，一位测试同学问另一位比较资深的测试同学能否指导一些测试领域比较系统的方法论，这位比较资深的同学说：「老老实实的去写测试用例、不断的去改进，不要期望一下就能学到多么高深的东西，这是不可能的」
一位好友看到这条 twitter 后说其实是有方法论的，只是这位同学没掌握而已，或者说这位同学不知道该如何教别人。

不管任何领域都是有方法论的，这点我认同，但是如果不经过大量的实践，而是上来就学方法论，真的能掌握吗？这个我要打一个问号。