# 4. Reverse an Array

Question:

Given an array arr of n elements. The task is to reverse the given array. The reversal of array should be in place.
Example 1
Input: n=5, arr = [1,2,3,4,5]

Output: [5,4,3,2,1]

Explanation: The reverse of the array [1,2,3,4,5] is [5,4,3,2,1]
Example 2
Input: n=6, arr = [1,2,1,1,5,1]

Output: [1,5,1,1,2,1]

Explanation: The reverse of the array [1,2,1,1,5,1] is [1,5,1,1,2,1].

Solution:

This one is simple all you have to do is reverse the whole array without creating a new one. That is what it means by in place. 

We can use something called two pointer one pointer we can keep at left first index and one at left last index and we can say that while left is greater then right take the left index and right index and make them reverse

And we can say do + 1 from left and - 1 from right to keep the pointer going.

That’s is super simple.