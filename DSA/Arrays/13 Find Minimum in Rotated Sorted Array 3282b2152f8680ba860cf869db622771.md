# 13. Find Minimum in Rotated Sorted Array

Suppose an array of length `n` sorted in ascending order is **rotated** between `1` and `n` times. For example, the array `nums = [0,1,2,4,5,6,7]` might become:

- `[4,5,6,7,0,1,2]` if it was rotated `4` times.
- `[0,1,2,4,5,6,7]` if it was rotated `7` times.

Notice that **rotating** an array `[a[0], a[1], a[2], ..., a[n-1]]` 1 time results in the array `[a[n-1], a[0], a[1], a[2], ..., a[n-2]]`.

Given the sorted rotated array `nums` of **unique** elements, return *the minimum element of this array*.

You must write an algorithm that runs in `O(log n) time`.

**Example 1:**

```
Input: nums = [3,4,5,1,2]
Output: 1
Explanation: The original array was [1,2,3,4,5] rotated 3 times.
```

**Example 2:**

```
Input: nums = [4,5,6,7,0,1,2]
Output: 0
Explanation: The original array was [0,1,2,4,5,6,7] and it was rotated 4 times.
```

**Example 3:**

```
Input: nums = [11,13,15,17]
Output: 11
Explanation: The original array was [11,13,15,17] and it was rotated 4 times.
```

sol:

This solution uses binary search to find the minimum element in a rotated sorted array. We maintain two pointers `l` and `r` to represent the current search space, and a variable `res` to track the smallest value seen so far. At each step, we first check if the current subarray is already sorted by comparing `nums[l]` and `nums[r]`. If it is sorted, then the smallest element in that range is simply `nums[l]`, so we update `res` and stop early. Otherwise, we calculate the middle index and update `res` with `nums[mid]`, since the minimum could be at mid.

Next, we determine which half of the array is sorted. If `nums[mid] >= nums[l]`, it means the left half is sorted, so the minimum must lie in the right half, and we move `l` to `mid + 1`. Otherwise, the right half is sorted and the minimum lies in the left half, so we move `r` to `mid - 1`. By continuously eliminating the sorted half and focusing on the unsorted portion where the rotation exists, we efficiently narrow down to the minimum element in O(log n) time.