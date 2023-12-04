# 104. Maximum Depth of Binary Tree

Given the `root` of a binary tree, return its *maximum depth*.

A binary tree's **maximum depth** is the number of nodes along the longest path from the root node down to the farthest leaf node.

#### Definition for a binary tree node.
```
 class TreeNode:
     def __init__(self, val=0, left=None, right=None):
         self.val = val
         self.left = left
         self.right = right
```

### Solution 1: Recursive Depth-First-Search(DFS)
A recursive call using DFS can be used to find the greatest depth of the subtrees from the root node.
- Time Complexity: O(N)
- Space Complexity(Worst Case): O(N)
```
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0
        return 1 + max(self.maxDepth(root.left), self.maxDepth(root.right))
```
