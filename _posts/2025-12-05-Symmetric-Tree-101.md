---
title: LeetCode 101. Symmetric Tree
description: Given the root of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).
author: Gismet Majidov
date: 2025-12-05 17:32:00 +0400
categories: [Problem-Solving, LeetCode]
tags: [LeetCode, problem solving, Tree, Depth-First Search, Recursion]
math: true
---

# [LeetCode 101. Symmetric Tree](https://leetcode.com/problems/symmetric-tree/description/)

## Problem Description

Given the `root` of a binary tree, check whether it is a **mirror of itself** (i.e., symmetric around its center).

Example 1:

![LeetCode 101 example 1 image](https://assets.leetcode.com/uploads/2021/02/19/symtree1.jpg)

Output: True

Example 2:

![LeetCode 101 example 2 image](https://assets.leetcode.com/uploads/2021/02/19/symtree2.jpg)

Output: False


## Approach

Consider this **"mirror of itself"**. Imagine you are given two trees and asked to check whether they are mirrors of each other. We start with the roots of each tree. If the roots are both `null`, then we are done, they
are trivially mirrors of each other. If only one of the roots is `null`, then return `false`. Otherwise, we check if the values of the roots are the same. Since they are mirrors of each other, we check if the left subtree of the root of the first tree is the mirror of the right subtree of the root of the second tree and also the right subtree of the root of the first tree is the mirror of the left subtree of the root of the second tree.

## Code

```java

class Solution {

    boolean isMirror(TreeNode root1, TreeNode root2){
        
        if(root1 == null && root2 == null) return true;
        if((root1 == null && root2 != null ) || (root1 != null && root2 == null)) return false;

        return root1.val == root2.val && isMirror(root1.left, root2.right)
        && isMirror(root1.right, root2.left);
    }

    public boolean isSymmetric(TreeNode root) {
        return isMirror(root, root);
    }
}

```
