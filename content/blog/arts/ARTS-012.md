---
title: ARTS 012
date: "2020-05-31 23:30"
description: "Longest Substring Without Repeating Characters, The Third Age of JavaScript, 前端和后端谁更高级"
---
## Algorithm
[Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

Given a string, find the length of the longest substring without repeating characters.

Example 1:
> Input: "abcabcbb"
>
> Output: 3 
>
> Explanation: The answer is "abc", with the length of 3. 

### Solution
```kotlin
fun lengthOfLongestSubstring(s: String): Int {
    var right = 0
    var left = 0
    val charCountMap = mutableMapOf<Char, Int>()
    val chars = s.toCharArray()
    var result = 0

    while (right < s.length) {
        val charRight = chars[right]
        charCountMap[charRight] = charCountMap.getOrPut(charRight) { 0 } + 1
        right++

        while (charCountMap[charRight]!! > 1) {
            val charLeft = chars[left]
            charCountMap[charLeft] = charCountMap.getOrPut(charLeft) { 0 } - 1
            left++
        }
        result = result.coerceAtLeast(right - left)
    }
    return result
}
```
## Review
[The Third Age of JavaScript](https://www.swyx.io/writing/js-third-age/)

### Fist Age 1997 - 2007
从一声巨响开始，到一声哀号结束。

关于 JavaScript 的起源和发展历程可以参考下 Wirfs-Brock Allen 和 Eich Breandan 两位作者写的 [JavaScript: The First 20 Years](https://zenodo.org/record/3707008#.XtPVdy2B124) 这篇论文，Eich 是 JavaScript 的创始人，也是 TC39 的主要参与者，Wirfs-Brock 也一直参与 TC39 的工作。中文翻译版可以参考这里：《[JavaScript 20 年](https://zhuanlan.zhihu.com/p/122334333)》。

（我个人认为应该分为两个阶段，以 Ajax 的出现作为分割点）

### Second Age 2009-2019
开始于诞生了 npm, Node.js, ES5 的 2009 年，随后各种 UI 框架和编译工具拓宽了 JS 的边界。

### Third Age 2020~
#### 清除遗留假设
* 第一个假设是 JS 生态需要依赖 CommonJS，这导致了一系列的妥协。ES Modules 作为它的替代者已经等候多时了。
* 第二个假设是 JavaScript 工具必须由 JavaScript 来构建。Deno 和 Relay 都是用 Rust 开发的，[Brandon Dail](https://twitter.com/aweary/status/1001874375472168960?s=20) 预测这种转变会在 2023 年完成。

#### 合并「工具层」
* Deno 以一种激进的方式重写了 runtime，将测试、代码格式化、linting 和打包这种工作集成在一起
* Rome 在 Node.js 的基础上将这些工作集成在一起
* 越来越多的产品将开发工具和运行环境集成在一起，如 Glitch, Repl.it, Codesandbox, GitHub Codespaces, Stackblitz

## Tips
None

## Share
这几天知乎上面出现了很多关于前端和后端相比谁更高级的问题，在其中一个题目是「[为什么绝大多数架构师都是后端？](https://www.zhihu.com/question/398139772/answer/1254415307)」的问题下发表了下自己的观点：
> 首先，我很向往那个只有「软件开发工程」、「程序员」这种岗位的年代，在那个年代没有那么多前后端的争论，也没有这种没意义的鄙视链的此起彼伏，而是用现在看来最低端的设备开创了个人电脑时代、互联网时代，在那个没有 Github 的年代做出了到现在都还在被广泛使用的开源项目。
> 
> 其次，「前端工程师」、「后端工程师」这种岗位的划分不是一直以来就有的，在这两个概念出现之前大家都是全栈，后来由于技术和互联网行业的发展，各个领域都更加的有深度，前后端都越来越复杂，一个人很难再搞定全部开发工作了，所以出现了岗位的划分。从互联网这个行业的出现到这种岗位划分的出现也就十几年的时间而已，过去的十几年可以发生这些变革，那么未来也一样会发生其他方向的变革。在技术发展的长河中，十几年也只是一个小插曲而已。
> 
> 第三，其实这种变革已经在发生了，各个领域基础设施的发展大大降低了开发成本和技术门槛，在十年前，C10K 还是一个热门话题，现在还有多少人关注呢？在十年前做过高并发、动静分离或者数据库分库分表的就可以称之为架构师了，现在呢？云服务已经很成熟的解决了这些问题，成为了标配。而 ServerLess 这类技术的出现也大大降低了后端开发的门槛，甚至有 Dark 这类产品让人压根都不知道自己是做后端。同样，前端领域也有非常大的变化，十年前用 jQuery 时的幸福感一点都不比现在用 React 差，那时候也没听说过前端还有编译、打包这种概念。
> 
> 说这些并不表示我对技术或者「程序员」这个岗位感到悲观，相反，我对未来非常的乐观，我相信在未来借助技术的发展各个角色都能够发挥更大的价值，前提是要保持理性，如果把自己局限在某个小的范围内，那肯定是很快就会看到天花板的，这个天花板并不是行业给的，而是自己给自己盖上去的。
>
> 再回到具体一点的看法，我认为更科学的岗位划分方式应该是按业务领域来划分，比如 Web 应用工程师、图形工程师、CAD 软件工程师、UI 框架工程师、服务器基础设施工程师、浏览器工程师，把目标聚焦在业务价值上，而不是把自己约束在某个编程语言或者平台。