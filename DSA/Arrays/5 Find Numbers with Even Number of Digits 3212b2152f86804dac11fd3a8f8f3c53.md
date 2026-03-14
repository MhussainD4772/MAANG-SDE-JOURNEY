# 5. Find Numbers with Even Number of Digits

Question:

Given an array `nums` of integers, return how many of them contain an **even number** of digits.

**Example 1:**

```
Input: nums = [12,345,2,6,7896]
Output: 2
Explanation:12 contains 2 digits (even number of digits).
345 contains 3 digits (odd number of digits).
2 contains 1 digit (odd number of digits).
6 contains 1 digit (odd number of digits).
7896 contains 4 digits (even number of digits).
Therefore only 12 and 7896 contain an even number of digits.
```

**Example 2:**

```
Input: nums = [555,901,482,1771]
Output: 1
Explanation:
Only 1771 contains an even number of digits.
```

sol:

So this is a simple one you take the each number in the array and count it digits if the digits are in even then it’s good if the digits are in odd then skip.

Best way is just take each number convert in string and then get it’s len and module the length with 2 if reminder is 0 good if 1 then skip