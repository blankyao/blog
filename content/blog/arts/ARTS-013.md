---
title: ARTS 013
date: "2020-06-07 21:23"
description: "Sketchpad, Partition Labels, 计算机简史"
---
## Review
[Sketchpad](https://en.wikipedia.org/wiki/Sketchpad)

Sketchpad 是 Ivan Sutherland 在 1963 年写的一个程序，并因此在 1988 年获得图灵奖，之所以能获得图灵奖是因为其在多个领域都有开创性的影响：
1. 开创了人机交互的方式，在此之前是没有人机交互这件事情的，计算机的工作方式是「批处理」模式，在需要用计算机时就将表示程序的打孔纸带输入计算机，然后计算机执行程序所指定的任务，在这个过程中是没有人和计算机之间的交互的；
2. 当之无愧的 CAD 的鼻祖；
3. 为 GUI 以及面向对象编程语言提供了灵感；
4. 为 oN-Line System 提供了灵感，啥是 oN-Line System 呢？我们今天用到的所有的计算机相关的东西基本上都和它有关，比如鼠标、显示器、超文本，甚至是互联网；

具体是个怎样的程序？可以看下 [DEMO 视频](https://www.youtube.com/watch?v=zFWBQKrvz24)，或者原始论文 [Sketchpad A man-machine graphical communication system](https://www.cl.cam.ac.uk/techreports/UCAM-CL-TR-574.pdf).

## Algorithm
[Partition Labels](https://leetcode.com/problems/partition-labels/)

A string S of lowercase letters is given. We want to partition this string into as many parts as possible so that each letter appears in at most one part, and return a list of integers representing the size of these parts.

### Solution
```kotlin
fun partitionLabels(S: String): List<Int> {
    val result = mutableListOf<Int>()
    val charLastIndexes = mutableMapOf<Char, Int>()
    val chars = S.toCharArray()

    for (index in chars.indices) {
        charLastIndexes[chars[index]] = index
    }

    var start = 0
    var end = 0
    for (index in chars.indices) {
        end = charLastIndexes[chars[index]]!!.coerceAtLeast(end)
        if (index == end) {
            result.add(end - start + 1)
            start = end + 1
        }
    }
    return result
}
```
## Tips
None

## Share
这周在医院照顾家人，顺便把[《计算机简史》](https://book.douban.com/subject/35043034/)看完了，非常推荐，就像人要了解自己的历史一样，作为计算机从业者，也要了解自己所在行业的历史，通过对历史的观察，创造更有价值的事物。