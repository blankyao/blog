---
title: ARTS 037
date: "2021-01-18 22:25:00"
description: "heroku values, 信任，Permutation in String"
---

## Review
[Heroku Values](https://gist.github.com/adamwiggins/5687294)

Heroku 的价值观。

## Share
信任 = （可信度+可靠度+亲近度）/ 自我导向

自我导向最直接的表达是“我能看到他对这件事情的利益诉求”，是一种动机上的表现，没有什么比“只关心自己的利益”更能给合作带来杀伤力了。

自我导向最极端的形式是不加掩饰的“唯利是图”，它包含一切只关注自身的行动，比如以自我为中心，想赢的欲望，利用别人的动机，试图显得聪明、机智、幽默，牺牲别人成全自己，等等。这个行为不难解释为什么有些人合作的时间越长越疏远，或者有的人自我感觉很好心，但是仍然无法让别人信赖。

避免自我导向，可以试着这样做：

一是积极倾听，不要试图掌控，和伙伴保持一种“跳舞”的感觉，找准节奏，互相给力。

二是做好为对方补位的准备，对方需要的时候，挺身而出，对方表演出色的时候，喝彩鼓励。

三是为失败承担责任的勇气，遭遇失败是再正常不过的事情，失败了，不互相指责，勇于敢于承担失败的后果，还有什么能比让别人看到你担当的气度更值得信赖的呢？

所以做值得信赖的合作伙伴，避免自我导向是重塑自己，让自己拥有更开阔的内心、更高的视角、更远的视野的行动。

## Algorithm
[Permutation in String](https://leetcode.com/problems/permutation-in-string/)

Given two strings s1 and s2, write a function to return true if s2 contains the permutation of s1. In other words, one of the first string's permutations is the substring of the second string.

### Solution
```kotlin
fun checkInclusion(s1: String, s2: String): Boolean {
    val l1 = s1.length
    val l2 = s2.length
    if (l1 > l2) return false

    val s1Array = s1.toCharArray()
    val s2Array = s2.toCharArray()

    val count = IntArray(26)
    for (i in 0 until l1) {
        count[s1Array[i] - 'a']++
        count[s2Array[i] - 'a']--
    }
    if (isAllZero(count)) return true

    for (i in l1 until l2) {
        count[s2Array[i] - 'a']--
        count[s2Array[i - l1] - 'a']++
        if (isAllZero(count)) return true
    }
    return false
}

fun isAllZero(array: IntArray): Boolean {
    for (i in array) {
        if (i != 0) return false
    }
    return true
}
```