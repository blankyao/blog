---
title: ARTS 025
date: "2020-08-31 01:44:00"
description: "Introducing the Smalltalk-80 System"
---
## Review
[Introducing the Smalltalk-80 System](http://tech-insider.org/star/research/acrobat/8108.pdf)

这是 1981 年 BYTE 杂志上介绍 Smalltalk 的一篇文章。Smalltalk 是什么？用我们现在对电脑组件的理解，Smalltalk 对应的是操作系统，但是跟我们理解的操作系统又不太一样，Smalltalk 允许用户自定义这个系统。而这个「自定义」跟我们现在常见的对系统进行自定义又不一样，现在我们一般所说的自定义指的是装个软件、换个主题，这里所说的自定义指的是由内而外的对系统进行自定义，不只是自定义外在表现，还可以自定义内部逻辑。

## Share
数学家并不是那种能够轻易摆布数字的人，他们常常做不到这点。数学家的主要技能是擅长在一个高层次上运用符号逻辑，尤其他们有着优秀的直觉判断力。

## Algorithm
[Permutations](https://leetcode.com/problems/permutations/)

Given a collection of distinct integers, return all possible permutations.

### Solution
```kotlin
class Solution {
    fun permute(nums: IntArray): List<List<Int>> {
        val result = mutableListOf<List<Int>>()
        backtrack(result, mutableListOf<Int>(), nums)
        return result
    }

    fun backtrack(result: MutableList<List<Int>>, currentList: MutableList<Int>, nums: IntArray) {
        if (currentList.size == nums.size) {
            result.add(mutableListOf<Int>().apply { addAll(currentList) })
            return
        }

        for (index in nums.indices) {
            if (currentList.contains(nums[index])) continue

            currentList.add(nums[index])
            backtrack(result, currentList, nums)
            currentList.removeAt(currentList.size - 1)
        }
    }
}
```
