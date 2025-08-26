# 498 Diagonal Traversal

## Strategy
Solved the problem using simulation method. Another way to solve the problem is to take diagonal "slices" of the array, and appending the slices depending on whether they are in the correct orientation
Setbacks
 - Designed algorithm to test case
 - didn't account for common cases

## Solution
```python
class Solution(object):
    def findDiagonalOrder(self, mat):
        """
        :type mat: List[List[int]]
        :rtype: List[int]
        """
        i, j = 0, 0
        # direction vectors for traversing matrix
        v_i, v_j = -1, 1
        rows, cols = len(mat), len(mat[0])
        target_length = rows * cols
        ret = []
        while len(ret) < target_length:
            if i >= rows:
                i = rows - 1
                j += 2
                v_i, v_j = -1, 1
            if j >= cols:
                j = cols - 1
                i += 2
                v_i, v_j = 1, -1
            if i < 0:
                i = 0
                v_i, v_j = 1, -1
            if j < 0:
                j = 0
                v_i, v_j = -1, 1
            ret.append(mat[i][j])
            i += v_i
            j += v_j
        return ret

# Test Cases
[[1, 2, 3],
 [4, 5, 6],
 [7, 8, 9]
ret = []
target_len = 3*3 = 6
v_i, v_j = 1, -1
i, j = 2, 0 
ret = [1, 2, 4, 7, 5, 3, 6, 8]
```
