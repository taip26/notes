# Coding Patterns for LeetCode Problems

Transcribed from this article: https://www.designgurus.io/blog/grokking-the-coding-interview-patterns

1. Two Pointers
 - traverse an array from two sides
 - particularly useful when the array is sorted
2. Island or Matrix Traversal
 - traverse a matrix to find islands/coniguous groups of elements
 - useful for grid problems and finding connected groups
3. Slow/Fast Pointers
 - pointers move at different speeds to traverse a data structure
 - useful for linked data structure problem such as cycle detection or middle of linked list
4. Sliding Window
 - use two pointers to cover a range of values while traversing a DS
 - useful in problems requiring contiguous subsets
5. Merge Intervals
 - merge overlapping intervals
 - useful for time intervals, ranges, and sequences
6. Cyclic Sort
 - sorting an array containing numbers in a given range
 - useful in problems where data is in a finite range of natural numbers
7. In-place Reversal of a Linked List
 - useful when you need constant space operations
8. Tree Breadth-First Search
 - used when you need to traverse level-by-level first
9. Tree Depth-First Search
 - used when you need to traverse deeper in the tree first
10. Two Heaps
 - use two heaps to divide a set of numbers into two parts
 - useful when you need to find the median of a set
11. Subsets
 - generate all subsets of a given set
12. Modified Binary Search
 - used when normal binary search doesn't do the trick
13. Top 'K' Elements
 - commonly used in problems containing sorting, searching, and heap
14. Bitwise XOR
 - use when needed to manipulate bits directly
15. Backtracking
 - explore all solutions and backtrack to latest "correct" point when headed down the wrong path
16. 0/1 Knapsack (DP)
 - when items have different values and weights, and we must optimize the values given a constraint
17. Topological Sort (Graph)
 - Hierarchical ordering of a digraph
 - useful for scheduling task problems
18. K-way merge
 - merge k sorted lists
19. Monotonic stack
 - using a stack to maintain an entirely non-increasing or non-decreasing order of elements
 - useful when needing to find the next greater or smaller elements
20. Multithreaded
 - design algorithms that can be executed concurrently
 - useful when subtasks can execute in parallel
