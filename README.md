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
>Given an input array consisting on only 0, 1, and 2, sort the array in a single traversal. You're not allowed to use any sorting function that Python provides.

#### Expected Time Complexity
O(n)

#### Analysis
The numbers, i.e 0, 1, 2, are sorted by moving 0's and 2's to the start and end of the array, respectively. To achieve the target time complexity, we perform a single traversal by maintaining two variables to keep track of the indices of the location for the last index of the 0's and first index of the 2's. Thanks to that, we move in-place 0's and 2's to the target locations efficiently.    


### Problem 5: Autocomplete with Tries
#### Description:
The problem description is included in the problem's notebook.

#### Expected Time Complexity
O(m*n), where m is the number of words and n is the length of the average word.

#### Analysis
Dictionary data structure was employed to represent the children of a Trie node. Another approach would be to use list instead. Dict-based approach has more memory overhead than list, but it is faster (?).

With the implemented approach, it takes O(m*n) time to list all possible suffixes for a prefix. We perform this through a series of steps, which are enumerated below: 
1. The node where the prefix ends is found in O(n) time, where n is the length of the prefix.
2. Once we know the end node of prefix, a recursive DFS method is employed to traverse all suffix nodes. Since all characters will be traversed in the worst case, the time complexity is the expected time complexity, which is O(m*n).



### Problem 6:  
#### Description:
>In this problem, we will look for smallest and largest integer from a list of unsorted integers. The code should run in O(n) time. Do not use Python's inbuilt functions to find min and max.

#### Expected Time Complexity:
O(n)

#### Analysis
Two variables were initialized to the first element of the array to keep track of the minimum and maximum of the given array. These variable values are then updated by comparisons to all elements of an array through a single traversal. Since there is a single traversal and O(1) work are done for each element, the time complexity is O(n).


## Acknowledgements
The project is developed as a part of the Data Structures & Algorithms course offered by Udacity. 