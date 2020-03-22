---
title: ARTS 002
date: "2020-03-22 23:47"
description: "ARTS #002"
---

## Algorithm
题目：[Combination Sum](https://leetcode.com/problems/combination-sum/)

Given a set of candidate numbers (candidates) (without duplicates) and a target number (target), find all unique combinations in candidates where the candidate numbers sums to target.

The same repeated number may be chosen from candidates unlimited number of times.

Note:

All numbers (including target) will be positive integers.
The solution set must not contain duplicate combinations.

Example:
```
Input: candidates = [2,3,6,7], target = 7,
A solution set is:
[
  [7],
  [2,2,3]
]
```

### Solution
```java
class Solution {
    public  List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> result = new ArrayList<>();
        combination(candidates, target, result, new ArrayList<>(), 0);
        return result;
    }

    public  void combination(int[] candidates, int target, List<List<Integer>> result, List<Integer> solution, int startIndex) {
        if (target == 0) {
            List<Integer> solutionCopy = new ArrayList<>(solution);
            result.add(solutionCopy);
            return;
        } else if (target < 0) {
            return;
        }

        for (int i = startIndex; i < candidates.length; i++) {
            solution.add(candidates[i]);
            combination(candidates, target - candidates[i], result, solution, i);
            solution.remove(solution.size() - 1);
        }
    }
}
```
我是用 backtracking 来解的，也可以用 dynamic programming 来解。

## Review
[How Microsoft Lost the API War](https://blog.blankyao.com/how-microsoft-lost-the-api-war/)

## Tip
backtracking 算法中的三个关键点：
1. In each recursive call to the backtracking algorithm, we need to make exactly one decision, and our choice must be consistent with all previous decisions.
2. When we design new recursive backtracking algorithms, we must ﬁgure out in advance what information we will need about past decisions in the middle of the algorithm. If this information is nontrivial, our recursive algorithm might need to solve a more general problem than the one we were originally asked to solve.
3. Try all possibilities for the next decision that are consistent with past decisions, and let the Recursion Fairy worry about the rest. No being clever here. No skipping “obviously” stupid choices. **Try everything. You can make the algorithm faster later.**

## Share
前几天在 [ZEIT](https://zeit.co) CEO [Guillermo Rauch](https://twitter.com/rauchg) 的 [2019 年回顾](https://rauchg.com/2020/2019-in-review) 里看到一个对原生应用的观点
> Native means Platform Fidelity, not Native Code.

一般来说，我们把用 JS 这种无法编译为平台原生二进制可执行文件的开发方式称为不是原生应用，但是 Rauch 认为这个判断标准是不合理的，应该改为「如果一个应用达到了所使用平台的质量标准，就应该被称为是原生的」。这也解释了为什么 Electron 这么成功的把 Web 技术栈推向了桌面端。是否是原生和 HTML 以及 JS 的性能没关系，重要的是应用是否能达到平台的标准，事实也证明，有一些基于 React Native 或者 Electron 开发的应用完全达到了这个标准，所以，当我们听到或者看到一个应用不是用所谓的原生的方式开发时不要立即就打上性能差、体验差的标签。

另外，Rauch 还预测在移动端也会有类似 React Native 的技术会像 Electron 一样成功。

[The new API is HTML.](https://blog.blankyao.com/how-microsoft-lost-the-api-war/)