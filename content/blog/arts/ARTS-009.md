---
title: ARTS 009
date: "2020-05-11 11:11"
description: "ARTS #009"
---
## Algorithm
题目：[Find Largest Value in Each Tree Row](https://leetcode.com/problems/find-largest-value-in-each-tree-row/)

You need to find the largest value in each row of a binary tree.

Example:

>Input: 
>
>          1
>         / \
>        3   2
>       / \   \  
>      5   3   9 
>
> Output: [1, 3, 9]

### Solution
```kotlin
class Solution {
    fun largestValues(root: TreeNode?): List<Int> {
        val result = mutableListOf<Int>()

        if (root == null) return result

        val queue = LinkedList<TreeNode>()
        queue.add(root!!)
        while (queue.size > 0) {
            val curArray = arrayListOf<TreeNode>()
            var max = Int.MIN_VALUE
            while (queue.size > 0) {
                val element = queue.pop()
                curArray.add(element)
                max = max.coerceAtLeast(element.`val`)
            }
            result.add(max)

            for (element in curArray) {
                if (element.left != null) {
                    queue.add(element.left!!)
                }

                if (element.right != null) {
                    queue.add(element.right!!)
                }
            }        
        }
        return result
    }
}
```

## Review
[The Future of Programming](http://worrydream.com/dbx/)

> The most dangerous thought you can have as a creative person is to think you know what you're doing.

1. coding → direct manipulation of data
2. procedures → goals and constraints
3. text dump → spatial representations
4. sequential → concurrent

这个演讲信息量非常大，我这里只是简单摘录了一下，对里面更详细的内容还在一点点研究。

## Tips
None

## Share
> 一个临床大夫，有从事临床研究的兴趣，有参加高质量临床试验的经历，并牵头完成了至少一项临床试验，并且这个临床试验的结果为临床诊疗提供了有价值的证据，在一定程度上改变了临床实践。那么，这个临床大夫就可以称之为 Physician scientist。

我是 Engineer Scientist.
