# 70. Climbing Stairs

You are climbing a staircase. It takes n steps to reach the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

## Solution

With the brute force solution, it will be running in 2^n time.
This solution is extremely inefficient and when making a decision tree, one can see that the same operations are repeated.

This is why I opted to use dynamic programming with tabulation to solve this problem, resulting in a much faster time complexity.
### Tabular: 
Time Complexity: O(n)
Space Complexity: O(1)


I used a two-pointer approach, letting me go through only half the size of the linked list.
```
class Solution:
    def climbStairs(self, n: int) -> int:
        one, two = 1,1
        for i in range(n-1):
            temp = one
            one = one + two
            two = temp
        return one
```
