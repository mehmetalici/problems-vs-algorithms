# Problems vs Algorithms
A collection of solutions for various algorithmic questions in the following fields:
* Basic algorithms
* Sorting algorithms
* Divide & Conquer algorithms

Each solution features a test module that involves individual test-cases for huge, invalid and regular inputs.  

## Performance Analysis
The analysis for all seven problems are given under this section. 

### Problem 1: Finding the Square-Root of an Integer
#### Description:

>Find the square root of the integer without using any Python library. You have to find the floor value of the square root.
>
>Examples:
>Given number: 16, Answer: 4.
>
>If the given number is 27, the answer would be 5 because sqrt(5) = 5.196 whose floor value is 5.

#### Expected Time Complexity:
O(log(n))
#### Analysis:

A brute-force approach would be to try out candidates starting from 0 in a sequential manner, i.e 0, 1, 2, 3 ... sqrt(number). However, the complexity of this approach is O(sqrt(n)). 

A more efficient approach is to perform a binary search over the candidate space, which is the range from 0 to the given number. According to that, one half of the candidate space is thrown away based on a comparison of the given number with the square of the candidate lying on the middle. Performing this recursively, we arrive to the correct answer in O(logn) time.       

### Problem 2: Search in a Rotated Sorted Array
#### Description:

>You are given a sorted array which is rotated at some random pivot point.
>
>Example: [0,1,2,4,5,6,7] might become [4,5,6,7,0,1,2]
>
>You are given a target value to search. If found in the array return its index, otherwise return -1.
>
>You can assume there are no duplicates in the array and your algorithm's runtime complexity must be in the order of O(log n).
>
>Example:
>
>Input: nums = [4,5,6,7,0,1,2], target = 0, Output: 4


#### Expected Time Complexity:
O(log(n))

#### Analysis:
The solution is threefold: First, we find the pivot index through Divide & Conquer approach. Then, we divide the array by the pivot index to obtain two sorted sub-arrays. Finally, we perform Binary Search in the sub-array whose range covers the given number.

In the first part of the solution, we divide the array from the middle recursively to eventually reach to the pivot index. Checking for the pivot index is O(1), and therefore the recurrence relation is obtained as T(n) = T(n/2) + O(1). The general solution to this relation is, then, O(logn).

Next, dividing the array by the pivot as well as obtaining two sorted arrays are trivially O(1) each.

Finally, Binary Search algorithm takes O(logn) time to find the position of the number in the obtained sorted array.

### Problem 3: Rearrange Array Elements
#### Description
>Rearrange Array Elements so as to form two number such that their sum is maximum. Return these two numbers. You can assume that all array elements are in the range [0, 9]. The number of digits in both the numbers cannot differ by more than 1. You're not allowed to use any sorting function that Python provides.
>
>For example, for [1, 2, 3, 4, 5], possible answers are [531, 42] or [542, 31]. In scenarios such as these when there are more than one possible answers, return any one.
#### Expected Time Complexity:
O(nlog(n))

#### Analysis
The problem is solved through sorting the array and indexing for alternating positions for both numbers. 

For example, let our array `a = [3, 4, 1, 2, 5]`. Then, we apply `a = sorted(a, reverse=True)` to obtain `[5, 4, 3, 2, 1]`. Then indexing for alternating positions for two numbers, we have,

`a[::2] = [5, 3, 1]`, 

and,

`a[1::2] = [4, 2]`, 

to represent the target numbers 531 and 42, respectively. 

Converting them to integers, we return the numbers to complete the solution.      

The time complexity of the solution can be calculated as follows:
1. **Sorting the array**: We applied heapsort by using built-in heaps, and therefore, O(nlogn).
2. **Indexing**: Arrays provides random access at O(1) time for individual elements. Applying to all takes O(n) time.
3. **Converting from list to int**: A str conversion technique was employed for elegancy. This introduces additional overhead but it is not of importance for our problem. The complexity is O(n).

All in all, the complexity is O(nlogn) + O(n) + O(n) = O(nlogn).

The efficiency of the algorithm was demonstrated with tests, namely in problem_3_test.py.

### Problem 4: Dutch National Flag Problem
#### Description:
Given an input array consisting on only 0, 1, and 2, sort the array in a single traversal. You're not allowed to use any sorting function that Python provides.

#### Expected Time Complexity
O(n)

## Acknowledgements
The project is developed as a part of the Data Structures & Algorithms course offered by Udacity. 