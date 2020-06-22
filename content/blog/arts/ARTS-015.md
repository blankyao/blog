---
title: ARTS 015
date: "2020-06-22 21:22"
description: "Why Hypercard Had to Die, Longest Palindromic Substring, 浏览器成为了最大且最开放的计算平台"
---
## Algorithm
[Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/)

Given a string s, find the longest palindromic substring in s. You may assume that the maximum length of s is 1000.

Example 1:

> Input: "babad"
>
> Output: "bab"
>
> Note: "aba" is also a valid answer.

### Solution
```kotlin
fun longestPalindrome(s: String): String {
    val isPalindome = Array(s.length) { BooleanArray(s.length) }
    val chars = s.toCharArray()
    var result = ""
    for (index in s.indices) {
        isPalindome[index][index] = true
    }

    for (end in s.indices) {
        for (start in 0..end) {
            isPalindome[start][end] = chars[end] == chars[start] && (end - start < 3 || isPalindome[start + 1][end - 1])
            if (isPalindome[start][end] && end - start + 1 > result.length) {
                result = s.substring(start..end)
            }
        }
    }
    return result
}
```
## Review
[Why Hypercard Had to Die](http://www.loper-os.org/?p=568)

Hypercard 是苹果曾经在 Mac 平台推出的一款可以让用户非常方便的创建应用的工具，即使不会写代码，也可以自己动手去开发软件，就像作者在文章里面演示了一下从零开始「开发」出了一个计算机，放在今天来说，可以称之为是一个 Low Code 开发平台吧。在当年有很多忠实的用户，而且还为后来出现的 WWW 提供了灵感，可惜的是在 Jobs 回归苹果后给砍掉了。

Jobs 的回归可以说是直接影响了个人计算机的发展方向，在这之前，Doug Engelbart 和 Alan Kay 这群人所设想的个人计算机是人类智慧的延伸，和计算机刚出现时的给专业工程师用的计算机器定位有很大的差异，所以他们发明了图形界面、鼠标、显示器、键盘、面向对象编程等我们到今天都还在使用的东西。Jobs 学到了这些后才有了后来的 Mac, 不过，在 Jobs 砍掉 Hypercard 以及 Newton 后，也代表着苹果将个人计算机定位为「个人消费品」而不是他的老师们所设想的人类智慧的延伸。

Alan Kay 曾经在 [Hacker News](https://news.ycombinator.com/item?id=16836379) 里面发表观点，表示对 Mac 以及 iPhone 上没出现比 Smalltalk 更好的东西表示失望，对苹果放弃 Hypercard 表示不理解：
> I was disappointed that something better than Smalltalk wasn't on the Mac and iPhone (Smalltalk was truly wonderful in the context of the 70s, but we considered it just a step in a good direction).
>
> Not understanding Hypercard was one of Apple's largest mistakes in the world of end-users. It was a real breakthrough in something that end-users could really handle and be usefully programmable by them. Besides not understanding its significance on the Mac, we (old Parc hands) pleaded until we were blue in the face to make HC the basis of a really good web browser (it was a great model of a symmetric author-consumer media tool). Missing the latter was a tragedy.
> 
> In the light of the first comment, we could then contemplate an end-user system that combined what was great about Hypercard, Smalltalk, and some other experience from the 80s (e.g. the use-cases from Ashton-Tate "Framework", etc.).

## Tips
None

## Share
在 W3C 和 TC39 的努力下，浏览器成为了最大且最开放的计算平台，MacOS, Windows, Android 以及 iOS 永远都不会互相兼容，所以任何一个这些平台中的应用都不可能像浏览器中的应用一样横跨所有平台。另外，Android 和 iOS 这种封闭的平台把开发者当做「第三方开发者」，把开发者开发的应用当做自己系统的一个「插件」，带来了更多的限制。所以，还是拥抱浏览器吧。