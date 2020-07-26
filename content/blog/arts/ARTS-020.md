---
title: ARTS 020
date: "2020-07-26 23:57:00"
description: "Decode String, React Native Team Principles, 吴庆瑞"
---

## Algorithm
[Decode String](https://leetcode.com/problems/decode-string/)
Given an encoded string, return its decoded string.

The encoding rule is: k[encoded_string], where the encoded_string inside the square brackets is being repeated exactly k times. Note that k is guaranteed to be a positive integer.

You may assume that the input string is always valid; No extra white spaces, square brackets are well-formed, etc.

Furthermore, you may assume that the original data does not contain any digits and that digits are only for those repeat numbers, k. For example, there won't be input like 3a or 2[4].

### Solution
```kotlin
fun decodeString(s: String): String {
    val queue = LinkedList<Char>()
    for (char in s) {
        queue.add(char)
    }
    return doDecode(queue)
}

fun doDecode(queue: LinkedList<Char>) : String {
    var string = ""
    var count = 0
    var innerString = ""
    loop@ while (queue.size > 0) {
        val char = queue.pop()
        when {
            char.isDigit() -> {
                count = count * 10 + (char.toInt() - '0'.toInt())
            }
            char == '[' -> {
                innerString = doDecode(queue)
                while (count-- > 0) {
                    string += innerString
                }
                count = 0
            }
            char == ']' -> {
                break@loop;
            }
            else -> {
                string += char
            }
        }
    }

    return string
}
```
## Review
[React Native Team Principles](https://reactnative.dev/blog/2020/07/17/react-native-principles)

React Native 团队 Manager 公布了团队内部坚持的原则，单纯从原则的内容上来说并没什么特殊之处，重要的是这个产品有自己的原则，而且有原则背后的思考，这是我们值得去借鉴的。原则内容如下：
* 原生体验
* 大规模扩展
* 开发者效率
* 所有平台
* 声明式 UI

## Tips
None

## Share
这次分享个和技术无关的观点，前阵子在微博上看了讲新加坡和马来西亚分家的[系列文章](https://weibo.com/a/hot/7587104350083073_1.html)，其中有一篇讲到了吴庆瑞，吴庆瑞是李光耀的一个非常重要的合作伙伴，曾经负责过新加坡多个部门，像财政部、国防部、教育部等看起来毫无关系的部门，李光耀在给吴庆瑞的悼词里面的一段话对我的触动挺大，是这么写的：

> 当问题解决后，他在1970年重新回到国防部。他精通军事课题，阅读孙子、克劳塞维茨和利德尔·哈特的经典战略书籍。他订阅军事期刊，以掌握最新的武器资讯。他唯一的军事背景是在卫国军担任中士。**他在这些书籍和文章标上记号然后传给我阅读，坚持我一定要掌握足够的知识才能决定该批准哪些项目。我必须先阅读这些资料，然后与他认真讨论该添购哪些武器**。他实际上是我们武装部队的总参谋长 。

重点是我加粗的部分。为什么对我触动那么大呢？因为在工作和生活中遇到过太多走流程的形式主义了，而身为总理，竟然是需要掌握足够的知识才能去做审批，而不是靠自己的下属或者下属的信息来做决策。我想这是新加坡能成为奇迹的重要因素吧。