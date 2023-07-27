# QuickSelect Algorithm - Find the Kth Smallest Element in an Array

## What is QuickSelect?

Quickselect is an algorithm for finding the kth smallest element in an unordered list. It's similar to quicksort.

Quickselect works by choosing a "pivot" element and partitioning the data into two groups: one group with elements smaller than the pivot and another group with elements larger. Unlike quicksort, which recursively sorts both groups, quickselect only focuses on the group where the target element should be. This makes it faster on average, although it can be slower in the worst case.

Quickselect is usually done directly on the list, and besides finding the kth smallest element, it also sorts part of the data.

## Complexity Analysis

- Time complexity: $O(n)$ on average, $O(n^2)$ in the worst case

  $T(n) = T(n/2) + O(n) = O(n) + O(n/2) + O(n/4) + ... + O(1) = O(n)$

- Space complexity: $O(n)$

## Python Implementation

The algorithm can be implemented in Python as follows:

```python
class Solution:
    def findKthSmallest(self, nums, k):
        if not nums or k < 1 or k > len(nums):
            return -1
        return self.partition(nums, 0, len(nums) - 1, k - 1)
        
    def partition(self, nums, start, end, k):
        # start <= k <= end
        if start == end:
            return nums[k]
            
        left, right = start, end
        pivot = nums[(start + end) // 2]
        while left <= right:
            while left <= right and nums[left] < pivot:
                left += 1
            while left <= right and nums[right] > pivot:
                right -= 1
            if left <= right:
                nums[left], nums[right] = nums[right], nums[left]
                left, right = left + 1, right - 1
                
        # left is now bigger than right
        if k <= right:
            return self.partition(nums, start, right, k)
        if k >= left:
            return self.partition(nums, left, end, k)
        
        return nums[k]
```

## Understanding the Partitioning Choice in Quickselect/Quicksort: Why using `nums[left] < pivot` and `nums[right] > pivot`?

The partition in quickselect/quicksort is designed to accommodate the pivot value by allowing it to be placed either on the left or right side. This flexibility ensures that when a number equals the pivot value (`nums[i] == pivot`), it can be placed on either side of the partition.

The reason for partitioning the array in this manner is to prevent a situation where all the elements in the array, such as `[1, 1, 1, 1, 1, 1]` (containing identical elements), end up on a single side. By not assigning the case of `nums[i] == pivot` to either the left or right side during partitioning, the results of the partitioning process can be somewhat balanced.
