# Q1:
## Two Sum

## Problem (Short)

Given an integer array `nums` and an integer `target`, return the indices of the two numbers such that they add up to `target`.

- Exactly one solution exists  
- You may not use the same element twice  

### Example

```

Input: nums = [3, 2, 4], target = 6
Output: [1, 2]

````

---

## Solution 1 — Using `itertools.combinations` (Brute Force)

- Time Complexity: **O(n²)**
- Simple and Pythonic
- Not efficient for large inputs

```python
from itertools import combinations

def two_sum_combinations(nums, target):
    pairs = [
        (a, b)
        for a, b in combinations(range(len(nums)), 2)
        if nums[a] + nums[b] == target
    ]
    return pairs[0] if pairs else None


# Example
nums = [3, 2, 4]
target = 6

print(two_sum_combinations(nums, target))  # (1, 2)
````

---

## Solution 2 — Hash Map (Optimal)

* Time Complexity: **O(n)**
* Space Complexity: **O(n)**
* Best practice for interviews and production

```python
def two_sum(nums, target):
    seen = {}  # value -> index

    for i, num in enumerate(nums):
        complement = target - num

        if complement in seen:
            return [seen[complement], i]

        seen[num] = i


# Example
print(two_sum([3, 2, 4], 6))  # [1, 2]
```

---

## Summary

| Approach           | Time Complexity | Space | Notes                |
| ------------------ | --------------- | ----- | -------------------- |
| Combinations       | O(n²)           | O(1)  | Simple but slow      |
| Hash Map (Optimal) | O(n)            | O(n)  | Recommended solution |

```

