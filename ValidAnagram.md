# 242. Valid Anagram
Given two strings `s` and `t`, return `true` if `t` is an anagram of `s`, and `false` otherwise.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.


### Solution 1 (Brute Force)

Run a sorting algorithm on both strings s and t. Then, go through the new string comparing each character if they are equivalent. If the characters are not equiavelent, it is not an anagram and will return false. Else, it is an anagram and will return true.

Time complexity: O(NLogN)

### Solution 2 (Optimized)

Use a hashmap to count each occurence of the characters in the string, then check if the counts are the same in the two strings. For example, in "Annarn", N has count 3, A has count 2, r has count 1. With another string "Narnna", it is an anagram because they have the same counts. 

Time Complexity: O(N)
Space Complexity: O(N)

```
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if(len(s) != len(t)):
            return False
        schar, tchar = {},{}
        for i in range(len(s)):
            schar[s[i]] = 1 + schar.get(s[i], 0)
            tchar[t[i]] = 1 + tchar.get(t[i], 0)
        for c in schar:
            if schar[c] != tchar.get(c,0):
                return False
        return True
```