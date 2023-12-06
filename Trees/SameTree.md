# 100. Same Tree
Given the roots of two binary trees `p` and `q`, write a function to check if they are the same or not.

Two binary trees are considered the same if they are structurally identical, and the nodes have the same value.



### Recursive DFS Solution
A recursive depth first search algorithm can be used. First, to check if p and q don't have a root node, which should result in True.
Then, we want to check if p has a root node, if q has a root node, and then if the root nodes of p and q are the same. If these statements are true, then returns the value of the recursive call on the function that is performed to check if all elements of the trees are identical. 
- Time Complexity: O(N)
- Space Complexity: O(N)
```
class Solution:
    def isSameTree(self, p: Optional[TreeNode], q: Optional[TreeNode]) -> bool:
        if not p and not q:
            return True
        if p and q:
            if p.val == q.val:
                return self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)
```
