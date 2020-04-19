---
title: ARTS 006
date: "2020-04-19 23:30"
description: "ARTS #006"
---
## Algorithm
题目：[Maximum Level Sum of a Binary Tree](https://leetcode.com/problems/maximum-level-sum-of-a-binary-tree/)

Given the root of a binary tree, the level of its root is 1, the level of its children is 2, and so on.

Return the smallest level X such that the sum of all the values of nodes at level X is maximal.

Example:
> Input: [1,7,0,7,-8,null,null]
>
> Output: 2
>
> Explanation: 
> 
> Level 1 sum = 1.
> 
> Level 2 sum = 7 + 0 = 7.
> 
> Level 3 sum = 7 + -8 = -1.
>
> So we return the level with the maximum sum which is level 2.

### Solution
```java
class Solution {
    public int maxLevelSum(TreeNode root) {
        ArrayList<Integer> sums = new ArrayList<>();
        this.dfs(root, 0, sums);
        int maxLevel = 0;
        int max = 0;
        for (int i = 0; i < sums.size(); i++) {
            if (sums.get(i) > max) {
                max = sums.get(i);
                maxLevel = i;
            }
        }
        return maxLevel + 1;
    }
    
    public void dfs(TreeNode node, int level, ArrayList<Integer> sums) {
        if (node == null) return;
        
        if (sums.size() == level) {
            sums.add(node.val);
        } else {
            sums.set(level, sums.get(level) + node.val);
        }
        
        dfs(node.left, level + 1, sums);
        dfs(node.right, level + 1, sums);
    }
}
```
## Review
[Review | Dark's Philosophy](https://blog.blankyao.com/dark-philosophy/)

## Tips
为什么在 kotlin 可以直接写 ```123.toString()```，而在 Java 里面却不可以呢？看这里 —— [「Java里把int基本类型变成Integer包装类，有啥用？」](https://www.zhihu.com/question/375456014/answer/1063333033)

## Share
Null