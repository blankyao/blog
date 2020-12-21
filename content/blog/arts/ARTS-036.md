---
title: ARTS 036
date: "2020-12-21 23:22:00"
description: "making computers better; 管理的范式；Word Break"
---

## Review
[making computers better](https://adamwiggins.com/making-computers-better/)

信息时代发展到今天，电脑已经无处不在了，但是作者认为我们还远未达到顶点，这也是作者投身于「让电脑变得更好」这个目标的原因，作者认为更好的电脑有以下几个特征：

1. 辅助并且鼓励人类高尚的追求：科学、理性、艺术、哲学。
2. 直接支持人类的精神健康、身体健康、繁荣和幸福。
3. 帮助我们控制有问题的倾向（至少不会增强）：上瘾、身份焦虑、社会经济分裂、部落主义、恐惧、仇恨。

另外，作者分别从以下几个方面来分析如何让电脑变得更好：

1. 如何进行身份认证
2. 如何保存数据并进行协作
3. 如何和工具交互
4. 如何管理注意力
5. 如何为软件付费
6. 如何制作并分发软件

这篇文章的作者叫 Adam Wiggins, 虽然名气不大，但其实为软件开发领域做出了很大的贡献，作为 [Heroku](https://www.heroku.com/) 的创始人，发明了全新的 web 应用开发方式，也就是我们现在所说的 PaaS, 把 Heroku 卖给 Salesforce 后，Adam 又成立了 [Ink & Switch](https://www.inkandswitch.com/) 实验室，专门研究如何用数字设备来改进创作和效率，同时开始相关领域的投资，目前在做 [Muse](https://museapp.com) 这款 App.

作为一个每天花大量时间在使用电脑的软件开发工程师，我也非常希望电脑、操作系统以及软件都能有革命式的改进。

## Share
管理的范式：
1. 萃取优秀员工的经验，找到「输入和输出」
2. 统一交付标准
3. 用工具落地流程，流程要变成文件，变成工作指南
4. 以客户为导向打破部门墙

## Algorithm
[Word Break](https://leetcode.com/problems/word-break/)

Given a non-empty string s and a dictionary wordDict containing a list of non-empty words, determine if s can be segmented into a space-separated sequence of one or more dictionary words.

### Solution
```kotlin
fun wordBreak(s: String, wordDict: List<String>): Boolean {
    val canSegment = BooleanArray(s.length + 1)
    canSegment[0] = true

    for (end in 1..s.length) {
        for (start in 0 until end) {
            if (canSegment[start] && wordDict.contains(s.substring(start, end))) {
                canSegment[end] = true
                break
            }
        }
    }

    return canSegment[s.length]
}
```