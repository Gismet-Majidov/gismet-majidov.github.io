---
title: Every composite integer has a divisor less than or equal to its square root. But why?
description: For any composit integer, it has always a divisor less than or equal to its square root. 
author: Gismet Majidov
date: 2025-11-18 23:02:00 +0400
categories: [Math, Proof]
tags: [number theory, math, proof]
math: true
---

# Proof

Any composite integer `N` can be written as $ N = a * b $ where $1 < a, b < N$.

At least one of these two divisors `a` and `b` must be less than or equal to  $\sqrt{N}$.

Let's assume that both `a` and `b` are greater than $\sqrt{N}$. Then $a*b > N$. That is a **contradiction**. Therefore it must be the case that at least one of the divisors is less than or equal to $\sqrt{N}$. 