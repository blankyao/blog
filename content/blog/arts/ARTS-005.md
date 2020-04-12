---
title: ARTS 005
date: "2020-04-13 00:15"
description: "ARTS #005"
---

## Algorithm
题目：[Reduce Array Size to The Half](https://leetcode.com/problems/reduce-array-size-to-the-half/)

Given an array arr.  You can choose a set of integers and remove all the occurrences of these integers in the array.

Return the minimum size of the set so that at least half of the integers of the array are removed.

Example:
> Input: arr = [3,3,3,3,5,5,5,2,2,7]
>
> Output: 2
>
> Explanation: Choosing {3,7} will make the new array [5,5,5,2,2] which has size 5 (i.e equal to half of the size of the old array).
>
> Possible sets of size 2 are {3,5},{3,2},{5,2}.
>
> Choosing set {2,7} is not possible as it will make the new array [3,3,3,3,5,5,5] which has size greater than half of the size of the old array.

### Solution
```java
class Solution {
    public int minSetSize(int[] arr) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < arr.length; i++) {
            map.put(arr[i], map.getOrDefault(arr[i], 0) + 1);
        }

        int[] count = new int[arr.length + 1];
        for(int key : map.keySet()) {
            count[map.get(key)]++;
        }

        int steps = 0;
        int deleted = 0;
        for (int i = arr.length; i > 0; i--) {
            for (int j = 0; j < count[i]; j++) {
                steps++;
                deleted += i;
                if (deleted >= arr.length/2) return steps;
            }
        }
        return 0;
    }
}
```

第一次做的时候把数组元素按出现的次数排了个序，比较直观的做法，但是会导致 Time Limit Exceeded，后来在评论区里看到了不需要排序的做法就又改进了一下，思路还是挺巧妙的，没做排序，但是把元素出现的次数放在了数组的索引里，这样只要从后往前遍历就肯定是按从大到小的顺序了。

## Review
[Review | End-user programming](https://blog.blankyao.com/end-user-programming/)

## Tips
最近在用 RxJava，虽然之前了解过，但是没实际用过，所以在用的时候还是遇到了挺多不太理解的问题，查资料时看到 [What happens when we subscribe to a stream? A look inside RxJava](https://medium.com/@wasyl/what-happens-when-we-subscribe-to-rxjava-stream-d2d430febfd4) 这篇文章，文章不长，但是把 RxJava 各种操作背后的逻辑都讲清楚了，推荐。

## Share
这次的 Review 讲的是 End-user programming，其实现在有一些工具正是在基于这个理念在设计，比如我每天都在使用的 Notion，简洁、灵活又不失强大，youtube 上有一个[关于 Notion 使用的经验分享](https://www.youtube.com/watch?v=m9S5I3pWz94)，从视频里可以看到 Notion 可以如何更好的提高效率，如果你心动了，可以用[这个邀请链接](https://www.notion.so/?r=f258077dc70145da9dda68791e5eb7b3)进行注册。