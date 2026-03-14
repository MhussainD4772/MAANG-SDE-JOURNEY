# 2. Count of odd numbers in array

Question:

Given an array of n elements. The task is to return the count of the number of odd numbers in the array.
Example 1
Input: n=5, array = [1,2,3,4,5]

Output: 3

Explanation: The three odd elements are (1,3,5).

Example 2
Input: n=6, array = [1,2,1,1,5,1]

Output: 5

Explanation: The five odd elements are one 5 and four 1's.

sol : 

so we need to take the whole array we can just write

for num in arr: this will stop when all elements are over

The formula to find Odd num is :

odd = num % 2 ≠ 0

now that we only need to return the number of odd number we can say

count = 0 

and each time we find an odd number we do count += 1 which will increase count by 1.