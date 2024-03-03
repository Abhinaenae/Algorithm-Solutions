# TwoSum
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

### Solution (Optimized)

Initiate an empty hashmap. Loop through nums and find the difference of the target and your element n. If this difference is in the hashmap, you return the indices of that difference and i. If not, you add that element to the hashmap.

Time Complexity: O(N)
Space Complexity: O(N)


```
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        prevMap{}
        for i,n in enumerate(nums):
            diff = target-n
            if diff in prevMap:
                return [prevMap[diff], i]
            prevMap[n] = i
```

