---
title: ARTS 035
date: "2020-12-15 23:20:00"
description: "Patterns of resilience; 反脆弱；Task Scheduler"
---

## Review
[Patterns of resilience](https://www2.slideshare.net/ufried/patterns-of-resilience)

韧性模式：
1. 隔离
2. 舱壁
3. 完整参数检查
4. 松耦合
5. 异步通信
6. 位置透明
7. 事件驱动
8. 无状态
9. 松时间约束
10. 幂等
11. 自包含
12. 控制延迟
13. 超时
14. 熔断
15. 快速失败
16. Fan out & quickest reply
17. 有界队列
18. 限流
19. 监管
20. 监控
21. 错误处理
22. 升级

## Share
关于反脆弱：强韧性或复原力在波动性和无序性面前既不会受损也不会受益，而反脆弱性则会从中受益。对于名词叫什么，不是重点，重点是定义这个名词。重点是，在受到伤害，破坏后，最强最好的方式，不是恢复如初，而是要变得比之前更好！

## Algorithm
[Task Scheduler](https://leetcode.com/problems/task-scheduler/)

Given a characters array tasks, representing the tasks a CPU needs to do, where each letter represents a different task. Tasks could be done in any order. Each task is done in one unit of time. For each unit of time, the CPU could complete either one task or just be idle.

However, there is a non-negative integer n that represents the cooldown period between two same tasks (the same letter in the array), that is that there must be at least n units of time between any two same tasks.

Return the least number of units of times that the CPU will take to finish all the given tasks.

### Solution
```kotlin
fun leastInterval(tasks: CharArray, n: Int): Int {
    val taskCount = HashMap<Char, Int>()
    for (char in tasks) {
        taskCount[char] = taskCount.getOrPut(char) {0} + 1
    }

    val queue = PriorityQueue<Int>(compareByDescending { it })
    queue.addAll(taskCount.values)

    var times = 0
    while (!queue.isEmpty()) {
        val tempTaskList = ArrayList<Int>()
        for (i in 0..n) {
            if (!queue.isEmpty()) {
                tempTaskList.add(queue.poll())
            }
        }

        for (task in tempTaskList) {
            if (task - 1 > 0) {
                queue.offer(task - 1)
            }
        }

        times += if (queue.isEmpty()) tempTaskList.size else n + 1
    }
    return times
}
```