---
title: ARTS 016
date: "2020-07-01 00:58:00"
description: "Jump Game, Figma 的工程价值观"
---
## Algorithm
[55. Jump Game](https://leetcode.com/problems/jump-game/?tab=Description)

Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Determine if you are able to reach the last index.

### Solution
```kotlin
fun canJump(nums: IntArray): Boolean {
    var max = 0
    for (index in nums.indices) {
        if (max < index) return false
        max = max.coerceAtLeast(index + nums[index])
        if (max >= nums.size - 1) return true
    }
    return false
}
```
## Review
[Figma's engineering values](https://blog.blankyao.com/figma-engineering-values/)

## Tips
None

## Share
None