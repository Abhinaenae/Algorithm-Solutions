# 226. Invert Binary Tree
Given the root of a binary tree, invert the tree, and return its root.

### Explanation:
When we are given a visual depiction of the tree, we see that the sample output shows that the two children of the parent node are swapped in position. 

Keeping this in mind, if we recursively swap the two child nodes of a parent, then we will be able to invert the tree. A common algorithm we can use for this problem is Depth-First-Search.

- Time Complexity: O(n)
- Space Complexity: O(n) 
### Answer:

```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        # Edge case
        if not root:
            return root
        #swap children
        temp = root.right
        root.right = root.left
        root.left = temp
        #recursive call
        self.invertTree(root.right)
        self.invertTree(root.left)
        return root
```
