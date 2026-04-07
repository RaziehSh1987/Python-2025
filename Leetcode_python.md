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
````
# Q2:
## Valid Palindrome

## Problem (Short)

Given a string `s`, return `True` if it is a palindrome, or `False` otherwise.

- A palindrome reads the same forward and backward  
- Consider only alphanumeric characters (letters and digits)  
- Ignore cases  

---

## Examples

```

Input: s = "A man, a plan, a canal: Panama"
Output: True

```

After cleaning:  
```

"amanaplanacanalpanama"

```


Input: s = "race a car"
Output: False


---

## Solution 1 — Manual Filtering

- Time Complexity: **O(n)**
- Space Complexity: **O(n)**
- Easy to understand, step-by-step approach

```python
s = "A man, a plan, a canal: Panama"
target = ""

for i in s:
    if i.isalnum():
        target += i.lower()

if target == target[::-1]:
    print(True)
else:
    print(False)
```


---

## Solution 2 — Pythonic (Recommended)

* Time Complexity: **O(n)**
* Space Complexity: **O(n)**
* Cleaner and more concise

```python
def is_palindrome(s):
    cleaned = ''.join(c.lower() for c in s if c.isalnum())
    return cleaned == cleaned[::-1]
```

---

## Summary

| Approach      | Time Complexity | Space | Notes                           |
| ------------- | --------------- | ----- | ------------------------------- |
| Manual Filter | O(n)            | O(n)  | Step-by-step, beginner-friendly |
| Pythonic      | O(n)            | O(n)  | Clean and concise               |

````


````
# Q3:
## Most Frequent Element

## Problem (Short)

Given a list of integers `nums`, return the element that appears the most frequently.

- If there is a tie, return any one of them  

---

## Examples

```

Input: nums = [1, 3, 3, 2, 1, 3]
Output: 3

```

Explanation:  
3 appears 3 times, more than any other number.

```

Input: nums = [7, 7, 4, 4, 4]
Output: 4

````

---

## Solution 1 — Using `.count()` (Inefficient)

- Time Complexity: **O(n²)**
- Space Complexity: **O(n)**
- Not recommended for large inputs

```python
nums = [1, 3, 3, 2, 1, 3]

cnt = {}
for num in nums:
    cnt[num] = nums.count(num)

# get the key with the highest value
print(max(cnt, key=lambda k: cnt[k]))  # 3
```

---

## Solution 2 — Hash Map (Optimal)

* Time Complexity: **O(n)**
* Space Complexity: **O(n)**
* Recommended approach

```python
nums = [1, 3, 3, 2, 1, 3]

cnt = {}
for num in nums:
    cnt[num] = cnt.get(num, 0) + 1

print(max(cnt, key=lambda k: cnt[k]))  # 3
```

---

## Solution 3 — Using `collections.Counter`

* Time Complexity: **O(n)**
* Space Complexity: **O(n)**
* Most concise and Pythonic

```python
from collections import Counter

nums = [1, 3, 3, 2, 1, 3]
print(Counter(nums).most_common(1)[0][0])  # 3
```

---

## Summary

| Approach           | Time Complexity | Space | Notes                  |
| ------------------ | --------------- | ----- | ---------------------- |
| `.count()`         | O(n²)           | O(n)  | Simple but inefficient |
| Hash Map           | O(n)            | O(n)  | Best for interviews    |
| Counter (Built-in) | O(n)            | O(n)  | Clean and concise      |

```

