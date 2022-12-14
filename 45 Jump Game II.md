# 45. Jump Game II



## Description

     

You are given a **0-indexed** array of integers `nums` of length `n`. You are initially positioned at `nums[0]`.

Each element `nums[i]` represents the maximum length of a forward jump from index `i`. In other words, if you are at `nums[i]`, you can jump to any `nums[i + j]` where:

- `0 <= j <= nums[i]` and
- `i + j < n`

Return *the minimum number of jumps to reach* `nums[n - 1]`. The test cases are generated such that you can reach `nums[n - 1]`.

**Example 1:**

```
Input: nums = [2,3,1,1,4]
Output: 2
Explanation: The minimum number of jumps to reach the last index is 2. Jump 1 step from index 0 to 1, then 3 steps to the last index.

```

**Example 2:**

```
Input: nums = [2,3,0,1,4]
Output: 2

```

**Constraints:**

- `1 <= nums.length <= 104`
- `0 <= nums[i] <= 1000`

## Solution

1. Algo#1

Idea: recommend use algo from Neetcode.io

```
use BFS idea
1) first level is start position
2) then we cal the fartheset jump, update l and r pointer for the next winodws
3) levels is step     
```

Process:

![Untitled](img/45%20Jump%20Game.png))

Code:

```python
class Solution:
    def jump(self, nums: List[int]) -> int:
        l, r = 0, 0
        res = 0
        while r < len(nums) -1:   # menas still reach because last cover doesn't reach the end
            # cal the next level
            farthest = 0  # init
            for i in range(l, r+1):
                farthest = max(i + nums[i], farthest)
            # move the windows, see the piture
            l = r + 1
            r = farthest
            res += 1
        return res
```

1. Algo#2

Idea

```
     
```

Code:

```python

```
