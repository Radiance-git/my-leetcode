## [1071. Greatest Common Divisor of Strings](https://leetcode.com/problems/greatest-common-divisor-of-strings/)
**Difficulty:** Easy

### Problem
A string `t` is said to "divide" a string `s` if `s` can be built by concatenating `t` with itself one or more times. Given two strings `str1` and `str2`, find the largest string that divides both of them.

**Example:**
```
str1 = "ABCABC", str2 = "ABC"   →  "ABC"
str1 = "ABABAB", str2 = "ABAB"  →  "AB"
str1 = "LEET",   str2 = "CODE"  →  ""
```

**Constraints:**
- `1 <= str1.length, str2.length <= 1000`
- Both strings contain only uppercase English letters

### Approach
Two strings share a common "divisor" string only if `str1 + str2 == str2 + str1` — this confirms both are built from repetitions of some common base pattern. If that holds, the largest such divisor has a length equal to the GCD of the two strings' lengths, and it's simply the prefix of that length.

- **Time:** O(n + m) for the concatenation check, plus O(log(min(n, m))) for the GCD
- **Space:** O(n + m) for the concatenated strings

### Solution
```python
class Solution(object):
    @staticmethod
    def _gcd(a, b):
        while b != 0:
            a, b = b, a % b
        return a

    def gcdOfStrings(self, str1, str2):
        if str1 + str2 != str2 + str1:
            return ""

        gcd_len = self._gcd(len(str1), len(str2))
        return str1[:gcd_len]
```
