---
title: C++ Utility Codes
description: Some codes snippets that can come handy in coding problems
author: Gismet Majidov
date: 2025-12-28 03:25:00 +0400
categories: [Competitive programming, C++ helpers]
tags: [c++, competitive programming, coding, utility, programming]
math: true
---

# C++ Helper

## Max heap shorter

```cpp
template<typename T>
using MaxHeap = priority_queue<T>;
```

## Min heap shorter

```cpp
template<typename T>
using MinHeap = priority_queue<T, vector<T>, greater<T>>;
```

### Usage example
```cpp
MinHeap<pair<long long, int>> q;
MaxHeap<double> q;
```