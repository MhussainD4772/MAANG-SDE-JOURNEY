# 12. Longest Increasing Subsequence

Given an integer array `nums`, return *the length of the longest **strictly increasing subsequence***.

**Example 1:**

```
Input: nums = [10,9,2,5,3,7,101,18]
Output: 4
Explanation: The longest increasing subsequence is [2,3,7,101], therefore the length is 4.
```

**Example 2:**

```
Input: nums = [0,1,0,3,2,3]
Output: 4
```

**Example 3:**

```
Input: nums = [7,7,7,7,7,7,7]
Output: 1
```

sol : 

## Longest Increasing Subsequence using DP

We want to find the length of the longest increasing subsequence in the array.

A subsequence does not need to be continuous, but the order must stay the same.

### Core idea

For every index, I ask this question:

> What is the length of the longest increasing subsequence that ends at this index?
> 

That is what `dp[i]` means.

### Why dp starts with 1

Each element by itself is already an increasing subsequence of length 1.

So before doing any comparisons, every index starts with:

```python
dp = [1] * n
```

### How we build the answer

For each index `i`, we look at all previous indices `j`.

If `nums[j] < nums[i]`, then the current number can extend the increasing subsequence that ended at `j`.

So we check:

```python
dp[i] = max(dp[i], dp[j] + 1)
```

This means:

- take the subsequence ending at `j`
- add the current number to it
- see if that gives a better answer for index `i`

### Why we look at all previous indices

Because the best subsequence for the current number may not come from the immediate previous element.

It can come from any earlier smaller element.

So for each position, we must check all earlier positions and choose the best valid one.

### Example thought process

For array:

```python
[1, 2, 4, 3]
```

- `1` can only make subsequence `[1]` so length is 1
- `2` can extend `1`, so `[1, 2]` and length is 2
- `4` can extend `[1, 2]`, so `[1, 2, 4]` and length is 3
- `3` cannot extend `4`, but it can extend `[1, 2]`, so `[1, 2, 3]` and length is 3

So the dp array becomes:

```python
[1, 2, 3, 3]
```

And the final answer is the maximum value in `dp`, which is `3`.

### Plain English summary

We solve the problem by storing the best increasing subsequence length ending at every index.

Then for each number, we look back at all earlier numbers.

If an earlier number is smaller, we try extending its subsequence.

We keep the best possible length for each index.

At the end, the largest value in the dp array is the answer.

### Complexity

- Time complexity: `O(n²)`
- Space complexity: `O(n)`

### One line memory sentence

> At each index, look back, find the best smaller previous number, and extend its subsequence.
>