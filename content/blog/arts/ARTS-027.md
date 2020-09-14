---
title: ARTS 027
date: "2020-09-15 00:49:00"
description: "Google Technical Writing; 贾扬清；Construct Binary Tree from Inorder and Postorder Traversal"
---
## Review
学习了一下 Google 的 [Technical Writing](https://developers.google.com/tech-writing/overview?hl=zh-cn) 课程，虽然讲的是英文写作，但是对中文写作也很有帮助，从专业术语到句子再到段落和文档组织，非常完整，值得学习一下。

## Share
周末看了一下贾扬清和知乎 CTO 李大海在知乎做的一个[直播访谈](https://www.zhihu.com/zvideo/1280989974280634368)，非常值得一看，摘出两个比较有价值的观点分享一下：
1. AI 是一个系统工程，90% 的事情和算法无关
2. 没有所谓的「算法工程师」这个角色，要么是做算法研究，要么是做应用开发，中间的「调参侠」是没有长远价值的。算法科研人员的目标是做更好的算法，比如在计算机视觉领域，把模型做的更大更准，在移动端做的更小，是在 general 场景下做创新，「调参侠」的述求是把算法落地到应用里面去，除了调参之外，还要了解实际业务中的各种约束，找到最佳解决方案，端到端的解决问题，所以只是调参是不够的。所以，没有「算法工程师」，只有科研人员和应用工程师。

## Algorithm
[Construct Binary Tree from Inorder and Postorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/)

Given inorder and postorder traversal of a tree, construct the binary tree.

Note:
You may assume that duplicates do not exist in the tree.

### Solution
```kotlin
fun buildTree(inorder: IntArray, postorder: IntArray): TreeNode? {
    if (inorder.isEmpty()) return null
    
    val rootVal = postorder[postorder.size - 1]
    val root = TreeNode(rootVal)
    if (inorder.size == 1) return root
    
    val rootIndexInInorder = inorder.indexOf(rootVal)
    val leftInorder = inorder.copyOfRange(0, rootIndexInInorder)
    val leftPostorder = postorder.copyOfRange(0, rootIndexInInorder)
    root.left = buildTree(leftInorder, leftPostorder)

    val rightInorder = inorder.copyOfRange(rootIndexInInorder + 1, inorder.size)
    val rightPostorder = postorder.copyOfRange(rootIndexInInorder, inorder.size - 1)
    root.right = buildTree(rightInorder, rightPostorder)
    return root
}
```
