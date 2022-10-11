# 704. Binary Search

1 Topic: Binary Search
Create Time: August 24, 2022 2:38 PM
Difficulty: Easy
ID: 704
Last Review Time: October 11, 2022 6:45 AM

## Description

```
Given an array of integers nums which is sorted in ascending order, and an integer target, write a function to search target in nums. If target exists, then return its index. Otherwise, return -1.

You must write an algorithm with O(log n) runtime complexity.

 

Example 1:

Input: nums = [-1,0,3,5,9,12], target = 9
Output: 4
Explanation: 9 exists in nums and its index is 4
Example 2:

Input: nums = [-1,0,3,5,9,12], target = 2
Output: -1
Explanation: 2 does not exist in nums so return -1
```

## Solution

1. Algo#1

Idea

```
Use bruce force, T(n)     
```

Code:

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        # use brute force algo, time: O(n)
        """
        for i in range(len(nums)):
            if nums[i] == target:
                return i
        return -1
        """
```

1. Algo#2

Idea

```
 # idea
# Binary: meaning half
# note: this requires O(log(n)) runtime, so we can't use brute force algorithm

# idea: -1, 0, 7,5,9,12
#       l            r
# we use two pointers
# becasue if we only use one pointer, like L , we will see the left to continue iterate,
# that is to say, we only elminate one possibility, the same flow as the right.
# so, we will use middle here, divide left and right by 2
# now we only need to compare left to mid or mid to right based on the target value compared with  mid value
# For example, if m < target , we set  L = M +1
# then repeat the algorithm to get the final result.
# About Time complexity
# like 16 values:
# 16 -> 8 -> 4 -> 2 -> 1,  2^x = n   => x =log2(n)
# now we can mee the requirement O(log(n)) 
Two key points here:
# 1: we should use l <= r, for only one element
# 2, we should use l = m +1 and r = m - 1, not l=m, r=m
     because we want l cross r, avoid dead loop    
```

    

Code:

```python
class Solution(object):
    def search(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        l, r = 0, len(nums)-1
        while l <= r:
            # why we use l <= r instead of l < r,
            # for exmaple, only one num, 1, l=r=m =0, here we can use else brancher to return m(0)
            # maybe it will cause overlap
            # m = (l+r)//2
            m = l + (r-l)//2
            if target > m:
                l = m + 1
            elif target < m:
                r = m -1
            else:   # exactly equal m
                # here m has been set to index, so don't need to find the index
                return m
        return -1
```
