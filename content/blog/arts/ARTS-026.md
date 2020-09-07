---
title: ARTS 026
date: "2020-09-07 11:50:00"
description: "Smalltalk 与面向对象编程；Permutations II"
---
## Review
好久没写长文了，费劲九牛二虎之力写了[Smalltalk 与面向对象编程](https://zhuanlan.zhihu.com/p/220021357)这篇文章，写作过程中并没有体会到多少快感，更多的是拖延导致的焦虑，虽然目前已经写完，但是还是感觉不太满意，打算再优化一下后再放到博客里面来。

## Share
> 如果你对那些需要被考察的员工有自己的看法，但是你却不开诚布公地去探讨，这是不道德和毫无助益的。因为每个人都有权去直面指责自己的人，而且你的判断也不一定是正确的，因此你需要对自己的想法进行压力测试。这样做对你自己和他们都很有帮助。开诚布公地探讨你的观察，目的是弄清你和你的员工是怎样的人，这样才能人岗匹配。
>
> —— 《原则》

## Algorithm
[Permutations II](https://leetcode.com/problems/permutations-ii/)

Given a collection of numbers that might contain duplicates, return all possible unique permutations.

### Solution
```kotlin
class Solution {
    fun permuteUnique(nums: IntArray): List<List<Int>> {
        nums.sort()
        val usedIndices = mutableListOf<Int>()
        val result = mutableListOf<MutableList<Int>>()
        backtrack(result, mutableListOf<Int>(), nums, usedIndices)
        return result
    }

    fun backtrack(result: MutableList<MutableList<Int>>, currentItem: MutableList<Int>, nums: IntArray, usedIndices: MutableList<Int>) {
        if (currentItem.size == nums.size) {
            result.add(mutableListOf<Int>().apply { addAll(currentItem) })
            return
        }

        for (index in nums.indices) {
            if (usedIndices.contains(index)) continue
            if (index > 0 && nums[index] == nums[index - 1] && !usedIndices.contains(index - 1)) continue

            currentItem.add(nums[index])
            usedIndices.add(index)
            backtrack(result, currentItem, nums, usedIndices)
            usedIndices.remove(index)
            currentItem.removeAt(currentItem.size - 1)
        }
    }
}
```