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


## 1D Prefix Sum

```cpp

vector<int> presum(n+1);

for(int i = 1; i <=n; i++){
    presum[i] = presum[i-1] + arr[i-1];
}

//0-index
auto getSum = [&](int l, int r){
    return psum[r+1] - psum[l];
};

```

## 2D Prefix Sum

```cpp
//1-based indexing
vector<vector<int>> presum(m+1, vector<int>(n+1));

for(int i = 1; i <=m; i++){
    for(int j = 1; j<=n; j++){
        presum[i][j] = arr[i-1][j-1] + presum[i][j-1] + presum[i-1][j] - presum[i-1][j-1];
    }
}

//0-index search, (r1, c1) is the top-left corner indices and (r2,c2) for the bottom-right
auto getSum = [&](int r1, int c1, int r2, int c2){
    ++r1, ++c1, ++r2, ++c2;
    return presum[r2][c2] - presum[r1-1][c2] - presum[r2][c1-1] + presum[r1-1][c1-1];
};  
```