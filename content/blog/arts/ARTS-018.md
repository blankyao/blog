---
title: ARTS 018
date: "2020-07-13 22:35:00"
description: " Founding and Growing Adobe Systems, 3Sum, 状态机"
---

## Algorithm
[3Sum](https://leetcode.com/problems/3sum/)

Given an array nums of n integers, are there elements a, b, c in nums such that a + b + c = 0? Find all unique triplets in the array which gives the sum of zero.

Note:

The solution set must not contain duplicate triplets.

### Solution
```kotlin
fun threeSum(nums: IntArray): List<List<Int>> {
    val result = mutableListOf<List<Int>>()
    nums.sort()
    for (i in 0 until nums.size - 1) {
        if (i > 0 && nums[i] == nums[i - 1]) continue

        val target = 0 - nums[i]
        var low = i + 1
        var high = nums.size - 1

        while (low < high) {
            val currentResult = mutableListOf<Int>()
            currentResult.add(nums[i])

            val currentSum = nums[low] + nums[high]
            val left = nums[low]
            val right = nums[high]
            when {
                currentSum < target -> {
                    while (low < high && left == nums[low]) low++
                }
                currentSum > target -> {
                    while (low < high && right == nums[high]) high--
                }
                else -> {
                    currentResult.add(nums[low])
                    currentResult.add(nums[high])
                    result.add(currentResult)
                    while (low < high && left == nums[low]) low++
                    while (low < high && right == nums[high]) high--
                }
            }
        }
    }

    return result
}
```
刚做这道题时我是有些抗拒的，因为要考虑边界条件、去重啥的，很麻烦，但是看了下这篇文章[《一个函数秒杀 2Sum 3Sum 4Sum 问题》](https://mp.weixin.qq.com/s/fSyJVvggxHq28a0SdmZm6Q)感觉也挺有意思的。

## Review
[Founding and Growing Adobe Systems, Inc](https://blog.blankyao.com/founding-and-growing-adobe-systems-inc/)

## Tips
None

## Share
> 在复杂系统的设计中，“状态机推演”基本上是必须的步骤，否则你的系统会很不可靠。因为很多情形你可能都没有考虑过。更关键的是，如果你不在一开始就控制状态机，你很可能会随便搞几个变量来分别承载几个不同的情形，比如上面这个，你可能会用：用户是否注册，主页是否已分配，管理员标记了用户的问题……诸如此类的。等到问题变得很复杂了，你的状态空间就是所有这些变量的可能性的乘积。这时系统基本上就进入混沌状态，已经无法维护了。
>
> 很明显，状态机问题是个典型的构架问题，因为它不体现在你的代码中，只靠代码控制不住。而且一开始你不控制，后面新需求来了，你增加状态的时候，你不知不觉就会把系统搞到没法维护（只能靠试，好不好，只能测试才知道，测试覆盖不到的就倒霉），这种东西，就是要独立出来考量的，而且是每次加新需求，都要拿出来的。状态跃迁图不是放在架构文档里面那张死的图，而是你每次加代码都要对一次的“开发地图”。没有这样的认识，是不会感觉到架构设计是有意义的。

—— [状态机方法](https://zhuanlan.zhihu.com/p/59723017)