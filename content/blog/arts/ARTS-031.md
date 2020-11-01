---
title: ARTS 031
date: "2020-11-01 22:42:00"
description: "Life is short; Maximal Square"
---

## Review
[Life is short](http://www.paulgraham.com/vb.html)

生命是短暂的，如果真的意识到了这一点，我说的是真的意识到，而不只是停留在感叹的层面，最好是能到用数字衡量出来的程度，就不要把时间花在那些狗屁事情上，而是去做真正重要的事情。

## Share
前几天和同事讨论事情时提到了「技术深度」，在这之前我没太深入总结，后来总结了一下：我理解的技术深度指的是理解技术的原理，从需求分析到业务架构、从应用设计到代码实现都能够应用所掌握的技术知识和方法论获得深度的洞察，最终达到从设计到实现都能够在扩展性、可维护性、可测试性以及性能等方面满足业务当前的需求以及未来的迭代的效果。

## Algorithm
[Maximal Square](https://leetcode.com/problems/maximal-square/)

Given a 2D binary matrix filled with 0's and 1's, find the largest square containing only 1's and return its area.

### Solution

```kotlin
fun maximalSquare(matrix: Array<CharArray>): Int {
    val rows = matrix.size
    val cols = if(rows > 0) matrix[0].size else 0
    val dp = Array(rows + 1) { IntArray(cols + 1) }

    var maxLength = 0
    for (row in 1..rows) {
        for (col in 1..cols) {
            if (matrix[row - 1][col - 1] == '1') {
                dp[row][col] = minOf(dp[row][col - 1], dp[row - 1][col - 1], dp[row - 1][col]) + 1
                maxLength = maxOf(maxLength, dp[row][col])
            }
        }
    }

    return maxLength * maxLength
}
```