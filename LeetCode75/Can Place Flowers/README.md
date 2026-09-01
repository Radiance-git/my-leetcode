## [605. Can Place Flowers](https://leetcode.com/problems/can-place-flowers/)
**Difficulty:** Easy

### Problem
You have a flowerbed represented as an array of `0`s (empty) and `1`s (planted), where flowers can never be planted in adjacent plots. Given the flowerbed and an integer `n`, determine whether `n` new flowers can be planted without breaking the no-adjacent rule.

**Example:**
```
flowerbed = [1,0,0,0,1], n = 1  →  true
flowerbed = [1,0,0,0,1], n = 2  →  false
```

**Constraints:**
- `1 <= flowerbed.length <= 2 * 10^4`
- `flowerbed[i]` is `0` or `1`
- No two adjacent flowers in the input
- `0 <= n <= flowerbed.length`

### Approach
Scan through the flowerbed once. For each empty plot, check whether both neighbors (treating out-of-bounds as empty) are also empty. If so, plant a flower there and decrement `n`. At the end, check whether all `n` flowers were successfully placed.

- **Time:** O(len(flowerbed))
- **Space:** O(1) (modifies the input array in place)

### Solution
```python
class Solution(object):
    def canPlaceFlowers(self, flowerbed, n):

        for i in range(len(flowerbed)):
            if flowerbed[i] == 0:
                left_empty = (i == 0) or (flowerbed[i - 1] == 0)
                right_empty = (i == len(flowerbed) - 1) or (flowerbed[i + 1] == 0)

                if left_empty and right_empty:
                    flowerbed[i] = 1
                    n -= 1
        return n <= 0
```
