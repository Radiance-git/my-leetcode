## [345. Reverse Vowels of a String](https://leetcode.com/problems/reverse-vowels-of-a-string/)
**Difficulty:** Easy

### Problem
Given a string `s`, reverse only the vowels in it (`a`, `e`, `i`, `o`, `u`, in either case) and return the result. All other characters stay in their original positions.

**Example:**
```
s = "IceCreAm"  →  "AceCreIm"
s = "leetcode"  →  "leotcede"
```

**Constraints:**
- `1 <= s.length <= 3 * 10^5`
- `s` consists of printable ASCII characters

### Approach
Two pointers, one from each end of the string. Move the left pointer forward until it lands on a vowel, and the right pointer backward until it lands on a vowel. Swap the two vowels, then move both pointers inward. Repeat until the pointers meet.

- **Time:** O(n)
- **Space:** O(n) (strings are immutable in Python, so we convert to a list to swap in place, then join back)

### Solution
```python
class Solution(object):
    def reverseVowels(self, s):
        vowels = set("aeiouAEIOU")
        chars = list(s)
        left, right = 0, len(chars) - 1

        while left < right:
            if chars[left] not in vowels:
                left += 1
            elif chars[right] not in vowels:
                right -= 1
            else:
                chars[left], chars[right] = chars[right], chars[left]
                left += 1
                right -= 1

        return "".join(chars)
```
