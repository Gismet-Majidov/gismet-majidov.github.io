---
title: Programming Tips And Tricks For Problem-solving
description: Here are some practical ideas and tricks 
author: Gismet Majidov
date: 2026-01-01 01:51:00 +0400
categories: [Competitive programming, Ideas and Tricks]
tags: [competitive programming, coding, problem solving, programming, aha-moment ideas]
math: true
---

# Ideas and Tricks

## Unique ID for matrix cells

Use `id = row*colSize + col` where `row` and `col` are the row and column indices of the cell in a matrix/grid. For example, `id` can be used as a key for a hash table. 

## Bit Manipulation

### Check/Set/Clear/Flip a bit

```cpp

bool isSet = (mask&(1<<i)) == 0; //check bit
mask |= (1LL << i); //set bit
mask &= ~(1LL << i); //clear bit
mask ^= (1LL << i); //flip bit

// 1<< i makes an integer with only the i-th bit set

```

### Test if a mask contains another mask

```cpp

bool contains = (mask&sub) == sub;

```

### Turn off the Lowest Set Bit (LSB)

```cpp

mask = mask & (mask - 1);

//subtracting 1 flips the lowest 1 to 0 and all the trailing 0s to 1; AND removes the lowest 1
//Use cases: iterate through set bits fast, DP transitions
```

### Isolate the Lowest Set Bit (lowbit)

```cpp
int lsb = mask & -mask;

//-mask is two's complement; AND isolates the lowest set bit
//Use cases: Fenwick tree, extracting one bit at a time
```


