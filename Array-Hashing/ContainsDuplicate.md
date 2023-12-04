# 217. Contains Duplicate
Given an integer array `nums`, return `true` if any value appears at least twice in the array, and return `false` if every element is distinct.

### Example 1:

Input: `nums = [1,2,3,1]`\
Output: `true`
### Example 2:

Input: `nums = [1,2,3,4]`\
Output: `false`
### Example 3:

Input: `nums = [1,1,1,3,3,4,3,2,4,2]`\
Output: `true`

### Constraints:

- `1 <= nums.length <= 105`
- `-109 <= nums[i] <= 109`

### Solution (Brute Force)
You can visit each element in the array in a nested for loop and check if value1 equals value2 which is not at the same index as value1.
- Time Complexity: `O(n^2)`
- Space Complexity: `O(1)`
```
class Solution(object):
    def containsDuplicate(self, nums):
        for i,c in enumerate(nums):
            for j,d in enumerate(nums):
                if (c==d) and (i!=j):
                    return True
```

### Solution (Optimized Solution)
Because a solution of `O(n^2)` is not efficient in time, one would have to wonder if it is possible to optimize the brute force solution. Using a HashSet to make it so that the solution improves to be in linear time, but also has a trade-off where the space complexity will be in linear time, instead of constant time.

You can create a HashSet, then for every element in nums, you can check if that element is already in the HashSet to return true, if not, you add the element into the HashSet. If this loop completes without returning true, then there is no duplicate in the array nums.
- Time Complexity: `O(n)`
- Space Complexity: `O(n)`
```
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        hashset = set()
        for i in nums:
            if( i in hashset):
                return True
            hashset.add(i)
        return False
```
        
