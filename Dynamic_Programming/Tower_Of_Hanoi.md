# Tower of Hanoi

## Problem Statement

You are given three rods (numbered 1 to 3), and `N` disks initially placed on the first rod, one on top of each other in increasing order of size (the largest disk is at the bottom). You are supposed to move the `N` disks to another rod (either rod 2 or rod 3) using the following rules and in less than `2 ^ (N)` moves.

### Rules:
1. You can only move one disk in one move.
2. You cannot place a larger disk on top of a smaller disk.
3. You can only move the disk at the top of any rod.

### Note:
You may assume that initially, the size of the `i`th disk from the top of the stack is equal to `i`, i.e., the disk at the bottom has size `N`, the disk above that has size `N - 1`, and so on. The disk at the top has size 1.

## Solution

```python
def towerOfHanoi(n):
    # Return a 2-D array
    res = []
    def toh(n, A, B, C):
        if n > 0:
            toh(n - 1, A, C, B)
            res.append([A, C])
            toh(n - 1, B, A, C)
    toh(n, 1, 2, 3)
    return res
