# 2. Island Matrix Traversal

Notes gathered from this source: https://www.linkedin.com/pulse/islands-matrix-traversal-design-pattern-manas-rath-shifc/

General strategy - Traverse the matrix, when encountering an "island" use BFS/DFS to find connected components and mark all visited cells. Every time a BFS/DFS is initiated, increment counter

Associated LeetCodes:
 - 200. Number of Islands
   - http://leetcode.com/problems/number-of-islands/description/
