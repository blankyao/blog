---
title: ARTS 004
date: "2020-04-05 23:30"
description: "ARTS #004"
---

## Algorithm
题目：[N-Queens](https://leetcode.com/problems/n-queens/)

The n-queens puzzle is the problem of placing n queens on an n×n chessboard such that no two queens attack each other.

![N queens](https://assets.leetcode.com/uploads/2018/10/12/8-queens.png)

Given an integer n, return all distinct solutions to the n-queens puzzle.

Each solution contains a distinct board configuration of the n-queens' placement, where 'Q' and '.' both indicate a queen and an empty space respectively.

```
Input: 4
Output: [
 [".Q..",  // Solution 1
  "...Q",
  "Q...",
  "..Q."],

 ["..Q.",  // Solution 2
  "Q...",
  "...Q",
  ".Q.."]
]
Explanation: There exist two distinct solutions to the 4-queens puzzle as shown above.
```

这个在上篇[介绍 Constraint Programming 的文章](https://blog.blankyao.com/constraint-programming/)里已经有介绍过了，分别用了 backtracking search 和 prolog 来实现，这里就不重复了。

## Review
[REST != CRUD](/restful-not-crud/)

## Tip
在 kotlin 中用 inline 来提高效率。

```kotlin
fun isMultipleOf (number: Int, multipleOf : Int): Boolean{
    return number % multipleOf == 0
}
fun <T> ArrayList<T>.filterOnCondition(condition: (T) -> Boolean): ArrayList<T>{
    val result = arrayListOf<T>()
    for (item in this){
        if (condition(item)){
            result.add(item)
        }
    }
    return result
}
var list = arrayListOf<Int>()
    for (number in 1..10){
        list.add(number)
    }
val resultList = list.filterOnCondition { isMultipleOf(it, 5) }
print(resultList)
```
在这个案例里，我们将 isMultipleOf 方法作为参数传给 filterOnCondition 作为过滤的方法，这时候将 isMultipleOf 标记为 inline 则可以提高效率，因为在函数调用时，对 CPU 来说，要先跳转到这个函数体，然后执行这个函数，最后再跳回到调用这个方法的地方，而如果这个函数是 inline 的，在编译期间就可以将函数替换到调用的地方，这样在执行时就不用跳来跳去了。

## Share
[Constraint Programming](https://blog.blankyao.com/constraint-programming/)。

另外，本周还用了下 RxJava，多种编程思想一起用的感觉会让思维更加的开阔。