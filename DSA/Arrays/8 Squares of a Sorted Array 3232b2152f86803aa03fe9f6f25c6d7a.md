# 8. Squares of a Sorted Array

Given an integer array `nums` sorted in **non-decreasing** order, return *an array of **the squares of each number** sorted in non-decreasing order*.

**Example 1:**

```
Input: nums = [-4,-1,0,3,10]
Output: [0,1,9,16,100]
Explanation: After squaring, the array becomes [16,1,0,9,100].
After sorting, it becomes [0,1,9,16,100].
```

**Example 2:**

```
Input: nums = [-7,-3,2,3,11]
Output: [4,9,9,49,121]
```

Sol: Basic sol we see as soon as we look at this is take the sorted array do the square of each element and store it in new array and then sort the new array in non- decreasing order and return it.

That is like the most simple way to do it but no efficient. 

So a better and more optimized way to do this would be for us to use two pointers.

The approach would be set both the pointers at far left and far right and then do the square of each character and compare. which ever is greater add it to the end of the result array. 

And let’s say right is greater than left so add right character to the end of the array get the pointer of right one index towards left. and then do the same process again.

This will get us the answer in one go and in most optimized way.

Trick to reverse an array use [::-1]

So this is probably the best approach for us to solve this problem in the most optimized manner.