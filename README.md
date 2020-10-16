# Leetcode-Bulb-Switcher
Detailed solution to the problem Bulb Switcher

## Problem Statement
There are n bulbs that are initially off. You first turn on all the bulbs. Then, you turn off every second bulb. On the third round, you toggle every third bulb (turning on if it's off or turning off if it's on). For the i-th round, you toggle every i bulb. For the n-th round, you only toggle the last bulb. Find how many bulbs are on after n rounds.

## Example
**Input:** 3

**Output:** 1 

**Explanation:** 

At first, the three bulbs are [off, off, off].

After first round, the three bulbs are [on, on, on].

After second round, the three bulbs are [on, off, on].

After third round, the three bulbs are [on, off, off]. 

So you should return 1, because there is only one bulb is on.

## Explanation and Solution
The problem description makes it very clear that we given n bulbs that are off initially, and for each i from 1 to n, we toggle the bulbs that are multiples of i.

For example, let's take n = 5. Initially, all the 5 bulbs are off. We'll denote off bulbs by 0, and on bulbs by 1.

> [0, 0, 0, 0, 0]

Now, we will take i from 1 to 5 and toggle bulbs that are multiple of i.

For i = 1, we toggle the bulbs 1x1, 1x2, 1x3, 1x4, 1x5. The states of the bulbs change to the following

> [1, 1, 1, 1, 1]

For i = 2, we toggle the bulbs 2x1, 2x2. Any multiple of 2 higher than this is obviously greater than n = 5, so no use of them here. The states of the bulbs change to the following

> [1, 0, 1, 0, 1]

For i = 3, we toggle the bulbs 3x1. Any multiple of 3 higher than this is obviously greater than n = 5, so no use of them here. The states of the bulbs change to the following

> [1, 0, 0, 0, 1]

For i = 4, we toggle the bulbs 4x1. Any multiple of 4 higher than this is obviously greater than n = 5, so no use of them here. The states of the bulbs change to the following

> [1, 0, 0, 1, 1]

For i = 5, we toggle the bulbs 5x1. Any multiple of 5 higher than this is obviously greater than n = 5, so no use of them here. The states of the bulbs change to the following

> [1, 0, 0, 1, 0]

We can clearly tell that only two bulbs remain in the on state and that is also our answer.

If we look carefully at our output, we may notice that the on bulbs are numbered 1 and 4. Now, what can we say about these numbers? They are perfect squares! All perfect squares have this special property that they have odd number of factors. Further, if we toggle an on bulb odd number of times, we will get the on state again, and this is true for the bulbs that are positioned at perfect square numbers.

One question that arises in our mind is why perfect squares have odd number of factors? Well, if we do prime factorization of a perfect square, we will notice that the prime numbers are raised to even numbers in the prime factorizarion of a perfect square.

The prime factorization of a perfect square will be something like a<sup>p</sup> x b<sup>q</sup> x c<sup>r</sup>...and so on. Here p, q, r are even numbers. We know that the number of factors can be deduced by doing (p+1)x(q+1)x(r+1)...and so on. If we keep on multiplying odd numbers we will always get an odd number, so the total factors of a perfect square are always odd.

Building upon the mentioned logic, we can find total number of on bulbs by simply doing square root of the given number n, as square root of n will give the closest number whose square is less than or equal to n. Like if n = 101, then sqrt(101) is 10 (closest) and hence we have 10 on light bulbs.

Here, I've provided the C++ code.

    class Solution {
    public:
      int bulbSwitch(int n) {
        
        return (sqrt(n));
        
      }
    };
    
The time complexity of this code will be O(1) as we are doing a constant time operation of finding square root.
