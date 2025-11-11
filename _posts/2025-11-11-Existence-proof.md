---
title: Existence proof - A simple yet an interesting problem
description: Show that a solution exist for this easy problem :)
author: Gismet Majidov
date: 2025-11-11 22:40:00 +0800
categories: [Maths, Proof]
tags: [proofs, problem solving]
math: true
---


# Is it possible? 

## Problem

A lone philosopher starts climbing a mountain 6 AM and he reaches the top of the mountain at 10 PM. There he rests for the night. Next day he starts descending the mountain at 6 AM and reaches the bottom at 10 PM. Show that there was a certain time of the day when the philosopher was at the same height on both days. 


> Note that it is not necessary for the philosopher to travel at the same speed on both days. He may slow down, even stop for some moment before he continues. The only certain thing is that he starts his journy at 6 AM and ends it at 10 PM on both days. 
{: .prompt-info}

**Take a moment and ponder about it!**

## What you might have thought

One can think that this is a long journey (16 hours) and most likly there indeed exists such a time. Not bad but this idea would neither impress nor convince someone. Then you may desparately search for a time that would satisfy our need. But what time? is it 8:34 AM or maybe 9:12 PM? how do you know? You don't. 

## Your final answer

You may be still stuck in finding a specific time but after a while, you realize that your attemps at finds a specific time is futile. To reach this realization, you might reason as follows. `I say that philosopher was at the same height at 2:00 PM on both days. But wait! it doesn't feel right. What if he was not. What if at 2:00 PM he was at a height of 100 meters when he was ascending, (day 1) and he was at a height of 120 meters height when descending (day 2). Hmm... on day 2, he was descending from 120 meters height at 2:00 PM while he was going up from 100 meters on day 1 at that time. There is like 20 meters between these two heights and this difference gets smaller and smaller. It is like two people going towards each other, one is currently at the height of 100 and is going up and the other is at the height of 120 meters and is going down. So they must meet at the same point at a **specific time**. This shows that there is actually a certain time when the philosopher was at the same height on both days. There is nothing special about two these heights of 100 and 120 meters. It could be anything.`

So the idea is to think of two different philosophers - one at the bottom of the mountain at 6:00 AM and the other at the top of the mountain at 6:00 AM. They start their journey. One goes towards the top and the ohter goes towards the bottom. **What is inevitable?** that they will encounter each other on their way and the time of this encounter is the time for our problem - the time when the philosopher was at the same height on both days. We represent the philosopher on two different days as two different philosophers on a single day such that one is going up and the other is going down. Regardless of how they travel their journey, we know that **'they'** must meet eventually. And when they meet, we got our answer :). 


## Existence Proofs

This was a fun example of existance proof - specifically non-constructive existance proof. In general, when you are asked to show whether a certain object (in the above problem it was time, i know it sounds weird) exist that satisfies a particular condition. If I asked you to show that there is an integer `x` such that $x^2 = 4$, you would tell me that this is true and `x` is 2. So you find the object (`x`) in this case. Finding x itself showed that there is such an integer. 

This is an example of `constuctive existence proof` where you literally find the object that satisfies the condition. But sometimes finding that object is not easy. Sometimes It can even be the case that such an object does not exist. You would be wasting time, trying to find that object. Other times, it can actually be not easy (or practically not meaningful) to find the object even though you belive it exists. For our philosopher problem, finding the actuall time is not actually meaningful but we were able to show that there exists such a time. Ideally you should find the object if possible but if it is not so easy, then it is enough to find a process through which we can conclude that there exists such an object. This way of proving existence is called `non-constructive existence proof` where you don't actually find the object but just show a way that there must be one. 

For more, just search a few key terms from here on internet. 