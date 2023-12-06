# 20. Valid Parenthesis

Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.


### Solution
A stack can be used for this problem to keep track of open and closed brackets.

- Time Complexity: O(N)
- Space Complexity: O(N)

```
class Solution(object):
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        stack = []
        for c in s:
            if(c in '{[('):
                stack.append(c)
            else:
                if not stack or (c=='}' and stack[-1] != '{') or (c==']' and stack[-1] != '[') or (c==')' and stack[-1] != '('):
                    return False
                stack.pop()
        return not stack
```
