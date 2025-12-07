---
title: LeetCode 871. Minimum Number of Refueling Stops
description: Find the minimum number of refueling stops to reach the target position
author: Gismet Majidov
date: 2025-12-07 13:48:00 +0400
categories: [Problem-Solving, LeetCode]
tags: [LeetCode, problem solving, Greedy, Priority queue, regret greedy]
math: true
---

# Problem Description

A car travels from a starting position to a destination which is `target` miles east of the starting position.

There are gas stations along the way. The gas stations are represented as an array `stations` where `stations[i] = [positioni, fueli]` indicates that the `ith` gas station is $position_i$ miles east of the starting position and has $fuel_i$ liters of gas.

The car starts with an infinite tank of gas, which initially has `startFuel` liters of fuel in it. It uses **one** liter of gas **per one mile** that it drives. When the car reaches a gas station, it may stop and refuel, transferring all the gas from the station into the car.

Return the **minimum** number of refueling stops the car must make in order to reach its destination. If it **cannot** reach the destination, return **-1**.

Note that if the car reaches a gas station with **0** fuel left, the car can still refuel there. If the car reaches the destination with **0** fuel left, it is still considered to have arrived.


## Thought Process 

We have gas stations along the way from starting position to the target. When might we want to refuel? I can't see future gas stations. So it is hard to tell whether we should refuel at this gas station or not? What happens if I don't refuel ? because, after all, I want to minimize the number of refueling stations. Well, a possible scenario is that we run out of feul before we make it to the next gas station or to the target position. What should I do in such a scenario? Imagine we are in a real car and drive from start to target. We didn't fuel previously and unfortunately couldn't make it to the next gas station. What would we say? For example, we would say - "Oh, I wish I had refueled my tank in one of the previous stations, ideally in a station with the most fuel". Exactly, this is the idea. I mean, this may not be possible in real life unless somebody else drives back and brings us the fuel. But here we can simulate this "regretful" situation. 


## Approach

We can have a **`pos`** variable that denotes the current position we are at. We have **`fuel`** amount of fuel. With this fuel,the maximum position we can reach is **`pos += fuel`** position.  If our **`pos`** is equal to or greater than the **`target`**, then we are done. Otherwise, we have to continue. Till we reach the current position **`pos`**, we might have passed some gas stations. To go from the position **`pos`** forward, we need to refuel (keep in mind that **`pos`** is less than target, so we have to continue). Where do we refuel? or rather where should we have refueled? Of course, at one of the previous stations that we may have possibly passed. Here we have to make a greedy choice. From the previous gas stations where we didn't refuel, we should choose the one with the most fuel. For this, we can use set or priority queue data structure. I used priority queue as it naturally fits the situation. And we don't forget to update the answer (increase **`cnt`**).


## Code

```java
class Solution {
    public int minRefuelStops(int target, int startFuel, int[][] stations)  {
        
        int n = stations.length;
        long fuel = startFuel, pos = 0;
        int cnt = 0;
        int idx = 0;

        PriorityQueue<Integer> q = new PriorityQueue((a, b) -> {
            return (int)b - (int)a;
        }); // a and b are treated as Object by Java, so cast it into the appropriate type


        // first pos is increased by fuel and then the comparison is done
        while( (pos += fuel) < target){
            while(idx < n && pos >= stations[idx][0]){ //till pos, there may be gas stations
                q.add(stations[idx][1]);
                ++idx;
            }
            //No previous gas stations to get fuel, we fail to reach target, return -1
            if(q.isEmpty()) return -1;
            fuel = q.poll();
            cnt++;
        }

        //after the loop, it is certain that we have reached the target.
        //(because the while loop ends in two cases: either q is empty and return -1 or the loop condition is no longer satisfied, which means we have reached pass target)
        return cnt;
    }
}
```