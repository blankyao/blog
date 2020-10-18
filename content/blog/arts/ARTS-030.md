---
title: ARTS 030
date: "2020-10-18 22:55:00"
description: "Define Errors Out Of Existence; 如何减少公司对个人的依赖；Longest Palindromic Subsequence"
---
> 国庆假期休息了下，回来后工作又比较忙，所以 ARTS 暂停了两周。

## Review
Define Errors Out Of Existence

来自 [A Philosophy of Software Design](https://book.douban.com/subject/30218046/) 一书的第十章，对于异常处理有一个很大的误区，通常来说我们会认为跑出异常越多软件就越健壮，而实际上异常是导致软件复杂度提升的重要来源，减少异常可以有效的减少软件复杂度，进而减少 BUG 和维护成本。

## Share
如何减少公司对某个人的依赖？上周和一位朋友聚餐时他分享了一下之前在投行工作时公司为了避免公司对任何人产生依赖，强制要求每个人每年都有 5 天的时间休假，休假期间不能处理任何工作事务，不能和公司任何人有任何联系，连公司内网都访问不了。

## Algorithm
[Longest Palindromic Subsequence](https://leetcode.com/problems/longest-palindromic-subsequence/)

Given a string s, find the longest palindromic subsequence's length in s. You may assume that the maximum length of s is 1000.

### Solution
```kotlin
fun longestPalindromeSubseq(s: String): Int {
    val chars = s.toCharArray()
    val palindromeSubLengthArray = Array(s.length) {IntArray(s.length)}
    for (index in chars.indices) {
        palindromeSubLengthArray[index][index] = 1
    }

    for (end in chars.indices) {
        for (start in end - 1 downTo 0) {
            if (chars[end] == chars[start]) {
                palindromeSubLengthArray[start][end] = palindromeSubLengthArray[start + 1][end - 1] + 2
            } else {
                palindromeSubLengthArray[start][end] = palindromeSubLengthArray[start + 1][end].coerceAtLeast(palindromeSubLengthArray[start][end - 1])
            }
        }
    }

    return palindromeSubLengthArray[0][s.length - 1]
}
```
