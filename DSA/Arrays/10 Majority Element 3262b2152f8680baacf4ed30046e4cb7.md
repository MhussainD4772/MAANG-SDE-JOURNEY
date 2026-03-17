# 10. Majority Element

Given an array `nums` of size `n`, return *the majority element*.

The majority element is the element that appears more than `⌊n / 2⌋` times. You may assume that the majority element always exists in the array.

**Example 1:**

```
Input: nums = [3,2,3]
Output: 3
```

**Example 2:**

```
Input: nums = [2,2,1,1,1,2,2]
Output: 2
```

**Follow-up:** Could you solve the problem in linear time and in `O(1)` space?

SOL:

The simple solution to this would be to use an Hash. And count the elements in the array and which ever count is highest return that as the solution.

For example:

seen= {}

for n in nums:

if n in seen:

seen[n] += 1

else:

seen[n] = 1

if seen[n] >  len(nums) // 2:

return n

But now if we tall about the follow up to remove the hash and  solve this is 0(1) we would something called boyer moore alogorithm. Here we will just keep the res and count and that’s it 

```
res = None
        count = 0

        for n in nums:
            if count == 0:
                res = n
            if n == res:
                count+=1
            else:
                count-=1
        return res
```