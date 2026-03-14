# 1. Sum of Array Elements

Question: 

Given an array arr of size n, the task is to find the sum of all the elements in the array.
Example 1
Input: n=5, arr = [1,2,3,4,5]

Output: 15

Explanation: Sum of all the elements is 1+2+3+4+5 = 15
Example 2
Input: n=6, arr = [1,2,1,1,5,1]

Output: 11

Explanation: Sum of all the elements is 1+2+1+1+5+1 = 11

Solution: 

We can take sum as 0 and then each time we go forward we keep adding the next num to sum.

for example :

sum = 0

n = ( 1, 2, 3, 4, 5)

first iteration = sum(0) + arr(1) = 1

second iteration = sum (1) + arr(2) = 3

so on an so forth. 

n is the size of the array so we can use it with range function to go from start to end. And since we are defining sum at starting 0 and each time we go forward we need to take the i of arr.

$$
Formula = SUM = SUM + ARR[I]
$$