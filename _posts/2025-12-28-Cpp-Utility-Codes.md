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

## Binary search for the custome types

```cpp

// find the first event whose start is greater than the end of the current event
auto it = upper_bound(events.begin(), events.end(), events[i][1],
                [](int end, const vector<int>& event){
                    return end < event[0];
                }); //in the comparator, the first one is the value based on which you want to search and the second parameter's type is the type of the elements in the array (container)

auto it = lower_bound(arr.begin(), arr.end(), arr[i].age, [](const Person& person, int age){
    return person.age < age;
}); //for the lower_bound, the search value comes second
```