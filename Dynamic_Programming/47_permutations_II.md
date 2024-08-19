# 47. Permutations II

## Problem Statement

Given a collection of numbers, `nums`, that might contain duplicates, return all possible unique permutations in any order.

### Example 1:
- **Input:** nums = [1,1,2]
- **Output:**
  - [[1,1,2],
  -  [1,2,1],
  -  [2,1,1]]

### Example 2:
- **Input:** nums = [1,2,3]
- **Output:** [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]

## Solution

```python
class Solution:
    def permuteUnique(self, nums: List[int]) -> List[List[int]]:
        res = []
        permutes = []
        count = { n: 0 for n in nums }

        for n in nums:
            count[n] += 1
        
        def dfs():
            if len(permutes) == len(nums):
                res.append(permutes.copy())
                return 

            for n in count:
                if count[n] > 0:
                    permutes.append(n)
                    count[n] -= 1

                    dfs()

                    permutes.pop()
                    count[n] += 1
        dfs()
        return res
