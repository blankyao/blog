---
title: ARTS 007
date: "2020-04-26 23:40"
description: "ARTS #007"
---
## Algorithm
题目：[Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/)

Given an unsorted array of integers, find the length of longest increasing subsequence.

Example:
> Input: [10,9,2,5,3,7,101,18]
>
> Output: 4 
>
> Explanation: The longest increasing subsequence is [2,3,7,101], therefore the length is 4. 

### Solution
```kotlin
class Solution {
    fun lengthOfLIS(nums: IntArray): Int {
        if (nums.isEmpty()) return 0
        val isl = IntArray(nums.size)
        isl.fill(1)
        var lis = 1
        for (i in 1 until nums.size) {
            for (j in 0 until i) {
                if (nums[i] > nums[j]) {
                    isl[i] = isl[i].coerceAtLeast(isl[j] + 1)
                    lis = lis.coerceAtLeast(isl[i])
                }
            }
        }
        return lis
    }
}
```

在评论区看到一个更高效的解法：[O(nlogn) Clean and easy Java DP + Binary Search solution with detailed explanation](https://leetcode.com/problems/longest-increasing-subsequence/discuss/74916/O(nlogn)-Clean-and-easy-Java-DP-%2B-Binary-Search-solution-with-detailed-explanation)

## Review
[The Lines of Code That Changed Everything](https://slate.com/technology/2019/10/consequential-computer-code-software-history.html)

当做科普随便看看，文章介绍了一些有意思的东西，比如第一行现代代码、Email 的起源、第一次在编程语言里使用 Hello World. 另外还要感叹一下，这里面很多事情都是在 MIT 这类学校里发生的。

## Tips
Null

## Share
前几天看到[一篇文章](https://zhuanlan.zhihu.com/p/133907799)讲标准和设计的区别，几个关键点记录一下：
1. 设计是进入具体实现前的逻辑设计；
2. 标准的要求是“符合标准的设计在使用上都可以兼容”，这个目标，是全部由标准承载的。如果对比设计和实现，标准看起来是个文档，但实际上它的本质是代码；
3. 完备和抽象，就是卡在标准定义两头的一对矛盾，我们评论一个标准是否正确的时候，我们评价它写得太多，是从抽象上来说的，我们说它写得太少，是从完备性上来说的。你不能简单用文字的多少来评价这个多少。前者（完备和抽象）是形而上的判断，后者（文字多少）是形而下的判断；
4. 我们分解模块，分解层次，当你决定了一种约束，你也就决定了你这个模块的属性，它能完成的功能也被决定了。你不要以为你可以把什么功能都放上去。如果你有形而上的思维，这是一件非常明显的事，这也是架构必须具有的基本思维能力。而进行标准的设计，这种架构思维是基本的。