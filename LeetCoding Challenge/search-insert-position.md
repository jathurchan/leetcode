---
date: 2022.11.18
title: 35. Search Insert Position
difficulty:
    - easy
runtime: 92.31 # faster than (in %)
memory usage: 31.55    # less than (in %)
---
## Description
Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You must write an algorithm with `O(log n)` runtime complexity.

**Example 1:**

```
Input: nums = [1,3,5,6], target = 5
Output: 2

```

**Example 2:**

```
Input: nums = [1,3,5,6], target = 2
Output: 1

```

**Example 3:**

```
Input: nums = [1,3,5,6], target = 7
Output: 4

```

**Constraints:**

- `1 <= nums.length <= 104`
- `104 <= nums[i] <= 104`
- `nums` contains **distinct** values sorted in **ascending** order.
- `104 <= target <= 104`

## Approach 1: Binary Search
Time complexity: `O(log(n))`    |    Space complexity: `O(1)`
where `n` is the length of `nums`

``` python
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        left, right = 0, len(nums) - 1
        while left <= right:
            mid = (left + right) // 2
            if nums[mid] == target:
                return mid
            
            if nums[mid] < target:
                left = mid + 1
            else:
                right = mid - 1
        
        return left
```