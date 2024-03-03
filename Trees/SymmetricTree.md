# 101. Symmetric Tree
Given the root of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).


### Recursive DFS Solution
A recursive depth first search algorithm can be used on the root node. 
First, we want to check if the tree has no children, which would make it return true since it would be symmetric.
Then, we want to make sure that if the values of the trees don't match, then it would return False.
After this, we recursively call the function and see if both the left children of the left node and the right children of the right node are the same, and, if the right children of the left node and the left children are the same. If this recursive call reaches the base case, then we would return True.

- Time Complexity: O(N)
- Space Complexity: O(H), H being height of tree
```
class Solution:
    def isSymmetric(self, root: Optional[TreeNode]) -> bool:
        def dfs(left, right):
            if not left and not right:
                return True
            if (not left or not right) or (left.val != right.val):
                return False
            return dfs(left.left, right.right) and dfs(left.right, right.left)

        return dfs(root.left, root.right)
```
