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

### Solution 1: Recursive Depth-First-Search (DFS)
A recursive call using DFS can be used to find the greatest depth of the subtrees from the root node checking if the child nodes exist and keep a count, and if they do, then it continues to call until the leaf node is reached, where it will return the maximum depth
- Time Complexity: O(N)
- Space Complexity(Worst Case): O(N)
```
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0
        return 1 + max(self.maxDepth(root.left), self.maxDepth(root.right))
```
### Solution 2: Breadth-First-Search (BFS)
A BFS solution can also be used to find the maximum depth of the tree. The BFS uses a queue to count the number of levels in the tree and checks if there is a node in the next level of the tree, and if so, it will continue to check the next level until it reaches the leaf node. Once the leaf node is reached, it will return the level, which is the maximum depth.
- Time Complexity: O(N)
- Space Complexity(Worst Case): O(N)
```
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0
        level = 0
        q = deque([root])
        while q:
            for i in range(len(q)):
                node = q.popleft()
                if node.left:
                    q.append(node.left)
                if node.right:
                    q.append(node.right)

            level+=1
        return level
```

### Solution 3: Iterative Depth-First-Search (DFS)
An iterative DFS solution can be used along with the inclusion of a stack that processes the node and its children. You can get the depth of each node added onto the stack.
```
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0
        stack = [[root,1]]
        res = 0

        while stack:
            node,depth = stack.pop()

            if node:
                res = max(res, depth)
                stack.append([node.left, depth +1])
                stack.append([node.right, depth +1])
        return res
```

