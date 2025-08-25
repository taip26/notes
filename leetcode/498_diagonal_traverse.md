# 498 Diagonal Traversal

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
            if i < 0:
                i = 0
                v_i, v_j = 1, -1

            if i >= rows:
                i = rows - 1
                v_i, v_j = -1, 1

```
