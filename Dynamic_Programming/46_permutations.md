# 46. Permutations

## Problem Statement

Given an array `nums` of distinct integers, return all the possible permutations. You can return the answer in any order.

### Example 1:
- **Input:** nums = [1,2,3]
- **Output:** [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]

### Example 2:
- **Input:** nums = [0,1]
- **Output:** [[0,1],[1,0]]

### Example 3:
- **Input:** nums = [1]
- **Output:** [[1]]

## Solution

```python
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        perums = [[]]

        for n in nums:
            new_perums = []

            for p in perums:
                for j in range(len(p) + 1):
                    p_copy = p.copy()
                    p_copy.insert(j, n)
                    new_perums.append(p_copy)
            perums = new_perums
        return perums
