---
title: ARTS 001
date: "2020-03-15 23:08"
description: "ARTS #001"
---

## Algorithm
题目：[Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)

Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

Example:
```
Input: [-2,1,-3,4,-1,2,1,-5,4],
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```
### Solution
```java
class Solution {
    public int maxSubArray(int[] nums) {
        int[] sum = new int[nums.length + 1];
        int max = nums[0];
        for(int i = 1; i <= nums.length; i++) {
            sum[i] = Math.max(sum[i - 1] + nums[i - 1], nums[i - 1]);
            max = Math.max(max, sum[i]);
        }
        return max;
    }
}
```
入门级别的动态规划题目，知乎上有个[介绍动态规划的帖子](https://www.zhihu.com/question/23995189/answer/35429905)写的很不错，还有一篇[专栏文章](https://zhuanlan.zhihu.com/p/91582909)讲动态规划的套路:
1. 定义数组元素的含义
2. 找出数组元素之间的关系式
3. 找出初始值

## Review
[Hyrum's Law](https://blog.blankyao.com/hyrum%20law/)

## Tip
Writing solidifies, chat dissolves. Substantial decisions start and end with an exchange of complete thoughts, not one-line-at-a-time jousts. If it's important, critical, or fundamental, write it up, don't chat it down.

from [The Basecamp Guide to Internal Communication](https://basecamp.com/guides/how-we-communicate)

## Share
前几天突然想到了 [Bret Taylor](https://twitter.com/btaylor)，第一次知道 Bret 是在 2008 年左右，当时 Bret 做了个产品叫 FriendFeed，是一款聚合各个社交平台 feed 的产品，在做这个产品的过程中 Bret 还开发了 Tonardo —— 一个高性能 web 框架并将其开源，很快就在 Python 圈里流行了起来，一直到现在还有很多 Python 开发者在用。后来 Facebook 收购了 FriendFeed，Bret 去 Facebook 做了几年 CTO 后又创业做了 Quip，随后又被 Salesforce 收购，现在 Bret 是 Salesforce 的 COO。

从这些经历可以看得出来 Bret 绝对是一个「大佬」级别的人物，当年刚看到 Tonardo 这个框架时我还在想怎么随便一个创业公司就能开发出来这么牛逼的框架，实际上，在做 FriendFeed 之前 Bret 就已经是 Google Map 的 manager 了，Google Map 官方博客里的[有些文章](https://googleblog.blogspot.com/2005/02/mapping-your-way.html)就是 Bret 写的，而且，在去 Google 之前 Bret 在斯坦福读了 CS 的本科和研究生。

为什么会突然想到 Bret 呢？我也不知道，总之就是某天深夜突然想到了，可能是想给自己打点鸡血吧，看下自己所崇拜的人在做什么。

我记得之前 Bret 是有一个自己的博客的，但是搜了好久没搜到，但是搜到了 Bret [在 medium 上的博客](https://medium.com/@btaylor)，最新的一篇文章是在 2015 年写的，虽然有些久了，但是文章内容却让我大吃一惊，文章的标题是 [React with C++: Building the Quip Mac and Windows Apps](https://medium.com/@btaylor/react-with-c-building-the-quip-mac-and-windows-apps-c63155c1531b)，对，你没看错，一个这么段位这么高的人，早在十多年前就已经是 CXO 级别的人，早就已经实现了财务自由的人，却写了一篇实实在在的技术文章，而且不是那种写科技发展趋势或者科普类的文章哦，是实打实的技术文章，从架构到具体的代码实现细节都有！然后又搜到一篇访谈 —— [Google’s Bret Taylor gives a tour of Quip’s architecture](https://sdtimes.com/android/googles-bret-taylor-gives-tour-quips-architecture/)，这篇访谈写于 2016 年，本以为是会讲关于 Quip 的创业历程或者产品思考之类的，万万没想到，整篇文章里完全没有这类内容，而是在讲 Android 的碎片化、Android 在中国地区的消息推送问题、文档实时同步的技术挑战！

在不禁让我跟平时看到的现象去做对比，在我们这个大环境下，很多技术人都在讨论 35 岁危机，即使是专业能力比较不错的人也会担心年龄大了还一直做技术会被淘汰，所以大家都挤破头去做「管理」，然后每天忙于参加各种会议。这是什么原因呢？明明是有很多人是热爱技术的，但是为什么却没有选择一直在做技术呢？我想比较直接的原因是职场对走专业路线的技术专家并没有那么的友好，想要获得更高的收入、想要得到大家的尊重就必须要去晋升、去变成一个管理者。但是这个背后的原因又是什么呢？昨天和当年刚毕业时一起在腾讯工作了几年的同事探讨了下这个话题，xk 提到在医生和律师这样的职业里并没有这种现象，所以并不是我们这个大环境不尊重有专业能力的人，而是我们这个行业不需要这么多专业能力这么强的人，我想了下好像也是有道理的，这个是由我们做的事情决定的，虽然我们是科技工作者，但是其实跟流水线的工人有多大的差别呢？无非就是我们在用代码来做软件产品嘛！

可是想下硅谷，同样是在做软件，同样是在做互联网产品，为什么就有那么多像 Bret 这样专业能力极强的人呢？除了 Bret 这类人外，像微软这种公司白发苍苍的程序员前辈也是非常的普遍，为什么会有这种差异呢？从这一点上来说，我认为是我们大部分公司的管理者自己把标准降低了，因为本来就没有在做技术含量特别高的产品，招一批程序员加班搞出来个产品一样可以赚钱，自然我们就不需要什么专家了。我们基本上不会看到那些企业家成功之后还在关心技术，大部分人都是在侃侃而谈自己的商业模式。而硅谷的公司里面，首先这些公司的创始人可能就是某个世界顶级学校毕业的计算机硕士或是博士，所以在创业时就是想着用技术来改变世界，其次，大部分产品经理，不管是初级的还是 manager 级别的也都是有很强的计算机专业背景，这样就形成了一种氛围，如果你随便搞个没啥技术含量的东西可能没人会瞧得上，自然也不会吸引到高端人才。

这个世界会好吗？