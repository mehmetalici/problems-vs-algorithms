# Problems vs Algorithms
A collection of solutions for various algorithmic questions in the fields of,
* Basic algorithms,
* Sorting algorithms,
* Divide & Conquer algorithms.

Each solution features a test module that involves individual test-cases for huge, invalid and regular inputs.  

## Performance Analysis
Below is an analysis for 7 problems. The problem descriptions are also provided in the respective problem_x.py files, where x is the problem number.

### Problem 1: Finding the Square-Root of an Integer
The problem description reads:
```
Finding the Square Root of an Integer

Find the square root of the integer without using any Python library. You have to find the floor value of the square root.

Examples:
Given number: 16, Answer: 4.

If the given number is 27, the answer would be 5 because sqrt(5) = 5.196 whose floor value is 5.

The expected time complexity is O(log(n))
```

A brute-force approach would be to try out candidates starting from 0 in a sequential manner, i.e 0, 1, 2, 3 ... sqrt(number). However, the complexity of this approach is O(sqrt(n)). 

A more efficient approach is to perform a binary search over the candidate space, which is the range from 0 to the given number. According to that, one half of the candidate space is thrown away based on a comparison of the given number with the square of the candidate lying on the middle. Performing this recursively, we will arrive to the correct answer in O(logn) time.       

### Problem 2


## Acknowledgements
The project is developed as a part of the Data Structures & Algorithms course offered by Udacity. 