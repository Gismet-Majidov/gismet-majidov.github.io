---
title: Pigeonhole Principle
description: A surprisingly simple idea that has numerous applications in varity of problems. 
author: Gismet Majidov
date: 2026-01-15 00:34:00 +0400
categories: [Math, Proof methods]
tags: [proof, math, problem solving]
math: true
---

# Pigeonhole Principle

`If k pigeons fly to n pigeonholes where k > n, then there must be at least one pigeonhole that contains more than one pigeon` - As simple as it sounds, this idea has remarkable significance in various problems and proofs. 

There is almost no need for a formal proof of this principle. It is perfectly intutive as it is. But let's state it more formaly. 

> A function from one finite set to another smaller finite set is not one-to-one: There must be at least two elements in the domain that have the same image in the co-domain. 
{:.definition}

Without giving a formal treatment of the above defintion, let's take a look at a few problems to see the application of this principle. 

## Problem 1. People with the same birth month

**Among 13 people, is it the case that there must be at least two people who were born in the same month?**

Let's try to map the set of people to the set of months. The size of the set of people is 13 and the size of the set of months is 12, therefore by the above definition there must be at least two people who were born on the same month. A rather simple way to think about it is to assign each person to one month, after assigning 12 people to 12 different months, the final 13-th person must be assigned to one of the months which was already assigned a person. This tells us there is a month on which two people were born. 

## Problem 2. Two numbers that sum to 9

**Let $A = \\{1, 2, 3, 4, 5, 6, 7, 8\\}$.**

1. If four numbers are selected from $A$, there must be at least one pair of integers that hae a sum of 9.
2. If five numbers are selected from $A$, there must be at least one pair of integers that have a sum of 9.

The conclustion of statement 1 is false. For example one can select 1, 2, 3, 4, yet there is no pair of integesr that have a sum of 9. The conclustion of statement 2 is true. We can certainly select 5 numbers so that there is a pair of integers with sum of 9. For example, here is one: $\\{1, 2, 3, 4, 5\\}$. It is good to find a single example that works, however it is neither convincing nor interesting without a proof. Let's see a proof of this. 

First, let's consider what pairs of numbers add up to 9. There are 4 possible such set of integers from set $A$. 

$\\{1, 8\\}, \\{2,7\\}, \\{3, 6\\}, \\{4, 5\\}$

You can view each of these four disjoint sets as **pigeonhole** and each of the 5 integers to be selected as **pigeon**. So we have **5** pigeons that fly to four **pigeonholes**. Then one of these pigeonholes must contain two pigeons, namely among the 5 selected integers, at least two must be in the same set. We can again thihnk more simply. Obviously, if we select two numbers from the same set, we are done. That is the trivial case. Let's select one integer from each set. But this way we can only select 4 integers. The 5-th integer must be one of the four sets from each of which we have already selected a number. 

{We will continue...}