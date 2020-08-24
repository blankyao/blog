---
title: ARTS 024
date: "2020-08-24 23:37:00"
description: "As We May Think; Word Search"
---
## Review
[As We May Think](https://www.w3.org/History/1945/vbush/vbush.shtml)

如果不是这篇文章，可能计算机还只是一个计算工具。在文章的开头 Vannevar Bush 提到孟德尔的生物进化法则有几代之久都不为人所知，只是因为他的书没能被能够掌握并发展它的人看到，大量真正有意义的成果由于没有后续积累而丧失了，出版物已经大大超出了人们使用它们的能力，所以应该有更好的方式对知识进行记录、存储以及检索。Vannevar Bush 认为在严格的数学逻辑基础之上，将能开发用于日常事务的逻辑应用，这绝对是一个开创性的想法，要知道那时候还是用打孔卡作为输入方式让计算机执行计算的时代。最后，Vannevar Bush 提出来了 MEMEX 的设想，MEMEX 是一个机械化的个人图书馆，采用缩微胶片进行资料的存储，通过代码进行索引，在键盘上敲一下代码就会自动的将对应的资料投影到桌面上，另外还提出了「索引」的概念（超文本的原型），这样任何资料都可以随意的选出来，并且可以快速地找到相关资料。

## Share
林迪效应认为，对于不会自然消亡的事物，如一项技术或一个想法，其预期寿命与其当前的生命成正比；即，只要这一事物多存活一天，就意味着其预期生寿命会更长一些。

## Algorithm
[Word Search](https://leetcode.com/problems/word-search/)

Given a 2D board and a word, find if the word exists in the grid.

The word can be constructed from letters of sequentially adjacent cell, where "adjacent" cells are those horizontally or vertically neighboring. The same letter cell may not be used more than once.

Example:

> board =
>
> [
>
>  ['A','B','C','E'],
>
>  ['S','F','C','S'],
>
>  ['A','D','E','E']
> 
> ]
> 
> Given word = "ABCCED", return true.
> Given word = "SEE", return true.
> Given word = "ABCB", return false.

### Solution
```kotlin
class Solution {
    fun exist(board: Array<CharArray>, word: String): Boolean {
        for (y in board.indices) {
            for (x in board[y].indices) {
                if (search(board, x, y, word, 0)) return true
            }
        }
        return false
    }

    fun search(board: Array<CharArray>, x: Int, y: Int, word: String, index: Int): Boolean {
        if (index == word.length) return true
        if (x == -1 || y == -1 || y == board.size || x == board[y].size) return false
        if (board[y][x] != word[index]) return false

        val temp = board[y][x]
        board[y][x] = ' '
        val exist = search(board, x + 1, y, word, index + 1)
                || search(board, x - 1, y, word, index + 1)
                || search(board, x, y + 1, word, index + 1)
                || search(board, x, y - 1, word, index + 1)
        board[y][x] = temp
        return exist
    }
}
```