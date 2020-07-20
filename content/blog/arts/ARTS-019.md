---
title: ARTS 019
date: "2020-07-21 00:40:00"
description: "Container With Most Water, Why We Leverage Multi-tenancy in Uber’s Microservice Architecture"
---

## Algorithm
[Container With Most Water](https://leetcode.com/problems/container-with-most-water/)

Given n non-negative integers a1, a2, ..., an , where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

### Solution

```kotlin
fun maxArea(height: IntArray): Int {
    var maxArea = 0
    var start = 0
    var end = height.size - 1

    while (start < end) {
        var currentHeight = 0
        val currentWidth = end - start

        if (height[start] >= height[end]) {
            currentHeight = height[end]
            end--
        } else {
            currentHeight = height[start]
            start++
        }
        maxArea = maxArea.coerceAtLeast(currentWidth * currentHeight)
    }

    return maxArea
}
```

## Review
[Why We Leverage Multi-tenancy in Uber’s Microservice Architecture](https://eng.uber.com/multitenancy-microservice-architecture/)

非常不错的思路，将租户的理念引入到微服务基础设施中去，可以方便的进行并行测试、生产环境测试、金丝雀发布以及流量复制。

## Tips
None

## Share
None