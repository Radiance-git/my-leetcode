## [1431. Kids With the Greatest Number of Candies](https://leetcode.com/problems/kids-with-the-greatest-number-of-candies/)
**Difficulty:** Easy

### Problem
You're given an array `candies`, where `candies[i]` is how many candies the `i`-th kid has, plus an integer `extraCandies`. For each kid, determine whether giving them all the extra candies would make them the kid with the most candies (ties count).

**Example:**
```
candies = [2,3,5,1,3], extraCandies = 3  →  [true,true,true,false,true]
candies = [4,2,1,1,2], extraCandies = 1  →  [true,false,false,false,false]
candies = [12,1,12], extraCandies = 10   →  [true,false,true]
```

**Constraints:**
- `n == candies.length`
- `2 <= n <= 100`
- `1 <= candies[i] <= 100`
- `1 <= extraCandies <= 50`

### Approach
Find the current maximum in the array, then for each kid check whether their candies plus the extra candies would reach or exceed that maximum.

- **Time:** O(n)
- **Space:** O(n) for the result array

### Solution
```python
class Solution(object):
    def kidsWithCandies(self, candies, extraCandies):
        def get_largest_number(numbers_list):
            largest = numbers_list[0]
            for n in numbers_list:
                if n > largest:
                    largest = n
            return largest

        res = []
        largest_number = get_largest_number(candies)
        for candy in candies:
            if candy + extraCandies >= largest_number:
                res.append(True)
            else:
                res.append(False)
        return res
```
