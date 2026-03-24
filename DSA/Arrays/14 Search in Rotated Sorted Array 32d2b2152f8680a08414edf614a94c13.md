# 14.Search in Rotated Sorted Array

There is an integer array `nums` sorted in ascending order (with **distinct** values).

Prior to being passed to your function, `nums` is **possibly left rotated** at an unknown index `k` (`1 <= k < nums.length`) such that the resulting array is `[nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]]` (**0-indexed**). For example, `[0,1,2,4,5,6,7]` might be left rotated by `3` indices and become `[4,5,6,7,0,1,2]`.

Given the array `nums` **after** the possible rotation and an integer `target`, return *the index of* `target` *if it is in* `nums`*, or* `-1` *if it is not in* `nums`.

You must write an algorithm with `O(log n)` runtime complexity.

**Example 1:**

```
Input: nums = [4,5,6,7,0,1,2], target = 0
Output: 4
```

**Example 2:**

```
Input: nums = [4,5,6,7,0,1,2], target = 3
Output: -1
```

**Example 3:**

```
Input: nums = [1], target = 0
Output: -1
```

sol : The simple one would be just go thru the array and find the target and return it but this is a o(n) time which is not at all good. 

we have to do it in `O(log n)`

So the best way would be to use binary search, but the challenge here is you need to be careful cuz the array is rotated, even though it is a sorted array it is rotated at some random index.

so we set up a mid we check which side is sorted and then we see if the target falls within that side and which ever side target is on we bring the opposite side pointer closer. this is like the high level explanation. By eliminating half of the array in each step, we maintain O(log n) time complexity.

code :

 

```
class Solution:
    def search(self, nums: List[int], target: int) -> int:

        l, r = 0, len(nums) - 1

        while l <= r:
            m = l + (r - l) // 2

            if nums[m] == target:
                return m

            if nums[m] >= nums[l]:
                if target >= nums[l] and target < nums[m]:
                    r = m -1
                else:
                    l = m + 1
            else:
                if target > nums[m] and target <= nums[r]:
                    l = m + 1
                else:
                    r = m - 1

        return - 1
```