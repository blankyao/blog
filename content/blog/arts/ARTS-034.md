---
title: ARTS 034
date: "2020-12-07 21:49:00"
description: "No-code Revolution. Why Now? 开诚布公地探讨你的观察；Minimum Number of Arrows to Burst Balloons"
---

## Review
[No-code Revolution. Why Now?](https://blog.blankyao.com/no-code-revolution/)

## Share
谋前不惧，谋后不悔。

做决策最忌讳的是不作为与左右摇摆，正确决策>错误决策>不决策，在全面评估、权衡利弊之后，没有最优解的情况下，相信直觉是个不错的选择；坚持与选择同样重要，路都是越走越宽的，早决策早出发，把时间用来奔跑而非等待。

## Algorithm
[Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/)

Given a string s that consists of only uppercase English letters, you can perform at most k operations on that string.

In one operation, you can choose any character of the string and change it to any other uppercase English character.

Find the length of the longest sub-string containing all repeating letters you can get after performing the above operations.

### Solution
```kotlin
fun characterReplacement(s: String, k: Int): Int {
    var maxLength = 0
    var currentMaxCount = 0
    var start = 0
    var end = 0
    val count = IntArray(26)

    val chars = s.toCharArray()

    while (end < s.length) {
        currentMaxCount = currentMaxCount.coerceAtLeast(++count[chars[end] - 'A'])
        while (end - start + 1 > k + currentMaxCount) {
            count[chars[start] - 'A']--
            start++
        }
        maxLength = maxLength.coerceAtLeast(end - start + 1)
        end++
    }

    return maxLength
}
```