## [1768. Merge Strings Alternately](https://leetcode.com/problems/merge-strings-alternately/)
**Difficulty:** Easy

### Problem
Given two strings `word1` and `word2`, build a new string by taking characters from each one in turn, starting with `word1`. Once one string runs out, tack the remaining characters of the longer string onto the end.

**Example:**
```
word1 = "abc", word2 = "pqr"  →  "apbqcr"
word1 = "ab",  word2 = "pqrs" →  "apbqrs"
word1 = "abcd", word2 = "pq"  →  "apbqcd"
```

**Constraints:**
- `1 <= word1.length, word2.length <= 100`
- Both strings contain only lowercase English letters

### Approach
Walk both strings with a single index, appending one character from each at a time until the shorter one is exhausted, then append whatever's left of the longer string.

- **Time:** O(n + m)
- **Space:** O(n + m) for the output string

### Solution
```python
class Solution(object):
    def mergeAlternately(self, word1, word2):
        """
        :type word1: str
        :type word2: str
        :rtype: str
        """
        result = []
        i, j = 0, 0

        while i < len(word1) and j < len(word2):
            result.append(word1[i])
            result.append(word2[j])
            i += 1
            j += 1

        while i < len(word1):
            result.append(word1[i])
            i += 1
        while j < len(word2):
            result.append(word2[j])
            j += 1

        merged = ''.join(result)

        return merged
```
