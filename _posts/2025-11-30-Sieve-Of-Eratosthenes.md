---
title: Sieve of Eratosthenes - Or How to Hunt Primes
description: Sift the Two's and Sift the Three's. The Sieve of Eratosthenes. When the multiples sublime,The numbers that remain are Prime.
author: Gismet Majidov
date: 2025-11-30 15:7:00 +0400
categories: [Maths, Number Theory]
tags: [math, number theory]
math: true
---


# Sieve of Eratosthenes

Sieve of Eratosthenes is an ancient method of sorting out primes up to a given limit. It works by marking multiples of primes up to the given limit. At the end of the process, what remains is prime numbers. 

Let's demonstrate an example. 

`2, 3, 4, 5, 6, 7, 8, 9, 10`

We start with **2** as the first prime and mark its multiples as non-prime (to show marking, I chose to remove them). 

`2, 3, 5, 7, 9`.

Now we don't have any multiples of **2** except **2** itself as it is a prime. **The next number in the list must be a prime**[^1]. Now we continue with **3**. Let's mark its multiples.

`2, 3, 5, 7`

Then we do the same for **5** and **7**. In this case, they don't have any multiples left in the list. At the end of this process, we have the list `2, 3, 5, 7`, which is the list of all the primes up to 10. 


I leave an demonstration of this process below. 

![Animation of Sieve of Eratosthenes](../assets/img/math/Animation_Sieve_of_Eratosth.gif)*Animation of Sieve of Eratosthenes. Source: Wikipedia*


You may want to read more about Sieve of Eratothenes [here](https://en.wikipedia.org/wiki/Sieve_of_Eratosthenes).

[^1]: Let's prove this statement. Let us assume that the next number **n** is a composite number. Then **n** has at least one prime divisor, which is less than itself. We know that the multiples of every prime number **less** than **n** have already been marked. This implies that **n** must have been marked as it has at least one prime divisor less than itself. But this contradicts the fact that **it is the next number in the list**. Therefore it must be the case that **n** has no prime divisor less than itself. This means **n**  is the only primem divisor of **n**, thus **n** is a prime number.  


## Implementation of the Algorithm in Java

Basic implementation is as follows. 

1. Create a list of **N** numbers
2. Let **p** be the first prime **2**.
3. Go over every multiple of **p** in the list and mark them (starting from $2*p$)
4. Find the next prime greater than **p**. Let **p** now be equal to this new number. If there is no such number, then stop the process.

There is a tiny optimization we can make. **Every composite number has at least one prime divisor less than its square root**[^2]. So when going through these numbers, we only need to consider primes up to the square root of **N** as each composite number greater than the square root of **N** must have at least one prime divisor less than the square root of **N**. This is enough to conclude that every composite number greater than the square root of **N** will be marked. This ensures correctness. 

Another optimization is that we can start marking multiples of **p** from $p^2$ instead of $2*p$.[^3]

[^2]: This conclustion can be drawn from [this](https://gismet-majidov.github.io/posts/Divisor-less-than-sqrt/)
[^3]: This is because every multiple of **p** less than $p^2$ has already been marked. Because every multiple of **p** less than $p^2$ is $k * p$  for some $k<p$. Then $k$ is either a prime or it has a prime divisor less than **p** (obviously), which implies that $k*p$ must have been marked when we were considering $k$ or its smallest prime divisor.


### Code 

```java
import java.util.Arrays;

public class EratosthenesSieve {

    static final int N = 1000000;

    public static void main(String[] args) {

        boolean[] isPrime = new boolean[N + 1];
        Arrays.fill(isPrime, true);
        isPrime[0] = isPrime[1] = false;

        for (int i = 2; i * i <= N; i++) {
            if (isPrime[i]) {
                for (int j = i * i; j <= N; j += i)
                    isPrime[j] = false;
            }
        }

        // Test
        for (int i = 1; i <= 10; i++) {
            System.out.println(i + " is " + (isPrime[i] ? "prime" : "not prime"));
        }

    }

}
```