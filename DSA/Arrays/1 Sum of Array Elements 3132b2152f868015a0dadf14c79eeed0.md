# 1. Sum of Array Elements

Question: 

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