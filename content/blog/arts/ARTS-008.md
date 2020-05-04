---
title: ARTS 008
date: "2020-05-04 22:24"
description: "ARTS #008"
---
## Algorithm
题目：[Binary Tree Pruning](https://leetcode.com/problems/binary-tree-pruning/)

We are given the head node root of a binary tree, where additionally every node's value is either a 0 or a 1.

Return the same tree where every subtree (of the given tree) not containing a 1 has been removed.

(Recall that the subtree of a node X is X, plus every node that is a descendant of X.)

> Example 1:
> Input: [1,null,0,0,1]
> Output: [1,null,0,null,1]
> 
> xplanation: 
> Only the red nodes satisfy the property "every subtree not containing a 1".
> The diagram on the right represents the answer.

### Solustion
```kotlin
class Solution {
    fun pruneTree(root: TreeNode?): TreeNode? {
        if (root == null) return null

        val node = TreeNode(root.`val`)
        node.left =  pruneTree(root.left)
        node.right = pruneTree(root.right)

        if (node.left == null && node.right == null && node.`val` == 0) {
            return null
        }
        return node
    }
}
```
练习一下递归。（另外，kotlin 对 null 的处理还是挺不错的。）

## Review
[Laws of Software Evolution](https://blog.blankyao.com/laws-of-software-evolution/)

## Tips
好多年不写 C/C++，今天才知道 C/C++ 中的 volatile 和 Java 中的 volatile 不是同一个意思（也有可能是从前知道但是现在已经忘记了）。在 Java 中，volatile 关键字可以保障变量的「可见性」，变量被 volatile 修饰后，JVM 就不会将变量的值缓存在寄存器或者其他缓存中，这样就给了变量可见性，让变量的值在线程之间保持同步，也就是说，是用户多线程场景下的。

而在 C/C++ 中，volatile 的作用是告诉编译器不要对所声明的变量进行常量优化，因为其值是随时都会变化的，跟多线程没有任何关系，当需要读写内存映射设备时就需要用到 volatile。

## Share
> 编程最重要的事情，其实是让写出来的符号，能够简单地对实际或者想象出来的“世界”进行建模。一个程序员最重要的能力，是直觉地看见符号和现实物体之间的对应关系。不管看起来多么酷的语言或者范式，如果必须绕着弯子才能表达程序员心目中的模型，那么它就不是一个很好的语言或者范式。
>
> —— [《编程的宗派》](https://www.yinwang.org/blog-cn/2015/04/03/paradigms)