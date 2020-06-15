---
title: ARTS 014
date: "2020-06-16 00:07"
description: "The Rise and Fall of Commercial Smalltalk, Open the Lock"
---
## Review
[The Rise and Fall of Commercial Smalltalk](http://www.wirfs-brock.com/allen/posts/914)

这篇文章的作者是 [Allen Wirfs-Brock](http://www.wirfs-brock.com/allen/about)，来头非常大，作为 TC39 成员，多年来一直参与 ECMAScript 规范的制定，前几个月还和 Brendan Eich 一块发布了一篇关于 JavaScript 历史的重量级文章 [JavaScript: The First 20 Years](http://www.wirfs-brock.com/allen/posts/866).

Allen 之所以写这篇文章是因为在这之前有一位编程语言领域的专家写了一篇标题为 [Bits of History, Words of Advice](https://gbracha.blogspot.com/2020/05/bits-of-history-words-of-advice.html) 文章，发表了一些关于 Smalltalk 为什么没有流行起来的思考，而 Allen 对其中的大部分观点都不太认同，所以才写了这篇文章，两篇文章对比了一下，感觉 Allen 的这篇文章更有说服力一些。Allen 认为 Smalltalk 没有流行起来主要有以下几个原因：
1. Smalltalk 不只是一个编程语言，它是一个完整的个人计算平台。但是当一般人能够支付得起的能运行 Smalltalk 的个人计算硬件出现的时候，其他对硬件要求更低的平台已经主导了个人计算生态。
2. Xerox Smalltalk 是用来做试验的，没有严肃到可以被广泛使用或者可靠的应用部署。
3. 在生产环境使用 Smalltalk 需要很大的工程团队，在 1980 年代后期没有财大气粗的大公司愿意做这种投资，除了 HP 和 IBM，这种本来可以帮助 Smalltalk 在生产环境使用的大型计算公司，选择了另外一条路。
4. 那些希望将 Smalltalk 变得更强的小公司需要找到一个商业模式来支持这么大的工程努力，最明显的是企业应用开发市场。
5. 要想打开这个市场，需要为客户的一个重要问题提供一个解决方案，这些企业没弄懂的一个问题是如何从「绿屏幕」迁移到具有时尚外观的富客户端应用。
6. 有一些公司曾经相当成功的将 Smalltalk 引入企业市场，但是那些苛刻又变化无常的客户和 Smalltalk 公司高度的聚焦在他们对富客户端的承诺。
7. 因为这种聚焦，这些 Smalltak 公司在 1996 年对 web 浏览器的突然出现以及其在企业中的使用完全没有任何准备。在这时，Sun 作为一个比这些 Smalltalk 技术驱动的公司大非常多的公司，花费了大量精力将 Java 作为 web 和桌面客户端的解决方案来推广。
8. 企业将开发工具的采购从 Smalltalk 转移到可以承诺基于 web 或者 Java 的解决方案的公司。
9. Smalltalk 的收入大幅下降，聚焦在 Smalltalk 技术的公司失败了。
10. 在市场上失败的技术很少能够复活。

最后，再引用一段话：
> It takes incredible luck and timing to become of one of the world’s most widely used programming languages. It’s such a rare event that no language designer should start out with that expectation. You really should have some other motivation to justify your effort.
> 
> But my question for Newspeak and any similar efforts is: What is your goal? What drives the design? What impact do you want to have?
> 
> Smalltalk wasn’t created to rule the software world, it was created to enable the invention of a new software world. I want to hear about compelling visions for the next software world and what we will need to build it. Could Newspeak have such a role?

## Algorithm
[Open the Lock](https://leetcode.com/problems/open-the-lock/)

You have a lock in front of you with 4 circular wheels. Each wheel has 10 slots: '0', '1', '2', '3', '4', '5', '6', '7', '8', '9'. The wheels can rotate freely and wrap around: for example we can turn '9' to be '0', or '0' to be '9'. Each move consists of turning one wheel one slot.

The lock initially starts at '0000', a string representing the state of the 4 wheels.

You are given a list of deadends dead ends, meaning if the lock displays any of these codes, the wheels of the lock will stop turning and you will be unable to open it.

Given a target representing the value of the wheels that will unlock the lock, return the minimum total number of turns required to open the lock, or -1 if it is impossible.

### Solution
```kotlin
class Solution {
    fun openLock(deadends: Array<String>, target: String): Int {
        val visitedSet = HashSet<String>()
        visitedSet.addAll(deadends)
        var step = 0
        val queue = LinkedList<String>()
        queue.add("0000")

        while (queue.size > 0) {
            var nextCount = queue.size
            while (nextCount-- > 0) {
                val current = queue.poll()
                if (visitedSet.contains(current)) continue
                visitedSet.add(current)
                if (current == target) return step

                val nextSteps = nextSteps(current)
                queue.addAll(nextSteps)
            }

            step++
        }
        return -1
    }

    fun nextSteps(current: String): List<String> {
        val result = mutableListOf<String>()
        for (index in current.indices) {
            val currentChar = current.toCharArray()[index]

           result.add(current.substring(0, index) + (if (currentChar == '9') 0 else currentChar - '0' + 1) + current.substring(index + 1))
            result.add(current.substring(0, index) + (if (currentChar == '0') 9 else currentChar - '0' - 1) + current.substring(index + 1))
        }
        return result
    }
}
```