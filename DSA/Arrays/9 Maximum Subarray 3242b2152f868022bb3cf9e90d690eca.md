# 9. Maximum Subarray

Given an integer array `nums`, find the subarray with the largest sum, and return *its sum*.

**Example 1:**

```
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: The subarray [4,-1,2,1] has the largest sum 6.
```

**Example 2:**

```
Input: nums = [1]
Output: 1
Explanation: The subarray [1] has the largest sum 1.
```

**Example 3:**

```
Input: nums = [5,4,-1,7,8]
Output: 23
Explanation: The subarray [5,4,-1,7,8] has the largest sum 23.
```

The brute force way to do this would be to just start at each index and from there count all the numbers in the array and get the total and then go to next number repeat the same process for rest of the numbers and whatever is the highest sum just return that. But this would be too high on complexity.

Best option is to use something like a sliding window. For example if nums = 

`-2,1,-3,4,-1,2,1,-5,4`

We add -2 + 1 which is -1 so it would be safe for us to delete the -2 cuz the current sum is less than 0 now if we take 1 and - 3 it is -2 that also doesn’t seem right so what you can do is remove until -3 as that is the - number. rule is if the last prefix is negative probably remove it. Now do 4 -1 which is 3 and then + 2 is 5 and then + 1 is 6 and the -5 is 1 and then + 4 is 5 so we realize that sub array until that 6 is the largest sum of an sub array just return that

```
maxSub = nums[0]
        curSum = 0

        for n in nums:
            if curSum < 0:
                curSum = 0
            curSum += n
            maxSub = max(maxSub, curSum)
        return maxSub
```