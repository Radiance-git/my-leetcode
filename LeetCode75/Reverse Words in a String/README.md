## [151. Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string/)
**Difficulty:** Medium

### Problem
Given a string `s`, reverse the order of the words in it. A word is any sequence of non-space characters, and words are separated by at least one space. The output should have exactly one space between words, with no leading or trailing spaces — even if the input has extra or irregular spacing.

**Example:**
```
s = "the sky is blue"    →  "blue is sky the"
s = "  hello world  "    →  "world hello"
s = "a good   example"   →  "example good a"
```

**Constraints:**
- `1 <= s.length <= 10^4`
- `s` contains English letters, digits, and spaces
- At least one word is present

**Follow-up:** Can you do it in-place with O(1) extra space (in a language with mutable strings)?

### Approach
Split the string on whitespace (Python's `str.split()` with no arguments automatically collapses multiple spaces and ignores leading/trailing ones), reverse the resulting list of words, and join them back with a single space.

- **Time:** O(n)
- **Space:** O(n) for the list of words and the output string

### Solution
```python
class Solution(object):
    def reverseWords(self, s):
        words = s.split()
        return " ".join(reversed(words))
```
