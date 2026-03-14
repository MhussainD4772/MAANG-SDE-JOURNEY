# 3. Check if the Array is Sorted I

Question:

Given an array arr of size n, the task is to check if the given array is sorted in (ascending / Increasing / Non-decreasing) order. If the array is sorted then return True, else return False.
Example 1
Input: n = 5, arr = [1,2,3,4,5]

Output: True

Explanation: The given array is sorted i.e Every element in the array is smaller than or equals to its next values, So the answer is True.
Example 2
Input: n = 5, arr = [5,4,6,7,8]

Output: False

Explanation: The given array is Not sorted i.e Every element in the array is not smaller than or equal to its next values, So the answer is False. Here element 5 is not smaller than or equal to its future elements.

Sol:

we have to find out if the array is increasing in the ascending order meaning from lower to higher. ex: 1 2 3 4 5

So naturally the next number would always be higher than the previous number that is what we need to check.

ex = ARRAY[I] < ARRAY[I+1].

This means 1 < 2, 2<3, 3<4………………

This what we need to write in the optimal solution. what we need to keep in mind is we need to stop the loop iteration at the last second number in the array, in our case at 4 cuz 4< 5 is the last check we need. If let the loop to go till 5 which is last index then it will break cuz there is nothing for us to compare 5 with then ARRAY[I] < ARRAY[I+1] will not work cuz there is no i + 1 available.

The best way to stop our loop from goin out of bonds is to use the range n-1 function what it does it it stops the loop at the last second index and that solves the problem.