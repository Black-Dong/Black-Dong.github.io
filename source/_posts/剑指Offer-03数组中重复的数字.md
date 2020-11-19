---
title: 剑指Offer-03数组中重复的数字
date: 2020-11-19 10:47:30
tags:
    - Java
    - 剑指Offer
categories:
    - Java
    - 剑指Offer
---

* 一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。

<!-- more -->


### 剑指Offer-03数组中重复的数字
```
输入：[2, 3, 1, 0, 2, 5, 3]
输出：2 或 3
限制：2 <= n <= 100000
```

> 思路 1: 
>> 新建一个最大值长度的数组，将值放入值下标对应位置，若在放置过程中出现对应下标已有值，则直接返回。
>
> 思路 2:
>> 将数组中的值放入一个Map中（当Key）或Set中，使用containsKey或contains判断是否存在，存在则直接返回，不存在放入。
> 具体实现:
>> ```java
class Solution {
    public int findRepeatNumber(int[] nums) {
        Set<Integer> tempSet = new HashSet<>();
        for (int num : nums) {
            if (tempSet.contains(num)) {
                return num;
            }
            tempSet.add(num);
        }
        return nums[0];
    }
}
```
