---
title: LeetCode 3584 Maximum Product of First and Last Elements of a Subsequence 
description: You are given an integer array nums and an integer m. Return the maximum product of the first and last elements of any subsequence of nums of size m.
author: Gismet Majidov
date: 2025-11-29 14:40:00 +0400
categories: [Problem-Solving, LeetCode]
tags: [LeetCode, Greedy]
math: true
---


# [3584. Maximum Product of First and Last Elements of a Subsequence](https://leetcode.com/problems/maximum-product-of-first-and-last-elements-of-a-subsequence/description/)

## Problem Description

You are given an integer array `nums` and an integer `m`.

Return the **maximum** product of the `first` and `last` elements of any subsequence of `nums` of size `m`.


**Example 1:**

Input: nums = [-1,-9,2,3,-2,-3,1], m = 1

Output: 81

**Explanation**:

`The subsequence [-9] has the largest product of the first and last elements: -9 * -9 = 81. Therefore, the answer is 81.`

**Example 2:**

Input: nums = [1,3,-5,5,6,-4], m = 3

Output: 20

**Explanation:**

`The subsequence [-5, 6, -4] has the largest product of the first and last elements.`

**Example 3:**

Input: nums = [2,-1,2,-6,5,2,-5,7], m = 2

Output: 35

**Explanation**:

`The subsequence [5, 7] has the largest product of the first and last elements.`
 

**Constraints**:

 * 1 <= nums.length <= $10^5$
 * -$10^5$ <= nums[i] <= $10^5$
 * 1 <= m <= nums.length


## Thought Process

> Essentially we multiply two numbers in the array such that there are at least m - 2 numbers between them.
> Let's choose some element at index i as the first element of the subsequence. Then as the last element 
> of the subsequence we can choose any of the elements at least m - 1 away from the index i. Namely, 
> nums[i + m - 1], nums[i + m], nums[i + m + 1] ... nums[n]. When is the product of two numbers maximum?
> Well, if the current number is negative, then multiplying it by the smallest number gives us the maximum possible.
> Otherwise, we should multiply the current number by the maximum number to obtain the maximum product. 
>    
> Okay, then it is enough to know the maximum and the minimum of suffixes of the array. For a chose index i, we should know
> the minmum or the maximum element among nums[i + m - 1], nums[i + m], nums[i + m + 1] ... nums[n]. What can we use here to get maximum and the minimum? Well, we can precompute the max and min values for every suffix. We can have, for example, minNums array such that minNums[i] is the minimum element in the suffix nums[i ... n]. Furthermore, we can calculate these values and the answer in a singel pass (in a single loop).
{: .thought}


## Code 

```java
class Solution {
    public long maximumProduct(int[] nums, int m) {
        long ans = -(long)1e13;
        int n = nums.length;
        int[] minNums = new int[n + 1];
        int[] maxNums = new int[n + 1];
        minNums[n] = (int)1e6;
        maxNums[n] = -(int)1e6;

        //For every i, assume it is the start of the sequence
        for(int i = n - 1; i >= 0; i--){
            minNums[i] = Math.min(nums[i], minNums[i + 1]); //min element from index i to n
            maxNums[i] = Math.max(nums[i], maxNums[i + 1]); //the same for max
            //at least m elements including the current element
            if(i + m - 1 < n){ //within bounds 
                if(nums[i] < 0) ans = Math.max(ans, (long)nums[i] * minNums[i + m - 1]);
                else ans = Math.max(ans, (long)nums[i] * maxNums[i + m - 1]);
            }
        }

        return ans;
    }
}
```